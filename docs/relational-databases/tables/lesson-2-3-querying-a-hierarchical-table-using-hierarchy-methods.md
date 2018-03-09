---
title: "Создание запросов к иерархической таблице с помощью иерархических методов | Документация Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- HierarchyID
ms.assetid: 3b4f7dae-65b5-4d8d-8641-87aba9aa692d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5cdd782633ee4a2cf6970c9ce838bd623039a013
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="lesson-2-3---querying-a-hierarchical-table-using-hierarchy-methods"></a>Занятие 2.3. Создание запросов к иерархической таблице с помощью иерархических методов
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)] После заполнения таблицы HumanResources.EmployeeOrg эта задача продемонстрирует, как можно выполнять запросы к иерархии с помощью некоторых иерархических методов.  
  
### <a name="to-find-subordinate-nodes"></a>Поиск подчиненных узлов  
  
1.  Sariya имеет одного подчиненного. Чтобы запросить подчиненных Sariya, выполните следующий запрос, в котором используется метод [IsDescendantOf](../../t-sql/data-types/isdescendantof-database-engine.md) :  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
    Результатами будут Sariya и Wanida. Sariya перечисляется, поскольку она является потомком на нулевом уровне. Wanida является потомком на первом уровне.  
  
2.  Запросить эту информацию можно также с помощью метода [GetAncestor](../../t-sql/data-types/getancestor-database-engine.md) . `GetAncestor` принимает аргумент уровня, попытка вернуть который выполняется. Поскольку Wanida находится одним уровнем ниже Sariya, следует использовать метод `GetAncestor(1)` так, как показано в следующем коде:  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @CurrentEmployee  
    ```  
  
    В этот раз результатом будет только Wanida.  
  
3.  Теперь измените значение `@CurrentEmployee` на David (EmployeeID 6), а уровень на 2. Выполнение следующей инструкции также вернет значение Wanida:  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
    В этот раз в результате также будет возвращена Mary, являющаяся подчиненной David, и находящаяся на два уровня ниже.  
  
### <a name="to-use-getroot-and-getlevel"></a>Использование методов GetRoot и GetLevel  
  
1.  По мере роста иерархии становится труднее определять положение в ней ее членов. Можно использовать метод [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) для определения того, как глубоко по уровням находится каждая строка в иерархии. Выполните следующий код, чтобы увидеть уровни всех строк:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  Используйте метод [GetRoot](../../t-sql/data-types/getroot-database-engine.md) для нахождения корневого узла в иерархии. Следующий код возвращает единственную строку, являющуюся корневым узлом:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
  
Следующая задача проведет реорганизацию иерархии.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Переупорядочение данных в иерархической таблице с помощью иерархических методов](../../relational-databases/tables/lesson-2-4-reordering-data-in-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
  
