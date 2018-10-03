---
title: Оптимизация таблицы NewOrg | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- optimizing tables
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a031466e35fef90104ab81fec17010725f8f5c0c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146984"
---
# <a name="optimizing-the-neworg-table"></a>Оптимизация таблицы NewOrg
  **NewOrd** таблицы, созданной в [заполнение таблицы существующими иерархическими данными](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) содержит все сведения о сотрудниках и представляет иерархическую структуру с помощью `hierarchyid`тип данных. Эта задача добавляет новые индексы для поддержки поиска по столбцу `hierarchyid`.  
  
## <a name="clustered-index"></a>Кластеризованный индекс  
 `hierarchyid` Столбца (**OrgNode**) является первичным ключом для **NewOrg** таблицы. После создания таблицы в ней содержался кластеризованный индекс **PK_NewOrg_OrgNode** , обеспечивающий уникальность значений в столбце **OrgNode** . Кластеризованный индекс также поддерживает поиск по таблице по глубине.  
  
## <a name="nonclustered-index"></a>Некластеризованный индекс  
 Во время этого шага создаются два некластеризованных индекса для поддержки работы обычных видов поиска.  
  
#### <a name="to-index-the-neworg-table-for-efficient-searches"></a>Индексация таблицы NewOrg для обеспечения эффективного поиска.  
  
1.  Чтобы обеспечить функционирование запросов, работающих на одном и том же уровне иерархии, следует использовать метод [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) для создания вычисляемого столбца, содержащего уровень иерархии. Затем следует создать составной индекс, основанный на уровне и `Hierarchyid`. Запустите следующий код для создания вычисляемого столбца и индекса преимущественно в ширину:  
  
    ```  
    ALTER TABLE NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  Создайте уникальный индекс для столбца **EmployeeID** . Это стандартный единичный уточняющий запрос относительно одного сотрудника по номеру **EmployeeID** . Запустите следующий код, чтобы создать индекс для столбца **EmployeeID**:  
  
    ```  
    CREATE UNIQUE INDEX EmpIDs_unq ON NewOrg(EmployeeID) ;  
    GO  
    ```  
  
3.  Запустите следующий код, чтобы получить данные из таблицы, упорядоченные относительно каждого из этих трех индексов:  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM NewOrg   
    ORDER BY OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY H_Level, OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  Сравните результирующие наборы, чтобы понять порядок хранения для каждого типа индекса. Далее приводятся только первые четыре строки из каждого выходного набора.  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     Индекс преимущественно в глубину: записи сотрудников хранятся рядом с записью их менеджера.  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     Индекс преимущественно по **EmployeeID**: строки хранятся в соответствии с последовательностью значений **EmployeeID**.  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
> [!NOTE]  
>  Диаграммы, на которых показана разница между индексом преимущественно в глубину и индексом преимущественно в ширину, см. в разделе [Иерархические данные (SQL Server)](../hierarchical-data-sql-server.md).  
  
#### <a name="to-drop-the-unnecessary-columns"></a>Удаление ненужных столбцов  
  
1.  Столбец **ManagerID** представляет связь "сотрудник-менеджер", которая на данный момент представлена столбцом **OrgNode** . Если другим приложениям столбец **ManagerID** не нужен, то, возможно, стоит его удалить с помощью следующей инструкции:  
  
    ```  
    ALTER TABLE NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  Столбец **EmployeeID** также является избыточным. Столбец **OrgNode** уникально идентифицирует каждого сотрудника. Если другим приложениям столбец **EmployeeID** не нужен, то, возможно, стоит его удалить с помощью следующей инструкции:  
  
    ```  
    DROP INDEX EmpIDs_unq ON NewOrg ;  
    ALTER TABLE NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
#### <a name="to-replace-the-original-table-with-the-new-table"></a>Замена исходной таблицы на новую  
  
1.  Если в исходной таблице содержались дополнительные индексы или ограничения, добавьте их в таблицу **NewOrg** .  
  
2.  Замените старую таблицу **EmployeeDemo** новой. Запустите следующий код, чтобы удалить старую таблицу и присвоить новой таблице имя старой:  
  
    ```  
    DROP TABLE EmployeeDemo ;  
    GO  
    sp_rename 'NewOrg', EmployeeDemo ;  
    GO  
    ```  
  
3.  Запустите следующий код, чтобы изучить окончательную таблицу:  
  
    ```  
    SELECT * FROM EmployeeDemo ;  
    ```  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Сводка. преобразование таблицы в иерархическую структуру](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
