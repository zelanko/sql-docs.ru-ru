---
title: "Создание таблицы (SQL граф) | Документы Microsoft"
ms.custom: 
ms.date: 05/04/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
ms.assetid: 
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c32a8c4f683f20c4384089c1d2552614090f9b3d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-table-sql-graph"></a>Создание таблицы (граф SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Создает новую таблицу graph SQL либо как `NODE` или `EDGE` таблицы. 
  
> [!NOTE]   
>  Стандартные инструкции Transact-SQL, в разделе [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).
  
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
Этот документ описывает только аргументы, относящиеся к SQL graph. Полный список и описание поддерживаемых аргументов см. в разделе [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)

 *имя_базы_данных*    
 Имя базы данных, в которой создается таблица. *database_name* необходимо указать имя существующей базы данных. Если не указан, *имя_базы_данных* значения по умолчанию для текущей базы данных. Имя входа для текущего соединения должны быть связаны с Идентификатором пользователя, существующего в базы данных, указанной *имя_базы_данных*, и этот пользователь должен обладать разрешениями CREATE TABLE.  
  
 *schema_name*    
 Имя схемы, которой принадлежит новая таблица.  
  
 *имя_таблицы*    
 — Это имя узла или края таблицы. Имена таблиц должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). *имя_таблицы* не может превышать 128 символов, за исключением имен локальных временных таблиц (имена с префиксом знак номера (#)), не должна превышать 116 символов.  
  
 УЗЕЛ   
 Создает таблицу узла.

 EDGE  
 Создает краевую таблицу.  
  
## <a name="remarks"></a>Замечания  
Создание временной таблицы, узел или краевой таблице не поддерживается.  

Создание узла или край таблицы как временная таблица не поддерживается.

База данных Stretch не поддерживается для узла или края таблицы.

Узел или край таблицы не могут быть внешних таблицах (polybase поддержка graph таблиц). 
  
 
## <a name="examples"></a>Примеры  
  
### <a name="a-create-a-node-table"></a>A. Создание `NODE` таблицы
 В следующем примере показано, как создать `NODE` таблицы

```
 CREATE TABLE Person (
        ID INTEGER PRIMARY KEY, 
        name VARCHAR(100), 
        email VARCHAR(100)
 ) AS NODE;
```

### <a name="b-create-an-edge-table"></a>Б. Создание `EDGE` таблицы
В следующих примерах показано создание `EDGE` таблиц

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
 [INSERT (SQL граф)](../../t-sql/statements/insert-sql-graph.md)]  
 [График обработка с помощью SQL Server 2017 г.](../../relational-databases/graphs/sql-graph-overview.md)


