---
title: Использование схем XSD с заметками в запросах (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML]
- inline schemas [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- queries [SQLXML], annotated XSD schemas
- retrieving data
- mapping schema [SQLXML], queries
- multiple inline schemas
- annotated XSD schemas, queries
- XSD schemas [SQLXML], queries
- templates [SQLXML], annotated XSD schemas in queries
ms.assetid: 927a30a2-eae8-420d-851d-551c5f884f3c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c435ff3bacecb101784695fe42b8b2158625e058
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66014468"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>Использование схем XSD с заметками в запросах (SQLXML 4.0)
  Для получения данных из базы данных путем указания запроса XPath в шаблоне к схеме XSD можно задавать запросы к аннотированным схемам.  
  
 Элемент ** \<>SQL: XPath-Query** позволяет указать запрос XPath к XML-представлению, определяемому схемой с заметками. Схема с заметками, в которой выполняется запрос XPath, определяется с помощью `mapping-schema` атрибута элемента ** \<SQL: XPath-Query>** .  
  
 Шаблоны являются допустимыми XML-документами, которые содержат один или несколько запросов. Запросы FOR XML и XPath возвращают фрагмент документа. Шаблоны выполняют функцию контейнеров для фрагментов документов. Таким образом, они обеспечивают возможность указания единственного элемента верхнего уровня.  
  
 В примерах из этого раздела шаблоны задают запрос XPath по схеме с заметками для получения данных из базы данных.  
  
 В качестве примера рассмотрим следующую аннотированную схему.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID" type="xsd:string" />   
       <xsd:attribute name="FirstName" type="xsd:string" />   
       <xsd:attribute name="LastName"  type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Для иллюстрации эта схема XSD хранится в файле Schema2.xml. Затем можно выполнить запрос XPath к аннотированной схеме, определенной в следующем файле шаблона (Schema2T.xml).  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql"  
     >  
          Person.Contact[@ContactID="1"]  
</sql:xpath-query>  
```  
  
 Затем можно создать и запустить тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить запрос, содержащийся в файле шаблона. Дополнительные сведения см. [в разделе схемы XDR с Заметками &#40;не рекомендуется в SQLXML 4,0&#41;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="using-inline-mapping-schemas"></a>Использование встроенных схем сопоставления  
 Аннотированную схему можно включить непосредственно в шаблон, а затем выполнить определенный в шаблоне запрос XPath к встроенной схеме. Шаблон может также быть диаграммой обновления.  
  
 Шаблон может включать несколько встроенных схем. Чтобы использовать встроенную схему, включенную в шаблон, укажите атрибут **ID** с уникальным значением в элементе ** \<XSD: schema>** , а затем используйте **#idvalue** для ссылки на встроенную схему. Атрибут **ID** идентичен поведению **SQL: ID** ({URN: schemas-microsoft-com: XML-SQL} ID), используемому в схемах XDR.  
  
 Например, следующий шаблон определяет две встроенные аннотированные схемы.  
  
```  
<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema1' sql:is-mapping-schema='1'>  
  <xsd:element name='Employees' ms:relation='HumanResources.Employee'>  
    <xsd:complexType>  
      <xsd:attribute name='LoginID'   
                     type='xsd:string'/>  
      <xsd:attribute name='Title'   
                     type='xsd:string'/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema2' sql:is-mapping-schema='1'>  
  <xsd:element name='Contacts' ms:relation='Person.Contact'>  
    <xsd:complexType>  
  
      <xsd:attribute name='ContactID'   
                     type='xsd:string' />  
      <xsd:attribute name='FirstName'   
                     type='xsd:string' />  
      <xsd:attribute name='LastName'   
                     type='xsd:string' />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema1'>  
    /Employees[@LoginID='adventure-works\guy1']  
</sql:xpath-query>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema2'>  
    /Contacts[@ContactID='1']  
</sql:xpath-query>  
</ROOT>  
```  
  
 В шаблоне также задано два запроса XPath. Каждый элемент ** \<>XPath-Query** однозначно определяет схему сопоставления, указывая `mapping-schema` атрибут.  
  
 При указании встроенной схемы в шаблоне `sql:is-mapping-schema` заметка также должна быть указана в элементе ** \<XSD: schema>** . Заметка `sql:is-mapping-schema` имеет логическое значение (0 = false, 1 = true). Встроенная схема с **SQL: schema-Mapping-Schema = "1"** рассматривается как встроенная схема с заметками и не возвращается в XML-документе.  
  
 Заметка `sql:is-mapping-schema` принадлежит пространству имен шаблона `urn:schemas-microsoft-com:xml-sql`.  
  
 Чтобы протестировать этот пример, сохраните шаблон (InlineSchemaTemplate.xml) в локальном каталоге, а затем создайте и выполните тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) для запуска шаблона. Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML 4,0](../using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Помимо указания `mapping-schema` атрибута в элементе ** \<SQL: XPath-Query>** в шаблоне (при наличии запроса XPath) или в ** \<элементе атрибута updg: Sync>** в диаграмма обновления можно выполнять следующие действия.  
  
-   Укажите `mapping-schema` атрибут для ** \<корневого элемента>** (глобальное объявление) в шаблоне. Теперь эта схема сопоставления стала схемой по умолчанию и будет использоваться всеми узлами XPath и диаграммами обновления без явного указания заметки `mapping-schema`.  
  
-   Укажите атрибут `mapping schema` с помощью объекта `Command` ADO.  
  
 `mapping-schema` Атрибут, указанный в элементе ** \<XPath-Query>** или ** \<атрибута updg: Sync>** , имеет наивысший приоритет. объект ADO `Command` имеет самый низкий приоритет.  
  
 Обратите внимание, что если вы укажете запрос XPath в шаблоне и не укажете схему сопоставления, в которой выполняется запрос XPath, запрос XPath рассматривается как запрос типа **DBOBJECT** . Например, рассмотрим следующий шаблон.  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 В шаблоне определяется запрос XPath, но не задаются схемы сопоставления. Поэтому этот запрос рассматривается как запрос типа **DBOBJECT** , в котором Production. ProductPhoto — это имя таблицы, а @ProductPhotoID= "100" — это предикат, который находит ФОТОГРАФИЮ продукта со значением идентификатора 100. @LargePhotoстолбец, из которого извлекается значение.  
  
  
