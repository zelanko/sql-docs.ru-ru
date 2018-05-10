---
title: Изучение текущей структуры таблицы сотрудников | Документация Майкрософт
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 620defd42e27b122a92ee145da6b4b14d1cbf996
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-1-1---examining-the-current-structure-of-the-employee-table"></a>Занятие 1.1. Изучение текущей структуры таблицы сотрудников
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
Образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] (или более поздней версии) содержит таблицу **Employee** в схеме **HumanResources**. Чтобы не изменять исходную таблицу, на этом шаге создается копия таблицы **Employee** , называющаяся **EmployeeDemo**. Для упрощения этого примера копируется только пять столбцов из исходной таблицы. Затем выполняется запрос к таблице **HumanResources.EmployeeDemo** , позволяющий просмотреть структуру данных в таблице без использования типа данных **hierarchyid** .  
  
### <a name="to-copy-the-employee-table"></a>Копирование таблицы Employee  
  
1.  Запустите следующий код в окне редактора запросов, чтобы скопировать структуру и данные таблицы **Employee** в новую таблицу **EmployeeDemo**. Поскольку в исходной таблице уже используется hierarchyid, этот запрос фактически преобразует иерархию в плоскую структуру, чтобы получить записи руководителя и сотрудника. В следующих частях этого занятия мы будем реконструировать эту иерархию.
  
    ```  
    USE AdventureWorks ;  
    GO  
  
    SELECT emp.BusinessEntityID AS EmployeeID, emp.LoginID, 
      (SELECT  man.BusinessEntityID FROM HumanResources.Employee man 
            WHERE emp.OrganizationNode.GetAncestor(1)=man.OrganizationNode OR 
                (emp.OrganizationNode.GetAncestor(1) = 0x AND man.OrganizationNode IS NULL)) AS ManagerID
        , emp.JobTitle, emp.HireDate
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee emp ;
    GO
    ```  
  
### <a name="to-examine-the-structure-and-data-of-the-employeedemo-table"></a>Изучение структуры и данных таблицы EmployeeDemo  
  
-   Новая таблица **EmployeeDemo** представляет собой типичный пример таблицы в существующей базе данных, которую можно подвергнуть миграции в новую структуру. Запустите следующий код в окне редактора запросов, чтобы увидеть, как таблица использует самосоединение для отображения связей сотрудник-менеджер.  
  
    ```  
    SELECT   
        Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
        Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.JobTitle  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  JobTitle  
    NULL    NULL    1   adventure-works\ken0    Chief Executive Officer
    1   adventure-works\ken0    2   adventure-works\terri0  Vice President of Engineering
    1   adventure-works\ken0    16  adventure-works\david0  Marketing Manager
    1   adventure-works\ken0    25  adventure-works\james1  Vice President of Production
    1   adventure-works\ken0    234 adventure-works\laura1  Chief Financial Officer
    1   adventure-works\ken0    263 adventure-works\jean0   Information Services Manager
    1   adventure-works\ken0    273 adventure-works\brian3  Vice President of Sales
    2   adventure-works\terri0  3   adventure-works\roberto0    Engineering Manager
    3   adventure-works\roberto0    4   adventure-works\rob0    Senior Tool Designer
    ...  
    ```  
  
    Получаемый в результате набор содержит 290 строк.  
  
Обратите внимание, что использование предложения **ORDER BY** приводит к тому, что прямые подчиненные каждого уровня управления будут находиться вместе. Например, все семь прямых подчиненных уровня **MgrID** 1 (ken0) перечисляются вместе. Сгруппировать всех косвенных подчиненных уровня **MgrID** 1 тоже возможно, хотя это гораздо сложнее.  
  
В следующей задаче мы создадим новую таблицу с типом данных **hierarchyid** и переместим в нее данные.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Заполнение таблицы существующими иерархическими данными](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
  
