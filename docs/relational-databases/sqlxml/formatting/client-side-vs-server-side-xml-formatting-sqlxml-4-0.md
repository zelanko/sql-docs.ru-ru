---
title: Сравнение запроса XPath на стороне клиента и Форматирование серверные XML (SQLXML 4.0) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- FOR XML clause, formatting
- client-side XML formatting
- server-side XPath
- server-side XML formatting
- AUTO mode
- client-side XPath
ms.assetid: f807ab7a-c5f8-4e61-9b00-23aebfabc47e
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4d36a49c44ea4dfb7ca89c9598ccaf74b1a32ba8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="client-side-vs-server-side-xml-formatting-sqlxml-40"></a>Сравнение запроса XPath на стороне клиента и Форматирование XML-кода на сервере (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом разделе описываются основные различия между форматированием XML-кода в SQLXML на стороне клиента и на стороне сервера.  
  
## <a name="multiple-rowset-queries-not-supported-in-client-side-formatting"></a>Запросы к нескольким наборам строк не поддерживаются при форматировании на стороне клиента  
 Запросы, создающие несколько наборов строк, не поддерживаются при использовании форматирования XML-кода на стороне клиента. Например, предположим, что имеется виртуальный каталог, в котором определено форматирование на стороне клиента. Рассмотрим этот образец шаблона, который имеет две инструкции SELECT в  **\<sql:query >** блока:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
     SELECT FirstName FROM Person.Contact FOR XML Nested;   
     SELECT LastName FROM Person.Contact FOR XML Nested    
  </sql:query>  
</ROOT>  
```  
  
 При выполнении данного шаблона в коде приложения возвращается ошибка, так как форматирование XML-кода на стороне клиента не поддерживает форматирование нескольких наборов строк. При указании запросов в двух отделить  **\<sql:query >** блоки, вы получите желаемые результаты.  
  
## <a name="timestamp-maps-differently-in-client--vs-server-side-formatting"></a>Различное сопоставление типа timestamp при форматировании на стороне клиента и на стороне сервера  
 В XML на стороне сервера, форматирование столбца базы данных из **timestamp** тип сопоставляется с типом XDR i8 (Если параметр XMLDATA указан в запросе).  
  
 В XML на стороне клиента форматирование столбца базы данных из **отметка времени** сопоставляется либо **uri** или **bin.base64** тип XDR (в зависимости от того, следует ли binary base64 параметр указан в запросе). **Bin.base64** XDR тип полезен при использовании функции диаграммы обновления и массовой загрузки, так как этот тип преобразуется в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **timestamp** типа. Таким образом, операции вставки, обновления или удаления выполняются успешно.  
  
## <a name="deep-variants-are-used-in-server-side-formatting"></a>При форматировании на стороне сервера используются глубокие типы VARIANT  
 При форматировании XML-кода на стороне сервера используются глубокие типы VARIANT. При форматировании XML-кода на стороне клиента подтипы VARIANT преобразуются в строку в Юникоде, а вложенные типы VARIANT не используются.  
  
## <a name="nested-mode-vs-auto-mode"></a>Сравнение режима NESTED и режима AUTO  
 Режим NESTED предложения FOR XML на стороне клиента аналогичен режиму AUTO предложения FOR XML на стороне сервера, за исключением следующих моментов.  
  
### <a name="when-you-query-views-using-auto-mode-on-the-server-side-the-view-name-is-returned-as-the-element-name-in-the-resulting-xml"></a>При представлении запроса с помощью режима AUTO на стороне сервера имя представления возвращается в виде имени элемента в результирующем XML-коде  
 Например предположим, что следующее представление создается для таблицы Person.Contact в AdventureWorksdatabase:  
  
```  
CREATE VIEW ContactView AS (SELECT ContactID as CID,  
                               FirstName  as FName,  
                               LastName  as LName  
                        FROM Person.Contact)  
```  
  
 Следующий шаблон указывает запрос к представлению ContactView, а также форматирование XML-кода на стороне сервера:  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT *  
    FROM   ContactView  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 После применения этого шаблона возвращается следующий XML-код (приведены частичные результаты). Обратите внимание, что имена элементов — это имена представлений, к которым выполняется запрос.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ContactView CID="1" FName="Gustavo" LName="Achong" />   
  <ContactView CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
 При форматировании XML-кода на стороне сервера в режиме NESTED имена базовой таблицы возвращаются в виде имен элементов в результирующем XML-коде. Например, следующий измененный шаблон выполняет инструкцию SELECT, но XML-форматирование выполняется на стороне клиента (то есть **client-side-xml** присвоено значение true, если в шаблоне):  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT *  
    FROM   ContactView  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 В результате применения этого шаблона создается следующий XML-код. Обратите внимание, что именем элемента в этом случае является имя базовой таблицы.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact CID="1" FName="Gustavo" LName="Achong" />   
  <Person.Contact CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
### <a name="when-you-use-auto-mode-of-the-server-side-for-xml-the-table-aliases-specified-in-the-query-are-returned-as-element-names-in-the-resulting-xml"></a>При использовании режима AUTO предложения FOR XML на стороне сервера, псевдонимы таблиц, указанные в запросе, возвращаются в виде имен элементов в результирующем XML-коде  
 Например, рассмотрим следующий шаблон.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 В результате выполнения этого шаблона создается следующий XML-код.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <C fname="Gustavo" lname="Achong" />   
  <C fname="Catherine" lname="Abel" />   
...  
</ROOT>   
```  
  
 При использовании режима NESTED предложения FOR XML на стороне клиента, имена таблиц возвращаются в виде имен элементов в результирующем XML-коде. (Псевдонимы таблиц, указанные в запросе, не используются.) Например, рассмотрим следующий шаблон.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 В результате выполнения этого шаблона создается следующий XML-код.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact fname="Gustavo" lname="Achong" />   
  <Person.Contact fname="Catherine" lname="Abel" />   
...  
</ROOT>  
```  
  
### <a name="if-you-have-a-query-that-returns-columns-as-dbobject-queries-you-cannot-use-aliases-for-these-columns"></a>При наличии запроса, возвращающего столбцы в виде запросов объектов базы данных, использовать псевдонимы для этих столбцов нельзя  
 Например, рассмотрим следующий шаблон, выполняющий запрос, который возвращает идентификатор и фотографию сотрудника.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query client-side-xml="1">  
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML NESTED, elements  
</sql:query>  
</ROOT>  
```  
  
 Выполнение этого шаблона возвращает столбец Photo в виде запроса объекта базы данных. В запросе объекта базы данных `@P` ссылается на имя несуществующего столбца.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@P</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
 Если XML-форматирование выполняется на сервере (**client-side-xml = «0»**), можно использовать псевдоним для столбцов, возвращающих запросы, в фактический таблицу и столбец имен возвращаются (даже при наличии указанных псевдонимов). Например, следующий шаблон выполняет запрос и XML-форматирование выполняется на сервере ( **client-side-xml** параметр не указан и **Run On Client** параметр не выбран для виртуального корневого каталога). Запрос также указывает режим AUTO (а не режим NESTED на стороне клиента).  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query   
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML AUTO, elements  
</sql:query>  
</ROOT>  
```  
  
 При применении этого шаблона возвращается следующий XML-документ (обратите внимание, что псевдонимы в запросе объектов базы данных для столбца LargePhoto не используются):  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@LargePhoto</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
### <a name="client-side-vs-server-side-xpath"></a>Сравнение запроса XPath на стороне клиента и на стороне сервера  
 Запросы XPath на стороне клиента и на стороне сервера работают аналогично, за исключением следующих моментов.  
  
-   Преобразования данных, применяемые при использовании запросов XPath на стороне клиента, отличаются от применяемых при использовании запросов XPath на стороне сервера. Запрос XPath на стороне клиента использует функцию CAST вместо CONVERT mode 126.  
  
-   При указании **client-side-xml = «0»** (false) в шаблоне, запрашивается форматирование XML на стороне сервера. Таким образом, нельзя указать предложение FOR XML NESTED, так как сервер не распознает параметр NESTED. Это приводит к ошибке. Необходимо использовать режимы AUTO, RAW или EXPLICIT, которые сервер распознает.  
  
-   При указании **client-side-xml = «1»** (true) в шаблоне, запрашивается форматирование XML на стороне клиента. В этом случае можно указать предложение FOR XML NESTED. При указании FOR XML AUTO форматирование XML-кода происходит на серверной стороне хотя **client-side-xml = «1»** указанные в шаблоне.  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности FOR XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md)   
 [Форматирование XML на стороне клиента &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)   
 [Форматирование XML на стороне сервера &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/server-side-xml-formatting-sqlxml-4-0.md)  
  
  
