---
title: Назначение задания в категорию заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], assigning
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- SQL Server Agent jobs, assigning
- assigning job to category
ms.assetid: a9ea65a2-1d73-4582-a335-63adeb450cb6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 645953aa9864eb867617dc8aacd71735d978d4c7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177204"
---
# <a name="assign-a-job-to-a-job-category"></a>Назначение задания в категорию заданий
  В этом разделе описано, как назначать категории заданиям агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server.  
  
 Категории заданий помогают упорядочивать их, упрощая их фильтрацию и группирование. Например, все фоновые задания можно поместить в категорию «Обслуживание базы данных». Задание может быть отнесено либо к встроенной категории, либо к одной из созданных пользовательских категорий заданий.  
  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Назначение задания в категорию заданий  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, на котором заданию нужно назначить категорию.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Чтобы развернуть папку **Задания** , щелкните значок «плюс».  
  
4.  Щелкните правой кнопкой мыши задание, которое необходимо изменить, и выберите **Свойства**.  
  
5.  В диалоговом окне **Свойства задания —***имя_задания* в списке **Категория** выберите категорию задания, которую нужно назначить заданию.  
  
6.  Нажмите кнопку **ОК**.  
  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Назначение задания в категорию заданий  
  
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
 **Назначение задания в категорию заданий**  
  
 Используйте `JobCategory` , используя язык программирования, таком как Visual Basic, Visual C# или PowerShell.  
  
  
  
  
