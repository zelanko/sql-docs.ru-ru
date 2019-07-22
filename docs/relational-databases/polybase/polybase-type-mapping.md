---
title: Сопоставление типов с помощью PolyBase | Документация Майкрософт
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: aboke
ms.openlocfilehash: 1c9797eb7020b4381d21e5324ab2a3b23bb14b29
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061964"
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
| smallint      | Int16                     | smallint       | ShortWritable         |
| INT           | Int32                     | INT            | IntWritable           |
| BIGINT        | Int64                     | BIGINT         | LongWritable          |
| bit           | Логическое значение                   | boolean        | BooleanWritable       |
| FLOAT         | Double                    | double         | DoubleWritable        |
| REAL          | Один                    | FLOAT          | FloatWritable         |
| money         | Decimal                   | double         | DoubleWritable        |
| SMALLMONEY    | Decimal                   | double         | DoubleWritable        |
| NCHAR         | String<br /><br /> Char[] | строка         | Varchar               |
| NVARCHAR      | String<br /><br /> Char[] | строка         | Varchar               |
| char;          | String<br /><br /> Char[] | строка         | Varchar               |
| varchar       | String<br /><br /> Char[] | строка         | Varchar               |
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

| Тип данных Oracle | Тип SQL Server | 
| -------------    | --------------- |
|float             |float            |
|NUMBER            |Decimal          |
|LONG              |nvarchar         |
|BINARY_FLOAT      |Real             | 
|BINARY_DOUBLE     |float            | 
|CHAR              |CHAR             |
|VARCHAR2          |Varchar          | 
|NVARCHAR2         |nvarchar         | 
|RAW               |Varbinary        |
|LONG RAW          |Varbinary        | 
|BLOB              |Varbinary        |
|CLOB              |Varchar          |
|NCLOB             | nvarchar        | 
|ROWID             |Varchar          |
|UROWID            |Varchar          | 
|DATE              |Datetime2        |
|timestamp         |Datetime2        | 

**Несоответствие типов** 

**Число с плавающей запятой**: Oracle поддерживает числа с плавающей запятой с точностью до 126. SQL Server поддерживает лучшую точность — 53. Таким образом **Float (1–53)** можно сопоставить напрямую, но при этом существует потеря данных из-за усечения.

**Метка времени:** Timestamp и Timestamp with local timezone в Oracle поддерживают точность секунды до 9 десятичных цифр после запятой, тогда как DateTime2 в SQL Server поддерживает точность только до 7. 




## <a name="mongodb-type-mapping"></a>Сопоставление типов MongoDB

| Тип данных BSON     | Тип SQL Server |
| ------------------ | --------------- |
| Double             | float           |
| String             | nvarchar        |
| Двоичные данные        | nvarchar        |
| Идентификатор объекта.          | nvarchar        |
| Логическое значение            | bit             |
| Дата               | Datetime2       |
| 32-разрядное целое число     | int             |
| Отметка времени          | nvarchar        |
| 64-разрядное целое число     | BigInt          |
|Decimal 128         | Decimal         | 
| DBPointer          | nvarchar        |
| Javascript         | nvarchar        |
| Максимальный ключ            | nvarchar        |
| Минимальный ключ            | nvarchar        |
| Символ             | nvarchar        |
| Регулярное выражение | nvarchar        |
| Не определено/NULL     | nvarchar        |


MongoDB использует документы BSON для хранения записей данных. В отличие от предыдущих сценариев, в BSON нет схемы и поддерживается внедрение документов и массивов в другие документы. Это обеспечивает гибкость для пользователя. 


## <a name="teradata-type-mapping-reference"></a>Сопоставление типов Teradata

| Тип данных Teradata | Тип SQL Server | 
| -------------      | -------------   |
|INTEGER             |int              |
|SMALLINT            |SmallInt         |
|bigint              |BigInt           |
|BYTEINT             |SmallInt         |
|DECIMAL             |Decimal          |
|FLOAT               |Decimal          |
|BYTE                |Двоичный           |
|VARBYTE             |Varbinary        |
|BLOB                |varbinary        |
|CHAR                |Nchar            |
|CLOB                |nvarchar         |
|VARCHAR             |nvarchar         |
|Graphic             |Nchar            |
|JSON                |nvarchar         |
|VARGRAPHIC          |nvarchar         |
|DATE                |Дата             |
|timestamp           |Datetime2        |
|TIME                |Time             |
|TIME WITH TIME ZONE |Time             |
|TIMESTAMP WITH TIME ZONE|Time         |

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об использовании сопоставления см. в справочнике по Transact-SQL для [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md).
