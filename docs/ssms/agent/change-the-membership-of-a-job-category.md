---
title: "Изменение состава категории заданий | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 60a46ce2fd6a12645870d9a025b82e4ab23762a9
ms.lasthandoff: 04/11/2017

---
# <a name="change-the-membership-of-a-job-category"></a>Change the Membership of a Job Category
В этом разделе описывается изменение членства категории заданий в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)]или управляющих объектов SQL Server.  
  
Категории заданий помогают упорядочивать их, упрощая их фильтрацию и группирование. Вы можете создавать собственные категории заданий. Также можно изменять состав категорий заданий агента SQL Server.  
  
**В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
    [безопасность](#Security)  
  
-   **Для изменения состава категории заданий используется:**  
  
    [Среда Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Изменение состава категории заданий  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, на котором нужно изменить категорию заданий.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Задания** и выберите пункт **Управление категориями заданий**.  
  
4.  В диалоговом окне **Управление категориями заданий***имя_сервера* выберите категорию заданий, которую нужно изменить, и нажмите кнопку **Просмотреть задания**.  
  
5.  Установите флажок **Отображать все задания** .  
  
6.  Чтобы добавить задание в категорию, в основной сетке установите флажок в столбце **Выбор** , соответствующий заданию. Чтобы удалить задание из категории, снимите флажок. После завершения нажмите кнопку **ОК**.  
  
7.  Закройте диалоговое окно **Управление категориями заданий***имя_сервера* .  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Изменение состава категории заданий  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_update_job (Transact-SQL)](http://msdn.microsoft.com/en-us/cbdfea38-9e42-47f3-8fc8-5978b82e2623).  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
**Изменение состава категории заданий**  
  
Воспользуйтесь классом **JobCategory** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell.  
  

