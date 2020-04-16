---
title: Использование аннотированных схем XSD в запросах (S'LXML)
description: Узнайте, как указать запросы XPath в отношении аннотированной схемы XSD в S'LXML 4.0 для извлечения данных из базы данных.
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e9ecd9d65d0f70f7c25328c15bb886ca52122de2
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388682"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>Использование схем XSD с заметками в запросах (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Для получения данных из базы данных путем указания запроса XPath в шаблоне к схеме XSD можно задавать запросы к аннотированным схемам.  
  
 Элемент ** \<>sl:xpath** позволяет указать запрос XPath в отношении представления XML, определяемого аннотированной схемой. Аннотированная схема, на основе которой должен выполняться запрос XPath, идентифицируется с помощью атрибута **схемы отображения** ** \<>элемента sql:xpath-query.**  
  
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
  
 Затем можно создать и запустить тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить запрос, содержащийся в файле шаблона. Для получения дополнительной информации см. [Аннотированные XDR Schemas &#40;Deprecated в S'LXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="using-inline-mapping-schemas"></a>Использование встроенных схем сопоставления  
 Аннотированную схему можно включить непосредственно в шаблон, а затем выполнить определенный в шаблоне запрос XPath к встроенной схеме. Шаблон может также быть диаграммой обновления.  
  
 Шаблон может включать несколько встроенных схем. Чтобы использовать входящие схемы, которые включены в шаблон, укажите атрибут **идентификатора** с уникальным значением на ** \<элементе xsd:schema>,** а затем используйте **#idvalue** для ссылки на входящие схемы. Атрибут **идентификатора** идентичен по поведению **к sql:id** (зурн:schemas-microsoft-com:xml-sql) используется в схемах XDR.  
  
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
  
 В шаблоне также задано два запроса XPath. Каждый из элементов ** \<xpath-запроса>** однозначно определяет схему отображения, указывая атрибут **схемы отображения.**  
  
 При указании в шаблоне вневленной схемы должна быть также указана аннотация **sql:is-mapping-schema** также должна быть указана на элементе ** \<xsd:schema>** элемент. **Sql:is-mapping-schema** принимает значение Boolean (0'false, 1'true). Встраиваемый в рядовой схему с **sql:is-mapping-schema»1"** рассматривается как рядная аннотированная схема и не возвращается в документxML.  
  
 **Sql:is-mapping-schema** аннотация принадлежит к урне пространства имен **шаблона:schemas-microsoft-com:xml-sql**.  
  
 Чтобы протестировать этот пример, сохраните шаблон (InlineSchemaTemplate.xml) в локальном каталоге, а затем создайте и выполните тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) для запуска шаблона. Для получения дополнительной [информации см.](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)  
  
 В дополнение к указанию **атрибута схемы отображения** на ** \<sql:xpath-запрос>** элементом в шаблоне (когда есть запрос XPath), или на ** \<updg:sync>** элементв в updategram, вы можете сделать следующее:  
  
-   Укажите атрибут **отображения-схему** на элементе ** \<ROOT>** (глобальная декларация) в шаблоне. Затем эта схема отображения становится схемой по умолчанию, которая будет использоваться всеми узлами XPath и updategram, которые не имеют явной аннотации **схемы отображения.**  
  
-   Укажите атрибут **схемы отображения** с помощью объекта **ADO Command.**  
  
 Атрибут **отображения-схема,** указанный в ** \<>xpath-запроса** или ** \<updg:sync>** элемент имеет наивысший приоритет; Объект **командования** ADO имеет наименьший приоритет.  
  
 Обратите внимание, что если вы указываете запрос XPath в шаблоне и не указываете схему отображения, на основе которой выполняется запрос XPath, запрос XPath рассматривается как запрос типа **dbobject.** Например, рассмотрим следующий шаблон.  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 В шаблоне определяется запрос XPath, но не задаются схемы сопоставления. Таким образом, этот запрос рассматривается как запрос типа **dbobject,** в котором @ProductPhotoIDProduction.ProductPhoto является названием таблицы, а «100» — предикатом, который находит фотографию продукта со значением ID 100. @LargePhoto— это столбец, из которого можно получить значение.  
  
  
