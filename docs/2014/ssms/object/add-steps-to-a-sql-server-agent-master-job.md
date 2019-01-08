---
title: Добавление шагов к главному заданию агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9cc1e8ab-7ddc-427b-859e-203aa7e24642
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 18c4af67230726d831c2c192a782135f9afe3743
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52822688"
---
# <a name="add-steps-to-a-sql-server-agent-master-job"></a>Add Steps to a SQL Server Agent Master Job
  В этом разделе описывается добавление шагов в главное задание агента SQL Server в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Добавление шагов в главное задание агента SQL Server с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 Главное задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может быть ориентировано как на локальный, так и на удаленный сервер.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Если пользователь не является членом предопределенной роли сервера **sysadmin** , он может изменять только свои собственные задания. Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../agent/implement-sql-server-agent-security.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-add-steps-to-a-sql-server-agent-master-job"></a>Добавление шагов в главное задание агента SQL Server  
  
1.  В **обозревателе объектов** щелкните знак «плюс», чтобы развернуть сервер, содержащий задание, в которое нужно добавить шаги.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Чтобы развернуть папку **Задания** , щелкните значок «плюс».  
  
4.  Щелкните правой кнопкой мыши задание, в которое нужно добавить шаги, и выберите пункт **Свойства**.  
  
5.  В диалоговом окне **Свойства задания —** _имя_задания_ в разделе **Выберите страницу** выберите пункт **Шаги**. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [свойства задания: новое задание &#40;страница "шаги"&#41;](../agent/job-properties-new-job-steps-page.md).  

6.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-add-steps-to-a-sql-server-agent-master-job"></a>Добавление шагов в главное задание агента SQL Server  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- creates a job step that changes database access to read-only for the Sales database.   
    -- specifies 5 retry attempts, with each retry to occur after a 5 minute wait.   
    -- assumes that the Weekly Sales Data Backup job already exists  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).  
  
  
