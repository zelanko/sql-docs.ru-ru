---
title: Установка языка R и функций Python на виртуальной машине Azure
description: Выполняйте анализ данных R и Python и решения машинного обучения на SQL Server виртуальной машине в облаке Azure.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 6f034f3a766e4f82bd1bcfd182f4eee285f7f829
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345044"
---
# <a name="install-sql-server-machine-learning-services-with-r-and-python-on-an-azure-virtual-machine"></a>Установка SQL Server Службы машинного обучения с R и Python на виртуальной машине Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Вы можете установить интеграцию R и Python с Службы машинного обучения на SQL Server виртуальной машине в Azure, устраняя задачи установки и настройки. После развертывания виртуальной машины функции готовы к использованию.
 
Пошаговые инструкции см. в разделе [как подготавливать виртуальную машину Windows SQL Server в портал Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision).

Шаг [Настройка параметров SQL Server](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#3-configure-sql-server-settings) позволяет добавить машинное обучение в экземпляр.

<a name="firewall"></a>

## <a name="unblock-the-firewall"></a>Разблокирование брандмауэра

По умолчанию брандмауэр на виртуальной машине Azure включает правило, которое блокирует доступ к сети для локальных учетных записей пользователей.

Необходимо отключить это правило, чтобы обеспечить доступ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к экземпляру из удаленного клиента обработки и анализа данных.  В противном случае код машинного обучения не может выполняться в контекстах вычислений, использующих рабочую область виртуальной машины.

Чтобы разрешить доступ из удаленных клиентов обработки и анализа данных, выполните следующие действия.

1. На виртуальной машине откройте брандмауэр Windows в режиме повышенной безопасности.
2. Выберите **Правила для исходящих подключений**.
3. Отключите следующее правило:
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
## <a name="enable-odbc-callbacks-for-remote-clients"></a>Включение обратных вызовов ODBC для удаленных клиентов

Если предполагается, что клиенты, вызывающие сервер, должны будут выдавать запросы ODBC в рамках своих решений машинного обучения, необходимо убедиться, что панель запуска может выполнять вызовы ODBC от имени удаленного клиента. 

Для этого необходимо разрешить вход в экземпляр рабочим учетным записям SQL, которые используются панелью запуска. Дополнительные сведения см. в разделе [Добавление SQLRUserGroup в качестве пользователя базы данных](../security/create-a-login-for-sqlrusergroup.md).

<a name="network"></a>

## <a name="add-network-protocols"></a>Добавление сетевых протоколов

+ Включите именованные каналы.
  
  Службы [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] используют протокол именованных каналов для подключений между компьютерами клиента и сервера, а также для некоторых внутренних подключений. Если именованные каналы не включены, вам необходимо установить и включить их на виртуальной машине Azure и любом клиенте обработки и анализа данных, который подключен к серверу.
  
+ Включите протокол TCP/IP.

  Для подключения замыкания на себя требуется протокол TCP/IP. Если возникает ошибка "DBNETLIB; SQL Server не существует или доступ запрещен ", включите TCP/IP на виртуальной машине, которая поддерживает данный экземпляр.