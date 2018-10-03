---
title: Использование файла форматирования для пропуска поля данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], skipping data fields
- skipping data fields when importing
ms.assetid: 6a76517e-983b-47a1-8f02-661b99859a8b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7772acaa8fe5117d46e7aed625c8e45a4ab3806b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48073354"
---
# <a name="use-a-format-file-to-skip-a-data-field-sql-server"></a>Использование файла форматирования для пропуска поля данных (SQL Server)
  Количество полей в файле данных может превышать количество столбцов в таблице. В этом подразделе описан процесс изменения файлов форматирования в форматах XML и не XML с целью сопоставления столбцов таблицы с полями файла данных и пропуска остальных полей.  
  
> [!NOTE]  
>  И файлы форматирования, отличные от XML, и XML-файлы форматирования можно использовать для массового импорта файла данных в таблицу с помощью команды **bcp**, а также инструкции BULK INSERT или INSERT... SELECT * FROM OPENROWSET(BULK...). Дополнительные сведения см. в разделе [Использование файла форматирования для массового импорта данных (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md).  
  
## <a name="sample-data-file-and-table"></a>Образец таблицы и файла данных  
 В примерах этого подраздела используются следующие таблица и файл данных.  
  
### <a name="sample-table"></a>Образец таблицы  
 Для работы примеров необходимо, чтобы в образце базы данных `myTestSkipField` в схеме [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] была создана таблица `dbo` . Чтобы создать эту таблицу, в редакторе запросов среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , выполните следующий программный код.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestSkipField   
   (  
   PersonID smallint,  
   FirstName nvarchar(50) ,  
   LastName nvarchar(50)   
   );  
GO  
```  
  
### <a name="sample-data-file"></a>Образец файла данных  
 Файл данных `myTestSkipField-c.dat`содержит следующие записи:  
  
```  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
```  
  
 Для массового импорта из файла `myTestSkipField-c.dat` в таблицу `myTestSkipField` файл форматирования должен сделать следующий код:  
  
-   сопоставить первое поле данных с первым столбцом, `PersonID`;  
  
-   пропустить второе поле данных;  
  
-   сопоставить третье поле данных со вторым столбцом, `FirstName`;  
  
-   сопоставить четвертое поле данных с третьим столбцом, `LastName`.  
  
## <a name="non-xml-format-file-for-more-data-fields"></a>Не XML-файлы форматирования для дополнительных полей данных  
 Файл форматирования `myTestSkipField.fmt` сопоставляет поля в файле `myTestSkipField-c.dat` со столбцами таблицы `myTestSkipField`. Файл форматирования имеет символьный формат данных. Чтобы пропустить столбец, необходимо изменить его порядковый номер на «0», как показано для столбца `ExtraField` в файле форматирования.  
  
 В файле форматирования `myTestSkipField.fmt` содержатся следующие данные:  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     PersonID               ""  
2       SQLCHAR       0       100       ","    0     ExtraField             SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      2     FirstName              SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   3     LastName               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  Сведения о синтаксисе файлов форматирования в формате, отличном от XML, см. в разделе [Файлы формата, отличные от XML (SQL Server)](xml-format-files-sql-server.md).  
  
### <a name="examples"></a>Примеры  
 В следующем примере используется инструкция `INSERT ... SELECT * FROM OPENROWSET(BULK...)` с файлом форматирования `myTestSkipField.fmt` . В примере выполняется массовый импорт файла данных `myTestSkipField-c.dat` в таблицу `myTestSkipField` . Создание образца таблицы и файла данных см. выше в разделе «Образец таблицы и файла данных».  
  
 В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните следующий код:  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
   SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.fmt'    
       ) AS t1;  
GO   
```  
  
## <a name="xml-format-file-for-more-data-fields"></a>XML-файл форматирования для дополнительных полей данных  
 Файл форматирования в этом примере создан на основе другого файла форматирования `myTestSkipField.xml`, в котором количество полей совпадает с количеством столбцов таблицы `myTestSkipField`. Содержимое этого файла форматирования см. в разделе [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md).  
  
 Файл форматирования `myTestSkipField.xml` сопоставляет поля в файле `myTestSkipField-c.dat` со столбцами таблицы `myTestSkipField`. Файл форматирования имеет символьный формат данных.  
  
 В файле форматирования `myTestSkipField.xml` содержатся следующие данные:  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="PersonID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="3" NAME="FirstName" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="LastName" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
### <a name="examples"></a>Примеры  
 В следующем примере используется инструкция `INSERT ... SELECT * FROM OPENROWSET(BULK...)` с файлом форматирования `myTestSkipField.Xml` . В примере выполняется массовый импорт файла данных `myTestSkipField-c.dat` в таблицу `myTestSkipField` . Создание образца таблицы и файла данных см. выше в разделе «Образец таблицы и файла данных».  
  
 В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните следующий код:  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
  SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.xml'    
       ) AS t1;  
GO  
  
```  
  
> [!NOTE]  
>  Сведения о синтаксисе схемы XML и дополнительные образцы XML-файлов форматирования см. в разделе [XML-файлы форматирования (SQL Server)](xml-format-files-sql-server.md).  
  
## <a name="see-also"></a>См. также  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md)   
 [Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server)](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
  
