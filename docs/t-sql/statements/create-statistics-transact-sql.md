---
title: "СОЗДАТЬ СТАТИСТИКУ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STATISTICS
- STATISTICS_TSQL
- CREATE STATISTICS
- CREATE_STATISTICS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- query optimization statistics [SQL Server], creating
- indexed views [SQL Server], statistics
- FULLSCAN option
- CREATE STATISTICS statement
- filtered statistics [SQL Server]
- creating statistics [SQL Server]
- NORECOMPUTE clause
ms.assetid: b23e2f6b-076c-4e6d-9281-764bdb616ad2
caps.latest.revision: 105
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2e09604deac2b823243515c10398dc27c75941bd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-statistics-transact-sql"></a>CREATE STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Создает статистику оптимизации запросов на один или несколько столбцов таблицы, индексированного представления или внешней таблицы. Для большинства запросов оптимизатор уже создает достаточно статистики для формирования высококачественного плана запроса, но в некоторых случаях для повышения производительности запросов нужно создать дополнительные статистические данные с помощью инструкции CREATE STATISTICS или изменить структуру запроса.  
  
 Дополнительные сведения см. в разделе [статистики](../../relational-databases/statistics/statistics.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Create statistics on an external table  
CREATE STATISTICS statistics_name   
ON { table_or_indexed_view_name } ( column [ ,...n ] )   
    [ WITH FULLSCAN ] ;  
  
-- Create statistics on a regular table or indexed view  
CREATE STATISTICS statistics_name   
ON { table_or_indexed_view_name } ( column [ ,...n ] )   
    [ WHERE <filter_predicate> ]  
    [ WITH   
        [ [ FULLSCAN   
            [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
          | SAMPLE number { PERCENT | ROWS }   
            [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
          | STATS_STREAM = stats_stream ] ]   
        [ [ , ] NORECOMPUTE ]   
        [ [ , ] INCREMENTAL = { ON | OFF } ]  
    ] ;  
  
<filter_predicate> ::=   
    <conjunct> [AND <conjunct>]  
  
<conjunct> ::=  
    <disjunct> | <comparison>  
  
<disjunct> ::=  
        column_name IN (constant ,…)  
  
<comparison> ::=  
        column_name <comparison_op> constant  
  
<comparison_op> ::=  
    IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !<  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE STATISTICS statistics_name   
    ON [ database_name . [schema_name ] . | schema_name. ] table_name   
    ( column_name  [ ,...n ] )   
    [ WHERE <filter_predicate> ]  
    [ WITH {  
           FULLSCAN   
           | SAMPLE number PERCENT   
      }  
    ]  
[;]  
  
<filter_predicate> ::=   
    <conjunct> [AND <conjunct>]  
  
<conjunct> ::=  
    <disjunct> | <comparison>  
  
<disjunct> ::=  
        column_name IN (constant ,…)  
  
<comparison> ::=  
        column_name <comparison_op> constant  
  
<comparison_op> ::=  
    IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !<  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_статистики*  
 Имя создаваемой статистики.  
  
 *table_or_indexed_view_name*  
 — Имя таблицы, индексированного представления или внешней таблицы, в которой требуется создать статистику. Создание статистики для другой базы данных, укажите полное имя таблицы.  
  
 *столбец [,... n]*  
 Один или несколько столбцов, которые будут включены в статистику. Столбцы должны быть в порядке приоритета слева направо. Только первый столбец используется для создания гистограммы. Все столбцы используются для статистику корреляции между столбцами, называемую плотности.  
  
 Можно указать любой столбец, который может указываться в качестве ключевого столбца индекса, за исключением следующих столбцов.  
  
-   **XML**, full-text и нельзя указывать столбцы FILESTREAM.  
  
-   Вычисляемые столбцы могут быть указаны только в том случае, если параметры ARITHABORT и QUOTED_IDENTIFIER базы данных имеют значение ON.  
  
-   Столбцы, имеющие определяемый пользователем тип данных CLR, могут быть указаны, если этот тип поддерживает двоичное упорядочение. Вычисляемые столбцы, определенные как вызовы методов для столбца определяемого пользователем типа, могут быть указаны, если эти методы отмечены как детерминированные.  
  
 ГДЕ \<filter_predicate > указывает выражение для выбора подмножества включаемых строк при создании объекта статистики. Статистика, создаваемая с предикатом фильтра, называется отфильтрованной. Предикат фильтра использует простую логику сравнения и не может ссылаться на вычисляемый столбец, столбец определяемого пользователем ТИПА, столбец типа пространственных данных или **hierarchyID** столбец типа данных. Сравнения с помощью литералов NULL с операторами сравнения недопустимы. Вместо этого используются операторы IS NULL и IS NOT NULL.  
  
 Далее приведено несколько примеров использования предикатов фильтра для таблицы Production.BillOfMaterials:  
  
 `WHERE StartDate > '20000101' AND EndDate <= '20000630'`  
  
 `WHERE ComponentID IN (533, 324, 753)`  
  
 `WHERE StartDate IN ('20000404', '20000905') AND EndDate IS NOT NULL`  
  
 Дополнительные сведения о предикатах фильтра см. в разделе [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md).  
  
 FULLSCAN  
 Вычисляет статистику путем сканирования всех строк. FULLSCAN и SAMPLE 100 PERCENT имеют одинаковые результаты. FULLSCAN не может быть использован с параметром SAMPLE.  
  
 Если этот параметр опущен, SQL Server использует для создания статистики выборки и определяет размер выборки, необходимое для создания плана запроса высокого качества  
  
 Образец *номер* {% | СТРОКИ}  
 Указывает приблизительное процентное соотношение или число строк в таблице или индексированном представлении для оптимизатора запросов, которые используются при создании статистики. Для параметра PERCENT *номер* может быть от 0 до 100, а для СТРОК, *номер* может составлять от 0 до общее число строк. Фактическое процентное соотношение или число строк, отбираемых оптимизатором запросов, может не совпадать с заданным значением. Например, оптимизатор запросов просматривает все строки на странице данных.  
  
 Команда SAMPLE полезна в особых случаях, в которых план запроса на основе выборки по умолчанию не является оптимальным. В большинстве ситуаций нет необходимости указывать параметр SAMPLE, поскольку по умолчанию оптимизатор запросов применяет такие правила отбора, чтобы сформировать выборку статистически значимого размера, что необходимо для создания высококачественных планов запросов.  
  
 Параметр SAMPLE нельзя использовать вместе с параметром FULLSCAN. Если не указана ни одна из команд SAMPLE или FULLSCAN, оптимизатор запросов использует выбранные данные и вычисляет размер выборки по умолчанию.  
  
 Не рекомендуется указывать значения 0 PERCENT и 0 ROWS. Если для PERCENT или ROWS указано значение 0, объект статистики будет создан без статистических данных.  
 
 PERSIST_SAMPLE_PERCENT = {ON | {OFF}  
 Когда **ON**, статистики будут сохранять процента создания выборки для последующих обновлений, которые явно не указан процент выборки. Когда **OFF**, Процент выборки статистика будет сброшен для выборки по умолчанию при последующих обновлениях, которые явно не указан процент выборки. Значение по умолчанию — **OFF**. 
 
 **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4.  
  
 STATS_STREAM  **=**  *stats_stream*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 NORECOMPUTE  
 Отключите автоматический параметр обновления статистики, AUTO_STATISTICS_UPDATE, для *имя_статистики*. Если этот параметр указан, оптимизатор запросов завершит любое обновление статистики в процессе выполнения для *имя_статистики* и отключит будущие обновления.  
  
 Чтобы вновь включить обновление статистики, удалите статистику с [DROP STATISTICS](../../t-sql/statements/drop-statistics-transact-sql.md) и затем выполните инструкцию CREATE STATISTICS без параметра NORECOMPUTE.  
  
> [!WARNING]  
>  Использование этого параметра может привести к созданию неоптимальных планов запросов. Рекомендуется ограничить использование этого параметра, причем использовать его надлежит только опытным системным администраторам.  
  
 Дополнительные сведения о параметре auto_statistics_update см. в разделе [параметры ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md). Дополнительные сведения об отключении и повторном включении обновления статистики см. в разделе [статистики](../../relational-databases/statistics/statistics.md).  
  
 INCREMENTAL = { ON | OFF }  
 Когда **ON**, являются статистики создаются как статистики отдельно по секциям. Когда **OFF**, Статистика объединяются для всех секций. Значение по умолчанию — **OFF**.  
  
 Если статистики по секциям не поддерживаются, возвращается ошибка. Добавочные статистики не поддерживаются для следующих типов статистических данных.  
  
-   Статистики, созданные с индексами, не выровненными по секциям для базовой таблицы.  
  
-   Статистики, созданные в доступных для чтения базах данных-получателях AlwaysOn.  
  
-   Статистики, созданные в базах данных, доступных только для чтения.  
  
-   Статистики, созданные по фильтрованным индексам.  
  
-   Статистика, созданная по представлениям.  
  
-   Статистики, созданные по внутренним таблицам.  
  
-   Статистики, созданные с пространственными индексами или XML-индексами.  
  
**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="permissions"></a>Permissions  
 Требуется один из этих разрешений:  
  
-   ALTER TABLE  
  
-   Пользователь является владельцем таблицы  
  
-   Членство в **db_ddladmin** предопределенной роли базы данных  
  
## <a name="general-remarks"></a>Общие замечания  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно использовать базу данных tempdb для сортировки строк, включенных для создания статистики.  
  
### <a name="statistics-for-external-tables"></a>Статистика для внешних таблиц  
 При создании статистики внешней таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] импортирует внешние таблицы в временную [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы, а затем создает статистику. Для статистики образцы импортируются только строки выборки. При наличии больших внешней таблицы будет гораздо быстрее использовать выборки по умолчанию вместо параметра полной проверки.  
  
### <a name="statistics-with-a-filtered-condition"></a>Статистика с отфильтрованное условие  
 Отфильтрованная статистика может повысить производительность запросов, которые выполняют выборку из четко определенных подмножеств данных. Отфильтрованная статистика использует предикат фильтра в предложении WHERE для выбора подмножества данных, включенных в статистику.  
  
### <a name="when-to-use-create-statistics"></a>Условия использования инструкции CREATE STATISTICS  
 Дополнительные сведения об условиях использования CREATE STATISTICS см. в разделе [статистики](../../relational-databases/statistics/statistics.md).  
  
### <a name="referencing-dependencies-for-filtered-statistics"></a>Упоминаемые зависимости для отфильтрованной статистики  
 [Sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) представление каталога содержит каждый столбец в предикате отфильтрованной статистики как ссылаемую зависимость. Обратите внимание на операции, которые выполняются на столбцах таблицы, созданной до создания отфильтрованной статистики, потому что определение столбца таблицы, указанного в предикате отфильтрованной статистики, невозможно удалить, переименовать или изменить.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
*  Обновление статистики во внешних таблицах не поддерживается. Для обновления статистики в external table, drop и повторного создания статистики.  
*  Может содержать до 64 столбцов каждый объект статистики.
  
## <a name="examples"></a>Примеры  

### <a name="examples-use-the-adventureworks-database"></a>Примеры использования базы данных AdventureWorks.  

### <a name="a-using-create-statistics-with-sample-number-percent"></a>A. Использование инструкции CREATE STATISTICS с аргументом «SAMPLE число PERCENT»  
 В следующем примере создается статистика `ContactMail1`, использующая случайную 5-процентную выборку из столбцов `BusinessEntityID` и `EmailPromotion` таблицы `Contact` базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```t-sql  
CREATE STATISTICS ContactMail1  
    ON Person.Person (BusinessEntityID, EmailPromotion)  
    WITH SAMPLE 5 PERCENT;  
```  
  
### <a name="b-using-create-statistics-with-fullscan-and-norecompute"></a>Б. Использование инструкции CREATE STATISTICS с аргументами FULLSCAN и NORECOMPUTE  
 В следующем примере создается статистика `ContactMail2` по всем строкам для столбцов `BusinessEntityID` и `EmailPromotion` таблицы `Contact`, при этом автоматический перерасчет статистики блокируется.  
  
```t-sql  
CREATE STATISTICS NamePurchase  
    ON AdventureWorks2012.Person.Person (BusinessEntityID, EmailPromotion)  
    WITH FULLSCAN, NORECOMPUTE;  
```  
  
### <a name="c-using-create-statistics-to-create-filtered-statistics"></a>В. С помощью инструкции CREATE STATISTICS создания отфильтрованной статистики  
 В следующем примере создается отфильтрованная статистика `ContactPromotion1`. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] просматривает 50 процентов данных, а затем выбирает все строки с `EmailPromotion`, равным 2.  
  
```t-sql  
CREATE STATISTICS ContactPromotion1  
    ON Person.Person (BusinessEntityID, LastName, EmailPromotion)  
WHERE EmailPromotion = 2  
WITH SAMPLE 50 PERCENT;  
GO  
```  
  
### <a name="d-create-statistics-on-an-external-table"></a>Г. Создание статистики для внешней таблицы  
 Что нужно делать при создании статистики в external table, помимо списка столбцов, только одно решение, ли нужно создать статистику с помощью выборки строк или путем сканирования всех строк.  
  
 Поскольку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Импорт данных из внешней таблицы во временную таблицу для создания статистики, параметр полное сканирование займет больше времени. Для большой таблицы метод выборки по умолчанию обычно достаточно.  
  
```t-sql  
--Create statistics on an external table and use default sampling.  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress);  
  
--Create statistics on an external table and scan all the rows  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress) WITH FULLSCAN;  
```  

### <a name="e-using-create-statistics-with-fullscan-and-persistsamplepercent"></a>Д. С помощью инструкции CREATE STATISTICS с аргументами FULLSCAN и PERSIST_SAMPLE_PERCENT  
 В следующем примере создается `ContactMail2` статистику для всех строк в `BusinessEntityID` и `EmailPromotion` столбцы `Contact` таблицы и задает процент выборки 100 процентов для всех последующих обновлений, которые следует явным образом не данном задавать выборки процент.  
  
```t-sql  
CREATE STATISTICS NamePurchase  
    ON AdventureWorks2012.Person.Person (BusinessEntityID, EmailPromotion)  
    WITH FULLSCAN, PERSIST_SAMPLE_PERCENT = ON;  
```  
  
### <a name="examples-using-adventureworksdw-database"></a>Примеры использования базы данных AdventureWorksDW. 
  
### <a name="f-create-statistics-on-two-columns"></a>Е. Создание статистики по двум столбцам  
 В следующем примере создается `CustomerStats1` статистику на основании `CustomerKey` и `EmailAddress` столбцы `DimCustomer` таблицы. Статистические данные создаются на статистически значимой выборки строк в основе `Customer` таблицы.  
  
```t-sql  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress);  
```  
  
### <a name="g-create-statistics-by-using-a-full-scan"></a>Ж. Создать статистику с помощью полной проверки  
 В следующем примере создается `CustomerStatsFullScan` статистику, на основании сканирования всех строк в `DimCustomer` таблицы.  
  
```t-sql  
CREATE STATISTICS CustomerStatsFullScan 
ON DimCustomer (CustomerKey, EmailAddress) WITH FULLSCAN;  
```  
  
### <a name="h-create-statistics-by-specifying-the-sample-percentage"></a>З. Создать статистику, указав процент образца  
 В следующем примере создается `CustomerStatsSampleScan` статистику, на основании сканирование 50 процентов строк в `DimCustomer` таблицы.  
  
```t-sql  
CREATE STATISTICS CustomerStatsSampleScan 
ON DimCustomer (CustomerKey, EmailAddress) WITH SAMPLE 50 PERCENT;  
```  
  
## <a name="see-also"></a>См. также:  
 [Статистика](../../relational-databases/statistics/statistics.md)   
 [UPDATE STATISTICS (Transact-SQL)](../../t-sql/statements/update-statistics-transact-sql.md)   
 [sp_updatestats (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md)   
 [DBCC SHOW_STATISTICS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS (Transact-SQL)](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [sys.stats_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)  
  
  


