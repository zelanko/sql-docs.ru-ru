---
description: MATCH (Transact-SQL)
title: MATCH (SQL Graph) | Документы Майкрософт
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- MATCH
- MATCH_TSQL
- SHORTEST_PATH
dev_langs:
- TSQL
helpviewer_keywords:
- MATCH statement [SQL Server], SQL graph
- SQL graph, MATCH statement
- Shortest Path, shortest_path
author: shkale-msft
ms.author: shkale
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b3d0f5307b8a9b96dec8b81f00550dbcd639ac9a
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91116262"
---
# <a name="match-transact-sql"></a>MATCH (Transact-SQL)
[!INCLUDE[SQL Server 2017](../../includes/applies-to-version/sqlserver2017.md)]

  Определяет условие поиска для графа. MATCH может использоваться только с таблицами узлов и граничными таблицами графа в инструкции SELECT как часть предложения WHERE. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
MATCH (<graph_search_pattern>)

<graph_search_pattern>::=
  {  
      <simple_match_pattern> 
    | <arbitrary_length_match_pattern>  
    | <arbitrary_length_match_last_node_predicate> 
  }

<simple_match_pattern>::=
  {
      LAST_NODE(<node_alias>) | <node_alias>   { 
          { <-( <edge_alias> )- } 
        | { -( <edge_alias> )-> }
        <node_alias> | LAST_NODE(<node_alias>)
        } 
  }
  [ { AND } { ( <simple_match_pattern> ) } ]
  [ ,...n ]

<node_alias> ::=
  node_table_name | node_table_alias 

<edge_alias> ::=
  edge_table_name | edge_table_alias


<arbitrary_length_match_pattern>  ::=
  { 
    SHORTEST_PATH( 
      <arbitrary_length_pattern> 
      [ { AND } { <arbitrary_length_pattern> } ] 
      [ ,…n] 
    )
  } 

<arbitrary_length_match_last_node_predicate> ::=
  {  LAST_NODE( <node_alias> ) = LAST_NODE( <node_alias> ) }


<arbitrary_length_pattern> ::=
    {  LAST_NODE( <node_alias> )   | <node_alias>
     ( <edge_first_al_pattern> [<edge_first_al_pattern>…,n] )
     <al_pattern_quantifier> 
  }
    |  ( {<node_first_al_pattern> [<node_first_al_pattern> …,n] )
        <al_pattern_quantifier> 
        LAST_NODE( <node_alias> ) | <node_alias> 
 }
    
<edge_first_al_pattern> ::=
  { (  
        { -( <edge_alias> )->   } 
      | { <-( <edge_alias> )- } 
      <node_alias>
      ) 
  } 

<node_first_al_pattern> ::=
  { ( 
      <node_alias> 
        { <-( <edge_alias> )- } 
      | { -( <edge_alias> )-> }
      ) 
  } 


<al_pattern_quantifier> ::=
  {
        +
      | { 1 , n }
  }

n -  positive integer only.
 
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
*graph_search_pattern*  
Указывает шаблон для поиска или путь для прохода в графе. Для прохода по графу этот шаблон использует синтаксис ASCII-арта. Шаблон переходит с одного узла на другой через границу в направлении, указанном стрелкой. Имена или псевдонимы границы указываются в скобках. Имена узлов или псевдонимы отображаются на двух концах стрелки. Стрелка может указывать любое направление в шаблоне.

*node_alias*  
Имя или псевдоним таблицы узлов, указанный в предложении FROM.

*edge_alias*  
Имя или псевдоним граничной таблицы, указанный в предложении FROM.

*SHORTEST_PATH*   
Эта функция используется для поиска кратчайшего пути между двумя заданными узлами в графе или между определенным узлом и всеми остальными узлами в графе. В качестве входных данных она принимает шаблон произвольной длины, поиск которого повторно выполняется в графе. 

*arbitrary_length_match_pattern*  
Указывает узлы и ребра, которые нужно повторно обходить, пока не будет найден требуемый узел или достигнуто максимальное число итераций, указанное в шаблоне. 

*al_pattern_quantifier*   
Шаблон произвольной длины принимает квантификаторы шаблона стиля регулярного выражения, чтобы указать количество повторов для определенного шаблона поиска. Поддерживаются следующие квантификаторы шаблона поиска:   
* **+** : 1 или более повторов шаблона. Действие прекращается, как только будет найден кратчайший путь.    
* **{1,n}** : от 1 до "n" повторов шаблона. Действие прекращается, как только будет найден кратчайший путь.     

## <a name="remarks"></a>Комментарии  
Имена узлов в MATCH могут повторяться.  Другими словами, в одном запросе через узел можно проходить произвольное число раз.  
Имя границы не может повторяться внутри MATCH.  
Граница может указывать в любом направлении, но должна иметь явное направление.  
Операторы OR и NOT не поддерживаются в шаблоне MATCH. MATCH можно объединить с другими выражениями с помощью AND в предложении WHERE. Однако объединение с другими выражениями с помощью OR или NOT не поддерживается. 

## <a name="examples"></a>Примеры  
### <a name="a--find-a-friend"></a>A.  Поиск друга 
 В следующем примере создается таблица узлов Person и граничная таблица Friends, вставляются некоторые данные и затем с помощью MATCH выполняется поиск друзей Alice (человека в графе).

 ```sql
 -- Create person node table
 CREATE TABLE dbo.Person (ID INTEGER PRIMARY KEY, name VARCHAR(50)) AS NODE;
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

 ```sql
SELECT Person3.name AS FriendName 
FROM Person Person1, friend, Person Person2, friend friend2, Person Person3
WHERE MATCH(Person1-(friend)->Person2-(friend2)->Person3)
AND Person1.name = 'Alice';
 ```

### <a name="c--more-match-patterns"></a>В.  Дополнительные шаблоны `MATCH`
 Ниже приведен ряд дополнительных способов, которыми можно указать шаблон внутри MATCH.

 ```sql
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
 [CREATE TABLE (SQL Graph)](../../t-sql/statements/create-table-sql-graph.md)   
 [INSERT (граф SQL)](../../t-sql/statements/insert-sql-graph.md)  
 [Graph Processing with SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md) (Работа с графами в SQL Server 2017)  
