---
title: "Использование файла форматирования для массового импорта данных (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 09/20/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bulk importing [SQL Server], format files
- format files [SQL Server], importing data using
ms.assetid: 2956df78-833f-45fa-8a10-41d6522562b9
caps.latest.revision: 45
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 56c7e17bb97577907d21c0e1109ee3336337164b
ms.lasthandoff: 04/11/2017

---
# <a name="use-a-format-file-to-bulk-import-data-sql-server"></a>Использование файла форматирования для массового импорта данных (SQL Server)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Эта тема посвящена использованию файла форматирования в операциях массового импорта.  Файл форматирования сопоставляет поля в файле данных столбцам таблицы.  Ознакомьтесь с разделом [Создание файла форматирования (SQL Server)](../../relational-databases/import-export/create-a-format-file-sql-server.md) для получения дополнительных сведений.

|Контур|
|---|
|[Перед началом](#begin)<br />[Пример условий теста](#etc)<br />&emsp;&#9679;&emsp;[Образец таблицы](#sample_table)<br />&emsp;&#9679;&emsp;[Образец файла данных](#sample_data_file)<br />[Создание файлов форматирования](#create_format_file)<br />&emsp;&#9679;&emsp;[Создание файла форматирования в формате, отличном от XML](#nonxml_format_file)<br />&emsp;&#9679;&emsp;[Создание XML-файла форматирования](#xml_format_file)<br />[Использование файла форматирования для массового импорта данных](#import_data)<br />&emsp;&#9679;&emsp;[Использование bcp и файла форматирования в формате, отличном от XML](#bcp_nonxml)<br />&emsp;&#9679;&emsp;[Использование bcp и XML-файла форматирования](#bcp_xml)<br />&emsp;&#9679;&emsp;[Использование BULK INSERT и файла форматирования в формате, отличном от XML](#bulk_nonxml)<br />&emsp;&#9679;&emsp;[Использование BULK INSERT и XML-файла форматирования](#bulk_xml)<br />&emsp;&#9679;&emsp;[Использование OPENROWSET(BULK…) и файла форматирования в формате, отличном от XML](#openrowset_nonxml)<br />&emsp;&#9679;&emsp;[Использование OPENROWSET(BULK…) и XML-файла форматирования](#openrowset_xml)<p>                                                                                                                                                                                                                  </p>|
  
## Перед началом<a name="begin"></a>
* Чтобы файл форматирования мог работать с файлом символьных данных в Юникоде, все поля ввода должны представлять собой текстовые строки Юникода (то есть строки Юникода фиксированной длины или заканчивающиеся символом конца строки).
* Чтобы массово экспортировать или импортировать [SQLXML](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md) -данные, используйте один из следующих типов данных в файле форматирования:
  * SQLCHAR или SQLVARYCHAR (данные отправляются в кодовой странице клиента или кодовой странице, определенной параметрами сортировки);
  * SQLNCHAR или SQLNVARCHAR (данные отправляются в Юникоде);
  * SQLBINARY или SQLVARYBIN (данные отправляются без преобразования).
* База данных SQL Azure и хранилище данных SQL Azure поддерживают только [bcp](../../tools/bcp-utility.md).  Дополнительные сведения см. в следующих источниках:
  * [Загрузка данных в хранилище данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-overview-load/)
  * [Загрузка данных из SQL Server в хранилище данных SQL Azure (неструктурированные файлы)](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-load-from-sql-server-with-bcp/)
  * [Перенос данных](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-migrate-data/)

## Пример условий теста<a name="etc"></a>  
Примеры файлов форматирования в этой статье основаны на таблице и файле данных, которые определены ниже.

### **Образец таблицы**<a name="sample_table"></a>
Приведенный ниже сценарий создает тестовую базу данных и таблицу с именем `myFirstImport`.  Выполните следующий запрос Transact-SQL в Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS):
```tsql
CREATE DATABASE TestDatabase;
GO

USE TestDatabase;
CREATE TABLE dbo.MyFirstImport (
   PersonID smallint,
   FirstName varchar(25),
   LastName varchar(30),
   BirthDate Date
   );
```

### **Образец файла данных**<a name="sample_data_file"></a>
С помощью Блокнота создайте пустой файл `D:\BCP\myFirstImport.bcp` и вставьте следующие данные:
```
1,Anthony,Grosse,1980-02-23
2,Alica,Fatnowna,1963-11-14
3,Stella,Rosenhain,1992-03-02
```

Кроме того, можно выполнить следующий сценарий PowerShell для создания и заполнения файла данных:
```powershell
cls
# revise directory as desired
$dir = 'D:\BCP\';

$bcpFile = $dir + 'MyFirstImport.bcp';

# Confirm directory exists
IF ((Test-Path -Path $dir) -eq 0)
{
    Write-Host "The path $dir does not exist; please create or modify the directory.";
    RETURN;
};

# clear content, will error if file does not exist, can be ignored
Clear-Content -Path $bcpFile -ErrorAction SilentlyContinue;

# Add data
Add-Content -Path $bcpFile -Value '1,Anthony,Grosse,1980-02-23';
Add-Content -Path $bcpFile -Value '2,Alica,Fatnowna,1963-11-14';
Add-Content -Path $bcpFile -Value '3,Stella,Rosenhain,1992-03-02';

#Review content
Get-Content -Path $bcpFile;
Invoke-Item $bcpFile;
```

## Создание файлов форматирования<a name="create_format_file"></a>
SQL Server поддерживает два типа файлов форматирования: файлы форматирования в формате, отличном от XML, и XML-файлы форматирования.  Файл форматирования не в формате XML поддерживается более ранними версиями SQL Server.

### **Создание файла форматирования в формате, отличном от XML**<a name="nonxml_format_file"></a>
Дополнительные сведения см. в разделе [Файлы формата, отличные от XML (SQL Server)](../../relational-databases/import-export/non-xml-format-files-sql-server.md) .  Следующая команда будет использовать [служебную программу bcp](../../tools/bcp-utility.md) для создания файла форматирования `myFirstImport.fmt`в формате, отличном от XML, на основе схемы `myFirstImport`.  Чтобы создать файл форматирования при помощи служебной программы bcp, укажите аргумент **format** , а вместо пути файла данных задайте значение **nul** .  Параметр format также требует наличия параметра **-f** .  Кроме того, в этом примере квалификатор **c** используется для указания символьных данных, **t,** используется для указания запятой в качестве признака [конца поля](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md), а **T** используется для указания доверенного подключения с использованием встроенной системы безопасности.  В командной строке введите следующую команду:

```
bcp TestDatabase.dbo.myFirstImport format nul -c -f D:\BCP\myFirstImport.fmt -t, -T

REM Review file
Notepad D:\BCP\myFirstImport.fmt
```

Файл форматирования не в формате XML, `D:\BCP\myFirstImport.fmt` , должен выглядеть следующим образом:
```
13.0
4
1       SQLCHAR             0       7       ","      1     PersonID               ""
2       SQLCHAR             0       25      ","      2     FirstName              SQL_Latin1_General_CP1_CI_AS
3       SQLCHAR             0       30      ","      3     LastName               SQL_Latin1_General_CP1_CI_AS
4       SQLCHAR             0       11      "\r\n"   4     BirthDate              ""
```

> [!IMPORTANT]
> Убедитесь, что файл форматирования не в формате XML заканчивается символом перевода строки или возврата каретки.  В противном случае, скорее всего, появится следующее сообщение об ошибке:
> 
> `SQLState = S1000, NativeError = 0`  
> `Error = [Microsoft][ODBC Driver 13 for SQL Server]I/O error while reading BCP format file`

### **Создание XML-файла форматирования**<a name="xml_format_file"></a>  
Дополнительные сведения см. в разделе [XML-файлы форматирования (SQL Server)](../../relational-databases/import-export/xml-format-files-sql-server.md) .  Следующая команда будет использовать [служебную программу bcp](../../tools/bcp-utility.md) для создания XML-файла форматирования `myFirstImport.xml`на основе схемы `myFirstImport`. Чтобы создать файл форматирования при помощи служебной программы bcp, укажите аргумент **format** , а вместо пути файла данных задайте значение **nul** .  Параметр format всегда требует наличия параметра **-f** , а чтобы создать XML-файл форматирования, необходимо также задать параметр **-x** .  Кроме того, в этом примере квалификатор **c** используется для указания символьных данных, **t,** используется для указания запятой в качестве признака [конца поля](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md), а **T** используется для указания доверенного подключения с использованием встроенной системы безопасности.  В командной строке введите следующую команду:
```
bcp TestDatabase.dbo.myFirstImport format nul -c -x -f D:\BCP\myFirstImport.xml -t, -T

REM Review file
Notepad D:\BCP\myFirstImport.xml
```

Файл форматирования в формате XML, `D:\BCP\myFirstImport.xml` , должен выглядеть следующим образом:
```
\<?xml version="1.0"?>
\<BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <RECORD>
  \<FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>
  \<FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="25" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
  \<FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="30" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
  \<FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="11"/>
 </RECORD>
 <ROW>
  \<COLUMN SOURCE="1" NAME="PersonID" xsi:type="SQLSMALLINT"/>
  \<COLUMN SOURCE="2" NAME="FirstName" xsi:type="SQLVARYCHAR"/>
  \<COLUMN SOURCE="3" NAME="LastName" xsi:type="SQLVARYCHAR"/>
  \<COLUMN SOURCE="4" NAME="BirthDate" xsi:type="SQLDATE"/>
 </ROW>
</BCPFORMAT>
```

## Использование файла форматирования для массового импорта данных<a name="import_data"></a>
В приведенных ниже примерах используется база данных, файл данных и файлы форматирования, созданные ранее.

### **Использование [bcp](../../tools/bcp-utility.md) и [файла форматирования в формате, отличном от XML](../../relational-databases/import-export/non-xml-format-files-sql-server.md)**<a name="bcp_nonxml"></a>
В командной строке введите следующую команду:
```
REM Truncate table (for testing)
SQLCMD -Q "TRUNCATE TABLE TestDatabase.dbo.MyFirstImport;"

REM Import data
bcp TestDatabase.dbo.myFirstImport IN D:\BCP\myFirstImport.bcp -f D:\BCP\myFirstImport.fmt -T

REM Review results
SQLCMD -Q "SELECT * FROM TestDatabase.dbo.MyFirstImport"
```


### **Использование [bcp](../../tools/bcp-utility.md) и [XML-файла форматирования](../../relational-databases/import-export/xml-format-files-sql-server.md)**<a name="bcp_xml"></a>
В командной строке введите следующую команду:
```
REM Truncate table (for testing)
SQLCMD -Q "TRUNCATE TABLE TestDatabase.dbo.MyFirstImport;"

REM Import data
bcp TestDatabase.dbo.myFirstImport IN D:\BCP\myFirstImport.bcp -f D:\BCP\myFirstImport.xml -T

REM Review results
SQLCMD -Q "SELECT * FROM TestDatabase.dbo.MyFirstImport;"
```


### **Использование [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) и [файла форматирования в формате, отличном от XML](../../relational-databases/import-export/non-xml-format-files-sql-server.md)**<a name="bulk_nonxml"></a>
Выполните следующий запрос Transact-SQL в Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS):
```tsql
USE TestDatabase;  
GO

TRUNCATE TABLE myFirstImport; -- (for testing)
BULK INSERT dbo.myFirstImport   
   FROM 'D:\BCP\myFirstImport.bcp'   
   WITH (FORMATFILE = 'D:\BCP\myFirstImport.fmt');  
GO  

-- review results
SELECT * FROM TestDatabase.dbo.myFirstImport;
```

### **Использование [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) и [XML-файла форматирования](../../relational-databases/import-export/xml-format-files-sql-server.md)**<a name="bulk_xml"></a>
Выполните следующий запрос Transact-SQL в Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS):
```tsql
USE TestDatabase;  
GO

TRUNCATE TABLE myFirstImport; -- (for testing)
BULK INSERT dbo.myFirstImport   
   FROM 'D:\BCP\myFirstImport.bcp'   
   WITH (FORMATFILE = 'D:\BCP\myFirstImport.xml');  
GO  

-- review results
SELECT * FROM TestDatabase.dbo.myFirstImport;
```

### **Использование [OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md) и [файла форматирования в формате, отличном от XML](../../relational-databases/import-export/non-xml-format-files-sql-server.md)**<a name="openrowset_nonxml"></a>    
Выполните следующий запрос Transact-SQL в Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS):
```tsql
USE TestDatabase;
GO

TRUNCATE TABLE myFirstImport; -- (for testing)
INSERT INTO dbo.myFirstImport
    SELECT *
    FROM OPENROWSET (
        BULK 'D:\BCP\myFirstImport.bcp',
        FORMATFILE = 'D:\BCP\myFirstImport.fmt'
        ) AS t1;
GO

-- review results
SELECT * FROM TestDatabase.dbo.myFirstImport;
```

### **Использование [OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md) и [XML-файла форматирования](../../relational-databases/import-export/xml-format-files-sql-server.md)**<a name="openrowset_xml"></a>
Выполните следующий запрос Transact-SQL в Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS):
```tsql
USE TestDatabase;  
GO

TRUNCATE TABLE myFirstImport; -- (for testing)
INSERT INTO dbo.myFirstImport 
    SELECT *
    FROM OPENROWSET (
        BULK 'D:\BCP\myFirstImport.bcp',
        FORMATFILE = 'D:\BCP\myFirstImport.xml'  
       ) AS t1;
GO

-- review results
SELECT * FROM TestDatabase.dbo.myFirstImport;
```
  
## <a name="more-examples"></a>Другие примеры  
 [Создание файла форматирования (SQL Server)](../../relational-databases/import-export/create-a-format-file-sql-server.md)  
 [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
 [Использование файла форматирования для пропуска поля данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)  
 [Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [Файлы формата, отличные от XML (SQL Server)](../../relational-databases/import-export/non-xml-format-files-sql-server.md)   
 [XML-файлы форматирования (SQL Server)](../../relational-databases/import-export/xml-format-files-sql-server.md)  
  [Файлы форматирования для импорта или экспорта данных (SQL Server)](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)
  

