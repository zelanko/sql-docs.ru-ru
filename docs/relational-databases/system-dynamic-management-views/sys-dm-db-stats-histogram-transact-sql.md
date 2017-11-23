---
title: "sys.dm_db_stats_histogram (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.dm_db_stats_histogram
- sys.dm_db_stats_histogram_TSQL
- dm_db_stats_histogram
- dm_db_stats_histogram_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_stats_histogram dynamic management function
ms.assetid: 1897fd4a-8d51-461e-8ef2-c60be9e563f2
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 93aec7a71f3522114bc9ef6c2d19edaccaac2e57
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysdmdbstatshistogram-transact-sql"></a>sys.dm_db_stats_histogram (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Возвращает гистограммы статистики для указанного объекта (таблицы или индексированного представления) в текущем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных. Аналогично `DBCC SHOW_STATISTICS WITH HISTOGRAM`.

> [!NOTE] 
> Это DMF доступен, начиная с [!INCLUDE[ssSQL15](../../includes/ssSQL15-md.md)] SP1 CU2

## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_db_stats_histogram (object_id, stats_id)  
```  
  
## <a name="arguments"></a>Аргументы  
 *object_id*  
 Идентификатор объекта текущей базы данных, для которого запрашиваются статистические свойства. *object_id* имеет тип **int**.  
  
 *stats_id*  
 Идентификатор статистики для указанного аргумента *object_id*. Идентификатор статистики может быть получен из динамического административного представления [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) . *stats_id* имеет тип **int**.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|object_id |**int**|Идентификатор объекта (таблицы или индексированного представления), для которого возвращаются свойства объекта статистики.|  
|stats_id |**int**|Идентификатор объекта статистики. Является уникальным в пределах таблицы или индексированного представления. Дополнительные сведения см. в статье [sys.stats (Transact-SQL)](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md).|  
|step_number |**int** |Номер шага гистограммы. |
|range_high_key |**sql_variant** |Верхнее граничное значение столбца для шага гистограммы. Это значение столбца называется также ключевым значением.|
|range_rows |**real** |Предполагаемое количество строк, значение столбцов которых находится в пределах шага гистограммы, исключая верхнюю границу. |
|equal_rows |**real** |Предполагаемое количество строк, значение столбцов которых равно верхней границе шага гистограммы. |
|distinct_range_rows |**bigint** |Предполагаемое количество строк с различающимся значением столбца в пределах шага гистограммы, исключая верхнюю границу. |
|average_range_rows |**real** |Среднее количество строк с повторяющимися значениями столбцов в пределах шага гистограммы, исключая верхнюю границу (`RANGE_ROWS / DISTINCT_RANGE_ROWS` для `DISTINCT_RANGE_ROWS > 0`). |
  
 ## <a name="remarks"></a>Замечания  
 
 Результирующий набор для `sys.dm_db_stats_histogram` возвращает информацию, аналогичную `DBCC SHOW_STATISTICS WITH HISTOGRAM` , а также `object_id`, `stats_id`, и `step_number`.

 Так как столбец `range_high_key` является данных sql_variant тип, может потребоваться использовать `CAST` или `CONVERT` , если предикат не сравнения с константой не являющегося строкой.

### <a name="histogram"></a>Гистограмма
  
 Гистограмма измеряет частоту появления каждого различающегося значения в наборе данных. Оптимизатор запросов вычисляет гистограмму для значений столбца в первом ключевом столбце объекта статистики, выбирая значения столбцов путем статистической выборки строк или при помощи полного просмотра всех строк в таблице или представлении. Если гистограмма создается на основе выбранного набора строк, то сохраняемые итоговые значения количества строк и количества различающихся значений являются приблизительными и не всегда выражаются целыми числами.  
  
 Чтобы создать гистограмму, оптимизатор запросов сортирует значения столбцов, вычисляет количество значений, совпадающих с каждым различающимся значением столбца, а затем осуществляет статистическую обработку значений столбцов с получением непрерывных шагов гистограммы, максимальное количество которых составляет 200. Каждый шаг включает диапазон значений столбцов, за которым следует значение столбца, представляющее собой верхнюю границу. В этот диапазон входят все возможные значения столбца между граничными значениями, за исключением самих граничных значений. Наименьшим из отсортированных значений столбца является верхнее граничное значение первого шага гистограммы.  
  
 На следующей диаграмме показана гистограмма с шестью шагами. Первый шаг — это область слева от первого верхнего граничного значения.  
  
 ![](../../relational-databases/system-dynamic-management-views/media/a0ce6714-01f4-4943-a083-8cbd2d6f617a.gif "a0ce6714-01f4-4943-a083-8cbd2d6f617a")  
  
 В каждом шаге гистограммы:  
  
-   Полужирной линией верхнее граничное значение (*range_high_key*) и количество его вхождений (*equal_rows*)  
  
-   Закрашенная область слева от *range_high_key* представляет диапазон значений столбца и среднее количество вхождений каждого значения в столбце (*average_range_rows*). *Average_range_rows* для гистограммы первый шаг всегда равно 0.  
  
-   Пунктирные линии обозначают выбранные значения, используется для оценки общее количество уникальных значений в диапазоне (*distinct_range_rows*) и общее количество значений в диапазоне (*range_rows*). Оптимизатор запросов использует *range_rows* и *distinct_range_rows* для вычисления *average_range_rows* и не хранит выбранные значения.  
  
 Оптимизатор запросов определяет шаги гистограммы согласно их статистической значимости. Он использует алгоритм максимальной разности для сведения к минимуму числа шагов в гистограмме и вместе с тем максимального увеличения разницы между граничными значениями. Максимальное число шагов — 200. Число шагов гистограммы может быть меньше, чем количество различающихся значений, даже для столбцов, в которых число граничных точек меньше 200. Например, столбец со 100 различающимися значениями может иметь гистограмму, число граничных точек в которой меньше 100.  
  
## <a name="permissions"></a>Permissions  

Требуется наличие у пользователя разрешения на выбор столбцов статистики либо то, чтобы пользователь был владельцем таблицы или членом предопределенной роли сервера `sysadmin`, предопределенной роли базы данных `db_owner` или предопределенной роли базы данных `db_ddladmin`.

## <a name="examples"></a>Примеры  

### <a name="a-simple-example"></a>A. Простой пример    
Следующий пример создает и заполняет простой таблицы. Затем создает статистику по `Country_Name` столбца.

```tsql
CREATE TABLE Country
(Country_ID int IDENTITY PRIMARY KEY,
Country_Name varchar(120) NOT NULL);
INSERT Country (Country_Name) VALUES ('Canada'), ('Denmark'), ('Iceland'), ('Peru');

CREATE STATISTICS Country_Stats  
    ON Country (Country_Name) ;  
```   
Первичный ключ занимает `stat_id` номер 1, поэтому вызовов `sys.dm_db_stats_histogram` для `stat_id` номер 2, для возврата гистограммы статистики для `Country` таблицы.    
```tsql     
SELECT * FROM sys.dm_db_stats_histogram(OBJECT_ID('Country'), 2);
```


### <a name="b-useful-query"></a>Б. Удобный запрос:   
```tsql  
SELECT hist.step_number, hist.range_high_key, hist.range_rows, 
    hist.equal_rows, hist.distinct_range_rows, hist.average_range_rows
FROM sys.stats AS s
CROSS APPLY sys.dm_db_stats_histogram(s.[object_id], s.stats_id) AS hist
WHERE s.[name] = N'<statistic_name>';
```

### <a name="c-useful-query"></a>В. Удобный запрос:
В следующем примере выбираются из таблицы `Country` с предикатом столбца `Country_Name`.

```tsql  
SELECT * FROM Country 
WHERE Country_Name = 'Canada';
```

Следующий пример просматривает ранее созданной статистики для таблицы `Country` и столбец `Country_Name` для шага гистограммы, соответствующие предикату в приведенном выше запросе.

```tsql  
SELECT ss.name, ss.stats_id, shr.steps, shr.rows, shr.rows_sampled, 
    shr.modification_counter, shr.last_updated, sh.range_rows, sh.equal_rows
FROM sys.stats ss
INNER JOIN sys.stats_columns sc 
    ON ss.stats_id = sc.stats_id AND ss.object_id = sc.object_id
INNER JOIN sys.all_columns ac 
    ON ac.column_id = sc.column_id AND ac.object_id = sc.object_id
CROSS APPLY sys.dm_db_stats_properties(ss.object_id, ss.stats_id) shr
CROSS APPLY sys.dm_db_stats_histogram(ss.object_id, ss.stats_id) sh
WHERE ss.[object_id] = OBJECT_ID('Country') 
    AND ac.name = 'Country_Name'
    AND sh.range_high_key = CAST('Canada' AS CHAR(8));
```
  
## <a name="see-also"></a>См. также:  

[Инструкция DBCC SHOW_STATISTICS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
[Динамические административные представления и функции (Transact-SQL)](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_db_stats_properties (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)  
