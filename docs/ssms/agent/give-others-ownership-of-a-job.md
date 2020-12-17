---
description: Give Others Ownership of a Job
title: Give Others Ownership of a Job
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 9a1dc39795646c704d8168858475095cd549cb0e
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461365"
---
# <a name="give-others-ownership-of-a-job"></a>Give Others Ownership of a Job
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этой статье описано, как изменить владельца заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Перед началом работы**  [Ограничения](#Restrictions), [Безопасность](#Security)  
  
-   **Для передачи другим пользователям права владения заданием используется:**  
  
    [Среда SQL Server Management Studio](#SSMSProc2)  
  
    [Transact-SQL](#TsqlProc2)  
  
    [Управляющие объекты SQL Server](#SMOProc2)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a>Ограничения  
Чтобы создать задание, пользователь должен быть членом одной из предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или членом предопределенной роли сервера **sysadmin** . Задание может быть изменено его владельцем или членом роли **sysadmin** . Дополнительные сведения о предопределенных ролях базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
Чтобы изменить владельца задания, необходимо быть системным администратором.  
  
Назначение задания другому имени входа не гарантирует того, что новый владелец обладает достаточными разрешениями для успешного запуска задания.  
  
### <a name="security"></a><a name="Security"></a>безопасность  
Из соображений безопасности изменять определение задания может только его владелец или член роли **sysadmin** . Только члены предопределенной роли сервера **sysadmin** могут предоставлять права владения заданием другим пользователям, а также могут запускать любое задание, независимо от того, кто является его владельцем.  
  
> [!NOTE]  
> Если задать в качестве нового владельца задания пользователя, не являющегося членом предопределенной роли сервера **sysadmin** , а задание выполняет шаги, которым требуются учетные записи-посредники (например, выполнение пакета служб [!INCLUDE[ssIS](../../includes/ssis_md.md)] ), убедитесь в том, что пользователь имеет доступ к этой учетной записи-посреднику, в противном случае задание завершится ошибкой.  
  
#### <a name="permissions"></a><a name="Permissions"></a>Permissions  
Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProc2"></a>Использование среды SQL Server Management Studio  
**Передача другим пользователям права владения заданием**  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, **Задания**, затем щелкните правой кнопкой мыши задание и выберите пункт **Свойства**.  
  
3.  В списке **Владелец** выберите имя входа. Чтобы изменить владельца задания, необходимо быть системным администратором.  
  
    Назначение задания другому имени входа не гарантирует того, что новый владелец обладает достаточными разрешениями для успешного запуска задания.  
  
## <a name="using-transact-sql"></a><a name="TsqlProc2"></a>Использование Transact-SQL  
**Передача другим пользователям права владения заданием**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента Database Engine и разверните его.  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса введите следующие инструкции, использующие системную хранимую процедуру [sp_manage_jobs_by_login (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql.md) . В следующем примере производится передача всех заданий от пользователя `danw` пользователю `françoisa`.  
  
    ```  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'françoisa' ;  
    GO  
    ```  
  
## <a name="using-sql-server-management-objects"></a><a name="SMOProc2"></a>Использование управляющих объектов SQL Server  
**Передача другим пользователям права владения заданием**  
  
1.  Вызовите класс **Job** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Пример кода см. в разделе [Планирование автоматических административных задач в агенте SQL Server](../../relational-databases/server-management-objects-smo/tasks/scheduling-automatic-administrative-tasks-in-sql-server-agent.md).  
  
## <a name="see-also"></a>См. также:  
[Реализация заданий](../../ssms/agent/implement-jobs.md)  
[Создание заданий](../../ssms/agent/create-jobs.md)  
