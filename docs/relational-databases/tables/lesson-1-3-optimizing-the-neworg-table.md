---
title: Оптимизация таблицы NewOrg | Документация Майкрософт
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
- optimizing tables
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: be243734f05365ea7376e2e48e30479e46a7865c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-1-3---optimizing-the-neworg-table"></a>Занятие 1.3. Оптимизация таблицы NewOrg
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
Таблица **NewOrd** , созданная в задании [Заполнение таблицы существующими иерархическими данными](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) , содержит все сведения о сотрудниках и представляет иерархическую структуру с использованием типа данных **hierarchyid** . Эта задача добавляет новые индексы для поддержки поиска по столбцу **hierarchyid** .  
  
## <a name="clustered-index"></a>Кластеризованный индекс  
Столбец **hierarchyid** (**OrgNode**) является первичным ключом таблицы **NewOrg** . После создания таблицы в ней содержался кластеризованный индекс **PK_NewOrg_OrgNode** , обеспечивающий уникальность значений в столбце **OrgNode** . Кластеризованный индекс также поддерживает поиск по таблице по глубине.  
  
## <a name="nonclustered-index"></a>Некластеризованный индекс  
Во время этого шага создаются два некластеризованных индекса для поддержки работы обычных видов поиска.  
  
#### <a name="to-index-the-neworg-table-for-efficient-searches"></a>Индексация таблицы NewOrg для обеспечения эффективного поиска.  
  
1.  Чтобы обеспечить функционирование запросов, работающих на одном и том же уровне иерархии, следует использовать метод [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) для создания вычисляемого столбца, содержащего уровень иерархии. Затем следует создать составной индекс, основанный на уровне и **Hierarchyid**. Запустите следующий код для создания вычисляемого столбца и индекса преимущественно в ширину:  
  
    ```  
    ALTER TABLE HumanResources.NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON HumanResources.NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  Создайте уникальный индекс для столбца **EmployeeID** . Это стандартный единичный уточняющий запрос относительно одного сотрудника по номеру **EmployeeID** . Запустите следующий код, чтобы создать индекс для столбца **EmployeeID**:  
  
    ```  
    CREATE UNIQUE INDEX EmpIDs_unq ON HumanResources.NewOrg(EmployeeID) ;  
    GO
    ```  
  
3.  Запустите следующий код, чтобы получить данные из таблицы, упорядоченные относительно каждого из этих трех индексов:  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM HumanResources.NewOrg   
    ORDER BY OrgNode;  

    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM HumanResources.NewOrg   
    ORDER BY H_Level, OrgNode;  

    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM HumanResources.NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  Сравните результирующие наборы, чтобы понять порядок хранения для каждого типа индекса. Далее приводятся только первые четыре строки из каждого выходного набора.  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    Индекс преимущественно в глубину: записи сотрудников хранятся рядом с записью их менеджера.  

    ```
    LogicalNode OrgNode H_Level EmployeeID  LoginID
    /   0x  0   1   adventure-works\ken0
    /1/ 0x58    1   2   adventure-works\terri0
    /1/1/   0x5AC0  2   3   adventure-works\roberto0
    /1/1/1/ 0x5AD6  3   4   adventure-works\rob0
    /1/1/2/ 0x5ADA  3   5   adventure-works\gail0
    /1/1/3/ 0x5ADE  3   6   adventure-works\jossef0
    /1/1/4/ 0x5AE1  3   7   adventure-works\dylan0
    /1/1/4/1/   0x5AE158    4   8   adventure-works\diane1
    /1/1/4/2/   0x5AE168    4   9   adventure-works\gigi0
    /1/1/4/3/   0x5AE178    4   10  adventure-works\michael6
    /1/1/5/ 0x5AE3  3   11  adventure-works\ovidiu0
    ```

    Индекс преимущественно по **EmployeeID**: строки хранятся в соответствии с последовательностью значений **EmployeeID**.  

    ```
    LogicalNode OrgNode H_Level EmployeeID  LoginID
    /   0x  0   1   adventure-works\ken0
    /1/ 0x58    1   2   adventure-works\terri0
    /1/1/   0x5AC0  2   3   adventure-works\roberto0
    /1/1/1/ 0x5AD6  3   4   adventure-works\rob0
    /1/1/2/ 0x5ADA  3   5   adventure-works\gail0
    /1/1/3/ 0x5ADE  3   6   adventure-works\jossef0
    /1/1/4/ 0x5AE1  3   7   adventure-works\dylan0
    /1/1/4/1/   0x5AE158    4   8   adventure-works\diane1
    /1/1/4/2/   0x5AE168    4   9   adventure-works\gigi0
    /1/1/4/3/   0x5AE178    4   10  adventure-works\michael6
    /1/1/5/ 0x5AE3  3   11  adventure-works\ovidiu0
    /1/1/5/1/   0x5AE358    4   12  adventure-works\thierry0
    ```
  
> [!NOTE]  
> Диаграммы, на которых показана разница между индексом преимущественно в глубину и индексом преимущественно в ширину, см. в разделе [Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md).  
  
#### <a name="to-drop-the-unnecessary-columns"></a>Удаление ненужных столбцов  
  
1.  Столбец **ManagerID** представляет связь "сотрудник-менеджер", которая на данный момент представлена столбцом **OrgNode** . Если другим приложениям столбец **ManagerID** не нужен, то, возможно, стоит его удалить с помощью следующей инструкции:  
  
    ```  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  Столбец **EmployeeID** также является избыточным. Столбец **OrgNode** уникально идентифицирует каждого сотрудника. Если другим приложениям столбец **EmployeeID** не нужен, то, возможно, стоит его удалить с помощью следующей инструкции:  
  
    ```  
    DROP INDEX EmpIDs_unq ON HumanResources.NewOrg ;  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
#### <a name="to-replace-the-original-table-with-the-new-table"></a>Замена исходной таблицы на новую  
  
1.  Если в исходной таблице содержались дополнительные индексы или ограничения, добавьте их в таблицу **NewOrg** .  
  
2.  Замените старую таблицу **EmployeeDemo** новой. Запустите следующий код, чтобы удалить старую таблицу и присвоить новой таблице имя старой:  
  
    ```  
    DROP TABLE HumanResources.EmployeeDemo ;  
    GO  
    sp_rename 'HumanResources.NewOrg', 'EmployeeDemo' ;  
    GO  
    ```  
  
3.  Запустите следующий код, чтобы изучить окончательную таблицу:  
  
    ```  
    SELECT * FROM HumanResources.EmployeeDemo ;  
    ```  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Сводка. преобразование таблицы в иерархическую структуру](../../relational-databases/tables/lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
  
