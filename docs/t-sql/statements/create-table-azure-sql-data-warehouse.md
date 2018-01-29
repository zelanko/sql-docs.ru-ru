---
title: "Создание таблицы (хранилище данных Azure SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/14/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ea21c73c-40e8-4c54-83d4-46ca36b2cf73
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f6e639bf97ed132b6ace7128b4cbe9b6f3ce474e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="create-table-azure-sql-data-warehouse"></a>Создание таблицы (хранилище данных Azure SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Создает новую таблицу в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
 
Таблицы и их использовании см [таблиц в хранилище данных SQL](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-overview/).

Примечание: Дискуссиях о хранилище данных SQL в этой статье применяется к хранилищу данных SQL и параллельных хранилищ данных Если не указано иное. 
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

<a name="Syntax"></a>   
## <a name="syntax"></a>Синтаксис  
  
```  
-- Create a new table. 
CREATE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( 
      { column_name <data_type>  [ <column_options> ] } [ ,...n ]   
    )  
    [ WITH [ <table_option> [ ,...n ] ) ]  
[;]  
   
<column_options> ::=
    [ COLLATE Windows_collation_name ]  
    [ NULL | NOT NULL ] -- default is NULL  
    [ [ CONSTRAINT constraint_name ] DEFAULT constant_expression  ]
  
<table_option> ::= 
    {   
        CLUSTERED COLUMNSTORE INDEX --default for SQL Data Warehouse 
      | HEAP --default for Parallel Data Warehouse   
      | CLUSTERED INDEX ( { index_column_name [ ASC | DESC ] } [ ,...n ] ) -- default is ASC 
    }  
    { 
        DISTRIBUTION = HASH ( distribution_column_name ) 
      | DISTRIBUTION = ROUND_ROBIN -- default for SQL Data Warehouse
      | DISTRIBUTION = REPLICATE -- default for Parallel Data Warehouse
    }   
    | PARTITION ( partition_column_name RANGE [ LEFT | RIGHT ] -- default is LEFT  
        FOR VALUES ( [ boundary_value [,...n] ] ) )  
  
<data type> ::=   
      datetimeoffset [ ( n ) ]  
    | datetime2 [ ( n ) ]  
    | datetime  
    | smalldatetime  
    | date  
    | time [ ( n ) ]  
    | float [ ( n ) ]  
    | real [ ( n ) ]  
    | decimal [ ( precision [ , scale ] ) ]   
    | numeric [ ( precision [ , scale ] ) ]   
    | money  
    | smallmoney  
    | bigint  
    | int   
    | smallint  
    | tinyint  
    | bit  
    | nvarchar [ ( n | max ) ]  -- max applies only to SQL Data Warehouse 
    | nchar [ ( n ) ]  
    | varchar [ ( n | max )  ] -- max applies only to SQL Data Warehouse  
    | char [ ( n ) ]  
    | varbinary [ ( n | max ) ] -- max applies only to SQL Data Warehouse  
    | binary [ ( n ) ]  
    | uniqueidentifier  
```  

<a name="Arguments"></a>   
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных, который будет содержать новую таблицу. Значение по умолчанию — текущая база данных.  
  
 *schema_name*  
 Схема таблицы. Указание *схемы* является необязательным. Если это поле оставить пустым, будет использоваться схема по умолчанию.  
  
 *имя_таблицы*  
 Имя новой таблицы. Чтобы создать локальную временную таблицу, перед именем таблицы с #.  Пояснения и рекомендации для временных таблиц см. в разделе [временных таблиц в хранилище данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-temporary/). 
 
 *column_name*  
 Имя столбца таблицы.
   
### <a name="ColumnOptions"></a>Параметры столбца

 `COLLATE` *Windows_collation_name*  
 Задает параметры сортировки для выражения. Параметры сортировки должен быть одним из параметров сортировки Windows, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список параметров сортировки Windows, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в разделе [имя параметров сортировки Windows (Transact-SQL)](http://msdn.microsoft.com/library/ms188046\(v=sql11\)/).  
  
 `NULL` | `NOT NULL`  
 Указывает, является ли `NULL` допустимы значения в столбце. Значение по умолчанию — `NULL`.  
  
 [ `CONSTRAINT` *constraint_name* ] `DEFAULT` *constant_expression*  
 Указывает значение столбца по умолчанию.  
  
 | Аргумент | Объяснение |
 | -------- | ----------- |
 | *constraint_name* | Необязательное имя для ограничения. Имя ограничения уникален в пределах базы данных. Имя можно использовать повторно в других базах данных. |
 | *constant_expression* | Значение по умолчанию для столбца. Выражение должно быть литералом или константой. Например, эти константных выражений допустимы: `'CA'`, `4`. Они не допускаются: `2+3`, `CURRENT_TIMESTAMP`. |
  

### <a name="TableOptions"></a>Параметры структуры таблицы
Рекомендации по выбору тип таблицы см. в разделе [индексирование таблиц в хранилище данных SQL Azure](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-tables-index/).
  
 `CLUSTERED COLUMNSTORE INDEX`  
Сохраняет таблицу как кластеризованный индекс. Кластеризованный индекс применяется ко всем данным таблицы. Это значение по умолчанию для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].   
 
 `HEAP`   
  Сохраняет таблицу в виде кучи. Это значение по умолчанию для [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 `CLUSTERED INDEX`( *index_column_name* [,...*n* ] )  
 Сохраняет таблицу в виде кластеризованного индекса для одного или нескольких ключевых столбцов. Это сохраняет данные построчно. Используйте *index_column_name* для указания имени один или несколько ключевых столбцов в индексе.  Дополнительные сведения см. в разделе таблицы Rowstore в общие замечания.
 
 `LOCATION = USER_DB`   
 Этот параметр устарел. Он синтаксически принимается, но больше не требуется и больше не влияет на поведение.   
  
### <a name="TableDistributionOptions"></a>Параметры распространения таблицы
Чтобы понять, как выбрать лучший способ распространения и использовать распределенные таблицы, в разделе [распределение таблиц в хранилище данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-distribute/).

`DISTRIBUTION = HASH`( *distribution_column_name* )   
Назначает каждую строку одной распространения путем хэширования значение, хранящееся в *distribution_column_name*. Алгоритм детерминирована, что означает, что всегда хэширование то же значение для того же распространителя.  Столбец распределения должен быть определен как NOT NULL с момента всех строк, имеющих значение NULL будет назначаться одинаковое распределение.

`DISTRIBUTION = ROUND_ROBIN`   
Распределяет строки равномерно рассылки циклического перебора. Это значение по умолчанию для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].

`DISTRIBUTION = REPLICATE`    
Хранит одной копии таблицы на каждом вычислительном узле. Для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] таблица хранится в базе данных распространителя на каждом вычислительном узле. Для [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], в которой хранится таблица [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файловой группе, которая охватывает вычислительных узлов. Это значение по умолчанию для [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
### <a name="TablePartitionOptions"></a>Параметры секционирования таблицы
Рекомендации по использованию секций таблицы. в разделе [секционирование таблиц в хранилище данных SQL](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-partition/).

 `PARTITION`( *partition_column_name* `RANGE` [ `LEFT`  |  `RIGHT` ] `FOR VALUES` ([ *boundary_value* [,...*n*] ] ))   
Создает один или несколько секций таблицы. Ниже приведены фрагменты горизонтальной таблиц, которые позволяют выполнять операции над подмножеств строк независимо от того, хранится ли таблица как куча, кластеризованный индекс или кластеризованный индекс. В отличие от столбца распределения секции таблицы, не определяют распространения, где каждая строка хранится. Вместо этого секций таблицы определите, как группируются и хранятся в течение каждого распределения строк.  
 
| Аргумент | Объяснение |
| -------- | ----------- |
|*partition_column_name*| Указывает столбец, который [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] будет использовать для секционирования строк. Этот столбец может быть любого типа данных. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Сортирует по возрастанию значений столбцов секционирования. Упорядочение низкого на высокий выходит из `LEFT` для `RIGHT` для `RANGE` спецификации. |  
| `RANGE LEFT` | Указывает граничное значение принадлежит к секции в левой части (более низкие значения). Значение по умолчанию — влево. |
| `RANGE RIGHT` | Указывает граничное значение принадлежит к секции справа (более высокие значения). | 
| `FOR VALUES`( *boundary_value* [,...*n*] ) | Указывает граничные значения для секции. *boundary_value* является константным выражением. Он не может принимать значение NULL. Он должен совпадать или быть неявно преобразуемым в тип данных *partition_column_name*. Он не может быть усечен во время неявного преобразования, чтобы размер и масштаб значения не соответствует типу данных из *partition_column_name*<br></br><br></br>При указании `PARTITION` предложение, но не указывает граничное значение [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] будет создать секционированную таблицу с одной секцией. Если это применимо, можно разделить таблицу на две секции в дальнейшем.<br></br><br></br>При указании одного значения границ, результирующая таблица имеет две секции; одно для значений меньше, чем значение границы и один для значений больше, чем значение границы. Обратите внимание, при перемещении секции в несекционированную таблицу несекционированная таблица будет получать данные, но не будет иметь границы секций в своих метаданных.| 
 
 В разделе [создать секционированную таблицу](#PartitionedTable) в подразделе «примеры».

### <a name="DataTypes"></a>Типы данных
[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]поддерживает наиболее часто используемые типы данных. Ниже приведен список поддерживаемых типов данных вместе с их сведения и памяти в байтах. Чтобы лучше понять типы данных и способы их использования, см. [ типы данных для таблиц в хранилище данных SQL](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-data-types).

Таблица преобразования типов данных, см. в разделе неявные преобразования из [CAST и CONVERT (Transact-SQL)](http://msdn.microsoft.com/library/ms187928/).

`datetimeoffset` [ ( *n* ) ]  
 Значение по умолчанию для  *n*  — 7.  
  
 `datetime2` [ ( *n* ) ]  
То же, что `datetime`, за исключением того, что можно указать количество долей секунды. Значение по умолчанию для  *n*  — `7`.  
  
|*n*значение|Точность|Масштаб|  
|--:|--:|-:|  
|`0`|19|0|  
|`1`|21|1|  
|`2`|22|2|  
|`3`|23|3|  
|`4`|24|4|  
|`5`|25|5|  
|`6`|26|6|  
|`7`|27|7|  
  
 `datetime`  
 Сохраняет дату и время дня с 19 по 23 символов в соответствии с григорианского календаря. Дата может содержать год, месяц и день. Время содержит час, минуты и секунды. В качестве альтернативы можно отобразить трех разрядов для долей секунды. Размер при хранении составляет 8 байт.  
  
 `smalldatetime`  
 Сохраняет дату и время. Размер хранения — 4 байта.  
  
 `date`  
 Сохраняет дату, используя не более 10 символов для года, месяца и дня по часам григорианского календаря. Размер хранения составляет 3 байта. Дата хранится в виде целого числа.  
  
 `time` [ ( *n* ) ]  
 Значение по умолчанию для  *n*  — `7`.  
  
 `float` [ ( *n* ) ]  
 Приблизительный числовой тип данных для использования с плавающей запятой числовые. Данные с плавающей запятой является приблизительным, это означает, что не все значения в диапазоне типа данных могут быть отображены точно. *n*Указывает количество битов, используемых для хранения мантиссы `float` в экспоненциальном представлении. Таким образом  *n*  определяет размер, точность и хранилища. Если  *n*  указано, оно должно быть значением между `1` и `53`. Значение по умолчанию  *n*  — `53`.  
  
| *n*значение | Точность | Объем памяти |  
| --------: | --------: | -----------: |  
| 1-24   | 7 знаков  | 4 байта      |  
| 25-53  | 15 знаков | 8 байт      |  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]рассматривает  *n*  как один из двух возможных значений. Если `1` <=   *n*   <=  `24`,  *n*  рассматривается как `24`. Если `25`  <=   *n*   <=  `53`,  *n*  рассматривается как `53`.  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] `float` Тип данных соответствует стандарту ISO для всех значений  *n*  из `1` через `53`. Синоним для двойной точности является `float(53)`.  
  
 `real` [ ( *n* ) ]  
 Определение реального совпадает со значением с плавающей запятой. Синонимом по стандарту ISO для типа `real` является `float(24)`.  
  
 `decimal`[( *точности* [ *, масштаб* ])] | `numeric` [( *точности* [ *, масштаб* ])]  
 Хранит фиксированной точности и масштаба чисел.  
  
 *precision*  
 Максимальное количество десятичных разрядов числа (как слева, так и справа от десятичной запятой). Точность должна принимать значение от `1` через максимальная точность `38`. Точность по умолчанию — `18`.  
  
 *масштаб*  
 Максимальное количество десятичных разрядов числа справа от десятичной запятой. *Масштаб* должен быть числом от `0` через *точности*. Можно указать только *шкалы* Если *точности* указано. Масштаб по умолчанию — `0`, поэтому `0`  <=  *шкалы* <= *точности*. Максимальный размер хранилища зависит от точности.  
  
| Точность | Байты хранилища  |  
| ---------: |-------------: |  
|  1-9       |             5 |  
| 10-19      |             9 |  
| 20-28      |            13 |  
| 29-38      |            17 |  
  
 `money` | `smallmoney`  
 Типы данных, представляющие денежные значения.  
  
| Тип данных | Байты хранилища |  
| --------- | ------------: |  
| `money`|8|  
| `smallmoney` |4|  
  
 `bigint` | `int` | `smallint` | `tinyint`  
 Типы точных числовых данных, использующие целые значения. В следующей таблице показан хранилища.  
  
| Тип данных | Байты хранилища |  
| --------- | ------------: |  
| `bigint`|8|  
| `int` |4|  
| `smallint` |2|  
| `tinyint` |1|  
  
 `bit`  
 Тип данных integer, который может принимать значение `1`, `0`, или "значение NULL. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Оптимизирует хранение столбцов бит. Если в таблице 8 или менее битовые столбцы, столбцы хранятся как 1 байт. Если имеется от 9 – 16 бит столбцы, столбцы хранятся как 2 байта и т.д.  
  
 `nvarchar`[(  *n*   |  `max` )]-- `max` применяется только к [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
 Символьные данные Юникода с переменной длиной. *n*может иметь значение от 1 до 4000. Значение `max` указывает, что максимальный размер при хранении составляет 2^31-1 байт (2 ГБ). Объем памяти в байтах — два раза количество введенных символов + 2 байта. Введенные данные могут иметь длину в 0 символов.  
  
 `nchar` [ ( *n* ) ]  
 Данные символов Юникода фиксированной длины с длиной  *n*  символов. *n*должен быть числом от `1` через `4000`. Размер хранения составляет два раза  *n*  байт.  
  
 `varchar`[(  *n*    |  `max` )]-- `max` применяется только к [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].   
 Переменной длины не в Юникоде символьных данных с длиной  *n*  байт. *n*должен быть числом от `1` для `8000`. `max`Указывает, что максимальный размер хранилища равен 2 ^ 31-1 байт (2 ГБ). Размер хранения — это фактическая длина введенных данных плюс 2 байта.  
  
 `char` [ ( *n* ) ]  
 Данные символов не в Юникоде фиксированной длины, с длиной  *n*  байт. *n*должен быть числом от `1` для `8000`. Размер хранилища  *n*  байт. Значение по умолчанию для  *n*  — `1`.  
  
 `varbinary`[(  *n*    |  `max` )]-- `max` применяется только к [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
 Двоичные данные с переменной длиной. *n*может иметь значение от `1` для `8000`. Значение `max` указывает, что максимальный размер при хранении составляет 2^31-1 байт (2 ГБ). Размер хранения равен фактической длине данных плюс два байта. Значение по умолчанию для  *n*  — 7.  
  
 `binary` [ ( *n* ) ]  
 Двоичные данные фиксированной длины с длиной  *n*  байт. *n*может иметь значение от `1` для `8000`. Размер хранилища  *n*  байт. Значение по умолчанию для  *n*  — `7`.  
  
 `uniqueidentifier`  
 16-байтовый идентификатор GUID.  
   
<a name="Permissions"></a>  
## <a name="permissions"></a>Разрешения  
 Создание таблицы требуется разрешение в `db_ddladmin` предопределенной роли базы данных или:
 - `CREATE TABLE`разрешение в базе данных
 - `ALTER SCHEMA`разрешения на схему, которая будет содержать таблицу. 

Создание секционированной таблицы требуется разрешение в `db_ddladmin` предопределенной роли базы данных или

- `ALTER ANY DATASPACE`разрешение
  
 Получает имя входа, создается локальная временная таблица `CONTROL`, `INSERT`, `SELECT`, и `UPDATE` разрешений на таблицу.  
 
<a name="GeneralRemarks"></a>  
## <a name="general-remarks"></a>Общие замечания  
 
Минимальные и максимальные лимиты разделе [ограничения емкости хранилища данных SQL](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-service-capacity-limits/). 
 
### <a name="determining-the-number-of-table-partitions"></a>Определение числа секций таблицы
Каждой пользовательской таблицы делится на несколько таблиц меньшего размера, которые хранятся в разных местах, вызывается распределения. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]использует 60 распределения. В [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], количество распространением зависит от числа вычислительных узлов.
 
Каждого распределения содержит всех секций таблицы. Например если есть 60 распределения и четыре секции таблицы, будет существовать 320 секций. Если таблица имеет кластеризованный индекс, будет существовать один индекс columnstore на секцию, это означает, что имеется 320 индексы columnstore.

Мы рекомендуем использования меньше секций таблицы, чтобы обеспечить каждого индекса columnstore содержится достаточно строк, чтобы воспользоваться преимуществами индексы columnstore. Инструкции см. в разделе [секционирование таблиц в хранилище данных SQL](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-partition/) и [индексирование таблиц в хранилище данных SQL](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-tables-index/)  

  
 ### <a name="rowstore-table-heap-or-clustered-index"></a>Таблица Rowstore (куча или кластеризованный индекс)  
 Таблица rowstore — это таблица, хранятся в порядке по строкам. Это кучи или кластеризованного индекса. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Создает все таблицы rowstore с включенным сжатием страниц; Это не настраивается пользователем.   
 
 ### <a name="columnstore-table-columnstore-index"></a>Таблица ColumnStore (columnstore index)
Таблица columnstore — это таблица, хранятся в порядке по столбцам. Индекс columnstore — это технология, который управляет данные, хранящиеся в таблице columnstore.  Кластеризованный индекс columnstore не влияет на способ распределения данных; она влияет на способ хранения данных в пределах каждого распределения.

Чтобы изменить таблицу rowstore в таблицу columnstore, удалить все существующие индексы для таблицы и создать кластеризованный индекс. Пример см. в разделе [CREATE COLUMNSTORE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-columnstore-index-transact-sql.md).

Дополнительные сведения см. в следующих статьях:
- [ColumnStore индексы с версиями Сводка признаков](https://msdn.microsoft.com/library/dn934994/)
- [Индексирование таблиц в хранилище данных SQL](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-tables-index/)
- [Руководство по индексам columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md) 
 
<a name="LimitationsRestrictions"></a>  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Невозможно определить ограничение по умолчанию для столбца распределения.  
  
 ### <a name="partitions"></a>Секции
 При использовании секций, столбец секционирования не может иметь параметры сортировки только для Юникода. Например следующая инструкция завершается неудачно.  
  
 `CREATE TABLE t1 ( c1 varchar(20) COLLATE Divehi_90_CI_AS_KS_WS) WITH (PARTITION (c1 RANGE FOR VALUES (N'')))`  
 
 Если *boundary_value* представляет собой литеральное значение, которое должно быть неявно преобразован в тип данных в *partition_column_name*, возникнет несоответствие. Литеральное значение отображается с помощью [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] системных представлений, но преобразованное значение используется для [!INCLUDE[tsql](../../includes/tsql-md.md)] операций. 
 
  
 ### <a name="temporary-tables"></a>Временные таблицы
 Глобальные временные таблицы, которые начинаются с ## не поддерживаются.  
  
 Локальные временные таблицы имеют следующие ограничения:  
  
-   Они видимы только в текущем сеансе. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Удаляет их автоматически в конце сеанса. Чтобы удалить их explicitlt, используйте инструкцию DROP TABLE.   
-   Они не может быть переименован. 
-   Они не могут иметь секций или представления.  
-   Невозможно изменить их разрешения. `GRANT`, `DENY`, и `REVOKE` инструкции не может использоваться с локальных временных таблиц.   
-   Консольные команды базы данных блокируются для временных таблиц.   
-   Если в пакете используется несколько локальная временная таблица, они должны иметь уникальное имя. Если создание одной локальной временной таблицы, выполнении того же пакета несколько сеансов [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] внутренне добавляет числовой суффикс к имени локальной временной таблицы, для поддержания уникальное имя для каждой локальной временной таблицы.  
    
<a name="LockingBehavior"></a>   
## <a name="locking-behavior"></a>Режим блокировки  
 Получает эксклюзивную блокировку на таблицу. Принимает совмещаемую блокировку на объекты базы данных, СХЕМЫ и SCHEMARESOLUTION.  
 

<a name="ExamplesColumn"></a>   
## <a name="examples-for-columns"></a>Примеры для столбцов

### <a name="ColumnCollation"></a> A. Укажите параметры сортировки столбца 
 В следующем примере таблица `MyTable` создается с два набора параметров сортировки другого столбца. По умолчанию в столбце `mycolumn1`, имеет параметры сортировки по умолчанию Latin1_General_100_CI_AS_KS_WS. Столбец, `mycolumn2` с Frisian_100_CS_AS с параметрами сортировки.  
  
```  
CREATE TABLE MyTable   
  (  
    mycolumnnn1 nvarchar,  
    mycolumn2 nvarchar COLLATE Frisian_100_CS_AS )  
WITH ( CLUSTERED COLUMNSTORE INDEX )  
;  
  
```  
  
### <a name="DefaultConstraint"></a> Б. Укажите ограничение по умолчанию для столбца  
 В примере показан синтаксис для указания значения по умолчанию для столбца. Столбец colA имеет ограничение по умолчанию с именем constraint_colA и значение по умолчанию 0.  
  
```  
  
CREATE TABLE MyTable   
  (  
    colA int CONSTRAINT constraint_colA DEFAULT 0,  
    colB nvarchar COLLATE Frisian_100_CS_AS   
  )  
WITH ( CLUSTERED COLUMNSTORE INDEX )  
;  
```  

<a name="ExamplesTemporaryTables"></a> 
## <a name="examples-for-temporary-tables"></a>Примеры для временных таблиц

### <a name="TemporaryTable"></a> В. Создание локальной временной таблицы  
 В следующем коде создается локальная временная таблица с именем #myTable. Таблицы задано имя часть 3. Имя временной таблицы начинается со знака #.   
  
```  
CREATE TABLE AdventureWorks.dbo.#myTable   
  (  
   id int NOT NULL,  
   lastName varchar(20),  
   zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = HASH (id),  
    CLUSTERED COLUMNSTORE INDEX   
  )  
;  
```

<a name="ExTableStructure"></a>  
## <a name="examples-for-table-structure"></a>Примеры для структуры таблицы

### <a name="ClusteredColumnstoreIndex"></a> Г. Создайте таблицу с кластеризованным индексом columnstore  
 В следующем примере создается таблица распространения с кластеризованным индексом columnstore. Каждого распределения будут храниться в виде кластеризованного индекса columnstore.  
  
 Кластеризованный индекс columnstore не влияет на способ распределения данных; данные всегда распределены по строкам. Кластеризованный индекс влияет на способ хранения данных в пределах каждого распределения.  
  
```  
  
CREATE TABLE MyTable   
  (  
    colA int CONSTRAINT constraint_colA DEFAULT 0,  
    colB nvarchar COLLATE Frisian_100_CS_AS   
  )  
WITH   
  (   
    DISTRIBUTION = HASH ( colB ),  
    CLUSTERED COLUMNSTORE INDEX   
  )  
;  
```  
 
<a name="ExTableDistribution"></a> 
## <a name="examples-for-table-distribution"></a>Примеры для распределения таблиц

### <a name="RoundRobin"></a> Д. Создать таблицу ROUND_ROBIN  
 В следующем примере создается таблица ROUND_ROBIN с тремя столбцами и без секций. Данные распределены между все распределения. Создается таблица с КЛАСТЕРИЗОВАННЫМ ИНДЕКСОМ COLUMNSTORE, которая предоставляет данные по производительности и более высокую степень сжатия кучи или rowstore кластеризованного индекса.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH ( CLUSTERED COLUMNSTORE INDEX );  
```  
  
### <a name="HashDistributed"></a> Е. Создать таблицу хэша распределенных  
 В следующем примере создается в той же таблице, как в предыдущем примере. Тем не менее, для этой таблицы строки распределены (на `id` столбца) вместо случайным образом распределены как таблица ROUND_ROBIN. Создается таблица с КЛАСТЕРИЗОВАННЫМ ИНДЕКСОМ COLUMNSTORE, которая предоставляет данные по производительности и более высокую степень сжатия кучи или rowstore кластеризованного индекса.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = HASH (id),   
    CLUSTERED COLUMNSTORE INDEX  
  );  
```  
  
### <a name="Replicated"></a> G. Создание реплицированной таблицы  
 В следующем примере создается реплицированной таблицы, как в предыдущих примерах. Реплицированные таблицы копируются в полном объеме на каждом вычислительном узле. С этой копии на каждом вычислительном узле перемещения данных уменьшается для запросов. В этом примере создается с КЛАСТЕРИЗОВАННЫМ ИНДЕКСОМ, который обеспечивает более высокую степень сжатия данных, чем кучи и не может содержать достаточно строк, чтобы получить хорошее сжатие КЛАСТЕРИЗОВАННЫЙ индекс COLUMNSTORE.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = REPLICATE,   
    CLUSTERED INDEX (lastName)  
  );  
```  

<a name="ExTablePartitions"></a> 
## <a name="examples-for-table-partitions"></a>Примеры для секционированных таблиц

###  <a name="PartitionedTable"></a> H. Создание секционированной таблицы  
 В следующем примере создается той же таблицы, как показано в примере А, с добавлением секционирования RANGE LEFT для `id` столбца. Он указывает четыре граничные значения секционирования, что приводит к пять секций.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode int)  
WITH   
  (   
  
    PARTITION ( id RANGE LEFT FOR VALUES (10, 20, 30, 40 )),  
    CLUSTERED COLUMNSTORE INDEX      
  )  
;  
```  
  
 В этом примере данные будут отсортированы в следующих разделах:  
  
-   Секции 1: столбец < = 10   
-   Секции 2:10 < col < = 20   
-   Секции 3:20 < col < = 30   
-   Секции 4:30 < col < = 40   
-   5:40 секции < col  
  
 Если эта же таблица была секционирована RANGE RIGHT вместо RANGE LEFT (по умолчанию), данные будут отсортированы в следующих разделах:  
  
-   Раздел 1: col < 10  
-   Секции 2:10 < = col < 20   
-   Секции 3:20 < = col < 30    
-   Секции 4:30 < = col < 40   
-   Секции 5:40 < = col  
  
### <a name="OnePartition"></a> I. Создайте секционированную таблицу с одной секцией  
 В следующем примере создается секционированную таблицу с одной секцией. Оно не указывает все значения границ, что приводит к одной секции.  
  
```  
CREATE TABLE myTable (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode int)  
WITH   
    (   
      PARTITION ( id RANGE LEFT FOR VALUES ( )),  
      CLUSTERED COLUMNSTORE INDEX  
    )  
;  
```  
  
### <a name="DatePartition"></a> J. Создайте таблицу с секционированием даты  
 Следующий пример создает новую таблицу с именем `myTable`, с секционированием по `date` столбца. С помощью RANGE RIGHT и дат в качестве граничных значений, он помещает месяц данных в каждой секции.  
  
```  
CREATE TABLE myTable (  
    l_orderkey      bigint,       
    l_partkey       bigint,                                             
    l_suppkey       bigint,                                           
    l_linenumber    bigint,        
    l_quantity      decimal(15,2),  
    l_extendedprice decimal(15,2),  
    l_discount      decimal(15,2),  
    l_tax           decimal(15,2),  
    l_returnflag    char(1),  
    l_linestatus    char(1),  
    l_shipdate      date,  
    l_commitdate    date,  
    l_receiptdate   date,  
    l_shipinstruct  char(25),  
    l_shipmode      char(10),  
    l_comment       varchar(44))  
WITH   
  (   
    DISTRIBUTION = HASH (l_orderkey),  
    CLUSTERED COLUMNSTORE INDEX,  
    PARTITION ( l_shipdate  RANGE RIGHT FOR VALUES   
      (  
        '1992-01-01','1992-02-01','1992-03-01','1992-04-01','1992-05-01',
        '1992-06-01','1992-07-01','1992-08-01','1992-09-01','1992-10-01',
        '1992-11-01','1992-12-01','1993-01-01','1993-02-01','1993-03-01',
        '1993-04-01','1993-05-01','1993-06-01','1993-07-01','1993-08-01',
        '1993-09-01','1993-10-01','1993-11-01','1993-12-01','1994-01-01',
        '1994-02-01','1994-03-01','1994-04-01','1994-05-01','1994-06-01',
        '1994-07-01','1994-08-01','1994-09-01','1994-10-01','1994-11-01',
        '1994-12-01'  
      ))
  );  
```  
  
<a name="SeeAlso"></a>    
## <a name="see-also"></a>См. также: 
 
 [CREATE TABLE AS SELECT #40; Хранилище данных Azure SQL &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
