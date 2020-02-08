---
title: DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 669c6274301c09f260badfb354c8add67ae86791
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "74401636"
---
# <a name="dbcc-pdw_showmaterializedviewoverhead-transact-sql"></a>DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD (Transact-SQL)  

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Эта инструкция отображает количество добавочных изменений в базовых таблицах, которые хранятся в материализованных представлениях в службе "[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]". Коэффициент затрат рассчитывается по следующей формуле: TOTAL_ROWS / MAX (1, BASE_VIEW_ROWS).

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис

```
DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ( " [ schema_name .] materialized_view_name  " )
[;]
```
  
## <a name="arguments"></a>Аргументы

 *schema_name*     
 Имя схемы, которой принадлежит представление.

*materialized_view_name*   
Имя материализованного представления.

## <a name="remarks"></a>Remarks

Для сохранения материализованных представлений, обновляемых при изменении данных в базовых таблицах, подсистема хранилища данных добавляет отслеживаемые строки в каждое затронутое представление для отражения изменений. Выборка из материализованного представления предусматривает сканирование его кластеризованного индекса columnstore и применение всех дополнительных изменений.  Строки отслеживания (TOTAL_ROWS-BASE_VIEW_ROWS) не удаляются до тех пор, пока пользователи не перестроят материализованное представление.  

Коэффициент затрат overhead_ratio рассчитывается по следующей формуле: TOTAL_ROWS/MAX(1, BASE_VIEW_ROWS).  Если значение высокое, производительность SELECT будет снижена.  Пользователи могут перестроить материализованные представления, чтобы уменьшить коэффициент.

## <a name="permissions"></a>Разрешения  
  
Необходимо разрешение VIEW DATABASE STATE.  

## <a name="examples"></a>Примеры  

### <a name="a-this-example-returns-the-overhead-ratio-of-a-materialized-view"></a>A. Этот пример возвращает коэффициент накладных расходов для материализованного представления.

```sql
DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ( "dbo.MyIndexedView" )
```

Выходные данные:

|OBJECT_ID|BASE_VIEW_ROWS|TOTAL_ROWS|OVERHEAD_RATIO|
|--------|--------|--------|--------|  
|1 234|1|3 |3.0 |

</br>

### <a name="b-this-example-shows-how-the-materialized-view-overhead-increases-as-data-changes-in-base-tables"></a>Б. В этом примере показано, как увеличиваются издержки материализованных представлений по мере изменения данных в базовых таблицах.

Создание таблицы
```sql
CREATE TABLE t1 (c1 int NOT NULL, c2 int not null, c3 int not null)
```
Вставка пяти строк в t1
```sql
INSERT INTO t1 VALUES (1, 1, 1)
INSERT INTO t1 VALUES (2, 2, 2) 
INSERT INTO t1 VALUES (3, 3, 3) 
INSERT INTO t1 VALUES (4, 4, 4) 
INSERT INTO t1 VALUES (5, 5, 5) 
```
Создание материализованного представления MV1
```sql
CREATE materialized view MV1 
WITH (DISTRIBUTION = HASH(c1))  
AS
SELECT c1, count(*) total_number 
FROM dbo.t1 where c1 < 3
GROUP BY c1  
```
Выборка из материализованного представления возвращает две строки.

|c1|total_number|
|--------|--------| 
|1|1| 
|2|1|

Проверка издержек материализованного представления перед изменением данных в базовой таблице.
```sql
DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ("dbo.mv1")
```
Выходные данные:

|OBJECT_ID|BASE_VIEW_ROWS|TOTAL_ROWS|OVERHEAD_RATIO|
|--------|--------|--------|--------|  
|587149137|2|2 |1.00000000000000000 |

Обновление базовой таблицы.  Этот запрос обновляет один и тот же столбец в одной строке 100 раз одним и тем же значением.  Содержимое материализованного представления не изменяется.
```sql
DECLARE @p int
SELECT @p = 1
WHILE (@p < 101)
BEGIN
UPDATE t1 SET c1 = 1 WHERE c1 = 1
SELECT @p = @p+1
END  
```

Выборка из материализованного представления возвращает тот же результат.  

|c1|total_number|
|--------|--------| 
|1|1| 
|2|1|

Ниже приведены выходные данные DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ("dbo. mv1").  В материализованное представление (total_row-base_view_rows) добавлено 100 строк, и его overhead_ratio увеличивается. 

|OBJECT_ID|BASE_VIEW_ROWS|TOTAL_ROWS|OVERHEAD_RATIO|
|--------|--------|--------|--------|  
|587149137|2|102 |51.00000000000000000 |

После перестроения материализованного представления удаляются все строки отслеживания для добавочных изменений данных, а также уменьшается коэффициент издержек представления.  

```sql
ALTER MATERIALIZED VIEW dbo.MV1 REBUILD
go
DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ("dbo.mv1")
```
Выходные данные

|OBJECT_ID|BASE_VIEW_ROWS|TOTAL_ROWS|OVERHEAD_RATIO|
|--------|--------|--------|--------|  
|587149137|2|2 |1.00000000000000000 |

## <a name="see-also"></a>См. также раздел

[Настройка производительности с помощью материализованного представления](/azure/sql-data-warehouse/performance-tuning-materialized-views)   
[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
[System views supported in Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)  (Системные представления, поддерживаемые в службе "Хранилище данных SQL Azure")  
[T-SQL statements supported in Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements) (Инструкции Т-SQL, поддерживаемые в службе "Хранилище данных SQL Azure")
