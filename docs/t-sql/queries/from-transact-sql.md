---
title: "FROM (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JOIN
- FROM_TSQL
- FROM
- JOIN_TSQL
- CROSS_TSQL
- CROSS_APPLY_TSQL
- APPLY_TSQL
- CROSS_JOIN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- OUTER APPLY operator
- hints [SQL Server], FROM clause
- SELECT statement [SQL Server], FROM clause
- ISO syntax
- DELETE statement [SQL Server], FROM clause
- CROSS APPLY operator
- FROM clause
- APPLY operator
- joins [SQL Server], FROM clause
- UPDATE statement [SQL Server], FROM clause
- derived tables
ms.assetid: 36b19e68-94f6-4539-aeb1-79f5312e4263
caps.latest.revision: "97"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 20363fdc5408fbc79ba833c365bcb118fb1a2846
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="from-transact-sql"></a>Предложение FROM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Указывает таблицы, представления, производные таблицы и соединенные таблицы, которые используются в инструкциях DELETE, SELECT и UPDATE в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В инструкции SELECT требуется предложение FROM, за исключением тех случаев, когда список выбора содержит только константы, переменные и арифметические выражения (без имен столбцов).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
[ FROM { <table_source> } [ ,...n ] ]   
<table_source> ::=   
{  
    table_or_view_name [ [ AS ] table_alias ]   
        [ <tablesample_clause> ]   
        [ WITH ( < table_hint > [ [ , ]...n ] ) ]   
    | rowset_function [ [ AS ] table_alias ]   
        [ ( bulk_column_alias [ ,...n ] ) ]   
    | user_defined_function [ [ AS ] table_alias ]  
    | OPENXML <openxml_clause>   
    | derived_table [ [ AS ] table_alias ] [ ( column_alias [ ,...n ] ) ]   
    | <joined_table>   
    | <pivoted_table>   
    | <unpivoted_table>  
    | @variable [ [ AS ] table_alias ]  
    | @variable.function_call ( expression [ ,...n ] )   
        [ [ AS ] table_alias ] [ (column_alias [ ,...n ] ) ]  
    | FOR SYSTEM_TIME <system_time>   
}  
<tablesample_clause> ::=  
    TABLESAMPLE [SYSTEM] ( sample_number [ PERCENT | ROWS ] )   
        [ REPEATABLE ( repeat_seed ) ]   
  
<joined_table> ::=   
{  
    <table_source> <join_type> <table_source> ON <search_condition>   
    | <table_source> CROSS JOIN <table_source>   
    | left_table_source { CROSS | OUTER } APPLY right_table_source   
    | [ ( ] <joined_table> [ ) ]   
}  
<join_type> ::=   
    [ { INNER | { { LEFT | RIGHT | FULL } [ OUTER ] } } [ <join_hint> ] ]  
    JOIN  
  
<pivoted_table> ::=  
    table_source PIVOT <pivot_clause> [ [ AS ] table_alias ]  
  
<pivot_clause> ::=  
        ( aggregate_function ( value_column [ [ , ]...n ])   
        FOR pivot_column   
        IN ( <column_list> )   
    )   
  
<unpivoted_table> ::=  
    table_source UNPIVOT <unpivot_clause> [ [ AS ] table_alias ]  
  
<unpivot_clause> ::=  
    ( value_column FOR pivot_column IN ( <column_list> ) )   
  
<column_list> ::=  
    column_name [ ,...n ]   
  
<system_time> ::=  
{  
       AS OF <date_time>  
    |  FROM <start_date_time> TO <end_date_time>  
    |  BETWEEN <start_date_time> AND <end_date_time>  
    |  CONTAINED IN (<start_date_time> , <end_date_time>)   
    |  ALL  
}  
  
    <date_time>::=  
        <date_time_literal> | @date_time_variable  
  
    <start_date_time>::=  
        <date_time_literal> | @date_time_variable  
  
    <end_date_time>::=  
        <date_time_literal> | @date_time_variable  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
FROM { <table_source> [ ,...n ] }  
  
<table_source> ::=   
{  
    [ database_name . [ schema_name ] . | schema_name . ] table_or_view_name [ AS ] table_or_view_alias  
    | derived_table [ AS ] table_alias [ ( column_alias [ ,...n ] ) ]  
    | <joined_table>  
}  
  
<joined_table> ::=   
{  
    <table_source> <join_type> <table_source> ON search_condition   
    | <table_source> CROSS JOIN <table_source> 
    | left_table_source { CROSS | OUTER } APPLY right_table_source   
    | [ ( ] <joined_table> [ ) ]   
}  
  
<join_type> ::=   
    [ INNER ] [ <join hint> ] JOIN  
    | LEFT  [ OUTER ] JOIN  
    | RIGHT [ OUTER ] JOIN  
    | FULL  [ OUTER ] JOIN  
  
<join_hint> ::=   
    REDUCE  
    | REPLICATE  
    | REDISTRIBUTE  
```  
  
## <a name="arguments"></a>Аргументы  
\<table_source >  
 Указывает таблицу, представление, табличную переменную или источник производной таблицы с указанием или без указания псевдонима для использования в инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. В инструкции можно использовать до 256 источников таблиц, хотя предел изменяется в зависимости от доступной памяти и сложности других выражений в запросе. Отдельные запросы могут не поддерживать 256 источников таблиц.  
  
> [!NOTE]  
>  Производительность выполнения запросов может снизиться из-за большого количества таблиц, указанных в запросе. На время компиляции и оптимизации также влияют дополнительные факторы. К ним относятся наличие индексов и индексированных представлений на каждом \<table_source > и размер \<select_list > в инструкции SELECT.  
  
 Порядок источников таблицы после ключевого слова FROM не влияет на возвращаемый результирующий набор. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает ошибки, если в предложении FROM появляются повторяющиеся имена.  
  
 *представления table_or_view_name*  
 Имя таблицы или представления.  
  
 Если таблица или представление существует в другой базе данных на том же экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используйте полное доменное имя в форме *базы данных*. *схемы*. *object_name*.  
  
 Если таблица или представление существует вне экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]l, используйте четырехчастное имя в форме *связанный_сервер*. *каталог*. *схемы*. *Объект*. Дополнительные сведения см. в статье [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md). Четырехсоставного имени, которое создается с использованием [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md) работать так, как серверная часть имени может также использоваться для указания удаленного источника таблицы. Если указана функция OPENDATASOURCE, *имя_базы_данных* и *schema_name* могут применяться не ко всем источникам данных, зависит от возможностей поставщика OLE DB, который обращается к удаленному объекту.  
  
 [КАК] *table_alias*  
 Является псевдонимом для *table_source* , можно использовать либо для удобства и для различения таблицы или представления в самосоединении или во вложенном запросе. Псевдоним часто является сокращенным именем таблицы, использующимся для соотнесения с определенными столбцами таблиц в соединении. Если имя столбца существует более чем в одной таблице соединения, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребует, чтобы имя столбца было уточнено именем таблицы, представления или псевдонима. Если определен псевдоним, нельзя использовать имя таблицы.  
  
 При использовании производной таблицы, набора строк или табличной функции либо предложения оператора (как PIVOT или UNPIVOT), необходимая *table_alias* в конце предложения является соответствующим именем таблицы для всех столбцов, включая группирующие столбцы возвращается.  
  
 С помощью (\<table_hint >)  
 Указывает на то, что с данной таблицей и для данной инструкции оптимизатор запросов использует стратегию оптимизации или блокировки. Дополнительные сведения см. в разделе [Табличные указания (Transact-SQL)](../../t-sql/queries/hints-transact-sql-table.md).  
  
 *rowset_function*  

**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Указывает одну из функций набора строк, например OPENROWSET, возвращающую объект, который можно использовать вместо ссылки на таблицу. Дополнительные сведения о списке функций набора строк см. в разделе [функции наборов строк &#40; Transact-SQL &#41; ](../../t-sql/functions/rowset-functions-transact-sql.md).  
  
 Использование функций OPENROWSET и OPENQUERY для задания удаленного объекта зависит от возможностей поставщика OLE DB, который обращается к удаленному объекту.  
  
 *bulk_column_alias*  

**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Дополнительный псевдоним для замены имени столбца в результирующем наборе. Псевдонимы столбца разрешены только в инструкциях SELECT, использующих функцию OPENROWSET с параметром BULK. При использовании *bulk_column_alias*, определите псевдоним для каждого столбца таблицы в том же порядке, что и столбцы в файле.  
  
> [!NOTE]  
>  Данный псевдоним, если он присутствует, переопределяет атрибут NAME в элементах COLUMN файла XML.  
  
 *user_defined_function*  
 Указывает функцию с табличным значением.  
  
 OPENXML \<openxml_clause >  

**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Обеспечивает представление XML-документа в виде набора строк. Дополнительные сведения см. в разделе [OPENXML &#40; Transact-SQL &#41; ](../../t-sql/functions/openxml-transact-sql.md).  
  
 *derived_table*  
 Это вложенный запрос, который извлекает строки из базы данных. *derived_table* используется в качестве входных данных для внешнего запроса.  
  
 *Производный* *_table* можно использовать [!INCLUDE[tsql](../../includes/tsql-md.md)] конструктором табличных значений для указания нескольких строк. Например, `SELECT * FROM (VALUES (1, 2), (3, 4), (5, 6), (7, 8), (9, 10) ) AS MyTable(a, b);`. Дополнительные сведения см. в разделе [конструктор табличных значений &#40; Transact-SQL &#41; ](../../t-sql/queries/table-value-constructor-transact-sql.md).  
  
 *псевдоним_столбца*  
 Дополнительный псевдоним для замены имени столбца в результирующем наборе производной таблицы. Для каждого столбца в списке выбора следует включить по одному псевдониму столбца и заключить весь список псевдонимов столбцов в скобки.  
  
 *представления table_or_view_name* FOR SYSTEM_TIME \<system_time >  

**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Указывает, что возвращаются конкретной версии данных из указанного темпоральной таблицей и соответствующей таблицей журнала связанных с системным управлением версиями  
  
\<tablesample_clause >  
 Указывает, что из таблицы возвращается выборка данных. Выборка может быть приблизительной. Это предложение может быть использовано в инструкциях SELECT, UPDATE или DELETE в отношении любой первичной или соединяемой таблицы. TABLESAMPLE не может быть указано для представлений.  
  
> [!NOTE]  
>  При использовании предложения TABLESAMPLE к базам данных, которые были обновлены до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с уровнем совместимости базы данных 110 или больше, оператор PIVOT нельзя использовать в запросах рекурсивного обобщенного табличного выражения (CTE). Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
 SYSTEM  
 Зависящий от реализации метод выборки, определенный стандартами ISO. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это единственно доступный метод выборки, и он применяется по умолчанию. SYSTEM использует основанный на страницах метод выборки со случайным набором страниц, все строки которых возвращаются как подмножество выборки.  
  
 *sample_number*  
 Точное или приближенное константное числовое выражение, представляющее процент или количество строк. При указании PERCENT, *sample_number* неявно преобразуется в **float** значением; в противном случае он преобразуется в **bigint**. PERCENT является параметром по умолчанию.  
  
 PERCENT  
 Указывает, что *sample_number* процент строк таблицы, которые должны быть получены из таблицы. При указании PERCENT [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает приближенное значение указанного процента. При указании PERCENT аргумент *sample_number* выражение должно иметь значение от 0 до 100.  
  
 ROWS  
 Указывает, приблизительно *sample_number* строк будут извлечены. При указании ROWS [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает приближенное значение количества указанных строк. При указании ROWS *sample_number* выражение должно иметь целочисленное значение больше нуля.  
  
 REPEATABLE  
 Указывает, что заданная выборка может быть возвращена снова. При указании такого же *repeat_seed* значение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет возвращать то же подмножество строк до тех пор, пока не были изменены для всех строк в таблице. При указании другого *repeat_seed* значение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет скорее всего, вернет другую выборку строк в таблице. Изменениями считаются следующие действия над таблицей: вставка, обновление, удаление, перестроение или дефрагментация индекса, а также восстановление или присоединение базы данных.  
  
 *repeat_seed*  
 Константное целочисленное выражение, используемое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для формирования случайного числа. *repeat_seed* — **bigint**. Если *repeat_seed* не указан, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присваивает значение случайным образом. Для конкретной *repeat_seed* значение, результат выборки всегда равно Если изменения не были применены к таблице. *Repeat_seed* выражение должно иметь целое число больше нуля.  
  
 \<joined_table >  
 Результирующий набор, полученный из двух или более таблиц. Для нескольких соединений следует использовать скобки, чтобы изменить естественный порядок соединений.  
  
\<join_type >  
 Указание типа операции соединения.  
  
 **ВНУТРЕННЕЕ**  
 Указывает, что возвращаются все совпадающие пары строк. Отмена несовпадающих строк из обеих таблиц. Если тип соединения не указан, этот тип задается по умолчанию.  
  
 FULL [ OUTER ]  
 Указывает, что в результирующий набор включаются строки как из левой, так и из правой таблицы, несоответствующие условиям соединения, а выходные столбцы, соответствующие оставшейся таблице, устанавливаются в значение NULL. Этим дополняются все строки, обычно возвращаемые при помощи INNER JOIN.  
  
 LEFT [ OUTER ]  
 Указывает, что все строки из левой таблицы, не соответствующие условиям соединения, включаются в результирующий набор, а выходные столбцы из оставшейся таблицы устанавливаются в значение NULL в дополнение ко всем строкам, возвращаемым внутренним соединением.  
  
 RIGHT [ OUTER ]  
 Указывает, что все строки из правой таблицы, не соответствующие условиям соединения, включаются в результирующий набор, а выходные столбцы, соответствующие оставшейся таблице, устанавливаются в значение NULL в дополнение ко всем строкам, возвращаемым внутренним соединением.  
  
\<join_hint >  
 Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDS](../../includes/sssds-md.md)], указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запроса, оптимизатор использовать Указание одного соединения, или алгоритм выполнения каждого соединения, указанного в предложении FROM запроса. Дополнительные сведения см. в разделе [указания соединения &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-join.md).  
  
 Для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], эти указания соединения применяются для внутренних соединений по двум столбцам несовместимые распространения. Они могут повысить производительность запросов, ограничивая объем перемещения данных, которая происходит во время обработки запросов. Указания допустимого соединения для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , как показано ниже:  
  
 УМЕНЬШИТЬ  
 Уменьшает количество строк для перемещения для таблицы правой стороны соединения для обеспечения совместимости двух таблиц несовместимые распространения. Указание полусоединение называется также указанием REDUCE.  
  
 REPLICATE  
 В результате чего значения соединяющийся столбец в таблице на левую часть объединения, которую требуется реплицировать на все узлы. Таблица справа соединяется с реплицированной версии этих столбцов.  
  
 ПОВТОРНОЕ РАСПРОСТРАНЕНИЕ  
 Принудительно двух источников данных, будут распространяться на столбцы, указанные в предложении JOIN. Для распределенных таблицы [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] выполнит перемещения в случайном порядке. Для реплицируемой таблицы [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] выполнит trim перемещения. Чтобы понять, они перемещаются типов, см. в разделе «DMS планирование операций запроса» в разделе «Основные сведения о планов запросов» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]. Это указание может повысить производительность, когда план запроса использует широковещательных перемещения для разрешения объединения несовместимых распространения.  
  
 JOIN  
 Указывает, что данная операция соединения должна произойти между указанными источниками или представлениями таблицы.  
  
 ON \<search_condition >  
 Задает условие, на котором основывается соединение. Условие может указывать любой предикат, хотя чаще используются столбцы и операторы сравнения, например:  
  
```tsql
SELECT p.ProductID, v.BusinessEntityID  
FROM Production.Product AS p   
JOIN Purchasing.ProductVendor AS v  
ON (p.ProductID = v.ProductID);  
  
```  
  
 Если условие указывает столбцы, их имена и типы данных могут не совпадать, однако, если типы данных не совпадают, столбцы должны либо быть совместимыми, либо иметь типы, которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может неявно преобразовать. Если типы данных не могут быть преобразованы неявно, условие должно проводить явное преобразование типа данных при помощи функции CONVERT.  
  
 Могут существовать предикаты, использующие в предложении ON только одну из соединяемых таблиц. Такие предикаты также могут присутствовать в предложении WHERE запроса. Хотя размещение таких предикатов не оказывает влияния в случае внутренних соединений (INNER), при использовании внешних соединений (OUTER) они могут привести к другому результату. Это происходит потому, что предикаты в предложении ON применяются к таблице до соединения, в то время как предложение WHERE семантически применяется к результату соединения.  
  
 Дополнительные сведения об условиях поиска и предикатах см. в разделе [условие поиска &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
 CROSS JOIN  
 Указывает перекрестное произведение двух таблиц. Возвращает те же строки, что и соединение без предложения WHERE в старом режиме, не совместимом с SQL-92.  
  
 *left_table_source* {CROSS | ПРИМЕНИТЬ ВНЕШНЕЕ} *right_table_source*  
 Указывает, что *right_table_source* из указанных условий оператор вычисляется для каждой строки *left_table_source*. Эта функция полезна, когда *right_table_source* содержит табличная функция, которая принимает значения столбцов из *left_table_source* как один из его аргументов.  
  
 Вместе с ключевым словом APPLY должно быть указано либо CROSS, либо OUTER. Если указано CROSS, никакие строки не создаются при *right_table_source* сравнивается с определенной строки *left_table_source* и возвращает пустой результирующий набор.  
  
 При указании OUTER создается одна строка для каждой строки *left_table_source* , даже когда *right_table_source* вычисляется для этой строки и возвращает пустой результирующий набор.  
  
 Дополнительные сведения см. в разделе «Примечания».  
  
 *left_table_source*  
 Источник таблицы, определенный в предыдущем аргументе. Дополнительные сведения см. в разделе «Примечания».  
  
 *right_table_source*  
 Источник таблицы, определенный в предыдущем аргументе. Дополнительные сведения см. в разделе «Примечания».  
  
 *table_source* PIVOT \<pivot_clause >  
 Указывает, что *table_source* основано на *pivot_column*. *table_source* является таблицей или табличным выражением. Выходные данные выглядят таблицу, содержащую все столбцы *table_source* за исключением *pivot_column* и *value_column*. Столбцы *table_source*, за исключением *pivot_column* и *value_column*, называются столбцами группирования оператора pivot. Дополнительные сведения о PIVOT и UNPIVOT см. в разделе [с помощью PIVOT и UNPIVOT](../../t-sql/queries/from-using-pivot-and-unpivot.md).  
  
 Оператор PIVOT применяет операцию группирования к входной таблице по отношению к столбцам группирования и возвращает одну строку для каждой группы. Кроме того, выходные данные содержат один столбец для каждого значения, указанного в *column_list* , которая отображается в *pivot_column* из *input_table*.  
  
 Дополнительные сведения см. в разделе «Замечания» далее.  
  
 *aggregate_function*  
 Системная или определяемая пользователем агрегатная функция, имеющая один или более входов. Агрегатная функция должна быть инвариантной относительно значений NULL. Инвариантная относительно нулевых значений агрегатная функция при определении статистического значения не учитывает нулевые значения в группе.  
  
 Системная агрегатная функция COUNT(*) недопустима.  
  
 *value_column*  
 Столбец значений оператора PIVOT. При использовании с UNPIVOT, *value_column* не может быть именем существующего столбца на входе *table_source*.  
  
 ДЛЯ *pivot_column*  
 Столбец сведения оператора PIVOT. *pivot_column* должен иметь тип, неявно или явно преобразован в **nvarchar()**. Этот столбец не может быть **изображения** или **rowversion**.  
  
 При использовании UNPIVOT *pivot_column* имя выходного столбца, полученного из *table_source*. Не может быть существующего столбца в *table_source* с таким именем.  
  
 IN (*column_list* )  
 В предложении PIVOT представлены все значения в *pivot_column* , которые станут именами столбцов выходной таблицы. В списке не указаны имена столбцов, которые уже существуют во входном *table_source* , к которому применяется сведение.  
  
 В предложении UNPIVOT представлены столбцы в *table_source* , будут сведены в один *pivot_column*.  
  
 *table_alias*  
 Псевдоним выходной таблицы. *pivot_table_alias* должен быть указан.  
  
 Оператор UNPIVOT \< unpivot_clause >  
 Указывает, что входная таблица сведена из нескольких столбцов в *column_list* в один столбец называется *pivot_column*. Дополнительные сведения о PIVOT и UNPIVOT см. в разделе [с помощью PIVOT и UNPIVOT](../../t-sql/queries/from-using-pivot-and-unpivot.md).  
  
 По СОСТОЯНИЮ на \<ДАТА_И_ВРЕМЯ >  

**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Возвращает таблицу с одной записью для каждой строки, содержащей значения, которые были фактическими (текущими) в указанный момент времени в прошлом. На внутреннем уровне объединение выполняется между темпоральной таблицей и соответствующей таблицей журнала и результаты отфильтровываются так, чтобы возвращать значения в строке, которая была действительной на момент времени, заданного параметром  *\<ДАТА_И_ВРЕМЯ >* параметра. Значение для строки считается действительным Если *system_start_time_column_name* значение меньше или равно  *\<ДАТА_И_ВРЕМЯ >* значение параметра и *system_end_time_ column_name* значение больше, чем  *\<ДАТА_И_ВРЕМЯ >* значение параметра.   
  
 ИЗ \<дата_время_начала > TO \<дата_время_окончания >

**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].

  
 Возвращает таблицу, содержащую значения для всех версий записей, которые были активны в течение указанного интервала времени, независимо от того, начали ли они быть активными до  *\<дата_время_начала >* значение параметра для FROM аргумент или перестали быть активными после  *\<дата_время_окончания >* значение параметра для аргумента TO. На внутреннем уровне объединение выполняется между темпоральной таблицей и соответствующей таблицей журнала и результаты отфильтровываются так, чтобы возвращать значения для всех версий строк, которые были активными в течение указанного временного диапазона. Включаются строки, которые стали активными точно в нижнюю границу, определенных конечной точкой FROM, и не включаются строки, которые стали активными точно в верхнюю границу, определенных конечной точкой TO.  
  
 МЕЖДУ \<дата_время_начала > AND \<дата_время_окончания >  

**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Аналогично приведенному выше в **FROM \<дата_время_начала > TO \<дата_время_окончания >** описание, за исключением того, он включает строки, которые стали активными в верхнюю границу, определяется \<дата_время_окончания > Конечная точка.  
  
 CONTAINED IN (\<start_date_time >, \<end_date_time >)  

**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Возвращает таблицу, содержащую значения для всех версий записей, которые были открыты и закрыты в течение указанного интервала времени, определяемого двумя значениями даты и времени в аргументе CONTAINED IN. В эти строки включаются те, которые стали активными точно в нижнюю границу периода времени, и те, которые перестали быть активными точно в верхнюю границу периода времени.  
  
 ALL  
 Возвращает таблицу, содержащую значения из всех строк из текущей таблицы и таблицы журнала.  
  
## <a name="remarks"></a>Замечания  
 Предложение FROM поддерживает синтаксис SQL-92-SQL для соединенных и производных таблиц. Синтаксис SQL-92 предусматривает операторы соединения INNER, LEFT OUTER, RIGHT OUTER, FULL OUTER и CROSS.  
  
 UNION и JOIN в предложении FROM поддерживаются в представлениях и в производных таблицах и вложенных запросах.  
  
 Самосоединение — это таблица, соединенная сама с собой. Операции вставки или обновления, основанные на самосоединении, следуют порядку, указанному в предложении FROM.  
  
 Так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учитывает статистику распределения и количества элементов со связанных серверов, предоставляющих статистику распределения столбцов, то указание в соединении REMOTE не требуется для принудительной удаленной оценки соединения. Обработчик запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учитывает удаленную статистику и определяет, является ли стратегия удаленного соединения подходящей. Указание соединения REMOTE удобно для поставщиков, которые не предоставляют статистику распределения столбцов.  
  
## <a name="using-apply"></a>Использование оператора APPLY  
 Как левый, так и правый операнды оператора APPLY являются табличными выражениями. Основное отличие между этими операндами состоит в, *right_table_source* можно использовать табличную функцию, которая принимает столбец из *left_table_source* как один из аргументов функции. *Left_table_source* могут включать функции, возвращающие табличные значения, но не может содержать аргументы, которые являются столбцами из *right_table_source*.  
  
 Для предоставления табличного источника для предложения FROM оператор APPLY выполняет следующее:  
  
1.  Результатом является *right_table_source* для каждой строки *left_table_source* для создания наборов строк.  
  
     Значения в *right_table_source* зависят от *left_table_source*. *right_table_source* может быть представлен примерно следующим образом: `TVF(left_table_source.row)`, где `TVF` является табличной функции.  
  
2.  Объединяет результирующие наборы, которые создаются для каждой строки при вычислении *right_table_source* с *left_table_source* с помощью операции UNION ALL.  
  
     Список столбцов, полученный в результате выполнения оператора APPLY — это набор столбцов из *left_table_source* , объединенный со списком столбцов из *right_table_source*.  
  
## <a name="using-pivot-and-unpivot"></a>Использование операторов PIVOT и UNPIVOT  
 *Pivot_column* и *value_column* являются столбцами группирования, которые используются в операторе PIVOT. Для получения выходного результирующего набора оператор PIVOT выполняет следующее:  
  
1.  Применяет GROUP BY на его *input_table* для группирования столбцы и формирует одну выходную строку для каждой группы.  
  
     Столбцы группирования в выходной строке получить соответствующие значения столбца для этой группы в *input_table*.  
  
2.  Формирует значения столбцов в списке столбцов для каждой выходной строки, для чего выполняет следующее:  
  
    1.  Дополнительно группирует строки, созданные в GROUP BY на предыдущем шаге, к *pivot_column*.  
  
         Для каждого выходного столбца в *column_list*, выбирает подгруппу, которая удовлетворяет условию:  
  
         `pivot_column = CONVERT(<data type of pivot_column>, 'output_column')`  
  
    2.  *aggregate_function* оценивается *value_column* в данном подгруппе и этот результат возвращается как значение соответствующего *output_column*. Если подгруппа пуста, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приводит к возникновению ошибки значение null для этого *output_column*. Если используется агрегатная функция COUNT, а подгруппа пуста, то возвращается значение (0).  

> [!NOTE]
> Столбец идентификаторов в `UNPIVOT` предложение выполните параметров сортировки каталога. Для [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], параметры сортировки всегда является `SQL_Latin1_General_CP1_CI_AS`. Для [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] частично автономных баз данных, параметры сортировки всегда является `Latin1_General_100_CI_AS_KS_WS_SC`. Если столбец используется в сочетании с других столбцов, а затем предложение collate (`COLLATE DATABASE_DEFAULT`) требуется для предотвращения конфликтов.   
  
 Дополнительные сведения о PIVOT и UNPIVOT, включая примеры см. в разделе [с помощью PIVOT и UNPIVOT](../../t-sql/queries/from-using-pivot-and-unpivot.md).  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения для инструкции DELETE, SELECT или UPDATE.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-a-simple-from-clause"></a>A. Использование простого предложения FROM  
 В следующем примере извлекаются столбцы `TerritoryID` и `Name` из таблицы `SalesTerritory` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```tsql    
SELECT TerritoryID, Name  
FROM Sales.SalesTerritory  
ORDER BY TerritoryID ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
TerritoryID Name                            
----------- ------------------------------  
1           Northwest                       
2           Northeast                       
3           Central                         
4           Southwest                       
5           Southeast                       
6           Canada                          
7           France                          
8           Germany                         
9           Australia                       
10          United Kingdom                  
(10 row(s) affected)  
```  
  
### <a name="b-using-the-tablock-and-holdlock-optimizer-hints"></a>Б. Использование подсказок оптимизатора TABLOCK и HOLDLOCK  
 Следующая частичная транзакция показывает, как явно указать совмещаемую блокировку на таблицу `Employee` и как прочитать индекс. Блокировка удерживается на протяжении всей транзакции.  
  
```tsql    
BEGIN TRAN  
SELECT COUNT(*)   
FROM HumanResources.Employee WITH (TABLOCK, HOLDLOCK) ;  
```  
  
### <a name="c-using-the-sql-92-cross-join-syntax"></a>В. Использование синтаксиса SQL-92 для CROSS JOIN  
 В следующем примере возвращается векторное произведение двух таблиц `Employee` и `Department` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Список всех возможных комбинаций `BusinessEntityID` строк и все `Department` возвращаются имя строки.  
  
```wql    
SELECT e.BusinessEntityID, d.Name AS Department  
FROM HumanResources.Employee AS e  
CROSS JOIN HumanResources.Department AS d  
ORDER BY e.BusinessEntityID, d.Name ;  
```  
  
### <a name="d-using-the-sql-92-full-outer-join-syntax"></a>Г. Использование синтаксиса SQL-92 для FULL OUTER JOIN  
 В следующем примере возвращается название продукта и любые соответствующие заказы на продажу в таблице `SalesOrderDetail` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. В примере также возвращаются все заказы на продажу, продукты для которых не представлены в таблице `Product`, и все продукты с заказом на продажу, отличные от тех, которые представлены в таблице `Product`.  
  
```tsql  
-- The OUTER keyword following the FULL keyword is optional.  
SELECT p.Name, sod.SalesOrderID  
FROM Production.Product AS p  
FULL OUTER JOIN Sales.SalesOrderDetail AS sod  
ON p.ProductID = sod.ProductID  
ORDER BY p.Name ;  
```  
  
### <a name="e-using-the-sql-92-left-outer-join-syntax"></a>Д. Использование синтаксиса SQL-92 для LEFT OUTER JOIN  
 Следующий пример соединяет две таблицы по столбцу `ProductID` и сохраняет несовпадающие строки из левой таблицы. Таблица `Product` сопоставляется с таблицей `SalesOrderDetail` по столбцам `ProductID` в каждой таблице. В результирующем наборе отражаются все продукты (как входящие в заказы, так и не входящие).  
  
```tsql    
SELECT p.Name, sod.SalesOrderID  
FROM Production.Product AS p  
LEFT OUTER JOIN Sales.SalesOrderDetail AS sod  
ON p.ProductID = sod.ProductID  
ORDER BY p.Name ;  
```  
  
### <a name="f-using-the-sql-92-inner-join-syntax"></a>Е. Использование синтаксиса SQL-92 для INNER JOIN  
 Следующий пример возвращает все названия продуктов и идентификаторы заказов.  
  
```tsql    
-- By default, SQL Server performs an INNER JOIN if only the JOIN   
-- keyword is specified.  
SELECT p.Name, sod.SalesOrderID  
FROM Production.Product AS p  
INNER JOIN Sales.SalesOrderDetail AS sod  
ON p.ProductID = sod.ProductID  
ORDER BY p.Name ;  
```  
  
### <a name="g-using-the-sql-92-right-outer-join-syntax"></a>Ж. Использование синтаксиса SQL-92 для RIGHT OUTER JOIN  
 Следующий пример соединяет две таблицы по столбцу `TerritoryID` и сохраняет несовпадающие строки из правой таблицы. Таблица `SalesTerritory` сопоставляется с таблицей `SalesPerson` по столбцу `TerritoryID` каждой таблицы. В результирующем наборе отображаются все представители отдела продаж независимо от того, назначена им обслуживаемая территория или нет.  
  
```tsql    
SELECT st.Name AS Territory, sp.BusinessEntityID  
FROM Sales.SalesTerritory AS st   
RIGHT OUTER JOIN Sales.SalesPerson AS sp  
ON st.TerritoryID = sp.TerritoryID ;  
```  
  
### <a name="h-using-hash-and-merge-join-hints"></a>З. Использование подсказок соединения HASH и MERGE  
 Следующий пример выполняет соединение трех таблиц — `Product`, `ProductVendor` и `Vendor` — для формирования списка продуктов и их поставщиков. Оптимизатор запросов соединяет таблицы `Product` и `ProductVendor` (`p` и `pv`) с помощью соединения слиянием (MERGE). Затем результаты соединения слиянием таблиц `Product` и `ProductVendor` (`p` и `pv`) соединяются при помощи HASH в таблицу `Vendor` для формирования (`p` и `pv`) и `v`.  
  
> [!IMPORTANT]  
>  После того как задано указание соединения, ключевое слово INNER более не является необязательным и должно быть задано в явном виде для выполнения INNER JOIN.  
  
```tsql    
SELECT p.Name AS ProductName, v.Name AS VendorName  
FROM Production.Product AS p   
INNER MERGE JOIN Purchasing.ProductVendor AS pv   
ON p.ProductID = pv.ProductID  
INNER HASH JOIN Purchasing.Vendor AS v  
ON pv.BusinessEntityID = v.BusinessEntityID  
ORDER BY p.Name, v.Name ;  
```  
  
### <a name="i-using-a-derived-table"></a>И. Использование производной таблицы  
 Следующий пример использует производную таблицу, инструкцию `SELECT` после предложения `FROM`, для возврата имен и фамилий сотрудников и городов, в которых они проживают.  
  
```tsql    
SELECT RTRIM(p.FirstName) + ' ' + LTRIM(p.LastName) AS Name, d.City  
FROM Person.Person AS p  
INNER JOIN HumanResources.Employee e ON p.BusinessEntityID = e.BusinessEntityID   
INNER JOIN  
   (SELECT bea.BusinessEntityID, a.City   
    FROM Person.Address AS a  
    INNER JOIN Person.BusinessEntityAddress AS bea  
    ON a.AddressID = bea.AddressID) AS d  
ON p.BusinessEntityID = d.BusinessEntityID  
ORDER BY p.LastName, p.FirstName;  
```  
  
### <a name="j-using-tablesample-to-read-data-from-a-sample-of-rows-in-a-table"></a>К. Использование TABLESAMPLE для чтения данных из выборки строк в таблице  
 В следующем примере используется `TABLESAMPLE` в предложении `FROM` для возврата около `10` процентов всех строк из таблицы `Customer`.  
  
```tsql    
SELECT *  
FROM Sales.Customer TABLESAMPLE SYSTEM (10 PERCENT) ;  
```  
  
### <a name="k-using-apply"></a>Л. Использование оператора APPLY  
 Следующий пример исходит из того, что в базе данных существуют следующие таблицы с данной схемой:  
  
-   `Departments`: `DeptID`, `DivisionID`, `DeptName`, `DeptMgrID`  
  
-   `EmpMgr`: `MgrID`, `EmpID`  
  
-   `Employees`: `EmpID`, `EmpLastName`, `EmpFirstName`, `EmpSalary`  
  
 Также есть функция `GetReports(MgrID)` с табличным значением, возвращающая список всех сотрудников (`EmpID`, `EmpLastName`, `EmpSalary`), которые находятся в прямом или косвенном подчинении указанного менеджера `MgrID`.  
  
 В этом примере используется `APPLY` для возврата всех отделов и всех сотрудников этих отделов. Если в каком-либо отделе нет сотрудников, для этого отдела не будет возвращено никаких строк.  
  
```tsql
SELECT DeptID, DeptName, DeptMgrID, EmpID, EmpLastName, EmpSalary  
FROM Departments d CROSS APPLY dbo.GetReports(d.DeptMgrID) ;  
```  
  
 Если необходимо, чтобы запрос предоставил строки для тех отделов без сотрудников, в которых будут выданы значения NULL для столбцов `EmpID`, `EmpLastName` и `EmpSalary`, нужно вместо APPLY применить `OUTER APPLY`.  
  
```tsql
SELECT DeptID, DeptName, DeptMgrID, EmpID, EmpLastName, EmpSalary  
FROM Departments d OUTER APPLY dbo.GetReports(d.DeptMgrID) ;  
```  
  
### <a name="l-using-cross-apply"></a>М. Использование CROSS APPLY  
 В следующем примере показано получение моментального снимка всех планов запросов, находящихся в кэше планов, путем получения дескрипторов планов для всех планов запросов в кэше запросом динамического административного представления `sys.dm_exec_cached_plans`. Затем оператор `CROSS APPLY` передает дескрипторы планов в `sys.dm_exec_query_plan`. Вывод инструкции Showplan в формате XML для каждого плана, находящегося в кэше планов, находится в столбце `query_plan` возвращаемой таблицы.  
  
```tsql
USE master;  
GO  
SELECT dbid, object_id, query_plan   
FROM sys.dm_exec_cached_plans AS cp   
CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);   
GO  
```  
  
### <a name="m-using-for-systemtime"></a>Н. С помощью FOR SYSTEM_TIME  
  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Следующий пример использует аргумент date_time_literal_or_variable SYSTEM_TIME AS OF для возврата строк таблицы, которые были фактическое (текущий) начиная с 1 января 2014 г.  
  
```tsql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME AS OF '2014-01-01'  
WHERE ManagerID = 5;
```  
  
 В следующем примере используется date_time_literal_or_variable SYSTEM_TIME из date_time_literal_or_variable АРГУМЕНТУ должна вернуть все строки, которые были активны в течение периода, определенного как начиная с 1 января 2013 г. и 1 января 2014 г., эксклюзивное верхнюю границу.  
  
```tsql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME FROM '2013-01-01' TO '2014-01-01'  
WHERE ManagerID = 5;
```  
  
 В следующем примере используется date_time_literal_or_variable SYSTEM_TIME МЕЖДУ и date_time_literal_or_variable аргумент, чтобы вернуть все строки, которые были активны в течение периода, определенного как начиная с 1 января 2013 г. и 1 января 2014 г., включая верхнюю границу.  
  
```tsql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME BETWEEN '2013-01-01' AND '2014-01-01'  
WHERE ManagerID = 5;
```  
  
 В следующем примере используется FOR SYSTEM_TIME CONTAINED IN (date_time_literal_or_variable, date_time_literal_or_variable) аргумент, чтобы вернуть все строки, которые были открыты и закрыты в течение периода, определенного как начиная с 1 января 2013 г. и заканчивая 1 января 2014 г.  
  
```tsql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME CONTAINED IN ( '2013-01-01', '2014-01-01' )  
WHERE ManagerID = 5;
```  
  
 В следующем примере переменной, а не литерал для предоставления граничных значений даты для запроса.  
  
```tsql
DECLARE @AsOfFrom datetime2 = dateadd(month,-12, sysutcdatetime());
DECLARE @AsOfTo datetime2 = dateadd(month,-6, sysutcdatetime());
  
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME FROM @AsOfFrom TO @AsOfTo  
WHERE ManagerID = 5;
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="n-using-the-inner-join-syntax"></a>О. Использование синтаксиса INNER JOIN  
 В следующем примере возвращается `SalesOrderNumber`, `ProductKey`, и `EnglishProductName` столбцы из `FactInternetSales` и `DimProduct` таблиц, где ключ соединения `ProductKey`, соответствует в обеих таблицах. `SalesOrderNumber` И `EnglishProductName` столбцы каждого существует в одной из таблиц, поэтому нет необходимости указывать псевдоним таблицы с этими столбцами, как показано; эти псевдонимы приводятся исключительно для удобства чтения. Слово **AS** до псевдоним имя не является обязательным, но рекомендуется для удобства чтения и для соответствия стандарту ANSI.  
  
```tsql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
INNER JOIN DimProduct AS dp  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
 Поскольку `INNER` ключевое слово не требуется для внутренних соединений, этот же запрос можно записать так:  
  
```tsql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
JOIN DimProduct AS dp  
ON dp.ProductKey = fis.ProductKey;  
```  
  
 Объект `WHERE` предложение также может использоваться с этим запросом, чтобы ограничить результаты. В этом примере ограничивает результаты `SalesOrderNumber` значения больше, чем «SO5000»:  
  
```tsql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
JOIN DimProduct AS dp  
    ON dp.ProductKey = fis.ProductKey  
WHERE fis.SalesOrderNumber > 'SO50000'  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="o-using-the-left-outer-join-and-right-outer-join-syntax"></a>П. С помощью синтаксиса LEFT OUTER JOIN и RIGHT OUTER JOIN  
 Следующий пример соединяет `FactInternetSales` и `DimProduct` таблицы на `ProductKey` столбцов. Синтаксис левого внешнего соединения сохраняет несовпадающие строки из левой (`FactInternetSales`) таблицы. Поскольку `FactInternetSales` таблица не содержит `ProductKey` значения, которые не соответствуют `DimProduct` таблицы, этот запрос возвращает те же строки в первом примере внутреннее соединение выше.  
  
```tsql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
LEFT OUTER JOIN DimProduct AS dp  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
 Этот запрос можно переписать без `OUTER` ключевое слово.  
  
 Несовпадающие строки из правой таблицы, сохраняются в правые внешние соединения. Следующий пример возвращает те же строки, как в приведенном выше примере левого внешнего соединения.  
  
```tsql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM DimProduct AS dp 
RIGHT OUTER JOIN FactInternetSales AS fis  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
 В следующем запросе используется `DimSalesTerritory` таблицы в качестве левой таблицы в левое внешнее соединение. Он извлекает `SalesOrderNumber` значения из `FactInternetSales` таблицы. Если существует заказов для какого-либо `SalesTerritoryKey`, запрос будет возвращать значение NULL для `SalesOrderNumber` для этой строки. Этот запрос упорядочен по `SalesOrderNumber` столбца, чтобы все значения NULL в этом столбце будет отображаться в верхней части результатов.  
  
```tsql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
LEFT OUTER JOIN FactInternetSales AS fis  
    ON dst.SalesTerritoryKey = fis.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
 Этот запрос можно переписать с правое внешнее соединение, чтобы получить те же результаты:  
  
```tsql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM FactInternetSales AS fis 
RIGHT OUTER JOIN DimSalesTerritory AS dst  
    ON fis.SalesTerritoryKey = dst.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="p-using-the-full-outer-join-syntax"></a>Т. С помощью синтаксиса FULL OUTER JOIN  
 В следующем примере показано полное внешнее соединение, которое возвращает все строки из обоих соединяемых таблиц, но возвращает значение NULL для значения, которые не соответствуют из другой таблицы.  
  
```tsql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
FULL OUTER JOIN FactInternetSales AS fis  
    ON dst.SalesTerritoryKey = fis.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
 Этот запрос можно переписать без `OUTER` ключевое слово.  
  
```tsql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
FULL JOIN FactInternetSales AS fis  
    ON dst.SalesTerritoryKey = fis.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="q-using-the-cross-join-syntax"></a>У. Использование синтаксиса CROSS JOIN  
 В следующем примере возвращается векторное произведение `FactInternetSales` и `DimSalesTerritory` таблицы. Список всех возможных комбинаций `SalesOrderNumber` и `SalesTerritoryKey` возвращаются. Обратите внимание на отсутствие `ON` предложение в запросе перекрестного соединения.  
  
```tsql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
CROSS JOIN FactInternetSales AS fis  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="r-using-a-derived-table"></a>Ф. Использование производной таблицы  
 Следующий пример использует производную таблицу ( `SELECT` инструкции после `FROM` предложение) для возврата `CustomerKey` и `LastName` столбцы всех клиентов в `DimCustomer` в таблице `BirthDate` значения позже 1 января 1970 года и фамилию 'Smith'.  
  
```tsql
-- Uses AdventureWorks  
  
SELECT CustomerKey, LastName  
FROM  
   (SELECT * FROM DimCustomer  
    WHERE BirthDate > '01/01/1970') AS DimCustomerDerivedTable  
WHERE LastName = 'Smith'  
ORDER BY LastName;  
```  
  
### <a name="s-reduce-join-hint-example"></a>Х. УМЕНЬШИТЬ пример указание соединения  
 В следующем примере используется `REDUCE` указание соединения для изменения обработки производной таблицы в запросе. При использовании `REDUCE` указание соединения в этом запросе `fis.ProductKey` запланировано, репликации и вноситься distinct и затем присоединить их к `DimProduct` при случайном порядке из `DimProduct` на `ProductKey`. Результирующая таблица производного распространяется на `fis.ProductKey`.  
  
```tsql
-- Uses AdventureWorks  
  
EXPLAIN SELECT SalesOrderNumber  
FROM  
   (SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
    FROM DimProduct AS dp   
      INNER REDUCE JOIN FactInternetSales AS fis   
          ON dp.ProductKey = fis.ProductKey  
   ) AS dTable  
ORDER BY SalesOrderNumber;  
```  
  
### <a name="t-replicate-join-hint-example"></a>T. Пример указания REPLICATE соединения  
 В следующем примере показан один и тот же запрос аналогичен предыдущему примеру, за исключением того, что `REPLICATE` указание соединения используется вместо `REDUCE` указание соединения. Использование `REPLICATE` указание приводит значений в `ProductKey` (объединяющий) столбец из `FactInternetSales` таблицы реплицируются на все узлы. `DimProduct` Таблица соединяется с реплицированной версии этих значений.  
  
```tsql
-- Uses AdventureWorks  
  
EXPLAIN SELECT SalesOrderNumber  
FROM  
   (SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
    FROM DimProduct AS dp   
      INNER REPLICATE JOIN FactInternetSales AS fis  
          ON dp.ProductKey = fis.ProductKey  
   ) AS dTable  
ORDER BY SalesOrderNumber;  
```  
  
### <a name="u-using-the-redistribute-hint-to-guarantee-a-shuffle-move-for-a-distribution-incompatible-join"></a>Ф. Использование подсказки РАСПРОСТРАНЕНИЯ для обеспечения перемещения в случайном порядке для объединения несовместимых распространения  
 В следующем запросе используется указание запроса РАСПРОСТРАНЕНИЯ на соединении несовместимые распространения. Это гарантирует, что оптимизатор запросов будет использовать для перемещения в случайном порядке в плане запроса. Это также гарантирует план запроса не будет использовать перемещения широковещательной рассылки, который перемещает распределенные таблицы в реплицированную таблицу.  
  
 В следующем примере указанием REDISTRIBUTE принудительно случайный порядок перемещения на таблицу FactInternetSales, поскольку ProductKey столбец распределения для DimProduct и не является столбцом распределения для FactInternetSales.  
  
```tsql
-- Uses AdventureWorks  
  
EXPLAIN  
SELECT dp.ProductKey, fis.SalesOrderNumber, fis.TotalProductCost  
FROM DimProduct AS dp 
INNER REDISTRIBUTE JOIN FactInternetSales AS fis  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
## <a name="see-also"></a>См. также:  
 [CONTAINSTABLE (Transact-SQL)](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [FREETEXTTABLE (Transact-SQL)](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [OPENQUERY &#40; Transact-SQL &#41;](../../t-sql/functions/openquery-transact-sql.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
