---
title: Создание категории заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 07b942ad64043f93f014a54246b42ef5375ade97
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72798283"
---
# <a name="create-a-job-category"></a>Создание категории заданий
  В данном разделе описывается процесс создания категории заданий в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент предоставляет встроенные категории заданий, для которых можно назначать задания, кроме того, можно создать категорию задания и назначить ей задания. Категории заданий помогают упорядочивать их, упрощая их фильтрацию и группирование. Например, все фоновые задания можно поместить в категорию «Обслуживание базы данных». Можно создавать и собственные категории заданий.  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Многосерверные категории существуют только на главном сервере. На нем по умолчанию имеется только одна категория заданий: [**Без категорий (многосерверный)**]. Если загружается многосерверное задание, его категория на целевом сервере меняется на **Задания от главного сервера** .  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-job-category"></a>Создание категории заданий  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, на котором нужно создать категорию заданий.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Задания** и выберите пункт **Управление категориями заданий**.  
  
4.  В диалоговом окне **Управление категориями заданий**_server_name_ нажмите кнопку **добавить**.  
  
5.  В поле **Имя** нового диалогового окна введите имя новой категории заданий.  
  
6.  Установите флажок **Отображать все задания** . Выберите одно или несколько заданий для новой категории, установив флажки рядом с соответствующими заданиями.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  В диалоговом окне **Управление категориями заданий**_server_name_ нажмите кнопку **Обновить** , чтобы убедиться, что новая категория заданий активна. Если все выглядит так, как нужно, закройте это диалоговое окно.  
  
 Дополнительные сведения об этих диалоговых окнах см. в разделе [категории заданий: Управление категориями](job-categories-manage-job-categories.md) заданий и [свойствами категорий заданий и создание категории заданий](job-categories-properties-new-job-category.md).  

##  <a name="using-transact-sql"></a><a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-job-category"></a>Создание категории заданий  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_add_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql).  

##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющие объекты SQL Server  
 **Создание категории заданий**  
  
 Вызовите класс `JobCategory` с использованием выбранного языка программирования, например Visual Basic, Visual C# или PowerShell. Пример кода см. в разделе [Планирование автоматических административных задач в агенте SQL Server](sql-server-agent.md).  
