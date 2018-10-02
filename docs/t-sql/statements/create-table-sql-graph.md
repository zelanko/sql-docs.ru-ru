---
title: CREATE TABLE (граф SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/04/2017
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
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a143011f3fb93c9aeef6d699e89e0d12b664409c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855732"
---
# <a name="create-table-sql-graph"></a>CREATE TABLE (граф SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Создает новую таблицу графа SQL как таблицу `NODE` или `EDGE`. 
  
> [!NOTE]   
>  Сведения о стандартных инструкциях Transact-SQL см. в разделе [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    ( { <column_definition> } [ ,...n ] )   
    AS [ NODE | EDGE ]
[ ; ]  
```  
  
  
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
  
## <a name="remarks"></a>Remarks  
Создание временной таблицы в качестве таблицы узлов или граничной таблицы не поддерживается.  

Создание таблицы узлов или граничной таблицы в качестве временной таблицы не поддерживается.

Stretch Database не поддерживается для таблицы узлов или граничной таблицы.

Таблицы узлов или граничные таблицы не могут быть внешними (поддержка polybase для графовых таблиц отсутствует). 
  
 
## <a name="examples"></a>Примеры  
  
### <a name="a-create-a-node-table"></a>A. Создание таблицы `NODE`
 В следующем примере показано создание таблицы `NODE`.

```
 CREATE TABLE Person (
        ID INTEGER PRIMARY KEY, 
        name VARCHAR(100), 
        email VARCHAR(100)
 ) AS NODE;
```

### <a name="b-create-an-edge-table"></a>Б. Создание таблицы `EDGE`
В следующем примере показано создание таблиц `EDGE`.

```
 CREATE TABLE friends (
    id integer PRIMARY KEY,
    start_date date
 ) AS EDGE;

```

```
 -- Create a likes edge table, this table does not have any user defined attributes   
 CREATE TABLE likes AS EDGE;

```


## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [INSERT (граф SQL)](../../t-sql/statements/insert-sql-graph.md)  
 [Graph Processing with SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md) (Работа с графами в SQL Server 2017)

