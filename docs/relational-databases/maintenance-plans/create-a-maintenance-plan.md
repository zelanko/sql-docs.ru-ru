---
title: "Создание плана обслуживания | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "планы обслуживания [SQL Server], создание"
ms.assetid: a945cb65-ba7a-42f4-bbd9-6ec675745523
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Создание плана обслуживания
  В этом разделе описывается создание плана обслуживания одного или нескольких серверов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]можно создавать планы обслуживания двумя способами: с помощью мастера планов обслуживания или рабочей области конструирования. Мастер лучше подходит для создания простых планов обслуживания, а конструктор позволяет использовать расширенные возможности рабочего процесса с потоком операций.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
     
     [Предварительные требования](#Prerequisite)  
  
     [безопасность](#Security)  
  
-   **Для создания плана обслуживания используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 Для создания многосерверного плана обслуживания необходимо настроить многосерверную среду, содержащую один главный сервер и один или несколько целевых серверов. План многосерверного обслуживания необходимо создать и хранить на главном сервере. На целевых серверах эти планы можно просматривать, но нельзя хранить. 
 
###  <a name="Prerequisite"></a> Предварительные требования  
[Параметр конфигурации сервера Agent XPs](../../database-engine/configure-windows/agent-xps-server-configuration-option.md) должен быть включен.
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Для создания планов обслуживания и работы с ними пользователь должен быть членом предопределенной роли сервера **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Создание плана обслуживания с помощью мастера планов обслуживания  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть сервер, где нужно создать план обслуживания.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните правой кнопкой мыши папку **Планы обслуживания** и выберите пункт **Мастер планов обслуживания**.  
  
4.  Выполните предлагаемые мастером шаги, чтобы создать план обслуживания. Дополнительные сведения см. в статье [Use the Maintenance Plan Wizard](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md).  
  
#### Создание планов обслуживания при помощи области конструктора  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть сервер, где нужно создать план обслуживания.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните правой кнопкой мыши папку **Планы обслуживания** и выберите пункт **Создать план обслуживания**.  
  
4.  Создайте план обслуживания, выполнив действия, описанные в разделе [Создание планов обслуживания (область конструктора планов обслуживания)](../../relational-databases/maintenance-plans/create-a-maintenance-plan-maintenance-plan-design-surface.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Создание плана обслуживания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb;  
    GO  
    --  Adds a new job, executed by the SQL Server Agent service, called "HistoryCleanupTask_1".  
    EXEC dbo.sp_add_job  
       @job_name = N'HistoryCleanupTask_1',   
       @enabled = 1,   
       @description = N'Clean up old task history' ;   
    GO  
    -- Adds a job step for reorganizing all of the indexes in the HumanResources.Employee table to the HistoryCleanupTask_1 job.   
    EXEC dbo.sp_add_jobstep  
        @job_name = N'HistoryCleanupTask_1',   
        @step_name = N'Reorganize all indexes on HumanResources.Employee table',   
        @subsystem = N'TSQL',   
        @command = N'USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_LoginID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_rowguid ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX PK_Employee_BusinessEntityID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    ',   
        @retry_attempts = 5,   
        @retry_interval = 5 ;   
    GO  
    -- Creates a schedule named RunOnce that executes every day when the time on the server is 23:00.   
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',   
        @freq_type = 4,   
        @freq_interval = 1,   
        @active_start_time = 233000 ;   
    GO  
    -- Attaches the RunOnce schedule to the job HistoryCleanupTask_1.   
    EXEC sp_attach_schedule  
       @job_name = N'HistoryCleanupTask_1'  
       @schedule_name = N'RunOnce' ;   
    GO  
  
    ```  
  
 Дополнительные сведения см. в разделе:  
  
-   [sp_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)  
  
-   [sp_add_jobstep (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
-   [sp_add_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)  
  
-   [sp_attach_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  