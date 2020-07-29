---
title: Назначение задания в категорию заданий
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], assigning
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- SQL Server Agent jobs, assigning
- assigning job to category
ms.assetid: a9ea65a2-1d73-4582-a335-63adeb450cb6
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 06/03/2020
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 70adaeed56ef0d209f83ba16d74f476a4e3f7d75
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755319"
---
# <a name="assign-a-job-to-a-job-category"></a>Назначение задания в категорию заданий

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этой статье описано, как назначать категории заданиям агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server.  
  
Категории заданий помогают упорядочивать их, упрощая их фильтрацию и группирование. Например, все фоновые задания можно поместить в категорию «Обслуживание базы данных». Задание может быть отнесено либо к встроенной категории, либо к одной из созданных пользовательских категорий заданий.  

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="security"></a><a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Назначение задания в категорию заданий  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, на котором заданию нужно назначить категорию.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Чтобы развернуть папку **Задания** , щелкните значок «плюс».  
  
4.  Щелкните правой кнопкой мыши задание, которое необходимо изменить, и выберите **Свойства**.  
  
5.  В диалоговом окне **Свойства задания —** _имя\_задания_ в списке **Категория** выберите категорию задания, которую нужно назначить заданию.  
  
6.  Нажмите кнопку **ОК**.  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Назначение задания в категорию заданий  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_update_job (Transact-SQL)](https://msdn.microsoft.com/cbdfea38-9e42-47f3-8fc8-5978b82e2623).  
  
## <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющих объектов SQL Server  
**Назначение задания в категорию заданий**  
  
Воспользуйтесь классом **JobCategory** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell.  
  
