---
title: MATCH (SQL Graph) | Документы Майкрософт
ms.custom: ''
ms.date: 05/05/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- MATCH
- MATCH_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MATCH statement [SQL Server], SQL graph
- SQL graph, MATCH statement
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 72d151fc51eddbf2ce9a2cc4626fa4f5d2bec9de
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43081688"
---
# <a name="match-transact-sql"></a>MATCH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

  Определяет условие поиска для графа. MATCH может использоваться только с таблицами узлов и граничными таблицами графа в инструкции SELECT как часть предложения WHERE. 
  
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
Указывает шаблон для поиска или путь для прохода в графе. Для прохода по графу этот шаблон использует синтаксис ASCII-арта. Шаблон переходит с одного узла на другой через границу в направлении, указанном стрелкой. Имена границ или псевдонимы указываются в скобках. Имена узлов или псевдонимы отображаются на двух концах стрелки. Стрелка может указывать любое направление в шаблоне.

*node_alias*  
Имя или псевдоним таблицы узлов, указанный в предложении FROM.

*edge_alias*  
Имя или псевдоним граничной таблицы, указанный в предложении FROM.


## <a name="remarks"></a>Remarks  
Имена узлов в MATCH могут повторяться.  Другими словами, в одном запросе через узел можно проходить произвольное число раз.  
Имя границы не может повторяться внутри MATCH.  
Граница может указывать в любом направлении, но должна иметь явное направление.  
Операторы OR и NOT не поддерживаются в шаблоне MATCH. MATCH можно объединить с другими выражениями с помощью AND в предложении WHERE. Однако объединение с другими выражениями с помощью OR или NOT не поддерживается. 

## <a name="examples"></a>Примеры  
### <a name="a--find-a-friend"></a>A.  Поиск друга 
 В следующем примере создается таблица узлов Person и граничная таблица Friends, вставляются некоторые данные и затем с помощью MATCH выполняется поиск друзей Alice (человека в графе).

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

 ### <a name="b--find-friend-of-a-friend"></a>Б.  Поиск друга друга
 В следующем примере предпринимается попытка найти друга Alice. 

 ```
SELECT Person3.name AS FriendName 
FROM Person Person1, friend, Person Person2, friend friend2, Person Person3
WHERE MATCH(Person1-(friend)->Person2-(friend2)->Person3)
AND Person1.name = 'Alice';

 ```

### <a name="c--more-match-patterns"></a>В.  Дополнительные шаблоны `MATCH`
 Ниже приведен ряд дополнительных способов, которыми можно указать шаблон внутри MATCH.

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
 

## <a name="see-also"></a>См. также:  
 [CREATE TABLE (SQL Graph)](../../t-sql/statements/create-table-sql-graph.md)   
 [INSERT (граф SQL)](../../t-sql/statements/insert-sql-graph.md)  
 [Graph Processing with SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md) (Работа с графами в SQL Server 2017)  
