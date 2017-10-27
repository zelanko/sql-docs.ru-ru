---
title: "Создание таблицы с помощью типа данных hierarchyid | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- HierarchyID
ms.assetid: 0d1f361f-336c-4571-99d1-f4813b2d9fc4
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d3671dcea0c0825ba2624bc84a13ee9e2073a25f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-2-1---creating-a-table-using-the-hierarchyid-data-type"></a>Занятие 2.1. Создание таблицы с помощью типа данных hierarchyid
В следующем примере создается таблица EmployeeOrg, включающая данные о сотрудниках и их иерархическом подчинении. В этом примере в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] создается таблица (что не обязательно). Для простоты эта таблица содержит только 5 столбцов.  
  
-   OrgNode — это столбец типа **hierarchyid** , в котором хранятся иерархические связи.  
  
-   OrgLevel — это вычисляемый столбец, основанный на столбце OrgNode, в котором хранятся данные об уровне каждого узла в иерархии. Эти данные будут использоваться для создания индекса по ширине.  
  
-   Столбец EmployeeID содержит типичные идентификационные номера сотрудников, которые используются для таких задач, как расчет заработной платы. Новые приложения могут использовать столбец OrgNode, и этот отдельный столбец EmployeeID не требуется.  
  
-   Столбец EmpName содержит имя сотрудника.  
  
-   Столбец Title содержит должность сотрудника.  
  
### <a name="to-create-the-employeeorg-table"></a>Создание таблицы «EmployeeOrg»  
  
1.  В окне редактора запросов выполните следующий программный код, чтобы создать таблицу `EmployeeOrg` . Если задать столбец `OrgNode` в качестве первичного ключа кластеризованного индекса, создается индекс по глубине:  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    CREATE TABLE HumanResources.EmployeeOrg  
    (  
       OrgNode hierarchyid PRIMARY KEY CLUSTERED,  
       OrgLevel AS OrgNode.GetLevel(),  
       EmployeeID int UNIQUE NOT NULL,  
       EmpName varchar(20) NOT NULL,  
       Title varchar(20) NULL  
    ) ;  
    GO  
    ```  
  
2.  Чтобы создать составной индекс по столбцам `OrgLevel` и `OrgNode` для эффективного поиска в ширину, выполните следующий код:  
  
    ```  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
Таблица готова для записи данных. В результате выполнения следующего задания таблица будет заполнена данными с применением иерархических методов.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Заполнение иерархической таблицы с помощью иерархических методов](../../relational-databases/tables/lesson-2-2-populating-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
  

