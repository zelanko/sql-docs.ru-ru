---
title: Установка на виртуальной машине Azure
description: Выполняйте решения для обработки и анализа данных на языках R и Python в среде Служб машинного обучения SQL Server, развернутой на виртуальной машине в облаке Azure.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 01/02/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7516d23ade89b4d82858c209f46498207f06cde5
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882128"
---
# <a name="install-sql-server-machine-learning-services-with-python-and-r-on-an-azure-virtual-machine"></a>Установка Служб машинного обучения SQL Server с поддержкой R и Python на виртуальной машине Azure
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

Сведения об установке Python и R для Служб машинного обучения SQL Server на виртуальной машине в Azure. Этот процесс избавляет от задач установки и конфигурации Служб машинного обучения.

Выполните следующие действия.

1. Подготовка виртуальной машины SQL Server в Azure
1. Снятие блокировки брандмауэра
1. Включение обратных вызовов ODBC для удаленных клиентов
1. Добавление сетевых протоколов

## <a name="provision-sql-server-virtual-machine-in-azure"></a>Подготовка виртуальной машины SQL Server в Azure

Пошаговые инструкции см. в статье [Подготовка виртуальной машины Windows SQL Server на портале Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision). 

Вы добавляете Службы машинного обучения в экземпляр на шаге [Настройка параметров SQL Server](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#3-configure-sql-server-settings).

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
  
+ Включение TCP/IP

  Протокол TCP/IP требуется для замыкания соединений. Если появится ошибка "DBNETLIB; SQL Server не существует или доступ запрещен", включите протокол TCP/IP на виртуальной машине, поддерживающей экземпляр.