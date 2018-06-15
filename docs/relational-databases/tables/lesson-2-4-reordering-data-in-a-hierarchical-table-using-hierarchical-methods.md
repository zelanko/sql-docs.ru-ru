---
title: Переупорядочение данных в иерархической таблице с применением иерархических методов | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
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
- HierarchyID
ms.assetid: 7b8064c7-62c6-488d-84d2-57a5828fb907
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7a1058effc6a942bbe75d0f6369860fb4ab73330
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33007241"
---
# <a name="lesson-2-4---reordering-data-in-a-hierarchical-table-using-hierarchical-methods"></a>Занятие 2.4. Переупорядочение данных в иерархической таблице с применением иерархических методов
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
Реорганизация иерархии — это распространенная задача обслуживания. В этой задаче в первую очередь переместим одну строку в новую позицию в иерархии с помощью инструкции UPDATE с методом [GetReparentedValue](../../t-sql/data-types/getreparentedvalue-database-engine.md) . Затем переместим все поддерево в новое место.  
  
Метод `GetReparentedValue` имеет два аргумента. В первом аргументе описывается та часть иерархии, которая будет изменена. Например, если в иерархии **/1/4/2/3/** необходимо изменить сегмент **/1/4/** так, чтобы в результате получилась иерархия **/2/1/2/3/**, в которой последние два узла (**2/3/**) остались бы без изменений, необходимо указать в качестве первого аргумента изменяемые узлы (**/1/4/**). Второй аргумент предоставляет новый уровень иерархии; для этого примера это **/2/1/**. Эти два аргумента не обязаны содержать одинаковое число уровней.  
  
### <a name="to-move-a-single-row-to-a-new-location-in-the-hierarchy"></a>Перемещение одной строки на новое место в иерархии  
  
1.  В настоящий момент Wanida является подчиненной Sariya. В этой процедуре переместим Wanida из ее текущего узла **/1/1/** в другой так, чтобы она стала подчиненной Jill. Ее новым узлом будет узел **/3/1/** , следовательно, первым аргументом будет **/1/** , а вторым — **/3/** . Эти значения соответствуют значениям Sariya и Jill в столбце **OrgNode** . Исполните следующий код, чтобы переместить Wanida из организации Sariya в организацию Jill:  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 269 ;   
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 46 ;   
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 119 ;   
  
    UPDATE HumanResources.EmployeeOrg  
    SET OrgNode = @CurrentEmployee. GetReparentedValue(@OldParent, @NewParent)   
    WHERE OrgNode = @CurrentEmployee ;  
    GO  
    ```  
  
2.  Чтобы просмотреть результат, выполните следующий код:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
    Теперь Wanida находится в узле **/3/1/**.  
  
### <a name="to-reorganize-a-section-of-a-hierarchy"></a>Реорганизация раздела иерархии  
  
1.  Чтобы продемонстрировать, как можно одновременно переместить большее количество людей, сначала необходимо выполнить следующий код, чтобы добавить Ваниде подчиненного.  
  
    ```  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  Теперь Кевин — подчиненный Ваниды, которая является подчиненной Jill, которая является подчиненной David. Это означает, что Kevin находится на уровне **/3/1/1/**. Чтобы переместить всех подчиненных Jill к новому руководителю, мы присвоим новое значение всем узлам, имеющим значение **/3/** в столбце **OrgNode** . Выполните следующий код, чтобы произвести изменение, в результате которого Wanida станет подчиненной Sariya, но Kevin останется подчиненным Wanida:  
  
    ```  
    DECLARE @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 119 ; -- Jill  
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ; -- Sariya  
    DECLARE children_cursor CURSOR FOR  
    SELECT OrgNode FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @OldParent;  
    DECLARE @ChildId hierarchyid;  
    OPEN children_cursor  
    FETCH NEXT FROM children_cursor INTO @ChildId;  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
    START:  
        DECLARE @NewId hierarchyid;  
        SELECT @NewId = @NewParent.GetDescendant(MAX(OrgNode), NULL)  
        FROM HumanResources.EmployeeOrg WHERE OrgNode.GetAncestor(1) = @NewParent;  
  
        UPDATE HumanResources.EmployeeOrg  
        SET OrgNode = OrgNode.GetReparentedValue(@ChildId, @NewId)  
        WHERE OrgNode.IsDescendantOf(@ChildId) = 1;  
        IF @@error <> 0 GOTO START -- On error, retry  
            FETCH NEXT FROM children_cursor INTO @ChildId;  
    END  
    CLOSE children_cursor;  
    DEALLOCATE children_cursor;  
  
    ```  
  
3.  Чтобы просмотреть результат, выполните следующий код:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
------------ ------- -------- ---------- ------- -----------------  
/            Ox      0        6          David   Marketing Manager  
/1/          0x58    1        46         Sariya  Marketing Specialist  
/1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
/1/1/1/      0x5AD0  3        291        Kevin   Marketing Intern  
/2/          0x68    1        271        John    Marketing Specialist  
/2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
/3/          0x78    1        119        Jill    Marketing Specialist  
```  
  
Все организационное дерево, которое подчинялось Jill (Wanida и Kevin) теперь подчиняется Sariya.  
  
Хранимую процедуру для реорганизации раздела иерархии можно найти в подразделе "Перемещение поддеревьев" раздела [Реорганизация раздела иерархии](../../relational-databases/hierarchical-data-sql-server.md#BKMK_MovingSubtrees).  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Сводка. Управление данными в иерархической таблице](../../relational-databases/tables/lesson-2-5-summary-managing-data-in-a-hierarchical-table.md)  
  
  
  
