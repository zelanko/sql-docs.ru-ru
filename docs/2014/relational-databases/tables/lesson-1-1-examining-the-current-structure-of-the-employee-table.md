---
title: Изучение текущей структуры таблицы сотрудников | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 38c16d837dd886785479e1e2994b5b0f19372cfe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211434"
---
# <a name="examining-the-current-structure-of-the-employee-table"></a>Изучение текущей структуры таблицы сотрудников
  Образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] содержит таблицу **Employee** в схеме **HumanResources** . Чтобы не изменять исходную таблицу, на этом шаге создается копия таблицы **Employee** , называющаяся **EmployeeDemo**. Для упрощения этого примера копируется только пять столбцов из исходной таблицы. Затем выполняется запрос **HumanResources.EmployeeDemo** таблицы в структуру данных в таблице без использования `hierarchyid` тип данных.  
  
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
  
 Обратите внимание, что использование предложения `ORDER BY` приводит к тому, что прямые подчиненные каждого уровня управления будут находиться вместе. Например, все семь прямых подчиненных уровня **MgrID** 3 (roberto0) перечисляются вместе. Сгруппировать всех косвенных подчиненных уровня **MgrID** 3 тоже возможно, хотя это гораздо сложнее.  
  
 В следующей задаче мы создадим новую таблицу с типом данных `hierarchyid` и переместим в нее данные.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Заполнение таблицы существующими иерархическими данными](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
