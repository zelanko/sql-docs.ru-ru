---
title: "Создание запросов к иерархической таблице с помощью иерархических методов | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "HierarchyID"
ms.assetid: 3b4f7dae-65b5-4d8d-8641-87aba9aa692d
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Создание запросов к иерархической таблице с помощью иерархических методов
После того как таблица HumanResources.EmployeeOrg будет заполнена, эта задача продемонстрирует, как можно проводить запросы к иерархии с помощью некоторых иерархических методов.  
  
### Поиск подчиненных узлов  
  
1.  Sariya имеет одного подчиненного. Чтобы запросить подчиненных Sariya, выполните следующий запрос, в котором используется метод [IsDescendantOf](../../t-sql/data-types/isdescendantof-database-engine.md):  
  
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
  
2.  Запросить эту информацию можно также с помощью метода [GetAncestor](../../t-sql/data-types/getancestor-database-engine.md). `GetAncestor` принимает аргумент уровня, попытка вернуть который выполняется. Поскольку Wanida находится одним уровнем ниже Sariya, следует использовать метод `GetAncestor(1)` так, как показано в следующем коде:  
  
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
  
### Использование методов GetRoot и GetLevel  
  
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
  
## Следующая задача занятия  
[Переупорядочение данных в иерархической таблице с помощью иерархических методов](../../relational-databases/tables/reordering-data-in-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
  
