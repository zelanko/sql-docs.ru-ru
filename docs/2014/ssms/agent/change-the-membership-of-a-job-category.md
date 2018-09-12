---
title: Изменение состава категории заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2ab51f2eac94875b510d9f998120e47fdd9b6180
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43814000"
---
# <a name="change-the-membership-of-a-job-category"></a>Change the Membership of a Job Category
  В этом разделе описывается изменение членства категории заданий в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или управляющих объектов SQL Server.  
  
 Категории заданий помогают упорядочивать их, упрощая их фильтрацию и группирование. Вы можете создавать собственные категории заданий. Также можно изменять состав категорий заданий агента SQL Server.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Для изменения состава категории заданий используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Изменение состава категории заданий  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, на котором нужно изменить категорию заданий.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Задания** и выберите пункт **Управление категориями заданий**.  
  
4.  В диалоговом окне **Управление категориями заданий***имя_сервера* выберите категорию заданий, которую нужно изменить, и нажмите кнопку **Просмотреть задания**.  
  
5.  Установите флажок **Отображать все задания** .  
  
6.  Чтобы добавить задание в категорию, в основной сетке установите флажок в столбце **Выбор** , соответствующий заданию. Чтобы удалить задание из категории, снимите флажок. После завершения нажмите кнопку **ОК**.  
  
7.  Закройте диалоговое окно **Управление категориями заданий***имя_сервера*.  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Изменение состава категории заданий  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
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
  
 Дополнительные сведения см. в разделе [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).  
  
##  <a name="SMO"></a> Использование управляющих объектов SQL Server  
 **Изменение состава категории заданий**  
  
 Используйте `JobCategory` , используя язык программирования, таком как Visual Basic, Visual C# или PowerShell.  
  
  
