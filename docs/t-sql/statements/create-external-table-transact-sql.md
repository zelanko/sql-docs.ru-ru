---
title: "СОЗДАЙТЕ ВНЕШНЮЮ ТАБЛИЦУ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_EXTERNAL_TABLE
- CREATE EXTERNAL TABLE
- PolyBase, T-SQL
dev_langs: TSQL
helpviewer_keywords:
- External
- External, table create
- PolyBase, external table
ms.assetid: 6a6fd8fe-73f5-4639-9908-2279031abdec
caps.latest.revision: "30"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 802122cb7c0902c731b0fcc7d8522901ad7ea044
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="create-external-table-transact-sql"></a>СОЗДАЙТЕ ВНЕШНЮЮ ТАБЛИЦУ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Создает внешнюю таблицу PolyBase, которая ссылается на данные, хранящиеся в кластер Hadoop или хранилище больших двоичных объектов. Также можно использовать для создания внешней таблицы для [запроса эластичной базы данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  
  
 Используйте внешнюю таблицу для:  
  
-   Запрос Hadoop или Azure BLOB-объектов хранилища данных с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.  
  
-   Импортировать и хранить данные из Hadoop или BLOB-объекта хранилища Azure в вашей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.  
  
-   Создайте внешнюю таблицу для использования с эластичной базы данных  
     запрос.  
     
- Импортировать и сохранять данные из хранилища Озера данных Azure в хранилище данных SQL Azure
  
 См. также [СОЗДАНИЯ ВНЕШНЕГО источника данных &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) и [DROP EXTERNAL TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-external-table-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  

```  
-- Syntax for SQL Server 
  
-- Create a new external table  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH (   
        LOCATION = 'folder_or_filepath',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
  
}  
  
-- Create a table for use with Elastic Database query  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH ( <sharded_external_table_options> )  
[;]  
  
<sharded_external_table_options> ::=  
        DATA_SOURCE = external_data_source_name,   
        SCHEMA_NAME = N'nonescaped_schema_name',  
        OBJECT_NAME = N'nonescaped_object_name',  
        [DISTRIBUTION  = SHARDED(sharding_column_name) | REPLICATED | ROUND_ROBIN]]  
    )  
[;]  
```  

```  
-- Syntax for Azure SQL Database
  
-- Create a table for use with Elastic Database query  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH ( <sharded_external_table_options> )  
[;]  
  
<sharded_external_table_options> ::=  
        DATA_SOURCE = external_data_source_name,   
        SCHEMA_NAME = N'nonescaped_schema_name',  
        OBJECT_NAME = N'nonescaped_object_name',  
        [DISTRIBUTION  = SHARDED(sharding_column_name) | REPLICATED | ROUND_ROBIN]]  
    )  
[;]  
```  


```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
-- Create a new external table in SQL Server PDW  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH (   
        LOCATION = 'hdfs_folder_or_filepath',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name* . [schema_name]. | schema_name. ] *имя_таблицы*  
 Одно для трех - часть имя создаваемой таблицы. Для внешней таблицы только метаданные таблицы хранятся в SQL вместе с базовую статистику о файл или папку, указанную в хранилище больших двоичных объектов Azure или Hadoop. Никакие данные перемещается или хранящихся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 \<column_definition > [,... *n*  ] Одно или несколько определений столбца позволяет создать ВНЕШНЮЮ ТАБЛИЦУ. CREATE EXTERNAL TABLE и CREATE TABLE используется тот же синтаксис для определения столбца. Исключение, нельзя использовать ограничение по умолчанию во внешних таблицах. Подробная информация о определения столбцов и их типы данных, в разделе [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md) и [создание таблицы в базе данных Azure SQL](http://msdn.microsoft.com/library/d53c529a-1d5f-417f-9a77-64ccc6eddca1).  
  
 Определения столбцов, включая типы данных и количество столбцов должны соответствовать данным во внешних файлах. В случае несоответствия при запросе фактические данные будут отклонены строки файла.  
  
 Определения столбцов и тип для внешних таблиц, на которые ссылаются файлы во внешних источниках данных, необходимо сопоставить точное схемы внешнего файла. При определении типов данных, которые ссылаются на данные, хранящиеся в Hadoop или Hive, используйте следующие сопоставления типов данных SQL и Hive и приведение типа в тип данных SQL, при выборе из него. Типы включают все версии Hive, если не указано иное.  
  
|Тип данных SQL|Тип данных .NET|Тип данных Hive|Hadoop типа данных|Комментарии|  
|-------------------|--------------------|--------------------|----------------------------|--------------|  
|tinyint|Byte|tinyint|ByteWritable|Для чисел без знака только.|  
|smallint|Int16|smallint|ShortWritable||  
|int|Int32|int|IntWritable||  
|bigint|Int64|bigint|LongWritable||  
|bit|Логическое значение|boolean|BooleanWritable||  
|float|Double|double|DoubleWritable||  
|real|Один|float|FloatWritable||  
|money|Decimal|double|DoubleWritable||  
|smallmoney|Decimal|double|DoubleWritable||  
|nchar|Строковые значения<br /><br /> Char]|строка|text||  
|nvarchar|Строковые значения<br /><br /> Char]|строка|Текст||  
|char|Строковые значения<br /><br /> Char]|строка|Текст||  
|varchar|Строковые значения<br /><br /> Char]|строка|Текст||  
|binary|Byte[]|binary|BytesWritable|Применяется к Hive 0,8 и более поздней версии.|  
|varbinary|Byte[]|binary|BytesWritable|Применяется к Hive 0,8 и более поздней версии.|  
|date|DateTime|timestamp|TimestampWritable||  
|smalldatetime|DateTime|timestamp|TimestampWritable||  
|datetime2|DateTime|timestamp|TimestampWritable||  
|datetime|DateTime|timestamp|TimestampWritable||  
|time|TimeSpan|timestamp|TimestampWritable||  
|decimal|Decimal|decimal|BigDecimalWritable|Применяется к Hive0.11 и более поздней версии.|  
  
 РАСПОЛОЖЕНИЕ = "*folder_or_filepath*"  
 Указывает папки или путь к файлу и имя файла для фактических данных в хранилище больших двоичных объектов Azure или Hadoop. Расположение начинается с корневой папки; Корневая папка — расположение данных, указанные в источнике внешних данных.  
  
 При указании РАСПОЛОЖЕНИЯ должна быть папкой PolyBase запроса, выбирающего данные из внешней таблицы будут получать файлы из папки и всех ее вложенных папках. Так же, как Hadoop PolyBase не возвращает скрытые папки. Он также не возвращать файлы, для которых имя файла начинается с подчеркиванием (_) или точку (.).  
  
 В этом примере если РАСПОЛОЖЕНИЕ = «/ webdata /» PolyBase запрос возвращает строки из mydata.txt и mydata2.txt.  Он не вернет mydata3.txt так как он является вложенной в скрытую папку. Он не вернет _hidden.txt, так как он является скрытым.  
  
 ![Рекурсивные данные для внешних таблиц](../../t-sql/statements/media/aps-polybase-folder-traversal.png "рекурсивные данные для внешних таблиц")  
  
 Чтобы изменить только на чтение и по умолчанию в корневой папке, задайте для атрибута \<polybase.recursive.traversal > значение «false» в файле core-site.xml конфигурации. Этот файл находится в папке `<SqlBinRoot>\Polybase\Hadoop\Conf with SqlBinRoot the bin root of SQl Server`. Например, `C:\\Program Files\\Microsoft SQL Server\\MSSQL13.XD14\\MSSQL\\Binn`.  
  
 Источник_данных = *external_data_source_name*  
 Задает имя внешнего источника данных, содержащий расположение внешних данных. Это расположение, хранилище больших двоичных объектов Azure или Hadoop. Для создания внешнего источника данных, используйте [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 FILE_FORMAT = *external_file_format_name*  
 Задает имя объекта формата внешнего файла, который хранит метод тип и сжатие файла внешних данных. Чтобы создать формата внешних файлов, используйте [CREATE EXTERNAL FILE FORMAT &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
 Отклонить параметры  
 Можно указать отклонить параметры, определяющие способ обработки PolyBase *"грязных"* записывает он получает из внешнего источника данных. Запись данных считается измененные при его фактических типов данных или число столбцов не соответствуют определения столбцов из внешней таблицы.  
  
 Если не указать или изменить значения отклонения, PolyBase использует значения по умолчанию. Эти сведения о параметрах отклонить хранится как дополнительные метаданные, при создании внешней таблицы с помощью инструкции CREATE EXTERNAL TABLE.   При следующей инструкцией SELECT или ВЫБЕРИТЕ INTO SELECT выбирает данные из внешней таблицы, PolyBase будет использовать параметры отклонения для определения, число или процент строк, может быть отклонено прежде, чем фактический запрос завершится с ошибкой. . Запрос будет возвращать результаты (разделяемый), пока не будет превышено пороговое значение отклонения; Затем он завершается с соответствующим сообщением об ошибке.  
  
 REJECT_TYPE = **значение** | процент  
 Уточняет, является ли параметр REJECT_VALUE указан как литеральное значение или процент.  
  
 value  
 REJECT_VALUE является буквенные значения, а не в процентах. PolyBase запрос завершится ошибкой, если число отклоненных строк превышает *reject_value*.  
  
 Например если REJECT_VALUE = 5 и REJECT_TYPE = значение PolyBase, ВЫБЕРИТЕ запрос завершится ошибкой после отклонения 5 строк.  
  
 Процент  
 REJECT_VALUE представлены в процентах, а не литеральное значение. PolyBase запрос завершится ошибкой, если *процент* строки с ошибками превышает *reject_value*. Процент сбойных строк вычисляется с интервалами.  
  
 REJECT_VALUE = *reject_value*  
 Указывает значение или процент строк, которые может быть отклонено, прежде чем запрос завершится с ошибкой.  
  
 Для REJECT_TYPE = value, *reject_value* должно быть в диапазоне от 0 до 2 147 483 647.  
  
 REJECT_TYPE = процент, *reject_value* должно быть значение с плавающей запятой в диапазоне от 0 до 100.  
  
 REJECT_SAMPLE_VALUE = *reject_sample_value*  
 Этот атрибут является обязательным при указании REJECT_TYPE = процент. Он определяет количество строк, чтобы попытаться получить перед PolyBase повторно вычисляет процент отклоненных строк.  
  
 *Reject_sample_value* параметр должен быть целым числом от 0 до 2 147 483 647.  
  
 Например если REJECT_SAMPLE_VALUE = 1000, PolyBase будет вычислять процент сбойных строк после попытки импорта 1000 строк из файла внешних данных. Если процент сбойных строк меньше, чем *reject_value*, PolyBase попытается получить другой 1000 строк. Он продолжает повторно вычислить процент сбойных строк после предпринимается попытка импорта каждого дополнительных 1000 строк.  
  
> [!NOTE]  
>  Поскольку PolyBase вычисляет процент сбойных строк с интервалами, может превышать фактический процент сбойных строк *reject_value*.  
  
 Пример  
  
 В этом примере показано, как три варианта ОТКЛОНИТЬ взаимодействуют друг с другом. Например если REJECT_TYPE = процент REJECT_VALUE = 30 лет, а значение REJECT_SAMPLE_VALUE = 100, возможна следующая ситуация:  
  
-   PolyBase при попытке получить первые 100 строк; 25 успешно завершится неудачей и 75.  
  
-   Процент сбойных строк вычисляется как 25%, это меньше отклоняемое значение 30%. Таким образом PolyBase по-прежнему извлечения данных из внешнего источника данных.  
  
-   PolyBase пытается загрузить следующие 100 строк; Это время 25 успешно и 75 ошибкой.  
  
-   Процент сбойных строк повторно по мере 50%. Процент сбойных строк превысил значение 30% отклонения.  
  
-   Возникает ошибка запросов PolyBase с 50% Отклонено строк после попытки возвращения первые 200 строк. Обратите внимание, что совпадающие строки были возвращены до запроса PolyBase обнаруживает, что было превышено пороговое значение отклонения.  
  
 Параметры сегментированных внешней таблицы  
 Указывает внешний источник данных (источник данных SQL Server) и способ распространения [запроса эластичной базы данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  
  
 ИСТОЧНИК_ДАННЫХ  
 Источника внешних данных, таких как данные, хранящиеся в файловой системе Hadoop хранилище больших двоичных объектов или [диспетчера карты сегментов](https://azure.microsoft.com/documentation/articles/sql-database-elastic-scale-shard-map-management/).  
  
 SCHEMA_NAME  
 Предложение SCHEMA_NAME предоставляет возможность сопоставления определении внешней таблицы в таблицу в другую схему в удаленную базу данных. Используется для устранения неоднозначности между схемами, которые существуют на локальных и удаленных баз данных.  
  
 OBJECT_NAME  
 Предложение OBJECT_NAME позволяет выполнять сопоставление определении внешней таблицы с таблицей с другим именем в удаленную базу данных. Используется для устранения неоднозначности между имена объектов, которые существуют на локальных и удаленных баз данных.  
  
 РАСПРОСТРАНЕНИЯ  
 Необязательно. Это только является обязательным только для баз данных SHARD_MAP_MANAGER типа. Это свойство задает обработку таблицы как сегментированной таблице или реплицируемой таблицы. С **SHARDED** (*имя столбца*) таблицы, данные из различных таблиц не перекрываются. **РЕПЛИКАЦИЯ** указывает, что таблицы имеют те же данные на каждый сегмент. **ROUND_ROBIN** указывает, что метод конкретного приложения используется для распределения данных.  
  
## <a name="permissions"></a>Permissions  
 Требуются следующие разрешения пользователя.  
  
-   **CREATE TABLE**  
  
-   **ИЗМЕНЕНИЕ ЛЮБОЙ СХЕМЫ**  
  
-   **ИЗМЕНЯТЬ ЛЮБОЙ ВНЕШНИЙ ИСТОЧНИК ДАННЫХ**  
  
-   **ALTER ЛЮБОЙ ФОРМАТ ВНЕШНЕГО ФАЙЛА**  

-   **БАЗА ДАННЫХ УПРАВЛЕНИЯ**
  
 Следует отметить, что имя входа, создает внешний источник данных должен иметь разрешение на чтение и запись в источнике внешних данных, находящимся в хранилище больших двоичных объектов Azure или Hadoop.  


 > [!IMPORTANT]  

>  Разрешение ALTER ANY EXTERNAL DATA SOURCE предоставляет любому участнику возможность создания и изменения любого объекта источника внешних данных, и таким образом, он также предоставляет возможность доступа к все учетные данные уровня базы данных в базе данных. Это разрешение следует рассматривать как широкими правами и поэтому должен предоставлять только доверенным участникам в системе.

## <a name="error-handling"></a>Обработка ошибок  
 При выполнении инструкции CREATE EXTERNAL TABLE, PolyBase пытается подключиться к внешнему источнику данных. Если попытка соединения завершается ошибкой, инструкция завершится ошибкой и внешней таблицы не создаются. Он может занять около минуты больше окончиться неудачей, поскольку PolyBase повторяет попытки соединения перед неудачным запроса со временем выполнения команды.  
  
## <a name="general-remarks"></a>Общие замечания  
 В сценарии нерегламентированных запросов, т. е. ВЫБЕРИТЕ из ВНЕШНЕЙ таблицы, PolyBase сохраняет строки, полученные из внешнего источника данных во временной таблице. После завершения выполнения запроса PolyBase удаляет и временную таблицу. Постоянные данные не хранятся в таблицах SQL.  
  
 В отличие от этого в случае импорта, т. е. ВЫБЕРИТЕ в из ВНЕШНЕЙ таблицы, PolyBase сохраняет строки, полученные из внешнего источника данных как постоянные данные в таблицы SQL. Новая таблица создается во время выполнения запроса при Polybase получать внешние данные.  
  
 PolyBase можно передать некоторые вычисления запросов в Hadoop для повышения производительности запросов. Это называется Включение предиката. Для этого задайте параметр расположение диспетчера ресурсов Hadoop в [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 Можно создать несколько внешних таблиц, которые ссылаются на одном или разных внешних источников данных.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 В выпуске CTP2 функция экспорта не поддерживается, т. е. без возможности восстановления при сохранении данных SQL в к внешнему источнику данных. Эта функциональность будут доступны в CTP3-версии.  
  
 Поскольку выключение устройства хранятся данные для внешней таблицы, он не находится под контролем PolyBase и можно изменить или удалить в любое время внешним процессом. По этой причине запрос результаты с внешней таблицы не обязательно быть детерминированным. Тот же запрос может возвращать различные результаты при каждом запуске от внешней таблицы. Аналогичным образом запрос может завершиться ошибкой, если внешние данные удалены или перемещены.  
  
 Можно создать несколько внешних таблиц, что каждый ссылаться на различных внешних источников данных. Тем не менее если одновременно выполнять запросы к различные источники данных Hadoop, каждый источник Hadoop необходимо использовать параметр конфигурации сервера же 'hadoop connectivity'. Например вы невозможно запустить одновременно запроса для кластера Cloudera Hadoop и кластер Hortonworks Hadoop с момента эти использовать разные параметры конфигурации. Параметры конфигурации и поддерживаемые сочетания см. в разделе [конфигурация PolyBase &#40; Transact-SQL &#41; ](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  
  
 Только эти инструкции языка определения данных (DDL) являются допустимыми во внешних таблицах.  
  
-   CREATE TABLE и DROP TABLE  
  
-   CREATE STATISTICS и DROP STATISTICS  
  
-   Создание ПРЕДСТАВЛЕНИЯ и DROP VIEW  
  
 Конструкции и операции, которые не поддерживаются:  
  
-   Ограничение по умолчанию на столбцы внешней таблицы  
  
-   Операции языка Обработки данных delete, insert и update  
  
 Ограничения запроса.  
  
 PolyBase может использовать более 33 k-файлов в папке, при выполнении 32 параллельных запросов PolyBase. Это максимальное число включает файлы и вложенные папки в каждой папке HDFS. Если степень параллелизма меньше 32, пользователь может использовать запросы PolyBase папки, в которой содержат более 33 k файлы HDFS. Рекомендуется сохранять короткие пути к файлам внешних и использовать не более 30 k-файлы в папке HDFS. При обращении к слишком много файлов, может возникнуть исключение нехватки памяти в виртуальной машине Java (JVM).  

Таблица ограничений по ширине: PolyBase в SQL Server 2016 имеет ограничение ширины строки 32 КБ на основании максимальный размер одной строки, допустимые по определению таблицы. Если сумма столбца схемы превышает 32 КБ, PolyBase не будет запрашивать данные. 

В хранилище данных SQL это ограничение увеличен до 1 МБ.


## <a name="locking"></a>Блокировка  
 Общие блокировки на объект SCHEMARESOLUTION.  
  
## <a name="security"></a>безопасность  
 Файлы данных для внешней таблицы хранятся в хранилище больших двоичных объектов Azure или Hadoop. Эти файлы данных создаются и управляются собственного процесса. Это вы несете ответственность за управление безопасностью внешних данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-create-an-external-table-with-data-in-text-delimited-format"></a>A. Создайте внешнюю таблицу с данными в формате, разделенных текстом.  
 В этом примере показаны все действия, необходимые для создания внешнюю таблицу, которая содержит данные, форматированные в файлы с разбивкой текста. Он определяет внешнего источника данных *mydatasource* и формат внешнего файла *myfileformat*. Затем эти объекты уровня базы данных указываются в инструкции CREATE EXTERNAL TABLE. Дополнительные сведения см. в разделе [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) и [ФОРМАТА ВНЕШНЕГО файла CREATE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT,   
    FORMAT_OPTIONS (FIELD_TERMINATOR ='|')  
);  
  
CREATE EXTERNAL TABLE ClickStream (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
        LOCATION='/webdata/employee.tbl',  
        DATA_SOURCE = mydatasource,  
        FILE_FORMAT = myfileformat  
    )  
;  
  
```  
  
### <a name="b-create-an-external-table-with-data-in-rcfile-format"></a>Б. Создайте внешнюю таблицу с данными в формате RCFile.  
 В этом примере показаны все действия, необходимые для создания внешнюю таблицу, которая содержит данные в формате RCFiles. Он определяет внешнего источника данных *mydatasource_rc* и формат внешнего файла *myfileformat_rc*. Затем эти объекты уровня базы данных указываются в инструкции CREATE EXTERNAL TABLE. Дополнительные сведения см. в разделе [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) и [ФОРМАТА ВНЕШНЕГО файла CREATE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource_rc  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat_rc  
WITH (  
    FORMAT = RCFILE,  
    SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'  
)  
;  
  
CREATE EXTERNAL TABLE ClickStream_rc (   
    url varchar(50),  
    event_date date,  
    user_ip varchar(50)  
)  
WITH (  
        LOCATION='/webdata/employee_rc.tbl',  
        DATA_SOURCE = mydatasource_rc,  
        FILE_FORMAT = myfileformat_rc  
    )  
;  
  
```  
  
### <a name="c-create-an-external-table-with-data-in-orc-format"></a>В. Создайте внешнюю таблицу с данными в формате ORC.  
 В этом примере показаны все действия, необходимые для создания внешнюю таблицу, которая имеет данных, отформатированных в виде файлов ORC. Он определяет mydatasource_orc источника внешних данных и myfileformat_orc формата внешнего файла. Затем эти объекты уровня базы данных указываются в инструкции CREATE EXTERNAL TABLE. Дополнительные сведения см. в разделе [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) и [ФОРМАТА ВНЕШНЕГО файла CREATE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource_orc  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat_orc  
WITH (  
    FORMAT = ORC,  
    COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
)  
;  
  
CREATE EXTERNAL TABLE ClickStream_orc (   
    url varchar(50),  
    event_date date,  
    user_ip varchar(50)  
)  
WITH (  
        LOCATION='/webdata/',  
        DATA_SOURCE = mydatasource_orc,  
        FILE_FORMAT = myfileformat_orc  
    )  
;  
  
```  
  
### <a name="d-querying-hadoop-data"></a>Г. Запрос данных Hadoop  
 Навигации имеет внешнюю таблицу, которая подключается к файлу employee.tbl текста с разделителями в кластере Hadoop. Следующий запрос выглядит так же, как запрос к стандартной таблицы. Однако этот запрос извлекает данные из Hadoop, а затем вычисляет restuls.  
  
```  
SELECT TOP 10 (url) FROM ClickStream WHERE user_ip = 'xxx.xxx.xxx.xxx'  
;  
```  
  
### <a name="e-join-hadoop-data-with-sql-data"></a>Д. Объединение данных Hadoop с данными SQL  
 Этот запрос выглядит так же, как стандартные СОЕДИНЕНИЯ двух таблиц SQL. Разница — что PolyBase получает данные маршрута перемещения из Hadoop и включает его в таблице UrlDescription. Одна таблица — внешней таблицы, а другой — Стандартная таблица SQL.  
  
```  
SELECT url.description  
FROM ClickStream cs  
JOIN UrlDescription url ON cs.url = url.name  
WHERE cs.url = 'msdn.microsoft.com'  
;  
```  
  
### <a name="f-import-data-from-hadoop-into-a-sql-table"></a>Е. Импорт данных из Hadoop в таблицу SQL  
 В этом примере создается новый ms_user таблицы SQL, которое окончательно хранит результат соединения между таблицей SQL standard *пользователя* и внешней таблицы *навигации*.  
  
```  
SELECT DISTINCT user.FirstName, user.LastName  
INTO ms_user  
FROM user INNER JOIN (  
    SELECT * FROM ClickStream WHERE cs.url = 'www.microsoft.com'  
    ) AS ms_user  
ON user.user_ip = ms.user_ip  
;  
  
```  
  
### <a name="g-create-an-external-table-for-a-sharded-data-source"></a>Ж. Создание внешней таблицы для сегментированных данных источника  
 В этом примере сопоставляет удаленного DMV для внешней таблицы с помощью предложений SCHEMA_NAME и OBJECT_NAME.  
  
```  
CREATE EXTERNAL TABLE [dbo].[all_dm_exec_requests]([session_id] smallint NOT NULL,  
  [request_id] int NOT NULL,  
  [start_time] datetime NOT NULL,   
  [status] nvarchar(30) NOT NULL,  
  [command] nvarchar(32) NOT NULL,  
  [sql_handle] varbinary(64),  
  [statement_start_offset] int,  
  [statement_end_offset] int,  
  [cpu_time] int NOT NULL)  
WITH  
(  
  DATA_SOURCE = MyExtSrc,  
  SCHEMA_NAME = 'sys',  
  OBJECT_NAME = 'dm_exec_requests',  
  DISTRIBUTION=ROUND_ROBIN  
);   
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="h-importing-data-from-adls-into-azure-includessdwincludesssdw-mdmd"></a>З. Импорт данных из ADLS в Azure[!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
 
  
```  

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLUser 
WITH IDENTITY = '<clientID>@\<OAuth2.0TokenEndPoint>',
SECRET = '<KEY>' ;


CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (TYPE = HADOOP,
      LOCATION = 'adl://pbasetr.azuredatalakestore.net'
)



CREATE EXTERNAL FILE FORMAT TextFileFormat 
WITH ( FORMATTYPE = DELIMITEDTEXT 
     , FORMATOPTIONS ( FIELDTERMINATOR = '|' 
                     , STRINGDELIMITER = '' 
                     , DATEFORMAT = 'yyyy-MM-dd HH:mm:ss.fff' 
                     , USETYPE_DEFAULT = FALSE 
                     ) 
    )


CREATE EXTERNAL TABLE [dbo].[DimProductexternal] 
( [ProductKey] [int] NOT NULL, 
  [ProductLabel] nvarchar NULL, 
  [ProductName] nvarchar NULL ) 
WITH ( LOCATION='/DimProduct/' , 
       DATA_SOURCE = AzureDataLakeStore , 
       FILE_FORMAT = TextFileFormat , 
       REJECT_TYPE = VALUE ,
       REJECT_VALUE = 0 ) ;


CREATE TABLE [dbo].[DimProduct] 
WITH (DISTRIBUTION = HASH([ProductKey] ) ) 
AS SELECT * FROM 
[dbo].[DimProduct_external] ; 
     
```  
  
### <a name="i-join-external-tables"></a>И. Соединение внешних таблиц  
  
```  
SELECT url.description  
FROM ClickStream cs  
JOIN UrlDescription url ON cs.url = url.name  
WHERE cs.url = 'msdn.microsoft.com'  
;  
```  
  
### <a name="j-join-hdfs-data-with-pdw-data"></a>К. Объединение данных HDFS с данными PDW  
  
```  
SELECT cs.user_ip FROM ClickStream cs  
JOIN User u ON cs.user_ip = u.user_ip  
WHERE cs.url = 'www.microsoft.com'  
;  
  
```  
  
### <a name="k-import-row-data-from-hdfs-into-a-distributed-pdw-table"></a>Л. Импорт строк данных из HDFS в таблицу распределенных PDW  
  
```  
CREATE TABLE ClickStream_PDW  
WITH ( DISTRIBUTION = HASH (url) )  
AS SELECT url, event_date, user_ip FROM ClickStream  
;  
```  
  
### <a name="l-import-row-data-from-hdfs-into-a-replicated-pdw-table"></a>М. Импорт строк данных из HDFS в реплицируемой таблицы PDW  
  
```  
CREATE TABLE ClickStream_PDW  
WITH ( DISTRIBUTION = REPLICATE )  
AS SELECT url, event_date, user_ip   
FROM ClickStream  
;  
```  
  
## <a name="see-also"></a>См. также:  
 [Общие примеры запросов метаданных (SQL Server PDW)](http://msdn.microsoft.com/en-us/733fc99b-b9f6-4a29-b085-a1bd4f09f2ed)   
 [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [СОЗДАТЬ внешний TABLE AS SELECT &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [CREATE TABLE AS SELECT #40; Хранилище данных Azure SQL &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
  
  



