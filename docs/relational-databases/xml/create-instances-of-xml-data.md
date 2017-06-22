---
title: "Создание экземпляров XML-данных | Документация Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d02273b721b1b75b7bd134c8cd50c94ed2e9848d
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="create-instances-of-xml-data"></a>Создание экземпляров XML-данных
  В этом разделе описывается формирование XML-экземпляров.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]сформировать XML-экземпляры можно следующими способами:  
  
-   тип экземпляров приведения строки;  
  
-   использование инструкции SELECT с предложением FOR XML;  
  
-   использование постоянных назначений;  
  
-   использование массовой загрузки.  
  
## <a name="type-casting-string-and-binary-instances"></a>Строка приведения типа и двоичные экземпляры  
 Любые строковые типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , такие как [**n**][**var**]**char**, **[n]text**, **varbinary**и **image**, можно проанализировать в тип данных **xml** посредством приведения (CAST) или преобразования (CONVERT) строки к типу данных **xml** . Проверка нетипизированного XML подтверждает, что он сформирован правильно. Если есть схема, связанная с типом **xml** , также выполняется проверка. Дополнительные сведения см. в статье [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
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
 Если определяемый пользователем тип данных CLR имеет XML-сериализацию, экземпляры этого типа могут быть явно приведены к типу данных XML. Более подробные сведения о XML-сериализации определяемого пользователем типа данных CLR см. в статье [Сериализация XML из объектов базы данных CLR](http://msdn.microsoft.com/library/ac84339b-9384-4710-bebc-01607864a344).  
  
### <a name="white-space-handling-in-typed-xml"></a>Обработка пробела в типизированном XML  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пробел внутри содержимого элемента считается незначащим, если он появляется внутри последовательности данных, содержащей только пробельные символы, разделенных разметкой, например начальными и конечными тегами. Такой пробел не преобразуется в сущность. (секции CDATA игнорируются). Данная обработка пробела отличается от пробела, описанного в спецификации XML 1.0, опубликованной консорциумом World Wide Web (W3C). Это происходит потому, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средство синтаксического анализа XML распознает только ограниченное число подмножеств DTD, как указано в XML 1.0. Дополнительные сведения об ограниченных подмножествах DTD, поддерживаемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
 Синтаксический XML-анализатор отменяет незначащие пробелы при преобразовании строковых данных в XML по умолчанию, если выполняется одно из следующих условий:  
  
-   `The xml:space` не определен на элементе или его родителях;  
  
-   атрибут `xml:space` , действующий на элемент или на одного из его родителей, имеет значение по умолчанию.  
  
 Например:  
  
```  
declare @x xml  
set @x = '<root>      <child/>     </root>'  
select @x   
```  
  
 Результат:  
  
```  
<root><child/></root>  
```  
  
 Однако можно изменить это поведение. Чтобы сохранить пробел для экземпляра xml DT, необходимо использовать оператор CONVERT и его дополнительный параметр *style* , установленный в значение 1. Например:  
  
```  
SELECT CONVERT(xml, N'<root>      <child/>     </root>', 1)  
```  
  
 Если параметр *style* не используется или его значение установлено в 0, незначащий пробел не сохраняется для преобразования экземпляра xml DT. Дополнительные сведения о том, как использовать оператор CONVERT и его параметр *style* при преобразовании строковых данных в экземпляр xml DT, см. в статье [CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
### <a name="example-cast-a-string-value-to-typed-xml-and-assign-it-to-a-column"></a>Пример: приведение строкового значения к типизированному значению xml и присваивание его столбцу  
 Следующий пример приводит строковую переменную, содержащую фрагмент XML, в тип данных **xml** и затем сохраняет его в **xml** -столбец:  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
go  
DECLARE  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
```  
  
 Следующая операция вставки неявно преобразовывает строку в тип **xml** :  
  
```  
INSERT INTO T VALUES (3, @s)   
```  
  
 Можно применить функцию cast() для явного приведения строки в тип **xml** :  
  
```  
INSERT INTO T VALUES (3, cast (@s as xml))  
```  
  
 Или можно использовать функцию convert(), как показано ниже:  
  
```  
INSERT INTO T VALUES (3, convert (xml, @s))   
```  
  
### <a name="example-convert-a-string-to-typed-xml-and-assign-it-to-a-variable"></a>Пример: преобразование строкового значения в типизированное значение xml и присваивание его переменной  
 В следующем примере строка преобразовывается в тип **xml** и присваивается переменной типа **xml** :  
  
```  
declare @x xml  
declare  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
set @x =convert (xml, @s)  
select @x  
```  
  
## <a name="using-the-select-statement-with-a-for-xml-clause"></a>Использование инструкции SELECT с предложением FOR XML  
 Чтобы получить результаты в виде XML, можно использовать предложение FOR XML в инструкции SELECT. Например:  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = (SELECT Column1, Column2  
               FROM   Table1, Table2  
               WHERE   Some condition  
               FOR XML AUTO)  
 ...  
```  
  
 Инструкция SELECT возвращает текстовый XML-фрагмент, который затем анализируется в процессе присвоения переменной типа **xml** .  
  
 Также можно использовать [директиву TYPE](../../relational-databases/xml/type-directive-in-for-xml-queries.md) в предложении FOR XML, которая непосредственно возвращает результат запроса FOR XML в виде **xml** -данных:  
  
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
  
 В следующем примере типизированный результат **xml** -запроса FOR XML вставляется в **xml** -столбец:  
  
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
  
 Дополнительные сведения о предложении FOR XML см. в статье [FOR XML (SQL Server)](../../relational-databases/xml/for-xml-sql-server.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает экземпляры типа данных **xml** клиенту в результате выполнения различных серверных конструкций, таких как запросы FOR XML с директивой TYPE или запросы, в которых тип данных **xml** используется для возвращения XML из столбцов, переменных и выходных параметров SQL. В коде клиентского приложения поставщик ADO.NET требует, чтобы информация типа данных **xml** отправлялась сервером в двоичном представлении. Однако в запросах FOR XML без директивы TYPE XML-данные возвращаются в строковом формате. В любом случае поставщик клиента всегда будет иметь возможность обрабатывать XML-данные в любом из форматов.  
  
## <a name="using-constant-assignments"></a>Использование постоянных назначений  
 Строковая константа может быть использована там, где ожидается экземпляр **xml** -типа. Это то же самое, что и неявное приведение (CAST) строки в XML. Например:  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
-- Or  
SET @xmlDoc = N'<?xml version="1.0" encoding="ucs-2"?><doc/>'  
```  
  
 Предыдущий пример неявно преобразовывает строку в тип **xml** и присваивает его **xml** -переменной.  
  
 Следующий пример вставляет строковую константу в **xml** -столбец:  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
INSERT INTO T VALUES (3, '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>')   
```  
  
> [!NOTE]  
>  Для типизированного XML подлинность XML проверяется в отношении указанной схемы. Дополнительные сведения см. в статье [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="using-bulk-load"></a>Использование массовой загрузки  
 Улучшенная функциональность [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md) позволяет произвести массовую загрузку XML-документов в базу данных. Можно выполнить массовую загрузку XML-экземпляров из файлов в **xml** -столбец базы данных. Дополнительные сведения см. в статье [Примеры массового импорта и экспорта XML-документов (SQL Server)](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md). Дополнительные сведения о загрузке XML-документов см. в статье [Загрузка XML-данных](../../relational-databases/xml/load-xml-data.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Получение и запрос XML-данных](../../relational-databases/xml/retrieve-and-query-xml-data.md)|Описывает компоненты экземпляров XML, не фиксируемых при сохранении экземпляров в базах данных.|  
  
## <a name="see-also"></a>См. также:  
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Методы типа данных XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных (XML DML)](../../t-sql/xml/xml-data-modification-language-xml-dml.md)   
 [Данные XML (SQL Server)](../../relational-databases/xml/xml-data-sql-server.md)  
  
  
