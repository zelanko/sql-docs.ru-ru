---
description: CREATE TABLE (граф SQL)
title: CREATE TABLE (граф SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/09/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SQL_GRAPH_TSQL
- TABLE
- CREATE_TABLE_TSQL
- NODE
- NODE_TSQL
- AS_NODE
- AS_NODE_TSQL
- EDGE
- EDGE_TSQL
- AS_EDGE
- AS_EDGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- graph
- SQL graph
- CREATE TABLE SQL graph
- NODE
- EDGE
- SQL graph, CREATE TABLE statement
ms.assetid: ''
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 77fe857a66ca90b25e5cc4248304d37d68c2a2bd
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97438939"
---
# <a name="create-table-sql-graph"></a>CREATE TABLE (граф SQL)
[!INCLUDE[SQL Server 2017](../../includes/applies-to-version/sqlserver2017.md)]

Создает новую таблицу графа SQL как таблицу `NODE` или `EDGE`. 
  
> [!NOTE]   
>  Сведения о стандартных инструкциях Transact-SQL см. в разделе [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
CREATE TABLE   
    { database_name.schema_name.table_name | schema_name.table_name | table_name }
    ( { <column_definition> } 
       | <computed_column_definition>
       | <column_set_definition>
       | [ <table_constraint> ] [ ,... n ]
       | [ <table_index> ] }
          [ ,...n ]
    )   
    AS [ NODE | EDGE ]
    [ ON { partition_scheme_name ( partition_column_name )
           | filegroup
           | "default" } ]
[ ; ] 

< table_constraint > ::=
[ CONSTRAINT constraint_name ]
{
    { PRIMARY KEY | UNIQUE }
        [ CLUSTERED | NONCLUSTERED ]
        (column [ ASC | DESC ] [ ,...n ] )
        [
            WITH FILLFACTOR = fillfactor
           |WITH ( <index_option> [ , ...n ] )
        ]
        [ ON { partition_scheme_name (partition_column_name)
            | filegroup | "default" } ]
    | FOREIGN KEY
        ( column [ ,...n ] )
        REFERENCES referenced_table_name [ ( ref_column [ ,...n ] ) ]
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]
        [ NOT FOR REPLICATION ]
    | CONNECTION
        ( { node_table TO node_table } 
          [ , {node_table TO node_table }]
          [ , ...n ]
        )
        [ ON DELETE { NO ACTION | CASCADE } ]
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )
```  
  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
В этом документе описываются только аргументы, относящиеся к SQL Graph. Полный список и описание поддерживаемых аргументов см. в разделе [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).

 *database_name*    
 Имя базы данных, в которой создается таблица. Параметр *database_name* должен указывать имя существующей базы данных. Если не указано, в качестве *database_name* по умолчанию выбирается текущая база данных. Имя входа для текущего соединения должно быть связано с идентификатором пользователя, существующего в базе данных, указанной аргументом *database_name*, а этот пользователь должен обладать разрешениями CREATE TABLE.  
  
 *schema_name*    
 Имя схемы, которой принадлежит новая таблица.  
  
 *table_name*      
 Это имя таблицы узлов или граничной таблицы. Имена таблиц должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md). Аргумент *table_name* может состоять не более чем из 128 символов, за исключением имен локальных временных таблиц (имена с префиксом из одного символа решетки #), длина которых не должна превышать 116 символов.  
  
 NODE   
 Создает таблицу узлов.

 EDGE  
 Создает граничную таблицу.  
 
 *table_constraint*   
 Задает свойства ограничений PRIMARY KEY, UNIQUE, FOREIGN KEY, CONNECTION или CHECK либо определения DEFAULT, добавленного в таблицу.
 
 > [!NOTE]   
 > Ограничение CONNECTION применяется только к типу граничной таблицы.
 
 ON { partition_scheme | filegroup | "default" }    
 Указывает схему секционирования или файловую группу, в которой хранится таблица. Если аргумент partition_scheme указан, таблица будет разбита на секции, хранимые в одной или нескольких файловых группах, указанных в аргументе partition_scheme. Если указан аргумент filegroup, таблица сохраняется в файловой группе с таким именем. Это должна быть существующая файловая группа в базе данных. Если указано значение "default" или параметр ON не определен вообще, таблица сохраняется в файловой группе по умолчанию. Механизм хранения таблицы, указанный в инструкции CREATE TABLE, изменить в дальнейшем невозможно.

 ON {partition_scheme | filegroup | "default"}    
 Также может указываться в ограничении PRIMARY KEY или UNIQUE. С помощью этих ограничений создаются индексы. Если указан аргумент filegroup, индекс сохраняется в файловой группе с таким именем. Если указано значение "default" или параметр ON не определен вообще, индекс сохраняется в той же файловой группе, что и таблица. Если ограничение PRIMARY KEY или UNIQUE создает кластеризованный индекс, страницы данных таблицы сохраняются в той же файловой группе, что и индекс. Если ограничение создает кластеризованный индекс (с помощью параметра CLUSTERED или другим способом), а указанный аргумент partition_scheme отличается от аргументов partition_scheme и filegroup из определения таблицы, либо, наоборот, принимается во внимание только определение ограничения, а все остальное не учитывается.
  
## <a name="remarks"></a>Комментарии

Создание временной таблицы в качестве таблицы узлов или граничной таблицы не поддерживается.  

Создание таблицы узлов или граничной таблицы в качестве временной таблицы не поддерживается.

Stretch Database не поддерживается для таблицы узлов или граничной таблицы.

Таблицы узлов или граничные таблицы не могут быть внешними (поддержка PolyBase для графовых таблиц отсутствует). 

Несекционированную таблицу узлов графа или граничную таблицу невозможно преобразовать в секционированную. 
  
 
## <a name="examples"></a>Примеры  
  
### <a name="a-create-a-node-table"></a>A. Создание таблицы `NODE`
 В следующем примере показано создание таблицы `NODE`.

```sql
 CREATE TABLE Person (
        ID INTEGER PRIMARY KEY, 
        name VARCHAR(100), 
        email VARCHAR(100)
 ) AS NODE;
```

### <a name="b-create-an-edge-table"></a>Б. Создание таблицы `EDGE`
В следующем примере показано создание таблиц `EDGE`.

```sql
 CREATE TABLE friends (
    id INTEGER PRIMARY KEY,
    start_date DATe
 ) AS EDGE;
```

```sql
 -- Create a likes edge table, this table does not have any user defined attributes   
 CREATE TABLE likes AS EDGE;
```

В следующем примере моделируется правило, согласно которому **только** люди могут быть друзьями. Это означает, что эта граница не позволяет ссылаться на другие узлы, кроме Person.

```
/* Create friend edge table with CONSTRAINT, restricts for nodes and it direction */
CREATE TABLE dbo.FriendOf(
  CONSTRAINT cnt_Person_FriendOf_Person
    CONNECTION (dbo.Person TO dbo.Person) 
)AS EDGE;
```


## <a name="see-also"></a>См. также 
 [ALTER TABLE table_constraint](../../t-sql/statements/alter-table-table-constraint-transact-sql.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [INSERT (граф SQL)](../../t-sql/statements/insert-sql-graph.md)  
 [Graph Processing with SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md) (Работа с графами в SQL Server 2017)

