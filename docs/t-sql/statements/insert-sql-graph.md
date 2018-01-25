---
title: "INSERT (SQL граф) | Документы Microsoft"
description: "ВСТАВЬТЕ синтаксис SQL Graph узла или края таблицы."
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], SQL graph
- SQL graph, INSERT statement
ms.assetid: 
caps.latest.revision: "1"
author: shkale-msft
ms.author: shkale
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6bac7f1d7da67f319a9c84425b370bb61a35ca19
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="insert-sql-graph"></a>INSERT (граф SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Добавляет одну или несколько строк для `node` или `edge` в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 

> [!NOTE]   
>  Стандартные инструкции Transact-SQL, в разделе [вставить ТАБЛИЦУ (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md).
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="insert-into-node-table-syntax"></a>Вставка в таблицу синтаксис для узла 
Синтаксис для вставки в таблицу узел совпадает с обычной таблицы. 

```  
[ WITH <common_table_expression> [ ,...n ] ]  
INSERT   
{  
        [ TOP ( expression ) [ PERCENT ] ]   
        [ INTO ]   
        { <object> | rowset_function_limited   
          [ WITH ( <Table_Hint_Limited> [ ...n ] ) ]  
        }  
    {  
        [ (column_list) ] | [(<edge_table_column_list>)]  
        [ <OUTPUT Clause> ]  
        { VALUES ( { DEFAULT | NULL | expression } [ ,...n ] ) [ ,...n     ]   
        | derived_table   
        | execute_statement  
        | <dml_table_source>  
        | DEFAULT VALUES   
        }  
    }  
}  
[;]  
  
<object> ::=  
{   
    [ server_name . database_name . schema_name .   
      | database_name .[ schema_name ] .   
      | schema_name .   
    ]  
    node_table_name  | edge_table_name
}  
  
<dml_table_source> ::=  
    SELECT <select_list>  
    FROM ( <dml_statement_with_output_clause> )   
      [AS] table_alias [ ( column_alias [ ,...n ] ) ]  
    [ WHERE <on_or_where_search_condition> ]  
        [ OPTION ( <query_hint> [ ,...n ] ) ]  

<on_or_where_search_condition> ::=
    {  <search_condition_with_match> | <search_condition> }

<search_condition_with_match> ::=
    { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) }
    [ AND { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<search_condition> ::=
    { [ NOT ] <predicate> | ( <search_condition> ) }
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<graph_predicate> ::=
    MATCH( <graph_search_pattern> [ AND <graph_search_pattern> ] [ , ...n] )

<graph_search_pattern>::=
    <node_alias> { { <-( <edge_alias> )- | -( <edge_alias> )-> } <node_alias> }

<edge_table_column_list> ::=
    ($from_id, $to_id, [column_list])

```  
  
 
## <a name="arguments"></a>Аргументы  
 Этот документ описывает аргументы, относящиеся к SQL graph. Полный список и описание поддерживаемых аргументов в инструкции INSERT см. в разделе [вставить ТАБЛИЦУ (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)

 INTO  
 Необязательное ключевое слово, которое можно использовать между `INSERT` и целевой таблицы.  
  
 *search_condition_with_match*   
 `MATCH`предложение может использоваться при вставке в таблицу узла или край во вложенном запросе. Для `MATCH` синтаксис инструкции см. в разделе [соответствия GRAPH (Transact-SQL)](../../t-sql/queries/match-sql-graph.md)

 *graph_search_pattern*   
 Шаблон поиска для `MATCH` предложения как часть предиката графа.

 *edge_table_column_list*   
 Пользователи должны предоставить значения для `$from_id` и `$to_id` при вставке в граница. Если значение не указано или пустые значения вставляются в этих столбцах, будет возвращена ошибка. 
  

## <a name="remarks"></a>Remarks  
Вставка в узел — то же, что вставка в любой реляционной таблицы. Значения для столбца node_id $ создаются автоматически.

При вставке в краевую таблицу, пользователи должны предоставить значения для `$from_id` и `$to_id` столбцов.   

Инструкции BULK insert для таблицы узла — остается аналогично реляционной таблице.

Перед массовой вставки в краевую таблицу необходимо импортировать узел таблиц. Значения для `$from_id` и `$to_id` можно извлечь из `$node_id` узел таблицы и вставляются в качестве границ. 

  
### <a name="permissions"></a>Разрешения  
 Требуется разрешение INSERT на целевую таблицу.  
  
 Вставить разрешения по умолчанию предоставляются членам **sysadmin** предопределенной роли сервера **db_owner** и **db_datawriter** фиксированной роли базы данных, а также владельцу таблицы. Члены **sysadmin**, **db_owner**и **db_securityadmin** ролей, а также владелец таблицы могут передавать разрешения другим пользователям.  
  
 Чтобы выполнить инструкцию INSERT с помощью параметра BULK функции OPENROWSET, необходимо быть членом **sysadmin** предопределенной роли сервера или **bulkadmin** предопределенной роли сервера.  
  

## <a name="examples"></a>Примеры  
  
#### <a name="a--insert-into-node-table"></a>A.  Вставка в таблицу с узла  
 Следующий пример создает узел таблицы Person и вставляет строки 2 в этой таблице.

 ```
 -- Create person node table
 CREATE TABLE dbo.Person (ID integer PRIMARY KEY, name varchar(50)) AS NODE;
 
 -- Insert records for Alice and John
 INSERT INTO dbo.Person VALUES (1, 'Alice');
 INSERT INTO dbo.Person VALUES (2,'John');
 ```
  
#### <a name="b--insert-into-edge-table"></a>Б.  Вставьте в краевой таблицы  
 Следующий пример создает таблицу edge friend и в таблицу вставляется граница.

 ```
 -- Create friend edge table
 CREATE TABLE dbo.friend (start_date DATE) AS EDGE;

 -- Create a friend edge, that connect Alice and John
 INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'John'), '9/15/2011');
 ```

  
## <a name="see-also"></a>См. также  
 [Вставить ТАБЛИЦУ &#40; Transact-SQL &#41;](../../t-sql/statements/insert-transact-sql.md)   
 [График обработка с помощью SQL Server 2017 г.](../../relational-databases/graphs/sql-graph-overview.md)  


