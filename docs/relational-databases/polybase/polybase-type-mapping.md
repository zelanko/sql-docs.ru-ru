---
title: Сопоставление типов с помощью PolyBase | Документация Майкрософт
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9839c46f477fe31d29214eed10dce0d673c9fd00
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732614"
---
# <a name="type-mapping-with-polybase"></a>Сопоставление типов с помощью PolyBase

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается сопоставление между внешними источниками данных PolyBase и SQL Server. Эти сведения можно использовать, чтобы правильно определить внешние таблицы с помощью команды Transact-SQL [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).

## <a name="overview"></a>Обзор

При создании внешней таблицы с помощью PolyBase определения столбцов, включая типы данных и количество столбцов, должны соответствовать данным во внешних файлах. В случае несоответствия при запросе данных строки файла отклоняются.  
  
Во внешних таблицах, которые ссылаются на файлы во внешних источниках данных, определения столбцов и типов должны точно соответствовать схеме внешнего файла. При определении типов данных, которые ссылаются на данные, хранящиеся в Hadoop или Hive, используйте следующие сопоставления типов данных SQL и Hive и приведите тип к типу данных SQL при выборе. Типы включают все версии Hive, если не указано иное.

> [!NOTE]  
> SQL Server не поддерживает тип данных Hive *infinity* в любых преобразованиях. PolyBase будет завершаться ошибкой преобразования типов данных.

## <a name="hadoop-type-mapping-reference"></a>Сопоставление типов Hadoop

| Тип данных SQL | Тип данных .NET            | Тип данных Hive | Тип данных Hadoop/Java | Комментарии                       |
| ------------- | ------------------------- | -------------- | --------------------- | ------------------------------ |
| TINYINT       | Byte                      | TINYINT        | ByteWritable          | Только для чисел без знака.     |
| SMALLINT      | Int16                     | SMALLINT       | ShortWritable         |
| ssNoversion           | Int32                     | ssNoversion            | IntWritable           |
| BIGINT        | Int64                     | BIGINT         | LongWritable          |
| bit           | Логическое значение                   | boolean        | BooleanWritable       |
| FLOAT         | Double                    | double         | DoubleWritable        |
| REAL          | Один                    | FLOAT          | FloatWritable         |
| money         | Decimal                   | double         | DoubleWritable        |
| SMALLMONEY    | Decimal                   | double         | DoubleWritable        |
| NCHAR         | String<br /><br /> Char[] | строка         | text                  |
| NVARCHAR      | String<br /><br /> Char[] | строка         | Текст                  |
| char;          | String<br /><br /> Char[] | строка         | Текст                  |
| varchar       | String<br /><br /> Char[] | строка         | Текст                  |
| BINARY        | Byte[]                    | BINARY         | BytesWritable         | Применяется к Hive 0.8 и более поздней версии. |
| varbinary     | Byte[]                    | BINARY         | BytesWritable         | Применяется к Hive 0.8 и более поздней версии. |
| Дата          | DateTime                  | TIMESTAMP      | TimestampWritable     |
| smalldatetime | DateTime                  | TIMESTAMP      | TimestampWritable     |
| datetime2     | DateTime                  | TIMESTAMP      | TimestampWritable     |
| DATETIME      | DateTime                  | TIMESTAMP      | TimestampWritable     |
| time          | TimeSpan                  | TIMESTAMP      | TimestampWritable     |
| Decimal       | Decimal                   | Decimal        | BigDecimalWritable    | Применяется к Hive 0.11 и более поздней версии. |

<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

## <a name="oracle-type-mapping-reference"></a>Сопоставление типов Oracle

| Тип данных Oracle              | Тип SQL Server |
| ----------------------------- | --------------- |
| float                         | float           |
| Decimal                       | Decimal         |
| int                           | int             |
| Long                          | Ntext           |
| Binary Float                  | Real            |
| CHAR                          | Nchar           |
| Varchar2                      | nvarchar        |
| Raw                           | Varbinary       |
| Long Raw                      | image           |
| Bfile                         | image           |
| Большие двоичные объекты                          | image           |
| Clob                          | image           |
| Rowid                         | Varchar         |
| Дата                          | Datetime2       |
| Отметка времени                     | Datetime2       |
| Timestamp with local timezone | Datetime2       |

### <a name="type-mismatch-float"></a>Несоответствие типов (Float)

Oracle поддерживает числа с плавающей запятой с точностью до 126. SQL Server поддерживает лучшую точность — 53. Таким образом **Float (1–53)** можно сопоставить напрямую, но при этом существует потеря данных из-за усечения.

### <a name="type-mismatch-character-types"></a>Несоответствие типов (символьные типы)

Для типов, таких как **Long** и **Bfile**, Oracle поддерживает размер типа данных в 4 ГБ. SQL Server поддерживает размер в 2 ГБ. Аналогичным образом, для типов данных **Blob** и **clob** Oracle может поддерживать размер до 128 ТБ, тогда как для типов **LONGVARBINARY** или **WLONGVARBINARY** SQL Server не поддерживает больше 2 ГБ. Сопоставление типов с размером типа данных, превышающим 2 ГБ, может привести к усечению данных.  

### <a name="type-mismatch-timestamp"></a>Несоответствие типов (Timestamp)

Для **Timestamp** и **Timestamp with local timezone** в Oracle поддерживается точность в 9 долей секунды, тогда как для типа данных SQL Server DateTime2 поддерживается точность только в 7 долей секунды.

Также Simba сопоставляет **Date**, **Timestamp** и **Timestamp with local zone** с типом ODBC **SQL_TIMESTAMP** и в конечном счете с типом SQL Server — **Timestamp**. **Timestamp** — это автоматически созданный уникальный идентификатор строки. В идеальном случае тип **SQL_TIMESTAMP** следует сопоставить с типом **DateTime/DateTime2** SQL Server или типами Oracle **Date** и **Timestamp**, а **Timestamp with local zone** — с типом ODBC **SQL_TYPE_TIMESTAMP**.

### <a name="driver-configuration-option"></a>Параметр конфигурации драйвера

Размер буфера по умолчанию для столбцов **Long/LOB** составляет 1024 КБ (настраиваемое значение).

## <a name="mongo-type-mapping-reference"></a>Сопоставление типов Mongo

| Тип данных BSON     | Тип SQL Server |
| ------------------ | --------------- |
| Double             | float           |
| String             | nvarchar        |
| Объект             |
| Array              |
| Двоичные данные        | nvarchar        |
| Идентификатор объекта.          | nvarchar        |
| Логическое значение            | bit             |
| Дата               | Datetime2       |
| 32-разрядное целое число     | int             |
| Отметка времени          | nvarchar        |
| 64-разрядное целое число     | BigInt          |
| DBPointer          | nvarchar        |
| Javascript         | nvarchar        |
| Максимальный ключ            | nvarchar        |
| Минимальный ключ            | nvarchar        |
| Символ             | nvarchar        |
| Регулярное выражение | nvarchar        |
| Не определено/NULL     | nvarchar        |

### <a name="javascript-with-scope"></a>JavaScript (с инструкциями SCOPE)

Драйвер возвращает значение в виде строки "Javascript со SCOPE не поддерживается".

### <a name="type-mismatch-string"></a>Несоответствие типов (string)

Строки MongoDB преобразуются в тип **SQL_WVARCHAR** с размером столбца в 255, что является размером по умолчанию. Этот размер столбца настраивается как часть конфигурации драйвера. Несмотря на возможность настройки, тип **SQL_WVARCHAR** или тип SQL Server **Varchar** поддерживают максимальный размер только 2 ГБ, тогда как MongoDB может хранить данные размером до 4 ГБ. Это может привести к усечению данных.

### <a name="mongodb-driver-options"></a>Параметры драйвера MongoDB

- **Включение двойной буферизации** . Выбирается по умолчанию.
- **Документы для получения на каждый блок**. По умолчанию 4096.
- **Представление строк как строк типа SQL_WVARCHAR**. Выбирается по умолчанию. Если значение не выбрано, строки представляются как строки типа SQL_VARCHAR.
- **Размер строкового столбца**. По умолчанию 255.
- **Представление двоичных значений как значений типа SQL_LONGVARBINARY**. Выбирается по умолчанию. Если значение не выбрано, двоичные значения представляются как значения типа SQL_VARCHAR.
- **Размер двоичного столбца**. По умолчанию 32767.
- **Включение передачи**. Выбирается по умолчанию.

### <a name="schema-related-driver-configurations"></a>Конфигурации драйверов, относящихся к схеме

- **LoadMetadataTable**. По умолчанию метаданные загружаются из базы данных. Указывает драйверу загрузить определение схемы из указанного JSON-файла.
- **LocalMetadataFile**. Если чтение происходит из файла, необходимо указать полный путь.
- **Метод выборки**.  
  - **По умолчанию, в прямом порядке**. Когда данные образцов драйвера отсортированы от первой записи.
  - **В обратном порядке**: драйвер отбирает данные, начиная с последней записи.
- **SamplingLimit**. По умолчанию — 100 (максимальное число записей, которые драйвер может выбрать для создания определения временной таблицы). Если задано значение 0, драйвер включает в выборку каждый документ.
- **SamplingStepSize**. По умолчанию — 1 (интервал, с которым драйвер выбирает записи при проверке базы данных для создания определения временной таблицы). Например, если задано значение 2, он отбирает каждую вторую запись в базе данных.

## <a name="teradata-type-mapping-reference"></a>Сопоставление типов Teradata

| Тип данных Teradata               | Тип SQL Server |
| -------------------------------- | --------------- |
| int                              | int             |
| Small Int                        | SmallInt        |
| Big Int                          | BigInt          |
| Byte Int                         | TinyInt         |
| Decimal                          | Decimal         |
| float                            | float           |
| Byte                             | Двоичный          |
| Varbyte                          | Varbinary       |
| Большие двоичные объекты                             | image           |
| CHAR                             | Nchar           |
| Clob                             | Ntext           |
| Varchar                          | nvarchar        |
| GRAPHIC                          | Nchar           |
| JSON                             | Ntext           |
| Vargraphic                       | nvarchar        |
| Дата                             | Дата            |
| Time                             | Time            |
| Time with Time Zone              | Time            |
| Отметка времени                        | Datetime2       |
| Interval Year                    |
| Interval year to month           |
| Interval Month                   |
| Interval Day                     |
| Interval Day to Hour             |
| Interval Day to Minute           |
| Interval Day to Second           |
| Interval Hour                    |
| Interval Hour to Minute          |
| Interval Hour to Second          |
| Interval Minute                  |
| Interval Minute to Second        |
| Interval Second                  |
| Period (DATE)                    |
| Period (TIME)                    |
| Period (TIME with Timezone)      |
| Period (Timestamp)               |
| Period (Timestamp with Timezone) |

### <a name="period-data-type"></a>Тип данных Period

Тип данных **Period** представляет собой продолжительность, обозначенную начальной и конечной границами. По сути, это кортеж. Эквивалентный тип в SQL Server для **Period** отсутствует.

### <a name="time-with-time-zone-and-timestamp"></a>Типы Time with Time Zone и Timestamp

Типы **Time with Time Zone** и **Timestamp** содержат смещение часового пояса, которое теряется во время преобразования. Это можно исправить, если сопоставлять тип **SQL_Type_Time/SQL_Type_Timestamp** с **datetimeoffset** вместо **Time/DateTime2**.

### <a name="byteint"></a>Тип ByteInt

Simba сопоставляет тип Teradata **ByteInt**, содержащий значения в диапазоне от 0 до 255, с типом **TinyInt**, содержащим значения в диапазоне от –127 до 127. Это может привести к усечению.  

### <a name="clob"></a>CLOB

Тип данных **CLOB** с кодировкой **LATIN** должен принимать 2097088000 символов. Тем не менее при превышении 1073741823 значение размера буфера становится отрицательным.  

### <a name="driver-configuration-options"></a>Параметры конфигурации драйвера

- Используйте данные **DATE** для параметров **TIMESTAMP**.
- Включите режим пользовательского каталога для приложений 2.X.
- В столбце **CREATE_PARAMS** для **SQL_TIMESTAMP** должна возвращаться пустая строка.
- Возвращайте максимальное значение. Максимальный размер **CHAR/VARCHAR** — 32 КБ.

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об использовании сопоставления см. в справочнике по Transact-SQL для [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md).
