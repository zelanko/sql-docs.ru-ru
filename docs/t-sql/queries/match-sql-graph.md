---
title: "СООТВЕТСТВИЕ (SQL граф) | Документы Microsoft"
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MATCH
- MATCH_TSQL
dev_langs: TSQL
helpviewer_keywords:
- MATCH statement [SQL Server], SQL graph
- SQL graph, MATCH statement
ms.assetid: 
caps.latest.revision: "1"
author: shkale-msft
ms.author: shkale
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cbfa524cb9957ba557cfd239dae16a93aed919bf
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="match-transact-sql"></a>СООТВЕТСТВИЕ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

  Указывает условие поиска для графа. СООТВЕТСТВИЕ может использоваться только с graph узла и границей таблицы в инструкции SELECT как часть предложения WHERE. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
MATCH (<graph_search_pattern>)

<graph_search_pattern>::=
    {<node_alias> { 
                     { <-( <edge_alias> )- } 
                   | { -( <edge_alias> )-> }
                 <node_alias> 
                 } 
     }
     [ { AND } { ( <graph_search_pattern> ) } ]
     [ ,...n ]
  
<node_alias> ::=
    node_table_name | node_alias 

<edge_alias> ::=
    edge_table_name | edge_alias
```

## <a name="arguments"></a>Аргументы  
*graph_search_pattern*  
Указывает шаблон для поиска или в пути обхода в графе. Этот шаблон используется синтаксис art ASCII обход пути в графе. Шаблон переходит из одного узла на другой через ребром в направлении стрелки предоставлен. Внутри parantheses предоставляются Edge имена или псевдонимы. Имена узлов или псевдонимы отображаются по краям две стрелки. Стрелку могут попасть в любом направлении в шаблоне.

*node_alias*  
Имя или псевдоним таблицы узел, указанный в предложении FROM.

*edge_alias*  
Имя или псевдоним в предложении FROM краевую таблицу.


## <a name="remarks"></a>Remarks  
Имена узлов в СООТВЕТСТВИЕ может повторяться.  Другими словами, узел может быть обход произвольное число раз в одном запросе.  
Имя край не может повторяться внутри СОВПАДЕНИЯ.  
Граница может указывать в любом направлении, но он должен иметь явные направления.  
ИЛИ и не операторы не поддерживаются в шаблоне СОПОСТАВЛЕНИЯ. СОВПАДЕНИЯ можно объединить с другими выражениями с помощью и в предложении WHERE. Тем не менее, сочетая ее с другими выражений с помощью OR или не не поддерживается. 

## <a name="examples"></a>Примеры  
### <a name="a--find-a-friend"></a>A.  Найти друга 
 Следующий пример создает узел таблицы Person и друзья краевую таблицу, вставляет некоторые данные и использует соответствия для поиска дружественными Алиса человека в графе.

 ```
 -- Create person node table
 CREATE TABLE dbo.Person (ID integer PRIMARY KEY, name varchar(50)) AS NODE;
 CREATE TABLE dbo.friend (start_date DATE) AS EDGE;

 -- Insert into node table
 INSERT INTO dbo.Person VALUES (1, 'Alice');
 INSERT INTO dbo.Person VALUES (2,'John');
 INSERT INTO dbo.Person VALUES (3, 'Jacob');

-- Insert into edge table
INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'John'), '9/15/2011');

INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'Jacob'), '10/15/2011');

INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'John'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'Jacob'), '10/15/2012');

-- use MATCH in SELECT to find friends of Alice
SELECT Person2.name AS FriendName
FROM Person Person1, friend, Person Person2
WHERE MATCH(Person1-(friend)->Person2)
AND Person1.name = 'Alice';

 ```

 ### <a name="b--find-friend-of-a-friend"></a>Б.  Найти друг друга
 Следующий пример пытается найти друг друга Анна. 

 ```
SELECT Person3.name AS FriendName 
FROM Person Person1, friend, Person Person2, friend friend2, Person Person3
WHERE MATCH(Person1-(friend)->Person2-(friend2)->Person3)
AND Person1.name = 'Alice';

 ```

### <a name="c--more-match-patterns"></a>В.  Дополнительные `MATCH` шаблонов
 Ниже приведены некоторые дополнительные способы, в котором можно указать шаблон внутри СОВПАДЕНИЯ.

 ```
 -- Find a friend
    SELECT Person2.name AS FriendName
    FROM Person Person1, friend, Person Person2
    WHERE MATCH(Person1-(friend)->Person2);
    
-- The pattern can also be expressed as below

    SELECT Person2.name AS FriendName
    FROM Person Person1, friend, Person Person2 
    WHERE MATCH(Person2<-(friend)-Person1);


-- Find 2 people who are both friends with same person
    SELECT Person1.name AS Friend1, Person2.name AS Friend2
    FROM Person Person1, friend friend1, Person Person2, 
         friend friend2, Person Person0
    WHERE MATCH(Person1-(friend1)->Person0<-(friend2)-Person2);
    
-- this pattern can also be expressed as below

    SELECT Person1.name AS Friend1, Person2.name AS Friend2
    FROM Person Person1, friend friend1, Person Person2, 
         friend friend2, Person Person0
    WHERE MATCH(Person1-(friend1)->Person0 AND Person2-(friend2)->Person0);
 ```
 

## <a name="see-also"></a>См. также  
 [СОЗДАТЬ ТАБЛИЦУ &#40; Граф SQL &#41;](../../t-sql/statements/create-table-sql-graph.md)   
 [INSERT (SQL граф)](../../t-sql/statements/insert-sql-graph.md)]  
 [График обработка с помощью SQL Server 2017 г.](../../relational-databases/graphs/sql-graph-overview.md)  
