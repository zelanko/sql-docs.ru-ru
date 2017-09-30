---
title: "Примеры массового импорта и экспорта XML-документов (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 10/24/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- field terminators [SQL Server]
- bulk importing [SQL Server], data formats
- row terminators [SQL Server]
- OPENROWSET function, XML bulk load
- terminators [SQL Server]
- bulk exporting [SQL Server], data formats
- XML bulk load [SQL Server]
ms.assetid: dff99404-a002-48ee-910e-f37f013d946d
caps.latest.revision: 65
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 4e051789fad041a9515e00b01d6025cd2d7e6aed
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="examples-of-bulk-import-and-export-of-xml-documents-sql-server"></a>Примеры массового импорта и экспорта XML-документов (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

    
##  <a name="top"></a>
 Можно выполнить массовый импорт XML-документов в базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или осуществить массовый экспорт XML-документов из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В этом разделе приведены примеры и того, и другого.  
  
 Для выполнения массового импорта данных из файла в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или несекционированное представление могут использоваться следующие средства.  
  
-   Программа**bcp**   
 Программа **bcp** может выполнять экспорт везде в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , где работает инструкция SELECT, включая секционированные представления.  
  
-   BULK INSERT  
  
-   Инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...).  
  
 **Примечание.** Дополнительные сведения: 
  - [Массовый импорт и экспорт данных с использованием программы bcp (SQL Server)](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)
   - [Массовый импорт данных при помощи инструкции BULK INSERT или OPENROWSET(BULK...) (SQL Server)](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) 
    - [Как импортировать XML в SQL Server с помощью компонента массовой загрузки XML.](https://support.microsoft.com/en-us/kb/316005)
     - [Коллекции XML-схем (SQL Server)](../xml/xml-schema-collections-sql-server.md)
  
## <a name="examples"></a>Примеры  
 Далее следуют примеры.  
  
-  [А. Массовый импорт XML-данных в виде двоичного байтового потока](#binary_byte_stream)  
  
-  [Б. Массовый импорт XML-данных в существующую строку](#existing_row)  
  
-  [В. Массовый импорт XML-данных из файла, содержащего DTD](#file_contains_dtd)  
  
- [Г. Указание признаков конца поля явным образом при помощи файла форматирования](#field_terminator_in_format_file)  
  
-  [Д. Массовый экспорт XML-данных](#bulk_export_xml_data)  
  
## <a name="binary_byte_stream"></a>Массовый импорт XML-данных в виде двоичного байтового потока  
 При массовом импорте XML-данных из файла, содержащего объявление кодировки, которое необходимо применить, нужно указать параметр SINGLE_BLOB в функции OPENROWSET(BULK…). Параметр SINGLE_BLOB гарантирует, что средство синтаксического анализа XML в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] произведет импорт данных в соответствии со схемой кодирования, указанной в XML-объявлении.  
  
#### <a name="sample-table"></a>Образец таблицы  
 Для проверки представленного ниже примера A необходимо создать образец таблицы `T`.  
  
```  
USE tempdb  
CREATE TABLE T (IntCol int, XmlCol xml);  
GO  
```  
  
#### <a name="sample-data-file"></a>Образец файла данных  
 Перед запуском примера А необходимо создать файл в кодировке UTF-8 (`C:\SampleFolder\SampleData3.txt`), содержащий следующий образец, который определяет схему в кодировке `UTF-8` .  
  
```  
\<?xml version="1.0" encoding="UTF-8"?>  
<Root>  
          <ProductDescription ProductModelID="5">  
             <Summary>Some Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-a"></a>Пример A  
 В этом примере используется параметр `SINGLE_BLOB` в инструкции `INSERT ... SELECT * FROM OPENROWSET(BULK...)` для импорта данных из файла с именем `SampleData3.txt` и вставки экземпляра данных XML в таблицу с одним столбцом, образец таблицы `T`.  
  
```  
INSERT INTO T(XmlCol)  
SELECT * FROM OPENROWSET(  
   BULK 'c:\SampleFolder\SampleData3.txt',  
   SINGLE_BLOB) AS x;  
```  
  
#### <a name="remarks"></a>Замечания  
 С помощью параметра SINGLE_BLOB можно избежать несоответствия между кодировкой XML-документа (указанной в объявлении кодировки XML) и кодовой страницей строки, используемой сервером.  
  
 Если при использовании типов данных NCLOB или CLOB возникает конфликт кодовой страницы или кодировки, необходимо выполнить одно из следующих действий.  
  
-   Удалить XML-декларацию, чтобы успешно импортировать содержимое XML-файла данных.  
  
-   Указать кодовую страницу в параметре CODEPAGE запроса, который соответствует схеме кодирования, используемой в XML-декларации.  
  
-   Подобрать настройки параметров сортировки баз данных для схемы кодирования XML-данных, отличной от кодировки Юникод.  
  
 [&#91;В начало&#93;](#top)  
  
##  <a name="existing_row"></a> Массовый импорт XML-данных в существующую строку  
 В этом примере при помощи поставщика массового набора строк `OPENROWSET` в существующую строку или строки образца таблицы `T`добавляются инструкции XML.  
  
> [!NOTE]  
>  Чтобы выполнить этот пример, вначале необходимо выполнить скрипт проверки в примере А. В этом примере сначала создается таблица `tempdb.dbo.T` ; затем в нее проводится массовый импорт данных из файла `SampleData3.txt`.  
  
#### <a name="sample-data-file"></a>Образец файла данных  
 В примере Б используется измененная версия образца файла данных `SampleData3.txt` из предыдущего примера. Для запуска этого примера нужно изменить содержимое этого файла следующим образом:  
  
```  
<Root>  
          <ProductDescription ProductModelID="10">  
             <Summary>Some New Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-b"></a>Пример B-адреса  
  
```  
-- Query before update shows initial state of XmlCol values.  
SELECT * FROM T  
UPDATE T  
SET XmlCol =(  
SELECT * FROM OPENROWSET(  
   BULK 'C:\SampleFolder\SampleData3.txt',  
           SINGLE_BLOB  
) AS x  
)  
WHERE IntCol = 1;  
GO  
```  
  
 [&#91;В начало&#93;](#top)  
  
## <a name="file_contains_dtd"></a> Массовый импорт XML-данных из файла, содержащего DTD  
  
> [!IMPORTANT]  
>  Включать поддержку для определений типов документов (DTD) не рекомендуется, если только это не является неотъемлемой частью среды XML. Включение поддержки DTD увеличивает уязвимую контактную зону сервера и может привести к атаке типа «отказ в обслуживании». При необходимости включения поддержки DTD снизить риск для этой опасности можно с помощью обработки только доверенных XML-документов.  
  
 При попытке использования команды [bcp](../../tools/bcp-utility.md) для импорта XML-данных из файла, содержащего DTD, может возникнуть одна из следующих ошибок:  
  
 SQLState = 42000, NativeError = 6359  
  
 «Error = [Microsoft][SQL Server Native Client][ SQL Server]Разбор XML при помощи встроенного DTD не допускается. Используйте CONVERT с параметром стиля 2 для включения ограниченной поддержки встроенного DTD.»  
  
 «Не удалось выполнить BCP-копирование %s»  
  
 Чтобы избежать этой проблемы, можно импортировать XML-данные из файла, содержащего DTD, при помощи функции `OPENROWSET(BULK...)` , а затем указать параметр `CONVERT` в предложении `SELECT` . Базовым синтаксисом команды является:  
  
 `INSERT ... SELECT CONVERT(…) FROM OPENROWSET(BULK...)`  
  
#### <a name="sample-data-file"></a>Образец файла данных  
 Перед проверкой этого примера массового импорта создайте файл (`C:\temp\Dtdfile.xml`), содержащий следующий образец данных:  
  
```  
<!DOCTYPE DOC [<!ATTLIST elem1 attr1 CDATA "defVal1">]><elem1>January</elem1>  
```  
  
#### <a name="sample-table"></a>Образец таблицы  
 В примере В используется образец таблицы `T1` , созданный следующей инструкцией `CREATE TABLE` :  
  
```  
USE tempdb;  
CREATE TABLE T1(XmlCol xml);  
GO  
```  
  
#### <a name="example-c"></a>Пример В  
 В этом примере используется `OPENROWSET(BULK...)` и в предложении `CONVERT` указывается параметр `SELECT` для импорта XML-данных из `Dtdfile.xml` в образец таблицы `T1`.  
  
```  
INSERT T1  
  SELECT CONVERT(xml, BulkColumn, 2) FROM   
    OPENROWSET(Bulk 'c:\temp\Dtdfile.xml', SINGLE_BLOB) [rowsetresults];  
```  
  
 После выполнения инструкции `INSERT` определение DTD исключается из XML и хранится в таблице `T1` .  
  
 [&#91;В начало&#93;](#top)  
  
## <a name="field_terminator_in_format_file"></a> Указание признаков конца поля явным образом при помощи файла форматирования  
 В следующем примере демонстрируется, как выполнить массовый импорт XML-документа `Xmltable.dat`.  
  
#### <a name="sample-data-file"></a>Образец файла данных  
 Документ из `Xmltable.dat` содержит два значения XML, по одному в каждой строке. Первое значение XML имеет кодировку UTF-16, второе — UTF-8.  
  
 Содержимое этого файла данных показано в следующем шестнадцатеричном дампе:  
  
```  
FF FE 3C 00 3F 00 78 00-6D 00 6C 00 20 00 76 00  *..\<.?.x.m.l. .v.*  
65 00 72 00 73 00 69 00-6F 00 6E 00 3D 00 22 00  *e.r.s.i.o.n.=.".*  
31 00 2E 00 30 00 22 00-20 00 65 00 6E 00 63 00  *1...0.". .e.n.c.*  
6F 00 64 00 69 00 6E 00-67 00 3D 00 22 00 75 00  *o.d.i.n.g.=.".u.*  
74 00 66 00 2D 00 31 00-36 00 22 00 3F 00 3E 00  *t.f.-.1.6.".?.>.*  
3C 00 72 00 6F 00 6F 00-74 00 3E 00 A2 4F 9C 76  *\<.r.o.o.t.>..O.v*  
0C FA 77 E4 80 00 89 00-00 06 90 06 91 2E 9B 2E  *..w.............*  
99 34 A2 34 86 00 83 02-92 20 7F 02 4E C5 E4 A3  *.4.4..... ..N...*  
34 B2 B7 B3 B7 FE F8 FF-F8 00 3C 00 2F 00 72 00  *4.........\<./.r.*  
6F 00 6F 00 74 00 3E 00-00 00 00 00 7A EF BB BF  *o.o.t.>.....z...*  
3C 3F 78 6D 6C 20 76 65-72 73 69 6F 6E 3D 22 31  *\<?xml version="1*  
2E 30 22 20 65 6E 63 6F-64 69 6E 67 3D 22 75 74  *.0" encoding="ut*  
66 2D 38 22 3F 3E 3C 72-6F 6F 74 3E E4 BE A2 E7  *f-8"?><root>....*  
9A 9C EF A8 8C EE 91 B7-C2 80 C2 89 D8 80 DA 90  *................*  
E2 BA 91 E2 BA 9B E3 92-99 E3 92 A2 C2 86 CA 83  *................*  
E2 82 92 C9 BF EC 95 8E-EA 8F A4 EB 88 B4 EB 8E  *................*  
B7 EF BA B7 EF BF B8 C3-B8 3C 2F 72 6F 6F 74 3E  *.........</root>*  
00 00 00 00 7A                                   *....z*  
```  
  
#### <a name="sample-table"></a>Образец таблицы  
 При выполнении массового импорта или экспорта XML-документа следует использовать [признаки конца поля](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md) , которые не могут присутствовать в каком-либо документе, например последовательность из четырех значений NULL (`\0`), заканчивающаяся буквой `z`: `\0\0\0\0z`.  
  
 В этом примере показано, как использовать эти признаки конца поля в образце таблицы `xTable` . Чтобы создать этот образец таблицы, используйте следующую инструкцию `CREATE TABLE` :  
  
```  
USE tempdb;  
CREATE TABLE xTable (xCol xml);  
GO  
```  
  
#### <a name="sample-format-file"></a>Образец файла форматирования  
 Признак конца поля должен быть указан в файле форматирования. В примере Г создается файл форматирования `Xmltable.fmt` в формате, отличном от XML, который содержит следующее:  
  
```  
9.0  
1  
1       SQLBINARY     0       0       "\0\0\0\0z"    1     xCol         ""  
```  
  
 Этот файл форматирования можно использовать для массового импорта XML-документов в таблицу `xTable` при помощи команды `bcp` или инструкции `BULK INSERT` или `INSERT ... SELECT * FROM OPENROWSET(BULK...)` .  
  
#### <a name="example-d"></a>Пример Г  
 В этом примере используется файл форматирования `Xmltable.fmt` в инструкции `BULK INSERT` для импорта содержимого файла XML-данных с именем `Xmltable.dat`.  
  
```  
BULK INSERT xTable   
FROM 'C:\Xmltable.dat'  
WITH (FORMATFILE = 'C:\Xmltable.fmt');  
GO  
```  
  
 [&#91;В начало&#93;](#top)  
  
## <a name="bulk_export_xml_data"></a> Массовый экспорт XML-данных  
 В следующем примере для выполнения массового экспорта XML-данных из таблицы, созданной в предыдущем примере при помощи того же XML-файла форматирования, используется программа `bcp` . В следующей команде `bcp` `<server_name>` и `<instance_name>` являются заполнителями, которые должны быть заменены соответствующими значениями:  
  
```  
bcp bulktest..xTable out a-wn.out -N -T -S<server_name>\<instance_name>  
```  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не сохраняет кодировку XML, если XML-данные постоянно хранятся в базе данных. Поэтому оригинальная кодировка полей XML недоступна при экспорте XML-данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует для экспорта XML-данных кодировку UTF-16.  
  

## <a name="see-also"></a>См. также:  
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [Предложение SELECT (Transact-SQL)](../../t-sql/queries/select-clause-transact-sql.md)   
 [Программа bcp](../../tools/bcp-utility.md)   
 [Массовый импорт и экспорт данных (SQL Server)](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)  
  
  

