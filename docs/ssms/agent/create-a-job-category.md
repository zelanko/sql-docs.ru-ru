---
title: Создание категории заданий | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5451fd6edf7d84b8e939f0f62ae6fcebf6e2f069
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67688576"
---
# <a name="create-a-job-category"></a>Создание категории заданий
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В данном разделе описывается процесс создания категории заданий в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент предоставляет встроенные категории заданий, для которых можно назначать задания, кроме того, можно создать категорию задания и назначить ей задания. Категории заданий помогают упорядочивать их, упрощая их фильтрацию и группирование. Например, все фоновые задания можно поместить в категорию «Обслуживание базы данных». Можно создавать и собственные категории заданий.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Для создания категории заданий используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
Многосерверные категории существуют только на главном сервере. На нем по умолчанию имеется только одна категория заданий: [**Без категорий (многосерверный)** ]. Если загружается многосерверное задание, его категория на целевом сервере меняется на **Задания от главного сервера** .  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-job-category"></a>Создание категории заданий  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, на котором нужно создать категорию заданий.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Задания** и выберите пункт **Управление категориями заданий**.  
  
4.  В диалоговом окне **Управление категориями заданий**_имя_сервера_ нажмите кнопку **Добавить**.  
  
5.  В поле **Имя** нового диалогового окна введите имя новой категории заданий.  
  
6.  Установите флажок **Отображать все задания** . Выберите одно или несколько заданий для новой категории, установив флажки рядом с соответствующими заданиями.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  В диалоговом окне **Управление категориями заданий**_имя_сервера_ нажмите кнопку **Обновить** , чтобы убедиться в активности новой категории заданий. Если все выглядит так, как нужно, закройте это диалоговое окно.  
  
Дополнительные сведения о доступе к этим диалоговым окнам см. в разделах [Категории заданий — управление категориями заданий](../../ssms/agent/job-categories-manage-job-categories.md) и [Свойства категории заданий — создание категории заданий](../../ssms/agent/job-categories-properties-new-job-category.md).  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-create-a-job-category"></a>Создание категории заданий  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_add_category (Transact-SQL)](https://msdn.microsoft.com/6cca32cd-d941-4378-aed6-a7c90cb7520a).  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
**Создание категории заданий**  
  
Вызовите класс **JobCategory** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Пример кода см. в разделе [Планирование автоматических административных задач в агенте SQL Server](../../relational-databases/server-management-objects-smo/tasks/scheduling-automatic-administrative-tasks-in-sql-server-agent.md).  
  
