---
title: CREATE EXTERNAL TABLE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 6/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE_EXTERNAL_TABLE
- CREATE EXTERNAL TABLE
- PolyBase, T-SQL
dev_langs:
- TSQL
helpviewer_keywords:
- External
- External, table create
- PolyBase, external table
ms.assetid: 6a6fd8fe-73f5-4639-9908-2279031abdec
caps.latest.revision: 30
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 57c8288f9a19599f3047fddb030f05a1edfbb300
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39454548"
---
# <a name="create-external-table-transact-sql"></a>CREATE EXTERNAL TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Создает внешнюю таблицу для PolyBase или запросов эластичной базы данных. В зависимости от сценария синтаксис существенно отличается. Внешняя таблица, созданная для PolyBase, не может использоваться для запросов эластичной базы данных.  Аналогичным образом внешняя таблица, созданная для запросов эластичной базы данных, не может использоваться для PolyBase и т. д. 
  
> [!NOTE]  
>  PolyBase поддерживается только в SQL Server 2016 (или более поздней версии), хранилище данных SQL Azure и Parallel Data Warehouse. Запросы эластичной базы данных поддерживаются только в базе данных SQL Azure v12 или более поздней версии.  


- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует внешние таблицы для доступа к данным, хранящимся в кластере Hadoop или хранилище BLOB-объектов Azure. Внешняя таблица PolyBase ссылается на данные, хранящиеся в кластере Hadoop или хранилище BLOB-объектов Azure. Также может использоваться для создания внешней таблицы для [запроса эластичной базы данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  
  
 Внешняя таблица используется в следующих целях:  
  
-   Запрос к Hadoop или хранилищу больших двоичных объектов Azure с помощью инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Импорт и хранение данных из Hadoop или хранилища больших двоичных объектов Azure в вашей базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Создание внешней таблицы для использования с запросом эластичной  
     базы данных.  
     
- Импорт и сохранение данных из хранилища Azure Data Lake Store в хранилище данных SQL Azure
  
 См. также [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) и [DROP EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/drop-external-table-transact-sql.md).  
  
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
    | REJECT_TYPE = value | percentage,  
    | REJECT_VALUE = reject_value,  
    | REJECT_SAMPLE_VALUE = reject_sample_value,
    | REJECTED_ROW_LOCATION = '\REJECT_Directory'
  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name* . [ schema_name ] . | schema_name. ] *table_name*  
 Имя создаваемой таблицы, состоящее из одной, двух или трех частей. Если речь идет о внешней таблице, в SQL хранятся только метаданные таблицы, а также базовая статистика о файле или папке, на которые ссылается Hadoop и хранилище больших двоичных объектов Azure. Никакие данные не перемещаются и не хранятся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 \<column_definition> [ ,...*n* ] CREATE EXTERNAL TABLE допускает одно или несколько определений столбцов. CREATE EXTERNAL TABLE и CREATE TABLE используют одинаковый синтаксис для определения столбца. Исключение — параметр DEFAULT CONSTRAINT, который нельзя использовать с внешними таблицами. Подробную информацию об определениях столбцов и их типах данных см. в разделах [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md) и [CREATE TABLE в базе данных SQL Azure](http://msdn.microsoft.com/library/d53c529a-1d5f-417f-9a77-64ccc6eddca1).  
  
 Определения столбцов, включая типы данных и количество столбцов, должны соответствовать данным во внешних файлах. В случае несоответствия при запросе данных строки файла будут отклонены.  
  
 Во внешних таблицах, которые ссылаются на файлы во внешних источниках данных, определения столбцов и типов должны точно соответствовать схеме внешнего файла. При определении типов данных, которые ссылаются на данные, хранящиеся в Hadoop или Hive, используйте следующие сопоставления типов данных SQL и Hive и приведите тип к типу данных SQL при выборе. Типы включают все версии Hive, если не указано иное.

> [!NOTE]  
>  SQL Server не поддерживает тип данных Hive _infinity_ в любых преобразованиях. PolyBase будет завершаться ошибкой преобразования типов данных.


|Тип данных SQL|Тип данных .NET|Тип данных Hive|Тип данных Hadoop/Java|Комментарии|  
|-------------------|--------------------|--------------------|----------------------------|--------------|  
|TINYINT|Byte|TINYINT|ByteWritable|Только для чисел без знака.|  
|SMALLINT|Int16|SMALLINT|ShortWritable||  
|ssNoversion|Int32|ssNoversion|IntWritable||  
|BIGINT|Int64|BIGINT|LongWritable||  
|bit|Логическое значение|boolean|BooleanWritable||  
|FLOAT|Double|double|DoubleWritable||  
|REAL|Один|FLOAT|FloatWritable||  
|money|Decimal|double|DoubleWritable||  
|SMALLMONEY|Decimal|double|DoubleWritable||  
|NCHAR|String<br /><br /> Char[]|строка|text||  
|NVARCHAR|String<br /><br /> Char[]|строка|Текст||  
|char;|String<br /><br /> Char[]|строка|Текст||  
|varchar|String<br /><br /> Char[]|строка|Текст||  
|BINARY|Byte[]|BINARY|BytesWritable|Применяется к Hive 0.8 и более поздней версии.|  
|varbinary|Byte[]|BINARY|BytesWritable|Применяется к Hive 0.8 и более поздней версии.|  
|Дата|DateTime|TIMESTAMP|TimestampWritable||  
|smalldatetime|DateTime|TIMESTAMP|TimestampWritable||  
|datetime2|DateTime|TIMESTAMP|TimestampWritable||  
|DATETIME|DateTime|TIMESTAMP|TimestampWritable||  
|time|TimeSpan|TIMESTAMP|TimestampWritable||  
|Decimal|Decimal|Decimal|BigDecimalWritable|Применяется к Hive 0.11 и более поздней версии.|  
  
 LOCATION =  '*folder_or_filepath*'  
 Указывает путь к папке или файлу и имя файла для фактических данных в хранилище больших двоичных объектов Azure или Hadoop. Расположение начинается с корневой папки. Корневая папка — это расположение данных, указанное во внешнем источнике данных.  


В SQL Server инструкция CREATE EXTERNAL TABLE создает путь к папке и саму папку, если она еще не существует. Затем вы можете использовать инструкцию INSERT INTO, чтобы экспортировать данные из локальной таблицы SQL Server во внешний источник данных. Дополнительные сведения см. в разделе [Запросы PolyBase](/sql/relational-databases/polybase/polybase-queries). 

В хранилище данных SQL и в системе платформы Analytics инструкция [CREATE EXTERNAL TABLE AS SELECT](create-external-table-as-select-transact-sql.md) создает путь к папке и саму папку, если она еще не существует. В этих двух продуктах инструкция CREATE EXTERNAL TABLE не создает путь к папке и саму папку.

  
 Если вы укажете LOCATION в качестве папки, запрос PolyBase, который выбирает из внешней таблицы, извлечет файлы из этой папки и всех ее вложенных папок. Как и Hadoop, PolyBase не возвращает скрытые папки. Кроме того, не возвращаются файлы, имя которых начинается с подчеркивания (_) или точки (.).  
  
 В этом примере, если указано LOCATION='/webdata/', запрос PolyBase вернет строки из mydata.txt и mydata2.txt.  Он не вернет файл mydata3.txt, который вложен в скрытую папку. Он не вернет файл _hidden.txt, так как он является скрытым.  
  
 ![Рекурсивные данные для внешних таблиц](../../t-sql/statements/media/aps-polybase-folder-traversal.png "Рекурсивные данные для внешних таблиц")  
  
 Чтобы изменить значение по умолчанию и только для чтения в корневой папке, установите для атрибута \<polybase.recursive.traversal> значение 'false' в файле конфигурации core-site.xml. Этот файл находится в папке `<SqlBinRoot>\Polybase\Hadoop\Conf with SqlBinRoot the bin root of SQl Server`. Например, `C:\\Program Files\\Microsoft SQL Server\\MSSQL13.XD14\\MSSQL\\Binn`.  
  
 DATA_SOURCE = *external_data_source_name*  
 Задает имя внешнего источника данных, содержащего расположение внешних данных. Это расположение находится не в хранилище больших двоичных объектов Azure или Hadoop. Для создания внешнего источника данных используйте инструкцию [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 FILE_FORMAT = *external_file_format_name*  
 Задает имя объекта формата внешнего файла, который хранит тип файла и метод сжатия внешних данных. Чтобы создать формат внешнего файла, используйте [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
 Параметры отклонения  
 Можно указать параметры отклонения, определяющие, как PolyBase будет обрабатывать *грязные* записи, извлеченные из внешнего источника данных. Запись считается "грязной", если фактический тип данных или количество столбцов не совпадают с определениями столбцов во внешней таблице.  
  
 Если вы не указываете или не меняете значения отклонения, PolyBase использует значения по умолчанию. Сведения о параметрах отклонения сохраняются как дополнительные метаданные при создании внешней таблицы с помощью инструкции CREATE EXTERNAL TABLE.   При последующем выполнении инструкции SELECT или SELECT INTO SELECT для выбора данных из внешней таблицы PolyBase будет использовать параметры отклонения для определения числа или процента строк, которые можно отклонить, прежде чем запрос завершится ошибкой. , и делает это по-другому. Запрос будет возвращать (частичные) результаты, пока не будет превышено пороговое значение отклонения. Затем он выдаст соответствующее сообщение об ошибке.  
  
 REJECT_TYPE = **value** | percentage  
 Уточняет, указан параметр REJECT_VALUE как литеральное значение или процент.  
  
 value  
 REJECT_VALUE указан в виде литерала, а не в процентах. Запрос PolyBase завершится ошибкой, если число отклоненных строк превышает *reject_value*.  
  
 Например, если задано REJECT_VALUE = 5 и REJECT_TYPE = value, запрос PolyBase SELECT завершится ошибкой после отклонения пяти строк.  
  
 процент  
 REJECT_VALUE указывается в процентах, а не в виде литерала. Запрос PolyBase завершится ошибкой, когда *процент* отклоненных строк превысит *reject_value*. Процент отклоненных строк вычисляется с интервалами.  
  
 REJECT_VALUE = *reject_value*  
 Задает значение или процент строк, которые можно отклонить, прежде чем запрос завершится ошибкой.  
  
 Если задано REJECT_TYPE = value, значение *reject_value* должно быть целым числом от 0 до 2 147 483 647.  
  
 Если задано REJECT_TYPE = percentage, значение *reject_value* должно быть числом с плавающей точкой от 0 до 100.  
  
 REJECT_SAMPLE_VALUE = *reject_sample_value*  
 Этот атрибут является обязательным, если задано REJECT_TYPE = percentage. Он определяет количество строк, которое запрос попытается извлечь, прежде чем PolyBase пересчитает процент отклоненных строк.  
  
 Параметр *reject_sample_value* должен быть целым числом от 0 до 2 147 483 647.  
  
 Например, если задано REJECT_SAMPLE_VALUE = 1000, PolyBase рассчитает процент отклоненных строк после попытки импортировать 1000 строк из внешнего файла данных. Если процент отклоненных строк меньше значения *reject_value*, PolyBase попытается извлечь следующие 1000 строк. Он продолжает повторно вычислять процент отклоненных строк после каждой попытки извлечения 1000 строк.  
  
> [!NOTE]  
>  Поскольку PolyBase вычисляет процент отклоненных строк с интервалами, фактический процент отклоненных строк может превысить *reject_value*.  
  

Пример  
  
 В этом примере показано, как три параметра REJECT взаимодействуют друг с другом. Например, если задано REJECT_TYPE = percentage, REJECT_VALUE = 30 и REJECT_SAMPLE_VALUE = 100, произойдет следующее:  
  
-   PolyBase попытается извлечь первые 100 строк; из них 25 отклонено, а 75 — извлечено успешно.  
  
-   Процент строк с ошибками равен 25 %, что меньше значения отклонения — 30 %. Поэтому PolyBase продолжит извлечение данных из внешнего источника.  
  
-   PolyBase пытается загрузить следующие 100 строк. На этот раз 25 извлечено успешно и 75 — отклонено.  
  
-   Процент отклоненных строк пересчитывается и составляет 50 %. Процент отклоненных строк превысил значение отклонения 30 %.  
  
-   Запрос PolyBase завершается ошибкой, поскольку после попытки извлечение первых 200 строк 50 % из них было отклонено. Обратите внимание, что до того, как запрос PolyBase выявил превышение порога отклонения, были возвращены соответствующие строки.  
  
REJECTED_ROW_LOCATION = *расположение каталога*
  
  Указывает каталог во внешнем источнике данных, в который должны записываться строки и соответствующий файл ошибок.
Если указанный файл не существует, PolyBase создаст его от вашего имени. Создается дочерний каталог с именем "_rejectedrows". Благодаря символу "_" каталог исключается из других процессов обработки данных, если он явно не указан в параметре LOCATION. В этом каталоге создается папка, имя которой соответствует времени отправки загруженных данных в формате "ГодМесяцДень-ЧасМинутаСекунда" (например, 20180330-173205). В эту папку записываются файлы двух типов: файлы причин и файлы данных. 

Как файлы причин, так и файлы данных имеют идентификаторы queryID, связанные с инструкцией CTAS. Так как данные и причины хранятся в отдельных файлах, эти файлы имеют соответствующие суффиксы. 
  
 Параметры сегментированных внешних таблиц  
 Указывает внешний источник данных (не источник данных SQL Server) и метод распределения для [запроса эластичной базы данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  
  
 DATA_SOURCE  
 Внешний источник данных, например файловая система Hadoop, хранилище больших двоичных объектов Azure или [диспетчер карты сегментов](https://azure.microsoft.com/documentation/articles/sql-database-elastic-scale-shard-map-management/).  
  
 SCHEMA_NAME  
 Предложение SCHEMA_NAME позволяет сопоставить определение внешней таблицы с таблицей в другой схеме в удаленной базе данных. Используется для устранения неоднозначности между схемами, которые существуют одновременно в локальных и удаленных базах данных.  
  
 OBJECT_NAME  
 Предложение OBJECT_NAME позволяет сопоставить определение внешней таблицы с таблицей с другим именем в удаленной базе данных. Используется для устранения неоднозначности между именами объектов, которые существуют одновременно в локальных и удаленных базах данных.  
  
 DISTRIBUTION  
 Необязательный параметр. Он необходим только для баз данных типа SHARD_MAP_MANAGER. Этот параметр указывает, следует считать таблицу сегментированной или реплицированной. Если задано **SHARDED** (*column name*), данные из разных таблиц не перекрываются. **REPLICATED** указывает, что таблицы содержат одинаковые данные в каждом сегменте. **ROUND_ROBIN** указывает, что для распределения данных используется метод конкретного приложения.  
  
## <a name="permissions"></a>Разрешения  
 Требуются следующие разрешения:  
  
-   **CREATE TABLE**  
  
-   **ALTER ANY SCHEMA**  
  
-   **ALTER ANY EXTERNAL DATA SOURCE**  
  
-   **ALTER ANY EXTERNAL FILE FORMAT**  

-   **CONTROL DATABASE**
  
 Имя входа, которое создает внешний источник данных, должно иметь разрешение на чтение и запись во внешний источник данных, находящийся в хранилище больших двоичных объектов Azure или Hadoop.  


 > [!IMPORTANT]  

>  Разрешение ALTER ANY EXTERNAL DATA SOURCE предоставляет любому субъекту возможность создания и изменения объекта внешнего источника данных и, таким образом, также предоставляет возможность доступа ко всем учетным данным уровня базы данных в базе данных. Это разрешение следует рассматривать как высоко привилегированное, поэтому его следует предоставлять только доверенным субъектам в системе.

## <a name="error-handling"></a>Обработка ошибок  
 При выполнении инструкции CREATE EXTERNAL TABLE PolyBase пытается подключиться к внешнему источнику данных. Если попытка соединения завершается ошибкой, инструкция также завершается ошибкой и внешняя таблица не создается. Это может занять около минуты, поскольку PolyBase повторяет попытки соединения, прежде чем запрос будет завершен ошибкой.  
  
## <a name="general-remarks"></a>Общие замечания  
 Если используются нерегламентированные запросы, т. е. SELECT FROM EXTERNAL TABLE, PolyBase сохраняет строки, полученные из внешнего источника данных, во временной таблице. После выполнения запроса PolyBase удаляет временную таблицу. В таблицах SQL не сохраняются постоянные данные.  
  
 Если выполняется импорт, т. е. SELECT INTO FROM EXTERNAL TABLE, PolyBase сохраняет строки, полученные из внешнего источника данных, в виде постоянных данных в таблице SQL. Новая таблица создается во время выполнения запроса, когда Polybase извлекает внешние данные.  
  
 PolyBase может передать некоторые вычисления запросов в Hadoop для повышения производительности запросов. Это называется включением предиката. Для этого задайте параметр расположения диспетчера ресурсов Hadoop в [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 Вы можете создать несколько внешних таблиц, которые ссылаются на один или разные внешние источники данных.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 В CTP2 не поддерживается функция экспорта, т. е. возможность постоянного сохранения данных SQL во внешнем источнике данных. Эта функция будет доступна в CTP3.  
  
 Поскольку данные внешней таблицы хранятся вне устройства, они не находятся под контролем PolyBase и могут быть в любое время изменены или удалены внешним процессом. По этой причине результаты запроса к внешней таблице необязательно будут детерминированными. Один и то же запрос может возвращать разные результаты при каждом обращении к внешней таблице. Аналогичным образом запрос может завершиться ошибкой, если внешние данные удалены или перемещены.  
  
 Вы можете создать несколько внешних таблиц, которые ссылаются на разные внешние источники данных. Но если вы одновременно выполняете запросы к различным источникам данных Hadoop, каждый источник Hadoop должен иметь одинаковый параметр конфигурации сервера hadoop connectivity. Например, невозможно одновременно выполнить запрос к кластеру Cloudera Hadoop и кластеру Hortonworks Hadoop, поскольку они используют разные параметры конфигурации. Сведения о параметрах конфигурации и поддерживаемых сочетаниях см. в разделе [Конфигурация подключения к PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  
  
 Только эти инструкции DDL допускаются для внешних таблиц:  
  
-   CREATE TABLE и DROP TABLE  
  
-   CREATE STATISTICS и DROP STATISTICS  
Примечание. Инструкции CREATE и DROP STATISTICS для внешних таблиц не поддерживаются в базе данных SQL Azure. 
  
-   CREATE VIEW и DROP VIEW  
  
 Неподдерживаемые конструкции и операции:  
  
-   Ограничение DEFAULT для столбцов внешней таблицы  
  
-   Операции DML обновления, вставки и удаления  
  
 Ограничения запроса:  
  
 PolyBase может обработать не более 33 тысяч файлов на папку при выполнении параллельных запросов PolyBase со степенью 32. Это максимальное число включает файлы и вложенные папки в каждой папке HDFS. Если степень параллелизма меньше 32, пользователь может выполнять запросы PolyBase к папкам в HDFS, если в них содержится более 33 тысяч файлов. Рекомендуется указывать короткие пути к внешним файлам и следить за тем, чтобы в каждой папке HDFS было не более 30 тысяч файлов. При ссылке на слишком большое число файлов может возникнуть исключение, связанное с нехваткой памяти на виртуальной машине Java.  

Ограничения по ширине таблицы. В PolyBase в SQL Server 2016 ширина строки должна составлять не более 32 КБ в связи с максимальным размером допустимой строки в определении таблицы. Если схема суммы столбцов превышает 32 КБ, PolyBase не сможет запросить данные. 

В хранилище данных SQL это ограничение увеличено до 1 МБ.


## <a name="locking"></a>Блокировка  
 Общая блокировка на объект SCHEMARESOLUTION.  
  
## <a name="security"></a>безопасность  
 Файлы данных для внешней таблицы хранятся в хранилище больших двоичных объектов Azure или Hadoop. Эти файлы данных создаются и управляются вашими собственными процессами. В ваши обязанности входит управление безопасностью внешних данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-create-an-external-table-with-data-in-text-delimited-format"></a>A. Создайте внешнюю таблицу с данными с текстовыми разделителями.  
 В этом примере показаны все действия по созданию внешней таблицы с данными, отформатированными в виде файлов с текстовыми разделителями. В нем определяется внешний источник данных *mydatasource* и формат внешнего файла *myfileformat*. Затем эти объекты уровня базы данных указываются в инструкции CREATE EXTERNAL TABLE. Дополнительные сведения см. в разделе [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) и [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
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
 В этом примере показаны все действия по созданию внешней таблицы с данными, отформатированными в виде файлов RCFile. В нем определяется внешний источник данных *mydatasource_rc* и формат внешнего файла *myfileformat_rc*. Затем эти объекты уровня базы данных указываются в инструкции CREATE EXTERNAL TABLE. Дополнительные сведения см. в разделе [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) и [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource_rc  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat_rc  
WITH (  
    FORMAT_TYPE = RCFILE,  
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
 В этом примере показаны все действия по созданию внешней таблицы с данными, отформатированными в виде файлов ORC. В нем определяется внешний источник данных mydatasource_orc и формат внешнего файла myfileforma_orc. Затем эти объекты уровня базы данных указываются в инструкции CREATE EXTERNAL TABLE. Дополнительные сведения см. в разделе [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) и [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
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
 Clickstream — это внешняя таблица, соединенная с текстовым файлом с разделителями employee.tbl в кластере Hadoop. Следующий запрос выглядит так же, как запрос к стандартной таблице. Однако этот запрос извлекает данные из Hadoop, а затем вычисляет результаты.  
  
```  
SELECT TOP 10 (url) FROM ClickStream WHERE user_ip = 'xxx.xxx.xxx.xxx'  
;  
```  
  
### <a name="e-join-hadoop-data-with-sql-data"></a>Д. Объединение данных Hadoop с данными SQL  
 Этот запрос выглядит так же, как стандартный запрос JOIN для двух таблиц SQL. Разница в том, что PolyBase получает данные таблицы Clickstream из Hadoop, а затем объединяет их с таблицей UrlDescription. Одна таблица является внешней, а другая — стандартной таблицей SQL.  
  
```  
SELECT url.description  
FROM ClickStream cs  
JOIN UrlDescription url ON cs.url = url.name  
WHERE cs.url = 'msdn.microsoft.com'  
;  
```  
  
### <a name="f-import-data-from-hadoop-into-a-sql-table"></a>Е. Импорт данных из Hadoop в таблицу SQL  
 В этом примере создается новая таблица SQL — ms_user, в которой постоянно хранятся результаты объединения стандартной таблицы SQL *user* и внешней таблицы *ClickStream*.  
  
```  
SELECT DISTINCT user.FirstName, user.LastName  
INTO ms_user  
FROM user INNER JOIN (  
    SELECT * FROM ClickStream WHERE cs.url = 'www.microsoft.com'  
    ) AS ms_user  
ON user.user_ip = ms.user_ip  
;  
  
```  
  
### <a name="g-create-an-external-table-for-a-sharded-data-source"></a>Ж. Создание внешней таблицы для сегментированного источника данных  
 В этом примере удаленное динамическое административное представление сопоставляется с внешней таблицей с помощью предложений SCHEMA_NAME и OBJECT_NAME.  
  
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
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="h-importing-data-from-adls-into-azure-includessdwincludesssdw-mdmd"></a>З. Импорт данных из ADLS в Azure [!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
 
  
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
WITH
(
    FORMAT_TYPE = DELIMITEDTEXT 
    , FORMAT_OPTIONS ( FIELDTERMINATOR = '|' 
                     , STRINGDELIMITER = '' 
                     , DATEFORMAT = 'yyyy-MM-dd HH:mm:ss.fff' 
                     , USETYPE_DEFAULT = FALSE 
                     ) 
)


CREATE EXTERNAL TABLE [dbo].[DimProductexternal] 
( [ProductKey] [int] NOT NULL, 
  [ProductLabel] nvarchar NULL, 
  [ProductName] nvarchar NULL ) 
WITH
(
    LOCATION='/DimProduct/' , 
    DATA_SOURCE = AzureDataLakeStore , 
    FILE_FORMAT = TextFileFormat , 
    REJECT_TYPE = VALUE ,
    REJECT_VALUE = 0
) ;


CREATE TABLE [dbo].[DimProduct] 
WITH (DISTRIBUTION = HASH([ProductKey] ) ) 
AS SELECT * FROM 
[dbo].[DimProduct_external] ; 
     
```  
  
### <a name="i-join-external-tables"></a>И. Объединение внешних таблиц  
  
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
  
### <a name="k-import-row-data-from-hdfs-into-a-distributed-pdw-table"></a>Л. Импорт данных строк из HDFS в распределенную таблицу PDW  
  
```  
CREATE TABLE ClickStream_PDW  
WITH ( DISTRIBUTION = HASH (url) )  
AS SELECT url, event_date, user_ip FROM ClickStream  
;  
```  
  
### <a name="l-import-row-data-from-hdfs-into-a-replicated-pdw-table"></a>М. Импорт данных строк из HDFS в реплицированную таблицу PDW  
  
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
 [CREATE EXTERNAL TABLE AS SELECT (Transact-SQL)](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [CREATE TABLE AS SELECT (хранилище данных SQL Azure)](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
  
  



