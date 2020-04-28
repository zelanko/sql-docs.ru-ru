---
title: Создание экземпляров XML-данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- type casting string instances [XML in SQL Server]
- XML [SQL Server], typed
- xml data type [SQL Server], generating instances
- casting string instances [XML in SQL Server]
- typed XML
- generating XML instances [SQL Server]
- XML [SQL Server], generating instances
- white space [XML in SQL Server]
ms.assetid: dbd6c06f-db6e-44a7-855a-6a55bf374907
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae842748d2d510c5c00f329f5e28cd49a0c86ef3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62637612"
---
# <a name="create-instances-of-xml-data"></a>Создание экземпляров XML-данных
  В этом разделе описывается формирование XML-экземпляров.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]сформировать XML-экземпляры можно следующими способами:  
  
-   тип экземпляров приведения строки;  
  
-   использование инструкции SELECT с предложением FOR XML;  
  
-   использование постоянных назначений;  
  
-   использование массовой загрузки.  
  
## <a name="type-casting-string-and-binary-instances"></a>Строка приведения типа и двоичные экземпляры  
 Можно выполнить синтаксический анализ любых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] строковых типов данных, например [**n**] [**var**]**char**, **[n] text**, **varbinary**и **Image**, в тип `xml` данных путем приведения (приведения) или преобразования (преобразования) строки в тип `xml` данных. Проверка нетипизированного XML подтверждает, что он сформирован правильно. При наличии схемы, связанной с `xml` типом, также выполняется проверка. Дополнительные сведения см. в статье [Сравнение типизированного и нетипизированного XML](compare-typed-xml-to-untyped-xml.md).  
  
 XML-документы могут быть кодированы различными кодировками (например, UTF-8, UTF-16, windows-1252). Следующие правила дают сведения о том, как строка и двоичный источник взаимодействуют с кодировкой XML-документа, и как ведет себя синтаксический анализатор.  
  
 Так как тип **nvarchar** предполагает двухбайтовую кодировку Юникод, например UTF-16 или UCS-2, синтаксический XML-анализатор сочтет значение строки за XML-документ или фрагмент в двухбайтовой кодировке Юникод. Это значит, что XML-документ должен быть закодирован в двухбайтовой кодировке Юникод, а также совмещен с типом данных источника. XML-документ в кодировке UTF-16 может иметь отметку порядка байтов (BOM) UTF-16, но не обязан, так как контекст типа источника уточняет, что он может быть документом, закодированным только в двухбайтовой кодировке Юникод.  
  
 Содержимое строки **varchar** синтаксический XML-анализатор принимает за однобайтовый XML-документ/фрагмент. Так как строка источника **varchar** имеет связанную кодовую страницу, синтаксический анализатор будет использовать эту кодовую страницу для кодирования, если явно не была указана кодировка в самом XML. Если XML-экземпляр имеет отметку BOM или декларацию кодирования, отметка BOM или декларация должна быть согласована с кодовой страницей, иначе синтаксический анализатор выдаст ошибку.  
  
 Содержимое строки **varbinary** принимается за поток кодовых точек, который передается непосредственно синтаксическому XML-анализатору. Таким образом, XML-документ или фрагмент должен содержать встроенную отметку BOM или другие сведения о кодировании. Чтобы определить кодировку, синтаксическому анализатору достаточно будет просто просмотреть поток. Это значит, что XML в кодировке UTF-16 должен содержать отметку UTF-16 BOM, а экземпляр без отметки BOM и без декларации о кодировании будет интерпретироваться как UTF-8.  
  
 Если кодировка XML-документа не известна заранее, а данные вместо XML передаются как строка или двоичные данные до приведения в XML, рекомендуется рассматривать данные как **varbinary**. Например, при считывании данных из XML-файла с помощью функции OpenRowset() необходимо указать данные для считывания как значения **varbinary(max)** :  
  
```  
select CAST(x as XML)   
from OpenRowset(BULK 'filename.xml', SINGLE_BLOB) R(x)  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутренне представляет XML в эффективном двоичном представлении, использующем кодировку UTF-16. Пользовательская кодировка не сохранена, но она учитывается в процессе синтаксического анализа.  
  
### <a name="type-casting-clr-user-defined-types"></a>Приведение определяемых пользователем типов CLR  
 Если определяемый пользователем тип данных CLR имеет XML-сериализацию, экземпляры этого типа могут быть явно приведены к типу данных XML. Более подробные сведения о XML-сериализации определяемого пользователем типа данных CLR см. в статье [Сериализация XML из объектов базы данных CLR](../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md).  
  
### <a name="white-space-handling-in-typed-xml"></a>Обработка пробела в типизированном XML  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]пробел внутри содержимого элемента считается незначащим, если он появляется внутри последовательности данных, содержащей только пробельные символы, разделенных разметкой, например начальными и конечными тегами. Такой пробел не преобразуется в сущность. (секции CDATA игнорируются). Данная обработка пробела отличается от пробела, описанного в спецификации XML 1.0, опубликованной консорциумом World Wide Web (W3C). Это происходит потому, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средство синтаксического анализа XML распознает только ограниченное число подмножеств DTD, как указано в XML 1.0. Дополнительные сведения об ограниченных подмножествах DTD, поддерживаемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [CAST и CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
 Синтаксический XML-анализатор отменяет незначащие пробелы при преобразовании строковых данных в XML по умолчанию, если выполняется одно из следующих условий:  
  
-   `The xml:space` не определен на элементе или его родителях;  
  
-   атрибут `xml:space` , действующий на элемент или на одного из его родителей, имеет значение по умолчанию.  
  
 Пример:  
  
```  
declare @x xml  
set @x = '<root>      <child/>     </root>'  
select @x   
```  
  
 Результат:  
  
```  
<root><child/></root>  
```  
  
 Однако можно изменить это поведение. Чтобы сохранить пробел для экземпляра xml DT, необходимо использовать оператор CONVERT и его дополнительный параметр *style* , установленный в значение 1. Пример:  
  
```  
SELECT CONVERT(xml, N'<root>      <child/>     </root>', 1)  
```  
  
 Если параметр *style* не используется или его значение установлено в 0, незначащий пробел не сохраняется для преобразования экземпляра xml DT. Дополнительные сведения о том, как использовать оператор CONVERT и его параметр *style* при преобразовании строковых данных в экземпляр xml DT, см. в статье [CAST и CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
### <a name="example-cast-a-string-value-to-typed-xml-and-assign-it-to-a-column"></a>Пример: приведение строкового значения к типизированному значению xml и присваивание его столбцу  
 В следующем примере приведена строковая переменная, содержащая фрагмент XML, в тип `xml` данных, а затем она сохраняется в столбце `xml` Type:  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
go  
DECLARE  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
```  
  
 Следующая операция вставки неявно преобразовывает строку в `xml` тип:  
  
```  
INSERT INTO T VALUES (3, @s)   
```  
  
 Можно явно привести строку () к `xml` типу:  
  
```  
INSERT INTO T VALUES (3, cast (@s as xml))  
```  
  
 Или можно использовать функцию convert(), как показано ниже:  
  
```  
INSERT INTO T VALUES (3, convert (xml, @s))   
```  
  
### <a name="example-convert-a-string-to-typed-xml-and-assign-it-to-a-variable"></a>Пример: преобразование строкового значения в типизированное значение xml и присваивание его переменной  
 В следующем примере строка преобразуется в `xml` тип и присваивается переменной типа `xml` данных:  
  
```  
declare @x xml  
declare  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
set @x =convert (xml, @s)  
select @x  
```  
  
## <a name="using-the-select-statement-with-a-for-xml-clause"></a>Использование инструкции SELECT с предложением FOR XML  
 Чтобы получить результаты в виде XML, можно использовать предложение FOR XML в инструкции SELECT. Пример:  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = (SELECT Column1, Column2  
               FROM   Table1, Table2  
               WHERE   Some condition  
               FOR XML AUTO)  
 ...  
```  
  
 Инструкция SELECT возвращает текстовый XML-фрагмент, который затем анализируется во время присваивания переменной типа `xml` данных.  
  
 Можно также использовать [директиву Type](type-directive-in-for-xml-queries.md) в предложении FOR XML, которая напрямую возвращает результат запроса FOR XML в виде `xml` типа:  
  
```  
Declare @xmlDoc xml  
SET @xmlDoc = (SELECT ProductModelID, Name  
               FROM   Production.ProductModel  
               WHERE  ProductModelID=19  
               FOR XML AUTO, TYPE)  
SELECT @xmlDoc  
```  
  
 Результат:  
  
```  
<Production.ProductModel ProductModelID="19" Name="Mountain-100" />...  
```  
  
 В следующем примере типизированный `xml` результат запроса FOR XML вставляется в столбец `xml` типа:  
  
```  
CREATE TABLE T1 (c1 int, c2 xml)  
go  
INSERT T1(c1, c2)  
SELECT 1, (SELECT ProductModelID, Name  
           FROM Production.ProductModel  
           WHERE ProductModelID=19  
           FOR XML AUTO, TYPE)  
SELECT * FROM T1  
go  
```  
  
 Дополнительные сведения о предложении FOR XML см. в статье [FOR XML (SQL Server)](for-xml-sql-server.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает экземпляры типа данных `xml` клиенту в результате выполнения различных серверных конструкций, таких как запросы FOR XML с директивой TYPE или запросы, в которых тип данных `xml` используется для возвращения XML из столбцов, переменных и выходных параметров SQL. В коде клиентского приложения поставщик ADO.NET требует, чтобы информация типа данных `xml` отправлялась сервером в двоичном представлении. Однако в запросах FOR XML без директивы TYPE XML-данные возвращаются в строковом формате. В любом случае поставщик клиента всегда будет иметь возможность обрабатывать XML-данные в любом из форматов.  
  
## <a name="using-constant-assignments"></a>Использование постоянных назначений  
 Строковая константа может использоваться там, где ожидается экземпляр `xml` типа данных. Это то же самое, что и неявное приведение (CAST) строки в XML. Пример:  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
-- Or  
SET @xmlDoc = N'<?xml version="1.0" encoding="ucs-2"?><doc/>'  
```  
  
 Предыдущий пример неявно преобразует строку в тип `xml` данных и присваивает ее переменной `xml` типа.  
  
 В следующем примере константная строка вставляется в `xml` столбец типа:  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
INSERT INTO T VALUES (3, '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>')   
```  
  
> [!NOTE]  
>  Для типизированного XML подлинность XML проверяется в отношении указанной схемы. Дополнительные сведения см. в статье [Сравнение типизированного и нетипизированного XML](compare-typed-xml-to-untyped-xml.md).  
  
## <a name="using-bulk-load"></a>Использование массовой загрузки  
 Улучшенная функциональность [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) позволяет произвести массовую загрузку XML-документов в базу данных. Можно выполнить массовый загрузку экземпляров XML из файлов в `xml` столбцы типа в базе данных. Дополнительные сведения см. в статье [Примеры массового импорта и экспорта XML-документов (SQL Server)](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md). Дополнительные сведения о загрузке XML-документов см. в статье [Загрузка XML-данных](load-xml-data.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Получение и запрос данных XML](retrieve-and-query-xml-data.md)|Описывает компоненты экземпляров XML, не фиксируемых при сохранении экземпляров в базах данных.|  
  
## <a name="see-also"></a>См. также:  
 [Сравнение типизированного и нетипизированного XML](compare-typed-xml-to-untyped-xml.md)   
 [методов типа данных xml](/sql/t-sql/xml/xml-data-type-methods)   
 [Язык модификации XML-данных (XML DML)](/sql/t-sql/xml/xml-data-modification-language-xml-dml)   
 [Данные XML (SQL Server)](xml-data-sql-server.md)  
  
  
