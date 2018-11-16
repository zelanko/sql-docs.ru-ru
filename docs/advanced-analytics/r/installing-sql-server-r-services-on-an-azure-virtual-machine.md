---
title: Установите службы машинного обучения SQL Server с R и Python на виртуальной машине Azure | Документация Майкрософт
description: Запустите обработки и анализа данных R и Python и машинного обучения решения на виртуальной машине SQL Server в облаке Azure.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e416b99c3d4597cb2fe9346819184be43cd98402
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2018
ms.locfileid: "51512699"
---
# <a name="install-sql-server-machine-learning-services-with-r-and-python-on-an-azure-virtual-machine"></a>Установите службы машинного обучения SQL Server с R и Python на виртуальной машине Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Интеграция R и Python можно установить с помощью служб машинного обучения на виртуальной машине SQL Server в Azure, устраняя задачи установки и настройки. После развертывания виртуальной машины функции готовы к использованию.
 
Пошаговые инструкции см. в разделе [как Подготовка виртуальной машины Windows SQL Server на портале Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision).

[Параметры настройки SQL server](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#4-configure-sql-server-settings) делом, где добавить машинного обучения в вашем экземпляре.

<a name="firewall"></a>

## <a name="unblock-the-firewall"></a>Разблокирование брандмауэра

По умолчанию брандмауэр на виртуальной машине Azure использует правило, которое блокирует сетевой доступ для учетных записей локальных пользователей.

Необходимо отключить это правило, чтобы вы могли обращаться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр из удаленного клиента обработки и анализа.  В противном случае машинного кода не удается выполнить в контексте вычислений, использующих рабочее пространство виртуальной машины.

Чтобы включить доступ к удаленным данным обработки и анализа клиентам:

1. На виртуальной машине откройте брандмауэр Windows в режиме повышенной безопасности.
2. Выберите **Правила для исходящих подключений**.
3. Отключите следующее правило:
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
## <a name="enable-odbc-callbacks-for-remote-clients"></a>Включение обратных вызовов ODBC для удаленных клиентов

Если предполагается, что клиенты, осуществляющие вызов сервера будет необходимо отправлять запросы ODBC как часть своих решений машинного обучения, необходимо убедиться, что панель запуска может выполнять вызовы ODBC от имени удаленного клиента. 

Для этого необходимо разрешить вход в экземпляр рабочим учетным записям SQL, которые используются панелью запуска. Дополнительные сведения см. в разделе [Добавление SQLRUserGroup в качестве пользователя базы данных](../security/add-sqlrusergroup-to-database.md).

<a name="network"></a>

## <a name="add-network-protocols"></a>Добавление сетевых протоколов

+ Включите именованные каналы.
  
  Службы [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] используют протокол именованных каналов для подключений между компьютерами клиента и сервера, а также для некоторых внутренних подключений. Если именованные каналы не включены, вам необходимо установить и включить их на виртуальной машине Azure и любом клиенте обработки и анализа данных, который подключен к серверу.
  
+ Включите протокол TCP/IP.

  Он требуется для замыкания соединений. Если появляется ошибка «DBNETLIB; SQL Server не существует или доступ запрещен», включить TCP/IP на виртуальной машине, поддерживающей экземпляр.