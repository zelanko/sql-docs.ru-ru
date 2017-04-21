---
title: "Изучение текущей структуры таблицы сотрудников | Документация Майкрософт"
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
- examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e4f881ca9ee3cf85edbbb4d474406e94fe1658ef
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-1-1---examining-the-current-structure-of-the-employee-table"></a>Занятие 1.1. Изучение текущей структуры таблицы сотрудников
Образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] содержит таблицу **Employee** в схеме **HumanResources** . Чтобы не изменять исходную таблицу, на этом шаге создается копия таблицы **Employee** , называющаяся **EmployeeDemo**. Для упрощения этого примера копируется только пять столбцов из исходной таблицы. Затем выполняется запрос к таблице **HumanResources.EmployeeDemo** , позволяющий просмотреть структуру данных в таблице без использования типа данных **hierarchyid** .  
  
### <a name="to-copy-the-employee-table"></a>Копирование таблицы Employee  
  
1.  Запустите следующий код в окне редактора запросов, чтобы скопировать структуру и данные таблицы **Employee** в новую таблицу **EmployeeDemo**.  
  
    ```  
    USE AdventureWorks ;  
    GO  
  
    SELECT EmployeeID, LoginID, ManagerID, Title, HireDate   
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee ;  
    GO  
    ```  
  
### <a name="to-examine-the-structure-and-data-of-the-employeedemo-table"></a>Изучение структуры и данных таблицы EmployeeDemo  
  
-   Новая таблица **EmployeeDemo** представляет собой типичный пример таблицы в существующей базе данных, которую можно подвергнуть миграции в новую структуру. Запустите следующий код в окне редактора запросов, чтобы увидеть, как таблица использует самосоединение для отображения связей сотрудник-менеджер.  
  
    ```  
    SELECT   
         Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
         Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.Title  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  Title  
    NULL NULL                      109 adventure-works\ken0     Chief Executive Officer  
    3    adventure-works\roberto0  4   adventure-works\rob0     Senior Tool Designer  
    3    adventure-works\roberto0  9   adventure-works\gail0    Design Engineer  
    3    adventure-works\roberto0  11  adventure-works\jossef0  Design Engineer  
    3    adventure-works\roberto0  158 adventure-works\dylan0   Research and Development Manager  
    3    adventure-works\roberto0  263 adventure-works\ovidiu0  Senior Tool Designer  
    3    adventure-works\roberto0  267 adventure-works\michael8 Senior Design Engineer  
    3    adventure-works\roberto0  270 adventure-works\sharon0  Design Engineer  
    6    adventure-works\david0    2   adventure-works\kevin0   Marketing Assistant  
    ...  
    ```  
  
    Получаемый в результате набор содержит 290 строк.  
  
Обратите внимание, что использование предложения **ORDER BY** приводит к тому, что прямые подчиненные каждого уровня управления будут находиться вместе. Например, все семь прямых подчиненных уровня **MgrID** 3 (roberto0) перечисляются вместе. Сгруппировать всех косвенных подчиненных уровня **MgrID** 3 тоже возможно, хотя это гораздо сложнее.  
  
В следующей задаче мы создадим новую таблицу с типом данных **hierarchyid** и переместим в нее данные.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Заполнение таблицы существующими иерархическими данными](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
  

