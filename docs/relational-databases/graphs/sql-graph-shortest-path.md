---
title: КРАТЧАЙШИЙ путь (граф SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- SHORTEST PATH
- SHORTEST_PATH
dev_langs:
- TSQL
helpviewer_keywords:
- MATCH statement [SQL Server], SQL graph
- SQL graph, MATCH statement
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3ed9fbb373febd803fedfd7519df7656c23181f2
ms.sourcegitcommit: f97394f18f8509aec596179acd4c59d8492a4cd2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/08/2019
ms.locfileid: "67652840"
---
# <a name="shortestpath-transact-sql"></a>SHORTEST_PATH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver2015-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Указывает условие поиска для графа, который является поиск рекурсивно или несколько раз. SHORTEST_PATH может использоваться внутри MATCH с узлов и ребер таблицами графа, в инструкции SELECT. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="shortest-path"></a>Кратчайший путь
Функция SHORTEST_PATH позволяет найти:    
* Кратчайший путь между двумя заданные узлы/сущности
* Единый источник кратчайшего пути.
* Кратчайшего пути из нескольких узлов источника для нескольких целевых узлов.

Он принимает шаблон произвольной длины в качестве входных данных и возвращает кратчайшего пути, который существует между двумя узлами. Эта функция может использоваться только внутри MATCH. Функция возвращает только один кратчайший путь между любыми двумя узлами заданного. Если существует два или более короткий путь одинаковой длины между любой парой исходного и целевого узлов, функция возвращает только один путь, который был найден первый во время обхода. Обратите внимание на то, что, шаблон произвольной длины могут быть заданы только внутри функции SHORTEST_PATH. 

Ссылаться на [MATCH (SQL Graph)](../../t-sql/queries/match-sql-graph.md) синтаксиса. 

## <a name="for-path"></a>ДЛЯ ПУТИ
ДЛЯ пути должен использоваться с именами узлов или граничную таблицу в предложении FROM, который будет участвовать в шаблоне произвольной длины. ДЛЯ пути сообщает модулю, что возвращает упорядоченную коллекцию, представляющий список узлов или границ, найти пути обхода узлов или граничную таблицу. Атрибуты из этих таблиц, не может быть защищен непосредственно в предложении SELECT. Должен использоваться для проекта атрибуты из этих таблиц, граф пути агрегатные функции.  

## <a name="arbitrary-length-pattern"></a>Шаблон произвольной длины
Этот шаблон включает в себя узлы и ребра, которые должны обходиться повторно, пока не будет достигнут нужный узел, или пока максимальное число итераций, как указано в шаблоне выполняется. Каждый раз при выполнении запроса, в результате выполнения этого шаблона будет упорядоченная коллекция узлы и ребра, просматривать вдоль пути с начального узла конечного узла. Это шаблон регулярного выражения стиль синтаксиса и поддерживаются следующие квантификаторы два шаблона:

* **‘+’** : 1 или более повторов шаблона. Действие прекращается, как только будет найден кратчайший путь.
* **{1,n}** : от 1 до "n" повторов шаблона. Завершить работу, как только найден кратчайший.

## <a name="lastnode"></a>LAST_NODE
Функция LAST_NODE() позволяет двум шаблонам обхода произвольной длины цепочки. Он может использоваться в сценариях, где:    
* Несколько шаблонов кратчайшего пути используются в запросе и одним из шаблонов начинается с ПОСЛЕДНЕГО узла предыдущий шаблон.
* В том же LAST_NODE() слияния двух шаблонов кратчайшего пути.

## <a name="graph-path-order"></a>Порядок путь Graph
Порядок путь Graph ссылается порядку данных в выходном пути. Порядок путь выходных всегда начинается с не рекурсивной части шаблона, следуют ячейки и линии, которые отображаются в рекурсивной частями. Порядок, в котором граф обходится во время оптимизации запроса или выполнения имеет ничего общего с порядком, в выходных данных. Аналогичным образом направление стрелки в рекурсивном шаблоне также не влияет на порядок путь graph. 

## <a name="graph-path-aggregate-functions"></a>Агрегатные функции в путь Graph
Так как узлы и ребра вовлечено в шаблоне произвольной длины возвращаемого значения коллекции (узлы и границ, в этом пути), пользователи не может проецировать атрибуты, непосредственно использующий синтаксис обычной tablename.attributename. Для запросов, когда он необходим для прогнозирования значений атрибутов из промежуточного узла или граничной таблицы, в путь, пройденный, используйте следующий граф пути агрегатные функции: STRING_AGG, LAST_VALUE, SUM, AVG, MIN, MAX и COUNT. Ниже приведен общий синтаксис для использования этих агрегатных функций в предложении SELECT.

```
<GRAPH_PATH_AGGREGATE_FUNCTION>(<expression> , <separator>)  <order_clause>

    <order_clause> ::=
        { WITHIN GROUP (GRAPH PATH) }

    <GRAPH_PATH_AGGREGATE_FUNCTION> ::=
          STRING_AGG
        | LAST_VALUE
        | SUM
        | COUNT
        | AVG
        | MIN
        | MAX

```

### <a name="stringagg"></a>STRING_AGG
Функции STRING_AGG принимает выражение и разделитель в качестве входных данных и возвращает строку. Пользователи могут использовать эту функцию в предложении SELECT для атрибуты проекта из промежуточных узлов и ребер в путь, пройденный. 

### <a name="lastvalue"></a>LAST_VALUE
Проект, который может использоваться атрибуты из последнего узла путь, пройденный, Агрегатная функция LAST_VALUE. Является ошибкой предоставлять псевдоним таблицы edge в качестве входных данных для этой функции только имена таблиц узлов или псевдонимы могут использоваться.

**Последний узел**: Последний узел относится к узлу, который является последним в путь, пройденный, независимо от того, направление стрелки в предикате СОВПАДЕНИЯ. Например: `MATCH(SHORTEST_PATH(n(-(e)->p)+) )`. Здесь последний узел в пути будет последний узел посещенных P. 

В то время как последний узел является последний n-й узел в граф выходной путь для этого шаблона: `MATCH(SHORTEST_PATH((n<-(e)-)+p))`    

### <a name="sum"></a>SUM
Эта функция возвращает сумму значений атрибутов указанный узел/edge или выражение, которое было открыто по этому пути.

### <a name="count"></a>COUNT
Эта функция возвращает число непустых значений атрибута узла/крае в пути. Поддерживает функции COUNT "\*" оператор с псевдоним таблицы узлов или граничную. Без узлов или граничную таблицу псевдонима, использование \* является неоднозначным его будет привести к ошибке.

    {  COUNT( <expression> | <node_or_edge_alias>.* )  <order_clause>  }


### <a name="avg"></a>AVG
Возвращает среднее для значений атрибутов указанный узел/edge или выражение, которое было открыто по этому пути.

### <a name="min"></a>MIN
Возвращает минимальное значение из значения атрибута указанный узел/edge или выражение, которое отображается по этому пути.

### <a name="max"></a>MAX
Возвращает максимальное значение из значения атрибута указанный узел/edge или выражение, которое отображается по этому пути.

## <a name="remarks"></a>Примечания  
функция shortest_path может использоваться только внутри MATCH.     
LAST_NODE поддерживается только внутри shortest_path.     
Поиск взвешенных кратчайшего маршрута, все пути или все кратчайшего пути не поддерживается.         
В некоторых случаях Неподходящий план запроса может быть создан для запросов с большего количества прыжков, что приводит к более поздней версии время выполнения запросов. С помощью указания hash join может помочь.    


## <a name="examples"></a>Примеры 
Для примеров запросов, показано ниже, мы будем ot использовать узел и Краевые таблицы создаются в [пример графа SQL](./sql-graph-sample.md)

### <a name="a--find-shortest-path-between-2-people"></a>A.  Поиск кратчайшего пути между 2 человека
 В следующем примере мы поиск кратчайшего пути между Алексей и Алисе. Нам понадобится узел Person и FriendOf edge, созданный из графа пример сценария. 

 ```
SELECT PersonName, Friends
FROM (  
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        LAST_VALUE(Person2.name) WITHIN GROUP (GRAPH PATH) AS LastNode
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
    AND Person1.name = 'Jacob'
) AS Q
WHERE Q.LastNode = 'Alice'
 ```

 ### <a name="b--find-shortest-path-from-a-given-node-to-all-other-nodes-in-the-graph"></a>Б.  Поиск кратчайшего пути от заданного узла на другие узлы в графе. 
 В следующем примере вычисляется всех людей, к которым подключен Алексей в графе и кратчайшего пути, начиная с Алексей для всех пользователей. 

 ```
SELECT
    Person1.name AS PersonName, 
    STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends
FROM
    Person AS Person1,
    friendOf FOR PATH AS fo,
    Person FOR PATH  AS Person2
WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
AND Person1.name = 'Jacob'
 ```

### <a name="c--count-the-number-of-hopslevels-traversed-to-go-from-one-person-to-another-in-the-graph"></a>В.  Подсчитать число прыжков/уровни пройти, чтобы перейти от одного лица к другому в графе.
 В следующем примере выполняется поиск кратчайшего пути между Алексей и Алиса и выводит число прыжков, необходимое для перехода от Алексей Элис. 

 ```
 SELECT PersonName, Friends, levels
FROM (  
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        LAST_VALUE(Person2.name) WITHIN GROUP (GRAPH PATH) AS LastNode,
        COUNT(Person2.name) WITHIN GROUP (GRAPH PATH) AS levels
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
    AND Person1.name = 'Jacob'
) AS Q
WHERE Q.LastNode = 'Alice'
 ```

### <a name="d-find-people-1-3-hops-away-from-a-given-person"></a>Г. Поиск людей прыжков 1 – 3 от человека
В следующем примере вычисляется кратчайший путь между Алексею и всех людей, к которым он подключен в прыжков graph 1 – 3 от него. 

```
SELECT
    Person1.name AS PersonName, 
    STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends
FROM
    Person AS Person1,
    friendOf FOR PATH AS fo,
    Person FOR PATH  AS Person2
WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2){1,3}))
AND Person1.name = 'Jacob'
```

### <a name="e-find-people-exactly-2-hops-away-from-a-given-person"></a>Д. Поиск людей ровно 2 прыжков от человека
В следующем примере вычисляется кратчайший путь между Алексею и теми, кто ровно 2 прыжков от ему в графике. 

```
SELECT PersonName, Friends
FROM (
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        COUNT(Person2.name) WITHIN GROUP (GRAPH PATH) AS levels
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2){1,3}))
    AND Person1.name = 'Jacob'
) Q
WHERE Q.levels = 2
```

## <a name="see-also"></a>См. также  
 [MATCH (SQL Graph)](../../t-sql/queries/match-sql-graph.md)    
 [CREATE TABLE (SQL Graph)](../../t-sql/statements/create-table-sql-graph.md)   
 [INSERT (граф SQL)](../../t-sql/statements/insert-sql-graph.md)  
 [Graph Processing with SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md) (Работа с графами в SQL Server 2017)     
 
