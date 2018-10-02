---
title: INSERT (SQL Graph) | Документы Майкрософт
description: INSERT синтаксис для таблиц узлов или граничных таблиц SQL Graph.
ms.date: 05/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.custom: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], SQL graph
- SQL graph, INSERT statement
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c0a22547436f8a511a5a61db35ec99a919d84e4b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644032"
---
# <a name="insert-sql-graph"></a>INSERT (граф SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Добавляет одну или несколько строк в таблицу `node` или `edge` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 

> [!NOTE]   
>  Сведения о стандартных инструкциях Transact-SQL см. в разделе [INSERT TABLE (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md).
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="insert-into-node-table-syntax"></a>Синтаксис INSERT (вставки) в таблицу узлов 
Синтаксис вставки в таблицу узлов совпадает с синтаксисом ставки в обычную таблицу. 

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
 В этом документе описываются только аргументы, относящиеся к SQL Graph. Полный список и описание поддерживаемых аргументов в инструкции INSERT см. в разделе [INSERT TABLE (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md).

 INTO  
 Необязательное ключевое слово, которое можно использовать между `INSERT` и целевой таблицей.  
  
 *search_condition_with_match*   
 Предложение `MATCH` можно использовать во вложенном запросе при вставке в таблицу узлов или граничную таблицу. Сведения о синтаксисе инструкции `MATCH` см. в разделе [GRAPH MATCH (Transact-SQL)](../../t-sql/queries/match-sql-graph.md)

 *graph_search_pattern*   
 Шаблон поиска для предложения `MATCH` как часть предиката графа.

 *edge_table_column_list*   
 При вставке в граничную таблицу пользователи должны указать значения для `$from_id` и `$to_id`. Если в эти столбцы вставлены пустые значения или значения не указаны, будет возвращена ошибка. 
  

## <a name="remarks"></a>Remarks  
Вставка в таблицу узлов аналогична вставке в любую реляционную таблицу. Значения для столбца node_id $ создаются автоматически.

При вставке в граничную таблицу пользователи должны указать значения для столбцов `$from_id` и `$to_id`.   

Операция вставки с параметром BULK в таблицу узлов аналогична вставке в реляционную таблицу.

Перед массовой вставкой в граничную таблицу необходимо импортировать таблицы узлов. Затем значения для `$from_id` и `$to_id` можно извлечь из столбца `$node_id` таблицы узлов и вставить в виде границ. 

  
### <a name="permissions"></a>Разрешения  
 Требуется разрешение INSERT на целевую таблицу.  
  
 Разрешения INSERT назначаются по умолчанию членам предопределенной роли сервера **sysadmin**, предопределенных ролей базы данных **db_owner** и **db_datawriter**, а также владельцу таблицы. Члены ролей **sysadmin**, **db_owner** и **db_securityadmin**, а также владелец таблицы могут передавать разрешения другим пользователям.  
  
 Чтобы выполнить инструкцию INSERT с параметром BULK функции OPENROWSET, необходимо быть членом предопределенной роли сервера **sysadmin** или **bulkadmin**.  
  

## <a name="examples"></a>Примеры  
  
#### <a name="a--insert-into-node-table"></a>A.  Вставка в таблицу узлов  
 В следующем примере создается таблица узлов Person, и затем в нее вставляются две строки.

 ```
 -- Create person node table
 CREATE TABLE dbo.Person (ID integer PRIMARY KEY, name varchar(50)) AS NODE;
 
 -- Insert records for Alice and John
 INSERT INTO dbo.Person VALUES (1, 'Alice');
 INSERT INTO dbo.Person VALUES (2,'John');
 ```
  
#### <a name="b--insert-into-edge-table"></a>Б.  Вставка в граничную таблицу  
 В следующем примере создается граничная таблица Friend, и затем в нее вставляются границы.

 ```
 -- Create friend edge table
 CREATE TABLE dbo.friend (start_date DATE) AS EDGE;

 -- Create a friend edge, that connect Alice and John
 INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'John'), '9/15/2011');
 ```

  
## <a name="see-also"></a>См. также:  
 [INSERT TABLE (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [Graph Processing with SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md) (Работа с графами в SQL Server 2017)  


