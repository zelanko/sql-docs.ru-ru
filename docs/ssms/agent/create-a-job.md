---
title: Создание задания
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: b35af2b6-6594-40d1-9861-4d5dd906048c
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 41e8f5b262b5018bbbc847dc57c27204783e6f32
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75245930"
---
# <a name="create-a-job"></a>Создание задания
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается создание задания агента SQL Server в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server (SMO).  
  
Чтобы добавить шаги заданий, расписаний, предупреждений и уведомлений, которые можно отправить операторам, см. ссылки на разделы руководства.  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [Безопасность](#Security)  
  
-   **Для создания задания используется**  
  
    [SQL Server Management Studio](#SSMSProcedure),  
  
    [Transact-SQL](#TsqlProcedure)  
  
    [Управляющие объекты SQL Server](#SMOProcedure)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a>Ограничения  
  
-   Чтобы создать задание, пользователь должен быть членом одной из предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или членом предопределенной роли сервера **sysadmin** . Задание может быть изменено его владельцем или членом роли **sysadmin** . Дополнительные сведения о предопределенных ролях базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
-   Назначение задания другому имени входа не гарантирует того, что новый владелец обладает достаточными разрешениями для успешного запуска задания.  
  
-   Локальные задания кэшируются локальным агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поэтому внесение в задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] любых изменений неявно вызывает его повторное кэширование. Поскольку агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не помещает задание в кэш до вызова процедуры **sp_add_jobserver** , эффективнее вызывать процедуру **sp_add_jobserver** последней.  
  
### <a name="security"></a><a name="Security"></a>безопасность  
  
-   Чтобы изменить владельца задания, необходимо быть системным администратором.  
  
-   Из соображений безопасности изменять определение задания может только его владелец или член роли **sysadmin** . Только члены предопределенной роли сервера **sysadmin** могут предоставлять права владения заданием другим пользователям, а также могут запускать любое задание, независимо от того, кто является его владельцем.  
  
    > [!NOTE]  
    > Если задать в качестве нового владельца задания пользователя, не являющегося членом предопределенной роли сервера **sysadmin** , а задание выполняет шаги, которым требуются учетные записи-посредники (например, выполнение пакета служб [!INCLUDE[ssIS](../../includes/ssis_md.md)] ), убедитесь в том, что пользователь имеет доступ к этой учетной записи-посреднику, в противном случае задание завершится ошибкой.  
  
#### <a name="permissions"></a><a name="Permissions"></a>Permissions  
Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-sql-server-agent-job"></a>Создание задания агента SQL Server  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, на котором нужно создать задание агента SQL Server.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Задания** и выберите пункт **Создать задание…** .  
  
4.  На странице **Общие** в диалоговом окне **Создание задания** измените общие свойства задания. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания — создание задания (страница "Общие")](../../ssms/agent/job-properties-new-job-general-page.md)  
  
5.  На странице **Действия** задайте шаги задания. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания — создание задания (страница "Шаги")](../../ssms/agent/job-properties-new-job-steps-page.md)  
  
6.  На странице **Расписания** задайте расписания для задания. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания — создание задания (страница "Расписания")](../../ssms/agent/job-properties-new-job-schedules-page.md)  
  
7.  На странице **Предупреждения** задайте предупреждения для задания. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания — создание задания (страница "Предупреждения")](../../ssms/agent/job-properties-new-job-alerts-page.md)  
  
8.  На странице **Уведомления** задайте действия, которые должен выполнять агент [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после завершения задания. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания — создание задания (страница "Уведомления")](../../ssms/agent/job-properties-new-job-notifications-page.md).  
  
9. Страница **Цели** используется для управления целевыми серверами в задании. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания — создание задания (страница "Цели")](../../ssms/agent/job-properties-new-job-targets-page.md).  
  
10. После завершения нажмите кнопку **ОК**.  
  
## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-create-a-sql-server-agent-job"></a>Создание задания агента SQL Server  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
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
  
-   [sp_add_job (Transact-SQL)](https://msdn.microsoft.com/6ca8fe2c-7b1c-4b59-b4c7-e3b7485df274)  
  
-   [sp_add_jobstep (Transact-SQL)](https://msdn.microsoft.com/97900032-523d-49d6-9865-2734fba1c755)  
  
-   [sp_add_schedule (Transact-SQL)](https://msdn.microsoft.com/9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7)  
  
-   [sp_attach_schedule (Transact-SQL)](https://msdn.microsoft.com/80c80eaf-cf23-4ed8-b8dd-65fe59830dd1)  
  
-   [sp_add_jobserver (Transact-SQL)](https://msdn.microsoft.com/485252cc-0081-490a-9bd1-cbbd68eea286)  
  
## <a name="using-sql-server-management-objects"></a><a name="SMOProcedure"></a>Использование управляющих объектов SQL Server  
**Создание задания агента SQL Server**  
  
Вызовите метод **Create** класса **Job** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Пример кода см. в разделе [Планирование автоматических административных задач в агенте SQL Server](../../relational-databases/server-management-objects-smo/tasks/scheduling-automatic-administrative-tasks-in-sql-server-agent.md).  
  
