---
title: Создание задания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: b35af2b6-6594-40d1-9861-4d5dd906048c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7126b01fcaee1a0ab3f7776cc54e6eb0dbe2774d
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798308"
---
# <a name="create-a-job"></a>Create a Job
  В этом разделе описывается создание задания агента SQL Server в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server (SMO).  
  
 Чтобы добавить шаги заданий, расписаний, предупреждений и уведомлений, которые можно отправить операторам, см. ссылки на разделы руководства.  
  
-   **Перед началом:**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Для создания задания используется**  
  
     [SQL Server Management Studio](#SSMSProcedure),  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Управляющие объекты SQL Server](#SMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> ограничения  
  
-   Чтобы создать задание, пользователь должен быть членом одной из предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или членом предопределенной роли сервера **sysadmin** . Задание может быть изменено его владельцем или членом роли **sysadmin** . Дополнительные сведения о предопределенных ролях базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Предопределенные роли базы данных агента SQL Server](sql-server-agent-fixed-database-roles.md).  
  
-   Назначение задания другому имени входа не гарантирует того, что новый владелец обладает достаточными разрешениями для успешного запуска задания.  
  
-   Локальные задания кэшируются локальным агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поэтому внесение в задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] любых изменений неявно вызывает его повторное кэширование. Поскольку агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не помещает задание в кэш до вызова процедуры **sp_add_jobserver** , эффективнее вызывать процедуру **sp_add_jobserver** последней.  
  
###  <a name="Security"></a> безопасность  
  
-   Чтобы изменить владельца задания, необходимо быть системным администратором.  
  
-   Из соображений безопасности изменять определение задания может только его владелец или член роли **sysadmin** . Только члены предопределенной роли сервера **sysadmin** могут предоставлять права владения заданием другим пользователям, а также могут запускать любое задание, независимо от того, кто является его владельцем.  
  
    > [!NOTE]  
    >  Если задать в качестве нового владельца задания пользователя, не являющегося членом предопределенной роли сервера **sysadmin** , а задание выполняет шаги, которым требуются учетные записи-посредники (например, выполнение пакета служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] ), убедитесь в том, что пользователь имеет доступ к этой учетной записи-посреднику, в противном случае задание завершится ошибкой.  
  
####  <a name="Permissions"></a> Разрешения  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-sql-server-agent-job"></a>Создание задания агента SQL Server  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, на котором нужно создать задание агента SQL Server.  
  
2.  Щелкните знак «плюс», чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Задания** и выберите пункт **Создать задание…** .  
  
4.  На странице **Общие** в диалоговом окне **Создание задания** измените общие свойства задания. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания &#40;и страница&#41; "Общие задания](../../integration-services/general-page-of-integration-services-designers-options.md) ".  
  
5.  На странице **Действия** задайте шаги задания. Дополнительные сведения о параметрах, доступных на этой странице, см [. в разделе Свойства задания &#40;: страница&#41; "создание шагов задания".](job-properties-new-job-steps-page.md)  
  
6.  На странице **Расписания** задайте расписания для задания. Дополнительные сведения о параметрах, доступных на этой странице, см [. в разделе Свойства задания &#40;: страница&#41; "Создание расписаний заданий".](job-properties-new-job-schedules-page.md)  
  
7.  На странице **Предупреждения** задайте предупреждения для задания. Дополнительные сведения о параметрах, доступных на этой странице, см [. в разделе Свойства задания &#40;: страница&#41; "Создание предупреждений о задании".](job-properties-new-job-alerts-page.md)  
  
8.  На странице **Уведомления** задайте действия, которые должен выполнять агент [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после завершения задания. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания &#40;: страница&#41;"создание уведомлений о задании"](job-properties-new-job-notifications-page.md).  
  
9. Страница **Цели** используется для управления целевыми серверами в задании. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания &#40;: страница&#41;"создание целевых объектов задания"](job-properties-new-job-targets-page.md).  
  
10. После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-sql-server-agent-job"></a>Создание задания агента SQL Server  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backup';  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе:  
  
-   [sp_add_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [sp_add_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [sp_add_schedule (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [sp_attach_schedule (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [sp_add_jobserver &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
##  <a name="SMOProcedure"></a>Использование управляющие объекты SQL Server  
 **Создание задания агента SQL Server**  
  
 Вызовите метод `Create` класса `Job` на языке программирования по своему выбору (Visual Basic, Visual C# или PowerShell). Пример кода см. в разделе [Планирование автоматических административных задач в агенте SQL Server](sql-server-agent.md).  
  
##  <a name="SSMSProc2"></a>  
