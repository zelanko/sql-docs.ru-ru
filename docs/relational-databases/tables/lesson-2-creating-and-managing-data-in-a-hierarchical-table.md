---
title: Занятие 2. Создание данных и управление ими в иерархической таблице | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 95f55cff-4abb-4c08-97b3-e3ae5e8b24e2
author: stevestein
ms.author: sstein
ms.openlocfilehash: b54f60e71344bc04271378fbd84214b31bd9503c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85692491"
---
# <a name="lesson-2-create-and-manage-data-in-a-hierarchical-table"></a>Занятие 2. Создание данных в иерархической таблице и управление ими
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
На занятии 1 существующая таблица была изменена так, чтобы в ней использовался тип данных **hierarchyid** . Кроме того, столбец **hierarchyid** был заполнен представлением существующих данных. На этом занятии будет создана новая таблица и вставлены данные с помощью иерархических методов. Затем с помощью иерархических методов будет выполнен запрос данных и показано управление данными. 

## <a name="prerequisites"></a>предварительные требования  
Для работы с этим учебником требуется среда SQL Server Management Studio, доступ к серверу SQL Server и база данных AdventureWorks.

- Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Скачайте [примеры баз данных AdventureWorks2017](https://docs.microsoft.com/sql/samples/adventureworks-install-configure).

Инструкции по восстановлению баз данных в SSMS см. в статье [Восстановление базы данных](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).   
  
## <a name="create-a-table-using-the-hierarchyid-data-type"></a>Создание таблицы с помощью типа данных hierarchyid
В следующем примере создается таблица EmployeeOrg, включающая данные о сотрудниках и их иерархическом подчинении. В этом примере в базе данных AdventureWorks2017 создается таблица (что не обязательно). Для простоты эта таблица содержит только 5 столбцов.  
  
-   OrgNode — это столбец типа **hierarchyid** , в котором хранятся иерархические связи.   
-   OrgLevel — это вычисляемый столбец, основанный на столбце OrgNode, в котором хранятся данные об уровне каждого узла в иерархии. Эти данные будут использоваться для создания индекса по ширине.  
-   Столбец EmployeeID содержит типичные идентификационные номера сотрудников, которые используются для таких задач, как расчет заработной платы. Новые приложения могут использовать столбец OrgNode, и этот отдельный столбец EmployeeID не требуется.   
-   Столбец EmpName содержит имя сотрудника.    
-   Столбец Title содержит должность сотрудника.  

## <a name="create-the-employeeorg-table"></a>Создание таблицы EmployeeOrg  
  
1.  В окне редактора запросов выполните следующий программный код, чтобы создать таблицу `EmployeeOrg` . Если задать столбец `OrgNode` в качестве первичного ключа кластеризованного индекса, создается индекс по глубине:  
  
    ```sql  
    USE AdventureWorks2017 ;  
    GO  
    
    if OBJECT_ID('HumanResources.EmployeeOrg') is not null
     drop table HumanResources.EmployeeOrg 
         
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
  
    ```sql  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
Таблица готова для записи данных. В результате выполнения следующего задания таблица будет заполнена данными с применением иерархических методов.   

## <a name="populate-a-hierarchical-table-using-hierarchical-methods"></a>Заполнение иерархической таблицы с помощью иерархических методов
В AdventureWorks2017 в отделе маркетинга указано 8 работников. Иерархический список сотрудников выглядит следующим образом.  
  
**Дэвид**, **EmployeeID** 6, начальник отдела маркетинга. В подчинении у **Дэвида**находятся три специалиста по маркетингу:  
  
-   **Сара**, **EmployeeID** 46  
  
-   **Джон**, **EmployeeID** 271  
  
-   **Джил**, **EmployeeID** 119  
  
Маркетолог **Ванида** (**EmployeeID** 269), подчиняется **Саре**, а маркетолог **Мэри** (**EmployeeID** 272) подчиняется **Джону**.  
  
### <a name="insert-the-root-of-the-hierarchy-tree"></a>Вставка корневого элемента иерархического дерева  
  
1.  В следующем примере запись **Дэвид** (начальник отдела маркетинга) вставляется таблицу в качестве корневого элемента иерархии. **OrdLevel** — вычисляемый столбец. Следовательно, он не является частью инструкции INSERT. Для вставки первой записи в вершину иерархии используется метод [GetRoot()](../../t-sql/data-types/getroot-database-engine.md) .  
  
    ```sql  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES (hierarchyid::GetRoot(), 6, 'David', 'Marketing Manager') ;  
    GO  
    ```  
  
2.  Для просмотра начальной строки таблицы используйте следующий код:  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```sql  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    ```  
  
Как и на предыдущем занятии, для преобразования данных типа `ToString()` hierarchyid **в более наглядный формат используется метод** .  
  
### <a name="insert-a-subordinate-employee"></a>Вставка записи подчиненного  
  
1.  **Сара** подчиняется **Дэвиду**. Чтобы вставить в иерархию узел **Сара** , необходимо создать соответствующее значение **OrgNode** с типом данных **hierarchyid**. Следующий код создает переменную типа **hierarchyid** и присваивает ей корневое значение OrgNode таблицы. Затем эта переменная используется методом [GetDescendant()](../../t-sql/data-types/getdescendant-database-engine.md) для вставки строки, представляющей подчиненный узел. `GetDescendant` принимает два аргумента. Вот список вариантов с разными значениями аргументов.  
  
    -   Если родительская запись — NULL, `GetDescendant` возвращает значение NULL.  
    -   Если родительская запись — не NULL, а потомки child1 и child2 — NULL, метод `GetDescendant` возвращает одного потомка данного родителя.  
    -   Если родительская запись и потомок child1 — не NULL, а потомок child2 равен NULL, метод `GetDescendant` возвращает значение потомка родителя, который больше чем child1.   
    -   Если родитель и потомок child2 — не NULL, а потомок child1 равен NULL, метод `GetDescendant` возвращает значение потомка родителя, который меньше child2.   
    -   Если родитель, child1 и child2 не равны NULL, метод `GetDescendant` возвращает потомка родителя, который больше child1 и меньше child2.  
  
    В следующем примере в качестве аргументов корневого родительского элемента используются значения `(NULL, NULL)` , так как таблица пока не содержит никаких строк, кроме корневой. Чтобы вставить запись **Сара**, выполните следующий код:  
  
    ```sql  
    DECLARE @Manager hierarchyid   
    SELECT @Manager = hierarchyid::GetRoot()  
    FROM HumanResources.EmployeeOrg ;  
  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES  
    (@Manager.GetDescendant(NULL, NULL), 46, 'Sariya', 'Marketing Specialist') ;  
  
    ```  
  
2.  Чтобы обратиться к таблице и просмотреть вставленные записи, повторите запрос из первой процедуры:  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    ```  
  
### <a name="create-a-procedure-for-entering-new-nodes"></a>Создание процедуры ввода новых узлов  
  
1.  Для упрощения ввода данных можно создать следующую хранимую процедуру, вставляющую данные о сотрудниках в таблицу **EmployeeOrg** . Входные данные процедуры — это данные о добавляемом сотруднике. Это **EmployeeID** руководителя нового сотрудника, **EmployeeID** самого сотрудника, а также их имена и должности. В процедуре используются методы `GetDescendant()` и [GetAncestor()](../../t-sql/data-types/getancestor-database-engine.md) . Чтобы создать процедуру, выполните следующий код:  
  
    ```sql  
    CREATE PROC AddEmp(@mgrid int, @empid int, @e_name varchar(20), @title varchar(20))   
    AS   
    BEGIN  
       DECLARE @mOrgNode hierarchyid, @lc hierarchyid  
       SELECT @mOrgNode = OrgNode   
       FROM HumanResources.EmployeeOrg   
       WHERE EmployeeID = @mgrid  
       SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
       BEGIN TRANSACTION  
          SELECT @lc = max(OrgNode)   
          FROM HumanResources.EmployeeOrg   
          WHERE OrgNode.GetAncestor(1) =@mOrgNode ;  
  
          INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
          VALUES(@mOrgNode.GetDescendant(@lc, NULL), @empid, @e_name, @title)  
       COMMIT  
    END ;  
    GO  
    ```  
  
2.  В следующем примере вставляются записи об остальных 4 сотрудниках, прямо или косвенно подчиняющихся **Дэвиду**.  
  
    ```sql  
    EXEC AddEmp 6, 271, 'John', 'Marketing Specialist' ;  
    EXEC AddEmp 6, 119, 'Jill', 'Marketing Specialist' ;  
    EXEC AddEmp 46, 269, 'Wanida', 'Marketing Assistant' ;  
    EXEC AddEmp 271, 272, 'Mary', 'Marketing Assistant' ;  
    ```  
  
3.  Для просмотра строк таблицы **EmployeeOrg** выполните следующий запрос:  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```sql  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    /1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
    /2/          0x68    1        271        John    Marketing Specialist  
    /2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
    /3/          0x78    1        119        Jill    Marketing Specialist  
    ```  
  
Теперь таблица полностью заполнена записями о сотрудниках отдела маркетинга.  

## <a name="query-a-hierarchical-table-using-hierarchy-methods"></a>Создание запросов к иерархической таблице с помощью иерархических методов
После того как таблица HumanResources.EmployeeOrg будет заполнена, эта задача продемонстрирует, как можно проводить запросы к иерархии с помощью некоторых иерархических методов.  
  
### <a name="find-subordinate-nodes"></a>Поиск подчиненных узлов  
  
1.  Sariya имеет одного подчиненного. Чтобы запросить подчиненных Sariya, выполните следующий запрос, в котором используется метод [IsDescendantOf](../../t-sql/data-types/isdescendantof-database-engine.md) :  
  
    ```sql  
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
  
    ```sql  
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
  
    ```sql  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
    В этот раз в результате также будет возвращена Mary, являющаяся подчиненной David, и находящаяся на два уровня ниже.  
  
## <a name="use-getroot-and-getlevel"></a>Использование методов GetRoot и GetLevel  
  
1.  По мере роста иерархии становится труднее определять положение в ней ее членов. Можно использовать метод [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) для определения того, как глубоко по уровням находится каждая строка в иерархии. Выполните следующий код, чтобы увидеть уровни всех строк:  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  Используйте метод [GetRoot](../../t-sql/data-types/getroot-database-engine.md) для нахождения корневого узла в иерархии. Следующий код возвращает единственную строку, являющуюся корневым узлом:  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
   
  
## <a name="reorder-data-in-a-hierarchical-table-using-hierarchical-methods"></a>Переупорядочение данных в иерархической таблице с помощью иерархических методов
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Реорганизация иерархии — это распространенная задача обслуживания. В этой задаче в первую очередь переместим одну строку в новую позицию в иерархии с помощью инструкции UPDATE с методом [GetReparentedValue](../../t-sql/data-types/getreparentedvalue-database-engine.md) . Затем переместим все поддерево в новое место.  
  
Метод `GetReparentedValue` имеет два аргумента. В первом аргументе описывается та часть иерархии, которая будет изменена. Например, если в иерархии **/1/4/2/3/** необходимо изменить сегмент **/1/4/** так, чтобы в результате получилась иерархия **/2/1/2/3/** , в которой последние два узла (**2/3/** ) остались бы без изменений, необходимо указать в качестве первого аргумента изменяемые узлы ( **/1/4/** ). Второй аргумент предоставляет новый уровень иерархии; для этого примера это **/2/1/** . Эти два аргумента не обязаны содержать одинаковое число уровней.  
  
### <a name="move-a-single-row-to-a-new-location-in-the-hierarchy"></a>Перемещение одной строки на новое место в иерархии  
  
1.  В настоящий момент Wanida является подчиненной Sariya. В этой процедуре переместим Wanida из ее текущего узла **/1/1/** в другой так, чтобы она стала подчиненной Jill. Ее новым узлом будет узел **/3/1/** , следовательно, первым аргументом будет **/1/** , а вторым — **/3/** . Эти значения соответствуют значениям Sariya и Jill в столбце **OrgNode** . Исполните следующий код, чтобы переместить Wanida из организации Sariya в организацию Jill:  
  
    ```sql  
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
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
    Теперь Wanida находится в узле **/3/1/** .  
  
### <a name="reorganize-a-section-of-a-hierarchy"></a>Реорганизация раздела иерархии  
  
1.  Чтобы продемонстрировать, как можно одновременно переместить большее количество людей, сначала необходимо выполнить следующий код, чтобы добавить Ваниде подчиненного.  
  
    ```sql  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  Теперь Кевин — подчиненный Ваниды, которая является подчиненной Jill, которая является подчиненной David. Это означает, что Kevin находится на уровне **/3/1/1/** . Чтобы переместить всех подчиненных Jill к новому руководителю, мы присвоим новое значение всем узлам, имеющим значение **/3/** в столбце **OrgNode** . Выполните следующий код, чтобы произвести изменение, в результате которого Wanida станет подчиненной Sariya, но Kevin останется подчиненным Wanida:  
  
    ```sql  
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
  
    ```sql  
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
  
