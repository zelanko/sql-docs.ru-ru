---
title: Использование файла форматирования для пропуска поля данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 09/19/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], skipping data fields
- skipping data fields when importing
ms.assetid: 6a76517e-983b-47a1-8f02-661b99859a8b
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ff7be98f23994d1d2dffa35e09ceea874ce5e27b
ms.sourcegitcommit: 04c031f7411aa33e2174be11dfced7feca8fbcda
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "64946379"
---
# <a name="use-a-format-file-to-skip-a-data-field-sql-server"></a>Использование файла форматирования для пропуска поля данных (SQL Server)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Количество полей в файле данных может превышать количество столбцов в таблице. В этом подразделе описан процесс изменения файлов форматирования в форматах XML и не XML с целью сопоставления столбцов таблицы с полями файла данных и пропуска остальных полей.  Ознакомьтесь с разделом [Создание файла форматирования (SQL Server)](../../relational-databases/import-export/create-a-format-file-sql-server.md) для получения дополнительных сведений.

|Контур|
|---|
|[Пример условий теста](#etc)<br />&emsp;&#9679;&emsp;[Образец таблицы](#sample_table)<br />&emsp;&#9679;&emsp;[Образец файла данных](#sample_data_file)<br />[Создание файлов форматирования](#create_format_file)<br />&emsp;&#9679;&emsp;[Создание файла форматирования в формате, отличном от XML](#nonxml_format_file)<br />&emsp;&#9679;&emsp;[Изменение файла форматирования в формате, отличном от XML](#modify_nonxml_format_file)<br />&emsp;&#9679;&emsp;[Создание XML-файла форматирования](#xml_format_file)<br />&emsp;&#9679;&emsp;[Изменение файла форматирования в формате, отличном от XML](#modify_xml_format_file)<br />[Импорт данных с помощью файла форматирования для пропуска поля данных](#import_data)<br />&emsp;&#9679;&emsp;[Использование bcp и файла форматирования в формате, отличном от XML](#bcp_nonxml)<br />&emsp;&#9679;&emsp;[Использование bcp и XML-файла форматирования](#bcp_xml)<br />&emsp;&#9679;&emsp;[Использование BULK INSERT и файла форматирования в формате, отличном от XML](#bulk_nonxml)<br />&emsp;&#9679;&emsp;[Использование BULK INSERT и XML-файла форматирования](#bulk_xml)<br />&emsp;&#9679;&emsp;[Использование OPENROWSET(BULK…) и файла форматирования в формате, отличном от XML](#openrowset_nonxml)<br />&emsp;&#9679;&emsp;[Использование OPENROWSET(BULK…) и XML-файла форматирования](#openrowset_xml)<p>                                                                                                                                                                                                                  </p>|
  
> [!NOTE]
>  И файлы форматирования, отличные от XML, и XML-файлы форматирования можно использовать для массового импорта файла данных в таблицу с помощью команды служебной программы [bcp](../../tools/bcp-utility.md), а также инструкции [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) или INSERT... SELECT * FROM [OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md). Дополнительные сведения см. в разделе [Использование файла форматирования для массового импорта данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md).

## Пример условий теста<a name="etc"></a>  
Примеры измененных файлов форматирования базируются на таблице и файле данных, которые определены ниже.
  
### Образец таблицы<a name="sample_table"></a>
Приведенный ниже сценарий создает тестовую базу данных и таблицу с именем `myTestSkipField`.  Выполните следующий код Transact-SQL в Microsoft SQL Server Management Studio (SSMS):
 
```sql
CREATE DATABASE TestDatabase;
GO

USE TestDatabase;
CREATE TABLE myTestSkipField
   (
   PersonID smallint,
   FirstName varchar(25),
   LastName varchar(30)
   );
```
  
### Образец файла данных<a name="sample_data_file"></a>
Создайте пустой файл `D:\BCP\myTestSkipField.bcp` и вставьте следующие данные: 
```
1,SkipMe,Anthony,Grosse
2,SkipMe,Alica,Fatnowna
3,SkipMe,Stella,Rosenhain
```
  
## Создание файлов форматирования<a name="create_format_file"></a>
Для массового импорта из файла `myTestSkipField.bcp` в таблицу `myTestSkipField` файл форматирования должен сделать следующий код:
* сопоставить первое поле данных с первым столбцом, `PersonID`;
* пропустить второе поле данных;
* сопоставить третье поле данных со вторым столбцом, `FirstName`;
* сопоставить четвертое поле данных с третьим столбцом, `LastName`.  

Простейший способ создать файл форматирования заключается в использовании [служебной программы bcp](../../tools/bcp-utility.md).  Во-первых, создайте базовый файл форматирования из существующей таблицы.  Во-вторых, измените его в соответствии с фактическим файлом данных.
  
### <a name="nonxml_format_file"></a>Создание файла форматирования в формате, отличном от XML 
Дополнительные сведения см. в разделе [Файлы формата, отличные от XML (SQL Server)](../../relational-databases/import-export/non-xml-format-files-sql-server.md) . Следующая команда будет использовать [служебную программу bcp](../../tools/bcp-utility.md) для создания файла форматирования `myTestSkipField.fmt`, отличного от XML, на основе схемы `myTestSkipField`.  Кроме того, квалификатор `c` используется для указания символьных данных, `t,` используется для указания запятую в качестве признака конца поля, а `T` используется для указания доверенного соединения с использованием встроенной системы безопасности.  В командной строке введите следующую команду:

```
bcp TestDatabase.dbo.myTestSkipField format nul -c -f D:\BCP\myTestSkipField.fmt -t, -T
```

### Изменение файла форматирования в формате, отличном от XML <a name="modify_nonxml_format_file"></a>
Терминологию см. в разделе [Структура файлов форматирования в формате, отличном от XML](../../relational-databases/import-export/non-xml-format-files-sql-server.md#Structure) . Откройте `D:\BCP\myTestSkipField.fmt` в Блокноте и внесите следующие изменения:
1) Скопируйте всю строку для `FirstName` из файла форматирования и вставьте ее на следующей строке после `FirstName` .
2) Увеличьте значения порядка полей файла узлов на единицу для новой строки и всех последующих строк.
3) Увеличьте значение числа столбцов в соответствии с действительным числом полей в файле данных.
3) Измените порядок столбцов сервера с `2` на `0` во второй строке файла форматирования. 

Сравните внесенные изменения:  
**Перед**
```
13.0
3
1       SQLCHAR 0       7       ","      1     PersonID     ""
2       SQLCHAR 0       25      ","      2     FirstName    SQL_Latin1_General_CP1_CI_AS
3       SQLCHAR 0       30      "\r\n"   3     LastName     SQL_Latin1_General_CP1_CI_AS
```
**После**
```
13.0
4
1       SQLCHAR 0       7       ","      1     PersonID     ""
2       SQLCHAR 0       25      ","      0     FirstName    SQL_Latin1_General_CP1_CI_AS
3       SQLCHAR 0       25      ","      2     FirstName    SQL_Latin1_General_CP1_CI_AS
4       SQLCHAR 0       50      "\r\n"   3     LastName     SQL_Latin1_General_CP1_CI_AS

```

Теперь измененный файл форматирования отображает:
* 4 поля данных
* Первое поле данных в `myTestSkipField.bcp` сопоставляется с первым столбцом. `myTestSkipField.. PersonID`
* Второе поле данных в `myTestSkipField.bcp` не сопоставляется ни с одним из столбцов.
* Третье поле данных в `myTestSkipField.bcp` сопоставляется со вторым столбцом. `myTestSkipField.. FirstName`
* Четвертое поле данных в `myTestSkipField.bcp` сопоставляется с третьим столбцом. `myTestSkipField.. LastName`

### Создание файла форматирования в формате, отличном от XML <a name="xml_format_file"></a>  
Дополнительные сведения см. в разделе [XML-файлы форматирования (SQL Server)](../../relational-databases/import-export/xml-format-files-sql-server.md) .  Следующая команда будет использовать [служебную программу bcp](../../tools/bcp-utility.md) для создания XML-файла форматирования `myTestSkipField.xml`на основе схемы `myTestSkipField`.  Кроме того, квалификатор `c` используется для указания символьных данных, `t,` используется для указания запятую в качестве признака конца поля, а `T` используется для указания доверенного соединения с использованием встроенной системы безопасности.  Для создания XML-файла форматирования должен использоваться квалификатор `x` .  В командной строке введите следующую команду:

```
bcp TestDatabase.dbo.myTestSkipField format nul -c -x -f D:\BCP\myTestSkipField.xml -t, -T
```

### Изменение XML-файла форматирования <a name="modify_xml_format_file"></a>
Терминологию см. в разделе [Синтаксис схемы для XML-файлов форматирования](../../relational-databases/import-export/xml-format-files-sql-server.md#StructureOfXmlFFs) .  Откройте `D:\BCP\myTestSkipField.xml` в Блокноте и внесите следующие изменения:
1) Скопируйте все второе поле и вставьте его сразу после второго поля на следующей строке.
2) Увеличьте значение FIELD ID на 1 для нового поля и всех последующих полей.
3) Увеличьте значение COLUMN SOURCE на 1 для `FirstName`и `LastName` в соответствии с исправленным сопоставлением.

Сравните внесенные изменения:  
**Перед**
```
\<?xml version="1.0"?>
\<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <RECORD>
  \<FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>
  \<FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="25" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
  \<FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="30" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
 </RECORD>
 <ROW>
  \<COLUMN SOURCE="1" NAME="PersonID" xsi:type="SQLSMALLINT"/>
  \<COLUMN SOURCE="2" NAME="FirstName" xsi:type="SQLVARYCHAR"/>
  \<COLUMN SOURCE="3" NAME="LastName" xsi:type="SQLVARYCHAR"/>
 </ROW>
</BCPFORMAT>
```

**После**
```
\<?xml version="1.0"?>
\<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <RECORD>
  \<FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>
  \<FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="25" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
  \<FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="25" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
  \<FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="30" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
 </RECORD>
 <ROW>
  \<COLUMN SOURCE="1" NAME="PersonID" xsi:type="SQLSMALLINT"/>
  \<COLUMN SOURCE="3" NAME="FirstName" xsi:type="SQLVARYCHAR"/>
  \<COLUMN SOURCE="4" NAME="LastName" xsi:type="SQLVARYCHAR"/>
 </ROW>
</BCPFORMAT>
```

Теперь измененный файл форматирования отображает:
* 4 поля данных
* Поле 1, соответствующее столбцу 1, сопоставляется с первым столбцом таблицы. `myTestSkipField.. PersonID`
* Поле 2, не соответствующее ни одному из столбцов поэтому не сопоставляется ни с одним столбцом таблицы.
* Поле 3, соответствующее столбцу 3, сопоставляется со вторым столбцом таблицы. `myTestSkipField.. FirstName`
* Поле 4, соответствующее столбцу 4, сопоставляется с третьим столбцом таблицы. `myTestSkipField.. LastName`

## Импорт данных с помощью файла форматирования для пропуска поля данных<a name="import_data"></a>
В приведенных ниже примерах используется база данных, файл данных и файлы форматирования, созданные ранее.

### Использование [bcp](../../tools/bcp-utility.md) и [файла форматирования в формате, отличном от XML](../../relational-databases/import-export/non-xml-format-files-sql-server.md)<a name="bcp_nonxml"></a>
В командной строке введите следующую команду:
```
bcp TestDatabase.dbo.myTestSkipField IN D:\BCP\myTestSkipField.bcp -f D:\BCP\myTestSkipField.fmt -T
```

### Использование [bcp](../../tools/bcp-utility.md) и [XML-файла форматирования](../../relational-databases/import-export/xml-format-files-sql-server.md)<a name="bcp_xml"></a>
В командной строке введите следующую команду:
```
bcp TestDatabase.dbo.myTestSkipField IN D:\BCP\myTestSkipField.bcp -f D:\BCP\myTestSkipField.xml -T
```

### Использование [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) и [файла форматирования в формате, отличном от XML](../../relational-databases/import-export/non-xml-format-files-sql-server.md)<a name="bulk_nonxml"></a>
Выполните следующий код Transact-SQL в Microsoft SQL Server Management Studio (SSMS):
```sql
USE TestDatabase;  
GO

TRUNCATE TABLE myTestSkipField;
BULK INSERT dbo.myTestSkipField   
   FROM 'D:\BCP\myTestSkipField.bcp'   
   WITH (FORMATFILE = 'D:\BCP\myTestSkipField.fmt');  
GO  

-- review results
SELECT * FROM TestDatabase.dbo.myTestSkipField;
```

### Использование [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) и [XML-файла форматирования](../../relational-databases/import-export/xml-format-files-sql-server.md)<a name="bulk_xml"></a>
Выполните следующий код Transact-SQL в Microsoft SQL Server Management Studio (SSMS):
```sql
USE TestDatabase;  
GO

TRUNCATE TABLE myTestSkipField;
BULK INSERT dbo.myTestSkipField   
   FROM 'D:\BCP\myTestSkipField.bcp'   
   WITH (FORMATFILE = 'D:\BCP\myTestSkipField.xml');  
GO  

-- review results
SELECT * FROM TestDatabase.dbo.myTestSkipField;
```

### Использование [OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md) и [файла форматирования в формате, отличном от XML](../../relational-databases/import-export/non-xml-format-files-sql-server.md)<a name="openrowset_nonxml"></a>    
Выполните следующий код Transact-SQL в Microsoft SQL Server Management Studio (SSMS):
```sql
USE TestDatabase;
GO

TRUNCATE TABLE myTestSkipField;
INSERT INTO dbo.myTestSkipField
    SELECT *
    FROM OPENROWSET (
        BULK 'D:\BCP\myTestSkipField.bcp',
        FORMATFILE = 'D:\BCP\myTestSkipField.fmt'
        ) AS t1;
GO

-- review results
SELECT * FROM TestDatabase.dbo.myTestSkipField;
```

### Использование [OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md) и [XML-файла форматирования](../../relational-databases/import-export/xml-format-files-sql-server.md)<a name="openrowset_xml"></a>
Выполните следующий код Transact-SQL в Microsoft SQL Server Management Studio (SSMS):
```sql
USE TestDatabase;  
GO

TRUNCATE TABLE myTestSkipField;
INSERT INTO dbo.myTestSkipField 
    SELECT *
    FROM OPENROWSET (
        BULK 'D:\BCP\myTestSkipField.bcp',
        FORMATFILE = 'D:\BCP\myTestSkipField.xml'  
       ) AS t1;
GO

-- review results
SELECT * FROM TestDatabase.dbo.myTestSkipField;
```

  
## <a name="see-also"></a>См. также:  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)   
 [Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
  
