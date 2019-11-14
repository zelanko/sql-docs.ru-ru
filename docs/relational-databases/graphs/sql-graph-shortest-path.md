---
title: КРАТЧАЙШий путь (SQL Graph) | Документация Майкрософт
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
monikerRange: =azuresqldb-current||>=sql-server-ver15||=sqlallproducts-allversions||=azuresqldb-mi-current
ms.openlocfilehash: 9318a34b4853937983b107491c9210de80e5506c
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056402"
---
# <a name="shortest_path-transact-sql"></a>SHORTEST_PATH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver2015-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Задает условие поиска для диаграммы, поиск которого выполняется рекурсивно или повторяется. SHORTEST_PATH можно использовать внутри в инструкции SELECT для СОПОСТАВЛЕНИЯ с узлами графа и граничными таблицами. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="shortest-path"></a>Кратчайший путь
Функция SHORTEST_PATH позволяет найти:    
* Кратчайший путь между двумя заданными узлами или сущностями
* Один источник кратчайшие пути.
* Кратчайший путь от нескольких исходных узлов до нескольких целевых узлов.

Он принимает в качестве входных данных шаблон произвольной длины и возвращает кратчайший путь, существующий между двумя узлами. Эта функция может использоваться только внутри MATCH. Функция возвращает только один кратчайший путь между любыми двумя заданными узлами. Если существует два или более кратчайших пути с одинаковой длиной между любой парой исходного и целевого узлов, функция возвращает только один путь, который был найден первым во время обхода. Обратите внимание, что шаблон произвольной длины может указываться только внутри функции SHORTEST_PATH. 

Синтаксис см. в разделе [соответствие (SQL Graph)](../../t-sql/queries/match-sql-graph.md) . 

## <a name="for-path"></a>ДЛЯ ПУТИ
ДЛЯ PATH необходимо использовать с любым именем узла или граничной таблицы в предложении FROM, которое будет участвовать в шаблоне произвольной длины. ДЛЯ PATH указывает механизму, что в таблице node или EDGE будет возвращена упорядоченная коллекция, представляющая список узлов или ребер, найденных по пути. Атрибуты этих таблиц нельзя запланировать непосредственно в предложении SELECT. Для атрибутов проекта из этих таблиц необходимо использовать агрегатные функции пути графа.  

## <a name="arbitrary-length-pattern"></a>Шаблон произвольной длины
Этот шаблон включает в себя узлы и границы, которые необходимо многократно просматривать, пока не будет достигнут нужный узел или пока не будет выполнено максимальное число итераций, указанное в шаблоне. При каждом выполнении запроса результат выполнения этого шаблона будет упорядоченной коллекцией узлов, а границы проходят по пути от начального узла к конечному. Это шаблон синтаксиса регулярных выражений, и поддерживаются следующие два квантификатора шаблонов:

* **"+"** : Повторите шаблон 1 или более раз. Действие прекращается, как только будет найден кратчайший путь.
* **{1, n}** : Повторите шаблон 1 до n раз. Завершите работу, как только будет найден самый короткий.

## <a name="last_node"></a>LAST_NODE
Функция LAST_NODE () позволяет создавать цепочки для двух шаблонов прохода произвольной длины. Его можно использовать в сценариях, где:    
* В запросе используется более одного кратчайшего шаблона пути, и один шаблон начинается с последнего узла предыдущего шаблона.
* Два кратчайших шаблона пути объединяются в одном LAST_NODE ().

## <a name="graph-path-order"></a>Порядок расположения графа
Порядок пути к графу ссылается на порядок данных в выходном пути. Порядок выходных путей всегда начинается с нерекурсивной части шаблона, за которой следуют узлы и края, отображаемые в рекурсивной части. Порядок, в котором происходит обход диаграммы во время оптимизации или выполнения запроса, не связан с порядком, напечатанным в выходных данных. Аналогично, направление стрелки в рекурсивном шаблоне также не влияет на порядок расположения графа. 

## <a name="graph-path-aggregate-functions"></a>Агрегатные функции пути к графу
Поскольку узлы и грани, участвующие в шаблоне произвольной длины, возвращают коллекцию (узлов и границ, проходящих по этому пути), пользователи не могут проецировать атрибуты напрямую, используя стандартный синтаксис TableName. AttributeName. Для запросов, в которых необходимо использовать значения атрибутов из промежуточных узлов или граничных таблиц, в пути обхода используйте следующие агрегатные функции пути к графу: STRING_AGG, LAST_VALUE, SUM, AVG, MIN, MAX и COUNT. Общий синтаксис для использования этих агрегатных функций в предложении SELECT:

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

### <a name="string_agg"></a>STRING_AGG
Функция STRING_AGG принимает выражение и разделитель в качестве входных данных и возвращает строку. Пользователи могут использовать эту функцию в предложении SELECT для атрибутов проекта из промежуточных узлов или краев в пути обхода. 

### <a name="last_value"></a>LAST_VALUE
Для атрибутов проекта, начиная с последнего узла пути, можно использовать агрегатную функцию LAST_VALUE. Указание псевдонима краевой таблицы в качестве входных данных для этой функции является ошибкой, можно использовать только имена таблиц узлов или псевдонимы.

**Последний узел**. последний узел ссылается на узел, который отображается последним в пути, независимо от направления стрелки в предикате Match. Например: `MATCH(SHORTEST_PATH(n(-(e)->p)+) )`. Здесь последний узел в пути будет последним посещенным узлом P. 

В то время как последний узел — это последний n-й узел в пути выходного графа для этого шаблона: `MATCH(SHORTEST_PATH((n<-(e)-)+p))`    

### <a name="sum"></a>SUM
Эта функция возвращает сумму указанных значений атрибутов node/ребра или выражение, которое отображалось в пути обхода.

### <a name="count"></a>COUNT
Эта функция возвращает количество значений, отличных от NULL, требуемого атрибута node/ребр в пути. Функция COUNT поддерживает оператор "\*" с псевдонимом узла или краевой таблицы. Без псевдонима таблицы node или граничной использование \* неоднозначно и приведет к ошибке.

    {  COUNT( <expression> | <node_or_edge_alias>.* )  <order_clause>  }


### <a name="avg"></a>AVG
Возвращает среднее для указанных значений атрибутов node/ребра или выражение, которое присутствовало в пути обхода.

### <a name="min"></a>MIN
Возвращает минимальное значение из указанных значений атрибута node/ребра или выражение, которое отображалось в пути обхода.

### <a name="max"></a>MAX
Возвращает максимальное значение из указанных значений атрибута node/ребра или выражение, которое отображалось в пути обхода.

## <a name="remarks"></a>Remarks  
Функция shortest_path может использоваться только внутри MATCH.     
LAST_NODE поддерживается только в shortest_path.     
Поиск взвешенного кратчайшего пути, все пути или все короткие пути не поддерживаются.         
В некоторых случаях могут создаваться неправильные планы для запросов с большим числом прыжков, что приводит к увеличению времени выполнения запроса. Использование подсказки по хэш-соединению может помочь.    


## <a name="examples"></a>Примеры 
В приведенных здесь примерах запросов мы будем использовать таблицы node и ребра, созданные в [примере SQL Graph](./sql-graph-sample.md) .

### <a name="a--find-shortest-path-between-2-people"></a>A.  Найти кратчайший путь между 2 людьми
 В следующем примере мы найдут кратчайший путь между Джейкоб и Алисой. Нам потребуется узел Person и Фриендоф ребро, созданные на основе примера сценария Graph. 

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

 ### <a name="b--find-shortest-path-from-a-given-node-to-all-other-nodes-in-the-graph"></a>б.  Поиск кратчайшего пути от заданного узла ко всем остальным узлам в графе. 
 В следующем примере выполняется поиск всех людей, к которым подключен Джейкоб, в графе и кратчайшего пути, начиная с Джейкоб, для всех этих пользователей. 

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

### <a name="c--count-the-number-of-hopslevels-traversed-to-go-from-one-person-to-another-in-the-graph"></a>В.  Подсчитайте число прыжков/уровней, пройденных одним лицом к другому в графе.
 В следующем примере выполняется поиск кратчайшего пути между Джейкоб и Алисой и выводится число прыжков, которое требуется для перехода от Джейкоб к Алисе. 

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

### <a name="d-find-people-1-3-hops-away-from-a-given-person"></a>Г. Поиск людей 1-3 прыжков от определенного человека
В следующем примере выполняется поиск кратчайшего пути между Джейкоб и всеми людьми, к которым он подключен, в графе 1-3 на расстоянии от него. 

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

### <a name="e-find-people-exactly-2-hops-away-from-a-given-person"></a>Д. Поиск людей на расстоянии не более 2 прыжков от данного лица
В следующем примере выполняется поиск кратчайшего пути между Джейкоб и людьми, на которых ровно два прыжка от него в графе. 

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

## <a name="see-also"></a>См. также статью  
 [Совпадение (SQL Graph)](../../t-sql/queries/match-sql-graph.md)    
 [CREATE TABLE (SQL Graph)](../../t-sql/statements/create-table-sql-graph.md)   
 [INSERT (граф SQL)](../../t-sql/statements/insert-sql-graph.md)  
 [Graph Processing with SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md) (Работа с графами в SQL Server 2017)     
 
