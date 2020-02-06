---
title: Занятие 1. Преобразование таблицы в иерархическую структуру | Документация Майкрософт
ms.custom: ''
ms.date: 08/22/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05906db66c2bf4948e91dddafa2cdd54aaf936ec
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "72907297"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Урок 1. преобразование таблицы в иерархическую структуру
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
Если у клиентов имеются таблицы, в которых для выражения иерархических связей используются самосоединения, то эти таблицы можно преобразовать в иерархическую структуру, руководствуясь указаниями из данного занятия. Миграция от старого метода представления к методу представления, использующему тип данных **hierarchyid**, проходит относительно легко. После миграции пользователи получат компактное и легкое для понимания иерархическое представление, которое может быть проиндексировано несколькими способами для обеспечения эффективного поиска.  
  
В этом занятии происходит изучение существующей таблицы, создание новой таблицы, содержащей столбец **hierarchyid** , заполнение этой таблицы данными из таблицы источника, а также проводится демонстрация трех стратегий индексирования. Это занятие содержит следующие разделы:  
 
  
## <a name="prerequisites"></a>предварительные требования  
Для работы с этим учебником требуется среда SQL Server Management Studio, доступ к серверу SQL Server и база данных AdventureWorks.

- Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Скачайте [примеры баз данных AdventureWorks2017](https://docs.microsoft.com/sql/samples/adventureworks-install-configure).

Инструкции по восстановлению баз данных в SSMS см. в статье [Восстановление базы данных](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).  

## <a name="examine-the-current-structure-of-the-employee-table"></a>Изучение текущей структуры таблицы сотрудников
Образец базы данных Adventureworks2017 (или более поздней версии) содержит таблицу **Employee** в схеме **HumanResources**. Чтобы не изменять исходную таблицу, на этом шаге создается копия таблицы **Employee** , называющаяся **EmployeeDemo**. Для упрощения этого примера копируется только пять столбцов из исходной таблицы. Затем выполняется запрос к таблице **HumanResources.EmployeeDemo** , позволяющий просмотреть структуру данных в таблице без использования типа данных **hierarchyid** .  
  
### <a name="copy-the-employee-table"></a>Копирование таблицы Employee  
  
1.  Запустите следующий код в окне редактора запросов, чтобы скопировать структуру и данные таблицы **Employee** в новую таблицу **EmployeeDemo**. Поскольку в исходной таблице уже используется hierarchyid, этот запрос фактически преобразует иерархию в плоскую структуру, чтобы получить записи руководителя и сотрудника. В следующих частях этого занятия мы будем реконструировать эту иерархию.

   ```sql  
   USE AdventureWorks2017;  
   GO  
     if OBJECT_ID('HumanResources.EmployeeDemo') is not null
    drop table HumanResources.EmployeeDemo 

    SELECT emp.BusinessEntityID AS EmployeeID, emp.LoginID, 
     (SELECT  man.BusinessEntityID FROM HumanResources.Employee man 
        WHERE emp.OrganizationNode.GetAncestor(1)=man.OrganizationNode OR 
            (emp.OrganizationNode.GetAncestor(1) = 0x AND man.OrganizationNode IS NULL)) AS ManagerID,
          emp.JobTitle, emp.HireDate
   INTO HumanResources.EmployeeDemo   
   FROM HumanResources.Employee emp ;
   GO
   ```  
  
### <a name="examine-the-structure-and-data-of-the-employeedemo-table"></a>Изучение структуры и данных таблицы EmployeeDemo  
  
-   Новая таблица **EmployeeDemo** представляет собой типичный пример таблицы в существующей базе данных, которую можно подвергнуть миграции в новую структуру. Запустите следующий код в окне редактора запросов, чтобы увидеть, как таблица использует самосоединение для отображения связей сотрудник-менеджер.  
  
    ```sql  
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
    NULL    NULL                    1   adventure-works\ken0        Chief Executive Officer
    1   adventure-works\ken0        2   adventure-works\terri0      Vice President of Engineering
    1   adventure-works\ken0       16   adventure-works\david0    Marketing Manager
    1   adventure-works\ken0       25   adventure-works\james1    Vice President of Production
    1   adventure-works\ken0      234   adventure-works\laura1    Chief Financial Officer
    1   adventure-works\ken0    263 adventure-works\jean0       Information Services Manager
    1   adventure-works\ken0      273   adventure-works\brian3    Vice President of Sales
    2   adventure-works\terri0    3 adventure-works\roberto0    Engineering Manager
    3   adventure-works\roberto0    4   adventure-works\rob0        Senior Tool Designer
    ...  
    ```  
  
    Получаемый в результате набор содержит 290 строк.  
  
Обратите внимание, что использование предложения **ORDER BY** приводит к тому, что прямые подчиненные каждого уровня управления будут находиться вместе. Например, все семь прямых подчиненных уровня **MgrID** 1 (ken0) перечисляются вместе. Сгруппировать всех косвенных подчиненных уровня **MgrID** 1 тоже возможно, хотя это гораздо сложнее.  


## <a name="populate-a-table-with-existing-hierarchical-data"></a>Заполнение таблицы существующими иерархическими данными
В этой задаче создается таблица и заполняется данными из таблицы **EmployeeDemo** . Эта задача включает следующие шаги.  
  
-   Создание таблицы, содержащей столбец типа **hierarchyid** . Этот столбец может заменить существующие столбцы **EmployeeID** и **ManagerID** . Однако эти столбцы нужно сохранить. Это нужно для того, чтобы существующие приложения могли ссылаться на эти столбцы, а также для помощи при распознавании данных после передачи. Определение таблицы задает столбец **OrgNode** как первичный ключ, следовательно, этот столбец должен содержать уникальные значения. В кластеризованном индексе на основе столбца **OrgNode** будут храниться данные в последовательности ключа **OrgNode** .    
-   Создание временной таблицы, которая будет использована для слежения за тем, сколько сотрудников напрямую подчиняются каждому менеджеру. 
-   Заполнение новой таблицы данными из таблицы **EmployeeDemo** .  
  
### <a name="to-create-a-new-table-named-neworg"></a>Создание новой таблицы с именем NewOrg  
  
-   В окне редактора запросов запустите приведенный ниже код, чтобы создать таблицу с именем **HumanResources.NewOrg**.  
  
    ```sql   
    CREATE TABLE HumanResources.NewOrg  
    (  
      OrgNode hierarchyid,  
      EmployeeID int,  
      LoginID nvarchar(50),  
      ManagerID int  
    CONSTRAINT PK_NewOrg_OrgNode  
      PRIMARY KEY CLUSTERED (OrgNode)  
    );  
    GO  
    ```  
  
### <a name="create-a-temporary-table-named-children"></a>Создание временной таблицы с именем #Children  
  
1.  Создайте временную таблицу с именем **#Children** . В ней должен быть столбец **Num** , который должен содержать количество потомков каждого узла:  
  
    ```sql  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  Добавьте индекс, который значительно ускорит работу запроса, заполняющего таблицу **NewOrg** :  
  
    ```sql  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="populate-the-neworg-table"></a>Заполнение таблицы NewOrg  
  
1.  Рекурсивные запросы запрещают использование вложенных запросов со статистическими выражениями. Вместо этого заполните таблицу **#Children** с помощью следующего кода, который использует метод [ROW_NUMBER()](../../t-sql/functions/row-number-transact-sql.md) для заполнения столбца **Num** :  
  
    ```sql 
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM HumanResources.EmployeeDemo  
    GO 
    ```  
  
2.  Просмотрите таблицу **#Children** . Обратите внимание, что в столбце **Num** содержатся последовательные номера для каждого менеджера.  
  
    ```sql  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

    ```
    EmployeeID  ManagerID   Num
    1   NULL    1
    2        1    1
    16     1      2
    25     1      3
    234    1      4
    263    1      5
    273    1      6
    3        2    1
    4        3    1
    5        3    2
    6        3    3
    7        3    4
    ```


3.  Заполнение таблицы **NewOrg** . Используйте методы GetRoot и ToString, чтобы объединить значения столбца **Num** в формат **hierarchyid** ; затем обновите столбец **OrgNode** результирующими иерархическими значениями:  
  
    ```sql  
    WITH paths(path, EmployeeID)   
    AS (  
    -- This section provides the value for the root of the hierarchy  
    SELECT hierarchyid::GetRoot() AS OrgNode, EmployeeID   
    FROM #Children AS C   
    WHERE ManagerID IS NULL   

    UNION ALL   
    -- This section provides values for all nodes except the root  
    SELECT   
    CAST(p.path.ToString() + CAST(C.Num AS varchar(30)) + '/' AS hierarchyid),   
    C.EmployeeID  
    FROM #Children AS C   
    JOIN paths AS p   
       ON C.ManagerID = P.EmployeeID   
    )  
    INSERT HumanResources.NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM HumanResources.EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO 
    ```  
  
4.  Столбец типа данных **hierarchyid** становится более понятным, если его преобразовать в символьный формат. Просмотрите данные в таблице **NewOrg** , выполнив следующий код, содержащий два представления столбца **OrgNode** :  
  
    ```sql  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM HumanResources.NewOrg   
    ORDER BY LogicalNode;  
    GO  
    ```  
  
    Столбец **LogicalNode** содержит данные столбца типа данных **hierarchyid** , преобразованные в более доступную текстовую форму, представляющую иерархию. В оставшихся задачах для представления логического формата столбцов типа `ToString()` hierarchyid **также следует использовать метод** .  
  
5.  Удалите временную таблицу, она больше не понадобится:  
  
    ```sql  
    DROP TABLE #Children  
    GO  
    ```  
  
## <a name="optimizing-the-neworg-table"></a>Оптимизация таблицы NewOrg
Таблица **NewOrd** , созданная в задании [Заполнение таблицы существующими иерархическими данными](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) , содержит все сведения о сотрудниках и представляет иерархическую структуру с использованием типа данных **hierarchyid** . Эта задача добавляет новые индексы для поддержки поиска по столбцу **hierarchyid** .  
  

Столбец **hierarchyid** (**OrgNode**) является первичным ключом таблицы **NewOrg** . После создания таблицы в ней содержался кластеризованный индекс **PK_NewOrg_OrgNode** , обеспечивающий уникальность значений в столбце **OrgNode** . Кластеризованный индекс также поддерживает поиск по таблице по глубине.  
  
  
### <a name="create-index-on-neworg-table-for-efficient-searches"></a>Создание индекса таблицы NewOrg для эффективного поиска  
  
1.  Чтобы обеспечить функционирование запросов, работающих на одном и том же уровне иерархии, следует использовать метод [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) для создания вычисляемого столбца, содержащего уровень иерархии. Затем следует создать составной индекс, основанный на уровне и **Hierarchyid**. Запустите следующий код для создания вычисляемого столбца и индекса преимущественно в ширину:  
  
    ```sql  
    ALTER TABLE HumanResources.NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON HumanResources.NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  Создайте уникальный индекс для столбца **EmployeeID** . Это стандартный единичный уточняющий запрос относительно одного сотрудника по номеру **EmployeeID** . Запустите следующий код, чтобы создать индекс для столбца **EmployeeID**:  
  
    ```sql  
    CREATE UNIQUE INDEX EmpIDs_unq ON HumanResources.NewOrg(EmployeeID) ;  
    GO
    ```  
  
3.  Запустите следующий код, чтобы получить данные из таблицы, упорядоченные относительно каждого из этих трех индексов:  
  
    ```sql  
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

    Индекс преимущественно по**EmployeeID**: строки хранятся в соответствии с последовательностью значений **EmployeeID** .  

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
  
### <a name="drop-the-unnecessary-columns"></a>Удаление ненужных столбцов  
  
1.  Столбец **ManagerID** представляет связь "сотрудник-менеджер", которая на данный момент представлена столбцом **OrgNode** . Если другим приложениям столбец **ManagerID** не нужен, то, возможно, стоит его удалить с помощью следующей инструкции:  
  
    ```sql  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  Столбец **EmployeeID** также является избыточным. Столбец **OrgNode** уникально идентифицирует каждого сотрудника. Если другим приложениям столбец **EmployeeID** не нужен, то, возможно, стоит его удалить с помощью следующей инструкции:  
  
    ```sql  
    DROP INDEX EmpIDs_unq ON HumanResources.NewOrg ;  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
### <a name="replace-the-original-table-with-the-new-table"></a>Замена исходной таблицы на новую  
  
1.  Если в исходной таблице содержались дополнительные индексы или ограничения, добавьте их в таблицу **NewOrg** .  
  
2.  Замените старую таблицу **EmployeeDemo** новой. Запустите следующий код, чтобы удалить старую таблицу и присвоить новой таблице имя старой:  
  
    ```sql  
    DROP TABLE HumanResources.EmployeeDemo ;  
    GO  
    sp_rename 'HumanResources.NewOrg', 'EmployeeDemo' ;  
    GO  
    ```  
  
3.  Запустите следующий код, чтобы изучить окончательную таблицу:  
  
    ```sql  
    SELECT * FROM HumanResources.EmployeeDemo ;  
    ```  
  
## <a name="next-steps"></a>Дальнейшие действия
Следующая статья содержит сведения для создания иерархической таблицы и управления данными в ней. 

Дополнительные сведения см. в следующей статье:
> [!div class="nextstepaction"]
> [Дальнейшие действия](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)
