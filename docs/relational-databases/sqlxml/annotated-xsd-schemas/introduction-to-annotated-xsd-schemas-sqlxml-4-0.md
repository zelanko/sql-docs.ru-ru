---
title: Введение в аннотированные схемы XSD (S'LXML)
description: Узнайте о создании XML-представлений реляционных данных с помощью языка определения XML Schema (XSD) (S'LXML 4.0).
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- mapping schema [SQLXML], about mapping schema
- views [SQLXML]
- valid XSD schemas [SQLXML]
- annotations [SQLXML]
- XSD schemas [SQLXML], creating XML views
- annotated XSD schemas, creating XML views
- minimum XSD schema
- annotated XSD schemas, examples
- XML views [SQLXML]
ms.assetid: 15282db1-65c4-43be-bdb7-e9ef49cb33a2
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c165ca271c3230399d54363f22d2b220e5427830
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388655"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a>Введение в схемы XSD с заметками (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Можно создавать представления схем XML реляционных данных при помощи языка XSD. Затем можно выполнять запросы к этим представлениям при помощи языка XPath (XML Path). Это аналогично созданию представлений с помощью инструкции CREATE VIEW с последующим указанием запросов SQL к представлению.  
  
 Схема XML описывает структуру XML-документа, а также описывает различные ограничения на данные, содержащиеся в документе. При задании запросов XPath по схеме структура возвращаемого XML-документа определяется согласно схеме, по которой выполняется запрос XPath.  
  
 В схеме ** \<XSD элемент xsd:schema>** огражет всю схему; все объявления элементов должны содержаться в ** \<элементе xsd:schema>.** Можно описать атрибуты, определяющие пространство имен, в котором находится схема, и области имен, используемые в схеме, как свойства ** \<элемента xsd:schema>** элемент.  
  
 Действительная схема XSD должна содержать ** \<элемент xsd:schema>,** определяемый следующим образом:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 Элемент ** \<xsd:schema>** происходит от спецификации пространства имен XML Schema в http://www.w3.org/2001/XMLSchema.  
  
## <a name="annotations-to-the-xsd-schema"></a>Заметки к схеме XSD  
 Можно использовать схему XSD с заметками, которые описывают сопоставление с базой данных, запрашивают базу данных, а затем возвращают результаты в форме XML-документа. Заметки служат для сопоставления схемы XSD с таблицами и столбцами базы данных. Можно указывать запросы XPath к представлениям XML, созданным на основе схемы XSD, для запроса базы данных и получения результатов в виде XML.  
  
> [!NOTE]  
>  В [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 язык схем XSD поддерживает заметки, введенные в языке схем XDR в [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]. Схемы XDR с заметками в SQLXML 4.0 считаются устаревшими.  
  
 В контексте реляционной базы данных полезно сопоставить произвольную схему XSD с реляционным хранилищем. Один из способов достижения этого состоит в создании аннотированной схемы XSD. Схема XSD с аннотациями называется *схемой отображения,* которая предоставляет информацию, относящуюся к тому, как данные XML должны быть отображены в реляционном хранилище. По сути, схема сопоставления является XML-представлением реляционных данных. Эти сопоставления позволяют получать реляционные данные в виде XML-документа.  
  
## <a name="namespace-for-annotations"></a>Пространства имен для заметок  
 В схеме XSD аннотации указаны с помощью урны для **имен:schemas-microsoft-com:mapping-schema.** Как показано в следующем примере, самый простой способ указать пространство имен — указать его в ** \<теге xsd:schema>.**  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 Префикс пространства имен может быть произвольным. В этой документации префикс **sql** используется для обозначения пространства имен аннотации и различения аннотаций в этом пространстве имен от аннотаций в других областях имен.  
  
## <a name="example-of-an-annotated-xsd-schema"></a>Пример схемы XSD с заметками  
 В следующем примере схема XSD состоит из элемента ** \<Person.Contact>.** Элемент ** \<>сотрудника** имеет атрибут **ContactID** и ** \<элементы FirstName>** и ** \<LastName>** ребенка:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <xsd:element name="Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     type="xsd:string" />   
        <xsd:element name="LName"  
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 К схеме XSD добавляются заметки, что позволяет сопоставить ее элементы и атрибуты с именами таблиц и столбцов базы данных:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID"   
                       sql:field="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 В схеме отображения элемент ** \<контактного>** отображается на таблице Person.Contact в базе данных AdventureWorks с помощью аннотации **sql:relation.** Атрибуты ConID, FName и LName отображаются в столбцах ContactID, FirstName и LastName в таблице Person.Contact с помощью аннотаций **sql:field.**  
  
 Эта аннотированная схема XSD создает XML-представление реляционных данных. Затем можно выполнять запросы XPath к этому XML-представлению. Запрос XPath возвращает в качестве результата XML-документ в отличие от запросов SQL, которые возвращают наборы строк.  
  
> [!NOTE]  
>  В схеме сопоставления чувствительность к регистру для указанных реляционных значений (таких как имя таблицы или столбца) зависит от того, использует ли SQL Server чувствительные к регистру параметры сортировки. Дополнительные сведения см. в статье [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="other-resources"></a>Другие ресурсы  
 Дополнительные сведения о языке XSD, языке XPath и преобразованиях XSLT находятся на следующих веб-сайтах.  
  
-   XML Схема Часть 0: Праймер, Рекомендация W3C (https://www.w3.org/TR/xmlschema-0/)  
  
-   XML Схема Часть 1: Структуры, Рекомендация W3C (https://www.w3.org/TR/xmlschema-1/)  
  
-   XML Схема Часть 2:Datatypes, Рекомендация W3C (https://www.w3.org/TR/xmlschema-2/)  
  
-   XML Язык Пути (XPath) (https://www.w3.org/TR/xpath)  
  
-   XSL Преобразования (XSLT) (https://www.w3.org/TR/xslt)  
  
## <a name="see-also"></a>См. также:  
 [Аннотированные соображения безопасности схемы &#40;S'LXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)   
 [Аннотированные XDR Schemas &#40;утомлены в S'LXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
