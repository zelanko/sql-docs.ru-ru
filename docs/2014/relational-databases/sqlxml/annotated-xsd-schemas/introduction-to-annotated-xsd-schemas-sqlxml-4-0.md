---
title: Общие сведения о схемах XSD с заметками (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: d8813d34f2c669e9646b899230388fca649e4488
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66014460"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a>Введение в схемы XSD с заметками (SQLXML 4.0)
  Можно создавать представления схем XML реляционных данных при помощи языка XSD. Затем можно выполнять запросы к этим представлениям при помощи языка XPath (XML Path). Это аналогично созданию представлений с помощью инструкции CREATE VIEW с последующим указанием запросов SQL к представлению.  
  
 Схема XML описывает структуру XML-документа, а также описывает различные ограничения на данные, содержащиеся в документе. При задании запросов XPath по схеме структура возвращаемого XML-документа определяется согласно схеме, по которой выполняется запрос XPath.  
  
 В схеме XSD элемент ** \<XSD: schema>** включает всю схему; Все объявления элементов должны содержаться в элементе ** \<XSD: schema>** . Можно описать атрибуты, определяющие пространство имен, в котором находится схема, и пространства имен, используемые в схеме в качестве свойств элемента ** \<XSD: schema>** .  
  
 Допустимая схема XSD должна содержать элемент ** \<XSD: schema>** , определенный следующим образом:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 Элемент ** \<XSD: schema>** является производным от спецификации пространства имен схемы XML в http://www.w3.org/2001/XMLSchema.  
  
## <a name="annotations-to-the-xsd-schema"></a>Заметки к схеме XSD  
 Можно использовать схему XSD с заметками, которые описывают сопоставление с базой данных, запрашивают базу данных, а затем возвращают результаты в форме XML-документа. Заметки служат для сопоставления схемы XSD с таблицами и столбцами базы данных. Можно указывать запросы XPath к представлениям XML, созданным на основе схемы XSD, для запроса базы данных и получения результатов в виде XML.  
  
> [!NOTE]  
>  В [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 язык схем XSD поддерживает заметки, введенные в языке схем XDR в [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]. Схемы XDR с заметками в SQLXML 4.0 считаются устаревшими.  
  
 В контексте реляционной базы данных полезно сопоставить произвольную схему XSD с реляционным хранилищем. Один из способов достижения этого состоит в создании аннотированной схемы XSD. Схема XSD с заметками называется *схемой сопоставления*, которая предоставляет сведения о том, как данные XML должны сопоставляться с реляционным хранилищем. По сути, схема сопоставления является XML-представлением реляционных данных. Эти сопоставления позволяют получать реляционные данные в виде XML-документа.  
  
## <a name="namespace-for-annotations"></a>Пространства имен для заметок  
 В схеме XSD заметки задаются с помощью пространства имен **urn: schemas-microsoft-com: Mapping-Schema**. Как показано в следующем примере, проще всего указать пространство имен в теге ** \<XSD: schema>** .  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 Префикс пространства имен может быть произвольным. В этой документации префикс **SQL** используется для обозначения пространства имен annotation и для различения заметок в этом пространстве имен от других пространств имен.  
  
## <a name="example-of-an-annotated-xsd-schema"></a>Пример схемы XSD с заметками  
 В следующем примере схема XSD состоит из элемента ** \<Person. Contact>** . Элемент ** \<Employee>** имеет атрибут **ContactID** , а ** \<FirstName>** и ** \<LastName>** дочерним элементам:  
  
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
  
 В схеме сопоставления элемент ** \<Contact>** сопоставляется с таблицей Person. Contact в образце базы данных AdventureWorks с помощью `sql:relation` аннотации. Атрибуты ConID, FName и LName сопоставлены столбцам ContactID, FirstName и LastName таблицы Person.Contact с помощью заметок `sql:field`.  
  
 Эта аннотированная схема XSD создает XML-представление реляционных данных. Затем можно выполнять запросы XPath к этому XML-представлению. Запрос XPath возвращает в качестве результата XML-документ в отличие от запросов SQL, которые возвращают наборы строк.  
  
> [!NOTE]  
>  В схеме сопоставления чувствительность к регистру для указанных реляционных значений (таких как имя таблицы или столбца) зависит от того, использует ли SQL Server чувствительные к регистру параметры сортировки. Дополнительные сведения см. в статье [Collation and Unicode Support](../../collations/collation-and-unicode-support.md).  
  
## <a name="other-resources"></a>Другие ресурсы  
 Дополнительные сведения о языке XSD, языке XPath и преобразованиях XSLT находятся на следующих веб-сайтах.  
  
-   XML-схема, часть 0: учебник, рекомендация консорциума W3C (http://www.w3.org/TR/xmlschema-0/)  
  
-   XML-схема, часть 1: структуры, рекомендация консорциума W3C (http://www.w3.org/TR/xmlschema-1/)  
  
-   XML-схема, часть 2: типы типов, рекомендация консорциума W3C (http://www.w3.org/TR/xmlschema-2/)  
  
-   Язык XML Path (XPath) (http://www.w3.org/TR/xpath)  
  
-   Преобразования XSL (XSLT) (http://www.w3.org/TR/xslt)  
  
## <a name="see-also"></a>См. также  
 [Рекомендации по безопасности схемы с заметками &#40;SQLXML 4,0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)   
 [Схемы XDR с заметками &#40;нерекомендуемые в SQLXML 4,0&#41;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
