---
title: Запуск, остановка или приостановка службы агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 59821dc7a1a9824d630d174937e04272af014cab
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705132"
---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a>Start, Stop, or Pause the SQL Server Agent Service
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается, как запустить, остановить или перезапустить службу агента SQL Server в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
Службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно настроить для автоматического запуска вместе с операционной системой или запуска вручную для выполнения определенных заданий. Службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно остановить или приостановить, чтобы прекратить выполнение заданий, уведомления операторов и оповещения.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   [Запуск, остановка и перезапуск службы агента SQL Server с использованием среды SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен выполняться в качестве службы. Дополнительные сведения см. в статье [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).  
  
-   Узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображается в обозревателе объектов только при наличии у пользователя разрешения на использование узла.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
Дополнительные сведения о разрешениях Windows, необходимых для учетной записи службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделах [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей служб Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a>Запуск, остановка и перезапуск службы агента SQL Server  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, на котором нужно управлять службой агента SQL Server.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**и выберите команду **Запуск**, **Стоп**или **Перезапуск**.  
  
3.  В диалоговом окне **Контроль учетных записей** нажмите кнопку **Да**.  
  
4.  При появлении запроса о необходимости выполнения действия нажмите кнопку **Да**.  
  
Дополнительные сведения см. в разделе:  
  
-   [Запуск, остановка, приостановка, возобновление и перезапуск ядра СУБД, агента SQL Server и обозревателя SQL Server](http://msdn.microsoft.com/32660a02-e5a1-411a-9e57-7066ca459df6)  
  
-   [Автоматический запуск агента SQL Server (среда SQL Server Management Studio)](../../ssms/agent/autostart-sql-server-agent-sql-server-management-studio.md)  
  
