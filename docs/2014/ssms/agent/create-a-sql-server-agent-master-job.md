---
title: Создание задания агента главного сервера SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], master jobs
- jobs [SQL Server Agent], creating
- master SQL Server Agent job [SQL Server]
ms.assetid: c12ab23f-d7ee-43a5-8cd2-0a9121292bcd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e80d5790f78c83a8a1ff3059e12e0946e206c060
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211451"
---
# <a name="create-a-sql-server-agent-master-job"></a>Создание задания агента главного сервера SQL Server
  В этом разделе описывается создание задания [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] главного агента [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] в с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или. [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Изменения задания агента главного сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны распространяться на все связанные целевые серверы. Так как целевые серверы изначально не загружают задание, пока не указаны их цели, [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует завершить все шаги и расписания индивидуального задания перед указанием каких-либо целевых серверов. Иначе необходимо будет вручную запросить повторное скачивание измененного задания целевыми серверами либо с помощью хранимой процедуры **sp_post_msx_operation** , либо путем изменения задания в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [sp_post_msx_operation &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) или [Изменение задания](modify-a-job.md).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Распределенные задания, имеющие связанные с учетной записью-посредником шаги, выполняются в контексте учетной записи-посредника на целевом сервере. Убедитесь в том, что выполняются нижеприведенные условия, либо в том, что шаги заданий, связанные с учетной записью-посредником, не будут загружаться с главного сервера на целевой:  
  
-   В подразделе реестра **\ HKEY_LOCAL_MACHINE \софтваре\микрософт\микрософт\\<SQL Server*instance_name*> \SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) установлено значение 1 (true). По умолчанию для него задается значение 0 (false).  
  
-   На целевом сервере есть учетная запись-посредник. Ее имя совпадает с именем учетной записи-посредника на главном сервере, под которой выполняется шаг задания.  
  
 Если шаги задания, использующие учетную запись-посредник, завершаются с ошибками при скачивании с главного сервера на целевой, то в столбце **error_message** в таблице **sysdownloadlist** базы данных **msdb** появятся следующие сообщения об ошибках:  
  
-   «Для этого шага задания необходима учетная запись-посредник, однако проверка совпадения учетной записи-посредника на целевом сервере отключена.» Чтобы устранить эту ошибку, задайте для раздела реестра **AllowDownloadedJobsToMatchProxyName** значение 1.  
  
-   «Учетная запись-посредник не найдена.» Чтобы устранить эту ошибку, убедитесь, что на целевом сервере есть учетная запись-посредник, имя которой совпадает с именем посреднической учетной записи на главном сервере, под которой выполняется шаг задания.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a>Создание задания агента главного сервера SQL Server  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, на котором нужно создать задание агента SQL Server.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Задания** и выберите пункт **Создать задание…**.  
  
4.  На странице **Общие** в диалоговом окне **Создание задания** измените общие свойства задания. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания и создание задания &#40;Общие страницы&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
5.  На странице **Действия** задайте шаги задания. Дополнительные сведения о параметрах, доступных на этой странице, см [. в разделе Свойства задания: страница "Создание задания &#40;шаги"&#41;](job-properties-new-job-steps-page.md)  
  
6.  На странице **Расписания** задайте расписания для задания. Дополнительные сведения о параметрах, доступных на этой странице, см [. в разделе Свойства задания: создание задания &#40;расписания&#41;](job-properties-new-job-schedules-page.md)  
  
7.  На странице **Предупреждения** задайте предупреждения для задания. Дополнительные сведения о параметрах, доступных на этой странице, см [. в разделе Свойства задания: создание &#40;оповещений о задании&#41;](job-properties-new-job-alerts-page.md)  
  
8.  На странице **Уведомления** задайте действия, которые должен выполнять агент [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после завершения задания. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания: создание &#40;уведомлений&#41;странице "сведения о ](job-properties-new-job-notifications-page.md)задании".  
  
9. Страница **Цели** используется для управления целевыми серверами в задании. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания: страница создание &#40;целевые объекты задания&#41;](job-properties-new-job-targets-page.md).  
  
10. По окончании нажмите кнопку **ОК**.  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a>Создание задания агента главного сервера SQL Server  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb ;  
    GO  
    -- Adds a new job executed by the SQLServerAgent service called 'Weekly Sales Data Backup'  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    -- Adds a step (operation) to the 'Weekly Sales Data Backup' job.  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    -- Creates a schedule called RunOnce  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    -- Sets the 'RunOnce' schedule to the "Weekly Sales Data Backup' Job  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2  
    -- assumes that SEATTLE2 is registered as a target server for the current instance.  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 Дополнительная информация:  
  
-   [sp_add_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [sp_add_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [sp_add_schedule (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [sp_attach_schedule (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  

  
  
