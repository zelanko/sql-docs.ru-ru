---
title: Использование файла форматирования для массового импорта данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bulk importing [SQL Server], format files
- format files [SQL Server], importing data using
ms.assetid: 2956df78-833f-45fa-8a10-41d6522562b9
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f46357975476ac301c28f639a3508edc992e5e5b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101751"
---
# <a name="use-a-format-file-to-bulk-import-data-sql-server"></a>Использование файла форматирования для массового импорта данных (SQL Server)
  Эта тема посвящена использованию файла форматирования в операциях массового импорта. Файл форматирования сопоставляет поля файла данных столбцам таблицы.  При массовом импорте данных можно использовать как формат XML, так и формат, отличный от XML, если импорт выполняется с помощью команды **bcp** или инструкций BULK INSERT или INSERT... SELECT * FROM OPENROWSET(BULK...) языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!IMPORTANT]  
>  Чтобы файл форматирования мог работать с файлом данных в Юникоде, все поля входных данных должны быть представлены в виде текстовых строк в Юникоде (то есть в Юникоде в виде строк фиксированной длины или заканчивающимися символом конца строки).  
  
> [!NOTE]  
>  Если вы не знакомы с файлами форматирования, см. раздел [не XML-файлы форматирования &#40;SQL Server&#41; ](xml-format-files-sql-server.md) и [XML-файлы форматирования &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
## <a name="format-file-options-for-bulk-import-commands"></a>Параметры файла форматирования для команд массового импортирования  
 В следующей таблице перечислены параметры файла форматирования для каждой команды массового импортирования.  
  
|Команда массовой загрузки|Параметр файла форматирования|  
|------------------------|-----------------------------------|  
|BULK INSERT|FORMATFILE = '*путь_к_файлу_форматирования*'|  
|Инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...).|FORMATFILE = '*путь_к_файлу_форматирования*'|  
|**bcp** … **В поле**|**-f** *format_file*|  
  
 Дополнительные сведения см. в статьях [Программа bcp](../../tools/bcp-utility.md), [BULK INSERT (SQL Server)](/sql/t-sql/statements/bulk-insert-transact-sql) и [OPENROWSET (SQL Server)](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Для массового экспорта или импорта данных SQLXML используйте один из следующих типов данных в файле форматирования: SQLCHAR или SQLVARYCHAR (данные отправляются в кодовой странице клиента или в кодовой странице, предполагаемой параметрами сортировки), SQLNCHAR или SQLNVARCHAR (данные отправляются в формате Юникод) и SQLBINARY или SQLVARYBIN (данные отправляются без преобразования).  
  
## <a name="examples"></a>Примеры  
 В примерах этой статьи показано, как использовать файлы форматирования для массового импорта данных с помощью команды **bcp**, а также инструкций BULK INSERT и INSERT ... SELECT * FROM OPENROWSET(BULK...). Перед выполнением примеров массового импортирования необходимо создать учебную таблицу, файл данных и файл форматирования.  
  
### <a name="sample-table"></a>Образец таблицы  
 Для выполнения этих примеров необходимо создать таблицу **myTestFormatFiles** в схеме **dbo** образца базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]. Для создания этой таблицы в редакторе запросов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните следующий код:  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestFormatFiles (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50),  
   Col4 nvarchar(50)  
   );  
GO  
```  
  
### <a name="sample-data-file"></a>Образец файла данных  
 В примере используется образец файла данных `myTestFormatFiles-c.Dat`, который содержит следующие записи. Для создания файла данных введите в командной строке [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows:  
  
```  
10,Field2,Field3,Field4  
15,Field2,Field3,Field4  
46,Field2,Field3,Field4  
58,Field2,Field3,Field4  
```  
  
### <a name="sample-format-files"></a>Образцы файлов форматирования  
 В некоторых примерах в этом разделе используется файл форматирования XML `myTestFormatFiles-f-x-c.Xml`, в других примерах используются файлы других форматов (не XML). Во всех файлах форматирования содержатся символьные данные и используется нестандартный признак конца поля (,).  
  
#### <a name="the-sample-non-xml-format-file"></a>Образец файла форматирования в формате, отличном от XML  
 В приведенном ниже примере используется команда **bcp** для создания XML-файла форматирования из таблицы `myTestFormatFiles`. Файл `myTestFormatFiles.Fmt` содержит следующие сведения:  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     Col1         ""  
2       SQLCHAR       0       100     ","      2     Col2         SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      3     Col3         SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   4     Col4         SQL_Latin1_General_CP1_CI_AS  
```  
  
 Чтобы воспользоваться командой **bcp** с параметром **format** для создания этого файла форматирования, введите в командной строке Windows следующее:  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -f myTestFormatFiles.Fmt -T  
  
```  
  
 Дополнительные сведения о создании файла форматирования см. в разделе [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md).  
  
#### <a name="the-sample-xml-format-file"></a>Образец XML-файла форматирования  
 В приведенном ниже примере используется команда **bcp** для создания XML-файла форматирования из таблицы `myTestFormatFiles`. Файл `myTestFormatFiles.Xml` содержит следующие сведения:  
  
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
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 Чтобы воспользоваться командой **bcp** с параметром **format** для создания этого файла форматирования, введите в командной строке Windows следующее:  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -x -f myTestFormatFiles.Xml -T  
```  
  
### <a name="using-bcp"></a>Использование команды bcp  
 В приведенном ниже примере используется команда **bcp** для массового импорта данных из файла данных `myTestFormatFiles-c.Dat` в таблицу `HumanResources.myTestFormatFiles` в образце базы данных. В примере используется файл форматирования XML `MyTestFormatFiles.Xml`. Перед импортированием файла данных все существующие строки таблицы удаляются.  
  
 В командной строке Windows введите:  
  
```  
bcp AdventureWorks2012..myTestFormatFiles in C:\myTestFormatFiles-c.Dat -f C:\myTestFormatFiles.Xml -T  
```  
  
> [!NOTE]  
>  Дополнительные сведения об этой команде см. в разделе [Программа bcp](../../tools/bcp-utility.md).  
  
### <a name="using-bulk-insert"></a>Использование предложения BULK INSERT  
 В следующем примере для массового импортирования данных из файла данных `myTestFormatFiles-c.Dat` в таблицу `HumanResources.myTestFormatFiles` образца базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] используется инструкция BULK INSERT. В примере используется файл форматирования, отличный от XML, `MyTestFormatFiles.Fmt`. Перед импортированием файла данных все существующие строки таблицы удаляются.  
  
 В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks2012;  
GO  
DELETE myTestFormatFiles;  
GO  
BULK INSERT myTestFormatFiles   
   FROM 'C:\myTestFormatFiles-c.Dat'   
   WITH (FORMATFILE = 'C:\myTestFormatFiles.Fmt');  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
> [!NOTE]  
>  Дополнительные сведения об этой инструкции см. в разделе [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
### <a name="using-the-openrowset-bulk-rowset-provider"></a>Использование поставщика массовых наборов строк OPENROWSET  
 В следующем примере для массового импорта данных из файла данных `INSERT ... SELECT * FROM OPENROWSET(BULK...)` в таблицу `myTestFormatFiles-c.Dat` образца базы данных `HumanResources.myTestFormatFiles` используется команда `AdventureWorks`. В примере используется файл форматирования XML `MyTestFormatFiles.Xml`. Перед импортированием файла данных все существующие строки таблицы удаляются.  
  
 В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks2012;  
DELETE myTestFormatFiles;  
GO  
INSERT INTO myTestFormatFiles  
    SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestFormatFiles-c.Dat',  
      FORMATFILE='C:\myTestFormatFiles.Xml'       
      ) as t1 ;  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
 Закончив эксперименты с образцом таблицы, удалите ее при помощи следующей инструкции:  
  
```  
DROP TABLE myTestFormatFiles  
```  
  
> [!NOTE]  
>  Дополнительные сведения о предложении OPENROWSET BULK см. в разделе [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql).  
  
## <a name="additional-examples"></a>Дополнительные примеры  
 [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md)  
  
 [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 [Использование файла форматирования для пропуска поля данных (SQL Server)](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
 [Использование файла форматирования для сопоставления столбцов таблицы полям файла данных (SQL Server)](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [Файлы формата, отличные от XML (SQL Server)](xml-format-files-sql-server.md)   
 [XML-файлы форматирования (SQL Server)](xml-format-files-sql-server.md)  
  
  
