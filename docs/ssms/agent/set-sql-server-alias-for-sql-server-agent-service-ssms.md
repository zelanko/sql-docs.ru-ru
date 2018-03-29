---
title: Настройка псевдонима SQL Server для службы агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- aliases [SQL Server], creating
- SQL Server Agent, aliases
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4a87a6895b4143925823b7899d9c01aa8851be80
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="set-a-sql-server-alias-for-the-sql-server-agent-service-sql-server-management-studio"></a>Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как задать псевдоним [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для использования при соединении с компонентом [!INCLUDE[ssDE](../../includes/ssde_md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. По умолчанию служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] соединяется с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] через именованные каналы по динамическим именам серверов, которые не требуют дополнительной настройки клиента. Необходимо настроить только псевдоним соединения сервера, если не используется установленный по умолчанию сетевой механизм передачи данных или если происходит подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , прослушивающему по альтернативному именованному каналу.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   [Настройка псевдонима SQL Server для службы агента SQL Server в среде SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] не будет работать правильно до тех пор, пока не будет выбран псевдоним, относящийся к местному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] отображается в обозревателе объектов только при наличии у пользователя разрешения на использование узла.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
Дополнительные сведения о разрешениях Windows, необходимых для учетной записи службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , см. в разделах [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей служб Windows](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-set-a-sql-server-alias-for-the-sql-server-agent-service"></a>Настройка псевдонима SQL Server для службы агента SQL Server  
  
1.  В **Обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)] и раскройте его.  
  
2.  Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
3.  В диалоговом окне **Свойства агента SQL***имя_сервера* в разделе **Выберите страницу** выберите **Соединение** и  
  
4.  в поле **Псевдоним локального хоста сервера** введите псевдоним сервера, с которым должен соединяться агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
5.  Нажмите кнопку **ОК**.  
  
