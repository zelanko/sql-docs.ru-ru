---
title: Установка на виртуальной машине Azure
description: Выполняйте обработку и анализ данных с помощью R и Python и запускайте решения машинного обучения на виртуальной машине SQL Server в облаке Azure.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: aeec25b561822e8083b89e03f0f7e74f40660f7b
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727615"
---
# <a name="install-sql-server-machine-learning-services-with-r-and-python-on-an-azure-virtual-machine"></a>Установка служб машинного обучения SQL Server с R и Python на виртуальной машине Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Вы можете установить интеграцию R и Python со Службами машинного обучения на виртуальную машину SQL Server в Azure, и в этом случае вам не придется выполнять установку и настройку. После развертывания виртуальной машины функции готовы к использованию.
 
Пошаговые инструкции см. в статье [Подготовка виртуальной машины Windows SQL Server на портале Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision).

Вы добавляете машинное обучение в свой экземпляр на шаге [Настройка параметров SQL Server](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#3-configure-sql-server-settings).

<a name="firewall"></a>

## <a name="unblock-the-firewall"></a>Снятие блокировки брандмауэра

По умолчанию брандмауэр на виртуальной машине Azure использует правило, которое блокирует сетевой доступ для локальных учетных записей пользователя.

Чтобы получить доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленного клиента обработки и анализа данных, необходимо отключить это правило.  В противном случае код машинного обучения не сможет выполняться в контекстах вычислений, использующих рабочую область виртуальной машины.

Чтобы разрешить доступ из удаленных клиентов для обработки и анализа данных, выполните следующие действия:

1. На виртуальной машине откройте брандмауэр Windows в режиме повышенной безопасности.
2. Выберите **Правила для исходящих подключений**.
3. Отключите следующее правило:
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
## <a name="enable-odbc-callbacks-for-remote-clients"></a>Включение обратных вызовов ODBC для удаленных клиентов

Если вы хотите, чтобы клиенты R, вызывающие сервер, могли отправлять запросы ODBC в рамках своих решений машинного обучения, вызовы ODBC на панели запуска должны выполняться от имени удаленного клиента. 

Для этого необходимо разрешить вход в экземпляр рабочим учетным записям SQL, которые используются панелью запуска. Дополнительные сведения см. в статье [Добавление SQLRUserGroup в качестве пользователя базы данных](../security/create-a-login-for-sqlrusergroup.md).

<a name="network"></a>

## <a name="add-network-protocols"></a>Добавление сетевых протоколов

+ Включите именованные каналы.
  
  Службы [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] используют протокол именованных каналов для подключений между компьютерами клиента и сервера, а также для некоторых внутренних подключений. Если именованные каналы не включены, вам необходимо установить и включить их на виртуальной машине Azure и любом клиенте обработки и анализа данных, который подключен к серверу.
  
+ Включите протокол TCP/IP.

  Протокол TCP/IP требуется для замыкания соединений. Если появится ошибка "DBNETLIB; SQL Server не существует или доступ запрещен", включите протокол TCP/IP на виртуальной машине, поддерживающей экземпляр.