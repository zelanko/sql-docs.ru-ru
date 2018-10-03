---
title: Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- mapping columns to fields during import [SQL Server]
- format files [SQL Server], mapping columns to fields
ms.assetid: e7ee4f7e-24c4-4eb7-84d2-41e57ccc1ef1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a35a70da1dac3d6dd2ff5e37f696654960883810
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48229024"
---
# <a name="use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server"></a>Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server)
  Файл данных может содержать поля, выстроенные в порядке, отличном от порядка соответствующих столбцов в таблице. В этом подразделе описывается изменение файлов форматирования в формате XML и в формате, отличном от XML для импорта файла данных, поля которого выстроены в ином порядке, нежели столбцы таблицы. Измененный файл форматирования сопоставляет поля данных соответствующим столбцам таблицы.  
  
> [!NOTE]  
>  Файлы форматирования в формате XML и в формате, отличном от XML, могут использоваться для массового импорта файла данных в таблицу командой **bcp**, инструкцией BULK INSERT или инструкцией INSERT... SELECT * FROM OPENROWSET(BULK...). Дополнительные сведения см. в статье [Использование файла форматирования для массового импорта данных (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md).  
  
## <a name="sample-table-and-data-file"></a>Образец таблицы и файла данных  
 В примерах этого подраздела используются следующие таблица и файл данных.  
  
### <a name="sample-table"></a>Образец таблицы  
 Для работы примеров этого раздела необходимо, чтобы в образце базы данных `myTestOrder` в схеме [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] была создана таблица `dbo` . Чтобы создать эту таблицу, в редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestOrder   
   (  
   Col1 smallint,  
   Col2 nvarchar(50) ,  
   Col3 nvarchar(50) ,   
   Col4 nvarchar(50)   
   );  
GO  
  
```  
  
### <a name="data-file"></a>Файл данных  
 Файл данных `myTestOrder-c.txt`содержит следующие записи:  
  
```  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
  
```  
  
 При массовом импорте данных из `myTestSkipCol2-c.dat` в таблицу `myTestSkipCol` файл форматирования должен сопоставить первое поле данных со столбцом `Col3`, второе поле данных — со столбцом `Col2`, третье поле данных — со столбцом `Col1`, а четвертое поле данных — со столбцом `Col4`.  
  
## <a name="using-a-non-xml-format-file"></a>Использование файла форматирования в формате, отличном от XML  
 Изменение порядка сопоставления столбцов достигается путем изменения значения порядка, чтобы указать для столбца позицию соответствующего поля данных.  
  
 В следующем образце файла форматирования формата, отличного от XML присутствует файл форматирования `myTestOrder.fmt`, который сопоставляет поля в файле `myTestOrder-c.txt` со столбцами таблицы `myTestOrder`. Дополнительные сведения о создании файлов данных и таблиц см. в находящемся выше разделе «Образец таблицы и файла данных». Файл форматирования имеет символьный формат данных.  
  
 В нем содержатся следующие данные:  
  
```  
9.0  
4  
1       SQLCHAR       0       100     ","     3     Col3               SQL_Latin1_General_CP1_CI_AS  
2       SQLCHAR       0       100     ","     2     Col2               SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       7       ","     1     Col1               ""  
4       SQLCHAR       0       100     "\r\n"  4     Col4               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  Дополнительные сведения о структуре файлов форматирования в формате, отличном от XML, см. в статье [Файлы формата, отличные от XML (SQL Server)](xml-format-files-sql-server.md).  
  
### <a name="example"></a>Пример  
 В следующем примере инструкция `BULK INSERT` производит массовый импорт данных из файла данных `myTestOrder-c.txt` в образец таблицы `myTestOrder` с использованием файла форматирования в формате, отличном от XML: `myTestOrder.fmt`.  
  
 В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestOrder  
FROM 'C:\myTestOrder-c.txt'   
WITH (formatfile='C:\myTestOrder.fmt');  
GO  
  
```  
  
## <a name="using-an-xml-format-file"></a>Использование XML-файла форматирования  
 Следующий образец файла форматирования в формате, отличном от XML представляет файл форматирования `myTestOrder.xml`, который сопоставляет поля в файле `myTestOrder-c.txt` столбцам таблицы `myTestOrder` (сведения о создании таблицы и файла данных см. в расположенном выше разделе «Образец таблицы и файла данных»).  
  
 В файле форматирования `myTestOrder.xml` содержатся следующие данные:  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="3" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="1" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
  
```  
  
> [!NOTE]  
>  Дополнительные сведения о синтаксисе XML-схемы и дополнительные образцы XML-файлов форматирования см. в статье [XML-файлы форматирования (SQL Server)](xml-format-files-sql-server.md).  
  
### <a name="example"></a>Пример  
 Следующий пример использует поставщик массового набора строк `OPENROWSET` для импорта данных из файла данных `myTestOrder-c.txt` в образец таблицы `myTestOrder` с использованием XML-файла форматирования `myTestOrder.xml` . Инструкция `INSERT… SELECT` задает список столбцов в списке выборки.  
  
 В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestOrder   
  SELECT Col1, Col2, Col3, Col4  
      FROM  OPENROWSET(BULK  'C:\myTestOrder-c.txt',  
      FORMATFILE='C:\myTestOrder.Xml'    
       ) AS t1;  
GO  
  
```  
  
## <a name="see-also"></a>См. также  
 [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md)   
 [Использование файла форматирования для пропуска поля данных (SQL Server)](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
  
