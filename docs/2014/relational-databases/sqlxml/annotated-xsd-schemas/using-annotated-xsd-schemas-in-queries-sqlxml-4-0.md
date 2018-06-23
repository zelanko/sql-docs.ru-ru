---
title: С помощью аннотированные схемы XSD в запросах (SQLXML 4.0) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bfd947684010ed0d71bdce44f329ccc1f0f34917
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193327"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>Использование схем XSD с заметками в запросах (SQLXML 4.0)
  Для получения данных из базы данных путем указания запроса XPath в шаблоне к схеме XSD можно задавать запросы к аннотированным схемам.  
  
 **\<Sql:xpath-запрос >** элемент позволяет указать запрос XPath к XML-представлению, определенному схемой с заметками. Аннотированной схемы, по которой запрос XPath должно быть выполнено определяется с помощью `mapping-schema` атрибут  **\<sql:xpath-запрос >** элемента.  
  
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
  
 Затем можно создать и запустить тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить запрос, содержащийся в файле шаблона. Дополнительные сведения см. в разделе [аннотированные схемы XDR &#40;в SQLXML 4.0&#41;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="using-inline-mapping-schemas"></a>Использование встроенных схем сопоставления  
 Аннотированную схему можно включить непосредственно в шаблон, а затем выполнить определенный в шаблоне запрос XPath к встроенной схеме. Шаблон может также быть диаграммой обновления.  
  
 Шаблон может включать несколько встроенных схем. Чтобы использовать встроенную схему, включенной в шаблон, укажите **идентификатор** с уникальным значением для атрибута  **\<xsd: schema >** элемент, а затем использовать **#idvalue**для ссылки на встроенную схему. **Идентификатор** атрибут идентичен в поведении **SQL: ID** ({urn: schemas-microsoft-com: XML-sql} id) используется в схемах XDR.  
  
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
  
 В шаблоне также задано два запроса XPath. Каждый из  **\<запрос xpath >** элементы уникальным образом идентифицирует схему сопоставления, указав `mapping-schema` атрибута.  
  
 При указании встроенную схему в шаблоне, `sql:is-mapping-schema` заметка также должна быть указана на  **\<xsd: schema >** элемента. Заметка `sql:is-mapping-schema` имеет логическое значение (0 = false, 1 = true). Встроенная схема с **sql: является mapping-schema = «1»** обрабатывается как встроенная Аннотированная схема и не возвращается в XML-документе.  
  
 Заметка `sql:is-mapping-schema` принадлежит пространству имен шаблона `urn:schemas-microsoft-com:xml-sql`.  
  
 Чтобы протестировать этот пример, сохраните шаблон (InlineSchemaTemplate.xml) в локальном каталоге, а затем создайте и выполните тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) для запуска шаблона. Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML 4.0](../using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Помимо указания `mapping-schema` атрибут  **\<sql:xpath-запрос >** элемент в шаблоне (при наличии запроса XPath) или на  **\<updg:sync >** элемент в диаграмме обновления можно сделать следующее:  
  
-   Укажите `mapping-schema` атрибут  **\<КОРНЕВОЙ >** элемента (глобальная декларация) в шаблоне. Теперь эта схема сопоставления стала схемой по умолчанию и будет использоваться всеми узлами XPath и диаграммами обновления без явного указания заметки `mapping-schema`.  
  
-   Укажите атрибут `mapping schema` с помощью объекта `Command` ADO.  
  
 `mapping-schema` Атрибуты, которые указаны на  **\<запрос xpath >** или  **\<updg:sync >** элемент имеет самый высокий приоритет; ADO `Command` объект имеет самый низкий приоритет.  
  
 Обратите внимание, что если указать запрос XPath в шаблоне и не задана схема сопоставления, по которой выполняется запрос XPath, запрос XPath обрабатывается как **dbobject** тип запроса. Например, рассмотрим следующий шаблон.  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 В шаблоне определяется запрос XPath, но не задаются схемы сопоставления. Таким образом, этот запрос обрабатывается как **dbobject** тип запроса, в котором Production.ProductPhoto — имя таблицы и @ProductPhotoID= '100' — предикат, который находит фотографию продукта со значением идентификатора 100. @LargePhoto — столбец, из которого требуется извлечь значение.  
  
  