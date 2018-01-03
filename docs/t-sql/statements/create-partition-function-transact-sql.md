---
title: "Создание функции СЕКЦИОНИРОВАНИЯ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE PARTITION FUNCTION
- PARTITION
- PARTITION FUNCTION
- PARTITION_FUNCTION_TSQL
- PARTITION_TSQL
- CREATE_PARTITION_FUNCTION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- RANGE RIGHT partition functions
- RANGE LEFT partition functions
- partitioned indexes [SQL Server], functions
- functions [SQL Server], creating
- partition functions [SQL Server], creating
- partitioned tables [SQL Server], functions
- CREATE PARTITION FUNCTION statement
ms.assetid: 9dfe8b76-721e-42fd-81ae-14e22258c4f2
caps.latest.revision: "57"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a095e1de4fdffc97d615a39fd7cf185c99493d02
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="create-partition-function-transact-sql"></a>CREATE PARTITION FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает функцию в текущей базе данных, которая сопоставляет строки таблицы или индекса с секциями, основываясь на значениях элементов заданного столбца. Инструкция CREATE PARTITION FUNCTION используется на начальной стадии создания секционированной таблицы или индекса. Таблица или индекс в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] могут содержать до 15 000 секций.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE PARTITION FUNCTION partition_function_name ( input_parameter_type )  
AS RANGE [ LEFT | RIGHT ]   
FOR VALUES ( [ boundary_value [ ,...n ] ] )   
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *partition_function_name*  
 Имя функции секционирования. Имена функций секционирования должны быть уникальными в пределах базы данных и соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
 *input_parameter_type*  
 Тип данных столбца, используемого для секционирования. В качестве столбцов секционирования могут использоваться данные любого типа, кроме **text**, **ntext**, **image**, **xml**, **timestamp**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, псевдонимов типов данных, а также определяемых пользователем типов данных CLR.  
  
 Столбец секционирования задается с помощью инструкции CREATE TABLE или CREATE INDEX.  
  
 *boundary_value*  
 Указывает граничные значения для каждой секции секционированной таблицы или индекса, который использует *partition_function_name*. Если *boundary_value* является пустым, функция секционирования сопоставляет всю таблицу или индекс с использованием *partition_function_name* с одной секцией. Может использоваться только один столбец секционирования, заданный с помощью инструкции CREATE TABLE или CREATE INDEX.  
  
 *boundary_value* является константным выражением, которое может ссылаться на переменные. К ним относятся переменные типов данных, определяемых пользователем, а также стандартные и пользовательские функции. Он не может ссылаться на выражения [!INCLUDE[tsql](../../includes/tsql-md.md)]. *boundary_value* должен совпадать или быть неявно преобразуемым в тип данных, предоставленных в *input_parameter_type*, не могут быть усечены во время неявного преобразования в образом, что размер и масштаб значения не совпадает с соответствующим *input_parameter_type*.  
  
> [!NOTE]  
>  Если *boundary_value* состоит из **datetime** или **smalldatetime** литералы, эти оцениваются, предполагая, что языком сеанса является us_english. Такое поведение является устаревшим. Чтобы убедиться, что определение функции секционирования работает правильно для всех языков сеанса, рекомендуется использование констант, интерпретируемых одинаково для всех языковых настроек, таких как формат «ггггммдд», либо выполнить явное преобразование литералов в определенный стиль. Чтобы определить язык сеанса сервера, выполните `SELECT @@LANGUAGE`.  
  
 *.. .n*  
 Указывает число значений, предоставленных *boundary_value*, не должно превышать 14,999. Количество созданных секций равно  *n*  + 1. Перечисление значений по порядку не является обязательным. Если значения выведены не по порядку, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] сортирует их, создает функцию и выдает предупреждение о том, что значения выданы не по порядку. Ядро СУБД возвращает ошибку, если  *n*  повторяющихся значений.  
  
 **СЛЕВА** | ПРАВИЛЬНО  
 Указывает, к какой стороне каждого интервала граничных значений, влево или вправо, *boundary_value* [ **,***.. .n* ] принадлежит, когда значения интервалов были отсортированы по [!INCLUDE[ssDE](../../includes/ssde-md.md)]по возрастанию слева направо. Если значение не задано, то по умолчанию используется значение LEFT.  
  
## <a name="remarks"></a>Remarks  
 Область действия функции секционирования ограничена базой данных, в которой она была создана. Функции секционирования располагаются в отдельном от других функций пространстве имен внутри базы данных.  
  
 Все строки, которым соответствуют значения NULL столбца секционирования, располагаются в самой левой секции, кроме случая, когда задано пустое граничное значение и параметр RIGHT. В данном случае самая левая секция является пустой, и в нее помещаются значения NULL.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения инструкции CREATE PARTITION FUNCTION необходимо наличие одного из следующих разрешений.  
  
-   Разрешение ALTER ANY DATASPACE. Это разрешение назначено по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенных ролей базы данных **db_owner** и **db_ddladmin** .  
  
-   Разрешение CONTROL или ALTER для базы данных, в которой создается функция секционирования.  
  
-   Разрешение CONTROL SERVER или ALTER ANY DATABASE для сервера базы данных, в которой создается функция секционирования.  
  
##  <a name="BKMK_examples"></a> Примеры  
  
### <a name="a-creating-a-range-left-partition-function-on-an-int-column"></a>A. Создание функции секционирования RANGE LEFT для столбца данных типа int  
 Следующая функция секционирования разбивает таблицу или индекс на четыре секции.  
  
```sql  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
```  
  
 В следующей таблице показано, как таблица, использующая эту функцию секционирования для столбца секционирования **col1** бы быть секционированы.  
  
|Секция|1|2|3|4|  
|---------------|-------|-------|-------|-------|  
|**Значения**|**Col1** <= `1`|**Col1**  >  `1` AND **col1** <= `100`|**Col1**  >  `100` AND **col1** <=`1000`|**Col1** > `1000`|  
  
### <a name="b-creating-a-range-right-partition-function-on-an-int-column"></a>Б. Создание функции секционирования RANGE RIGHT для столбца данных типа int  
 Следующая функция секционирования использует те же значения для *boundary_value* [ **,***.. .n* ] аналогичен предыдущему примеру, за исключением того, он указывает RANGE RIGHT.  
  
```sql  
CREATE PARTITION FUNCTION myRangePF2 (int)  
AS RANGE RIGHT FOR VALUES (1, 100, 1000);  
```  
  
 В следующей таблице показано, как таблица, использующая эту функцию секционирования для столбца секционирования **col1** бы быть секционированы.  
  
|Секция|1|2|3|4|  
|---------------|-------|-------|-------|-------|  
|**Значения**|**Col1** \<`1`|**Col1**  >=  `1` AND **col1** \<`100`|**Col1**  >=  `100` AND **col1** \<`1000`|**Col1** >= `1000`| 
  
### <a name="c-creating-a-range-right-partition-function-on-a-datetime-column"></a>В. Создание функции секционирования RANGE RIGHT для столбца данных типа datetime  
 Следующая функция секционирования разбивает таблицу или индекс на 12 секций, по одной на каждый месяц года, за которые значения в **datetime** столбца.  
  
```sql  
CREATE PARTITION FUNCTION [myDateRangePF1] (datetime)  
AS RANGE RIGHT FOR VALUES ('20030201', '20030301', '20030401',  
               '20030501', '20030601', '20030701', '20030801',   
               '20030901', '20031001', '20031101', '20031201');  
```  
  
 В следующей таблице показано, как таблица или индекс, использующие эту функцию секционирования для столбца секционирования **datecol** бы быть секционированы.  
  
|Секция|1|2|...|11|12|  
|---------------|-------|-------|---------|--------|--------|  
|**Значения**|**datecol** \<`February 1, 2003`|**datecol**  >=  `February 1, 2003` AND **datecol** \<`March 1, 2003`||**datecol**  >=  `November 1, 2003` AND **col1** \<`December 1, 2003`|**datecol** >= `December 1, 2003`| 
  
### <a name="d-creating-a-partition-function-on-a-char-column"></a>Г. Создание функции секционирования для столбца данных типа char  
 Следующая функция секционирования разбивает таблицу или индекс на четыре секции.  
  
```sql  
CREATE PARTITION FUNCTION myRangePF3 (char(20))  
AS RANGE RIGHT FOR VALUES ('EX', 'RXE', 'XR');  
```  
  
 В следующей таблице показано, как таблица, использующая эту функцию секционирования для столбца секционирования **col1** бы быть секционированы.  
  
|Секция|1|2|3|4|  
|---------------|-------|-------|-------|-------|  
|**Значения**|**Col1** \< `EX`...|**Col1**  >=  `EX` AND **col1** \< `RXE`...|**Col1**  >=  `RXE` AND **col1** \< `XR`...|**Col1** >= `XR`| 
  
### <a name="e-creating-15000-partitions"></a>Д. Создание 15 000 секций  
 Следующая функция секционирования разбивает таблицу или индекс на 15 000 секций.  
  
```sql  
--Create integer partition function for 15,000 partitions.  
DECLARE @IntegerPartitionFunction nvarchar(max) = 
    N'CREATE PARTITION FUNCTION IntegerPartitionFunction (int) 
    AS RANGE RIGHT FOR VALUES (';  
DECLARE @i int = 1;  
WHILE @i < 14999  
BEGIN  
SET @IntegerPartitionFunction += CAST(@i as nvarchar(10)) + N', ';  
SET @i += 1;  
END  
SET @IntegerPartitionFunction += CAST(@i as nvarchar(10)) + N');';  
EXEC sp_executesql @IntegerPartitionFunction;  
GO  
```  
  
### <a name="f-creating-partitions-for-multiple-years"></a>Е. Создание разделов на несколько лет  
 Следующая функция секционирования разбивает таблицу или индекс на 50 секций на **datetime2** столбца. Существует по одному разделу для каждого месяца с января 2007 года по январь 2011 года.  
  
```sql  
--Create date partition function with increment by month.  
DECLARE @DatePartitionFunction nvarchar(max) = 
    N'CREATE PARTITION FUNCTION DatePartitionFunction (datetime2) 
    AS RANGE RIGHT FOR VALUES (';  
DECLARE @i datetime2 = '20070101';  
WHILE @i < '20110101'  
BEGIN  
SET @DatePartitionFunction += '''' + CAST(@i as nvarchar(10)) + '''' + N', ';  
SET @i = DATEADD(MM, 1, @i);  
END  
SET @DatePartitionFunction += '''' + CAST(@i as nvarchar(10))+ '''' + N');';  
EXEC sp_executesql @DatePartitionFunction;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Секционированные таблицы и индексы](../../relational-databases/partitions/partitioned-tables-and-indexes.md)   
 [$PARTITION &#40; Transact-SQL &#41;](../../t-sql/functions/partition-transact-sql.md)   
 [ALTER PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [DROP PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.partition_functions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_parameters &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)   
 [sys.partition_range_values &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [sys.partitions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  

