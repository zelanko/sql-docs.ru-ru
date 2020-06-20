---
title: Создание плана обслуживания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- maintenance plans [SQL Server], creating
ms.assetid: a945cb65-ba7a-42f4-bbd9-6ec675745523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3df0c1cd06427deb051a9c4214d03084b44c6f9b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85024680"
---
# <a name="create-a-maintenance-plan"></a>Создание плана обслуживания
  В этом разделе описывается создание плана обслуживания одного или нескольких серверов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]можно создавать планы обслуживания двумя способами: с помощью мастера планов обслуживания или рабочей области конструирования. Мастер лучше подходит для создания простых планов обслуживания, а конструктор позволяет использовать расширенные возможности рабочего процесса с потоком операций.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для создания плана обслуживания используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Для создания многосерверного плана обслуживания необходимо настроить многосерверную среду, содержащую один главный сервер и один или несколько целевых серверов. План многосерверного обслуживания необходимо создать и хранить на главном сервере. На целевых серверах эти планы можно просматривать, но нельзя хранить.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для создания планов обслуживания или управления ими необходимо быть членом предопределенной роли сервера **sysadmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-maintenance-plan-using-the-maintenance-plan-wizard"></a>Создание плана обслуживания с помощью мастера планов обслуживания  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть сервер, где нужно создать план обслуживания.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните правой кнопкой мыши папку **Планы обслуживания** и выберите пункт **Мастер планов обслуживания**.  
  
4.  Выполните предлагаемые мастером шаги, чтобы создать план обслуживания. Дополнительные сведения см. в статье [Use the Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md).  
  
#### <a name="to-create-a-maintenance-plan-using-the-design-surface"></a>Создание планов обслуживания при помощи области конструктора  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть сервер, где нужно создать план обслуживания.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните правой кнопкой мыши папку **Планы обслуживания** и выберите команду **Создать план обслуживания**.  
  
4.  Создайте план обслуживания, выполнив действия, описанные в разделе [Создание планов обслуживания (область конструктора планов обслуживания)](create-a-maintenance-plan-maintenance-plan-design-surface.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-maintenance-plan"></a>Создание плана обслуживания  
  
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
  
-   [sp_add_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [sp_add_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [sp_add_schedule (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [sp_attach_schedule (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
  
