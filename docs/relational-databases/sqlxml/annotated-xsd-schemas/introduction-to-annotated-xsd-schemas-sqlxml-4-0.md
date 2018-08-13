---
title: Введение в схемы XSD с заметками (SQLXML 4.0) | Документация Майкрософт
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
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: f3167fd99964bf3bfba0bd6b8523fed6b6961f91
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39564518"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a>Введение в схемы XSD с заметками (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Можно создавать представления схем XML реляционных данных при помощи языка XSD. Затем можно выполнять запросы к этим представлениям при помощи языка XPath (XML Path). Это аналогично созданию представлений с помощью инструкции CREATE VIEW с последующим указанием запросов SQL к представлению.  
  
 Схема XML описывает структуру XML-документа, а также описывает различные ограничения на данные, содержащиеся в документе. При задании запросов XPath по схеме структура возвращаемого XML-документа определяется согласно схеме, по которой выполняется запрос XPath.  
  
 В схеме XSD  **\<xsd: schema >** элемент заключает в себе всю схему; всем объявлениям элементов должны содержаться в  **\<xsd: schema >** элемент. Вы можете описать атрибуты, определяющие пространство имен, в котором находится схема и пространства имен, которые используются в схеме как свойства  **\<xsd: schema >** элемент.  
  
 Должен содержать допустимую схему XSD  **\<xsd: schema >** элемент, определенный следующим образом:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 **\<Xsd: schema >** элемент является производным от спецификации пространства имен схемы XML в http://www.w3.org/2001/XMLSchema.  
  
## <a name="annotations-to-the-xsd-schema"></a>Заметки к схеме XSD  
 Можно использовать схему XSD с заметками, которые описывают сопоставление с базой данных, запрашивают базу данных, а затем возвращают результаты в форме XML-документа. Заметки служат для сопоставления схемы XSD с таблицами и столбцами базы данных. Можно указывать запросы XPath к представлениям XML, созданным на основе схемы XSD, для запроса базы данных и получения результатов в виде XML.  
  
> [!NOTE]  
>  В [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 язык схем XSD поддерживает заметки, введенные в языке схем XDR в [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]. Схемы XDR с заметками в SQLXML 4.0 считаются устаревшими.  
  
 В контексте реляционной базы данных полезно сопоставить произвольную схему XSD с реляционным хранилищем. Один из способов достижения этого состоит в создании аннотированной схемы XSD. Схемы XSD с заметками называется *схемы сопоставления*, который предоставляет сведения о сопоставлении XML-данные должны быть сопоставлены к реляционному хранилищу. По сути, схема сопоставления является XML-представлением реляционных данных. Эти сопоставления позволяют получать реляционные данные в виде XML-документа.  
  
## <a name="namespace-for-annotations"></a>Пространства имен для заметок  
 В схеме XSD заметки заданы при помощи пространства имен **urn: schemas-microsoft-com: Mapping-схемы**. Как показано в следующем примере, самый простой способ указать пространство имен — это указать его в  **\<xsd: schema >** тега.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 Префикс пространства имен может быть произвольным. В этой документации **sql** префикс используется для задания пространства имен заметок и для отличия заметок данного пространства имен от заметок других пространств имен.  
  
## <a name="example-of-an-annotated-xsd-schema"></a>Пример схемы XSD с заметками  
 В следующем примере схема XSD состоит из  **\<Person.Contact >** элемент. **\<Сотрудника >** элемент имеет **ContactID** атрибут и  **\<FirstName >** и  **\< LastName >** дочерние элементы:  
  
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
  
 В схеме сопоставления  **\<контакт >** элемент сопоставлен с таблицей Person.Contact в базе данных AdventureWorks при помощи **SQL: Relation** заметки. Атрибуты ConID, FName и LName сопоставлены столбцам ContactID, FirstName и LastName таблицы Person.Contact с помощью **SQL: field** заметок.  
  
 Эта аннотированная схема XSD создает XML-представление реляционных данных. Затем можно выполнять запросы XPath к этому XML-представлению. Запрос XPath возвращает в качестве результата XML-документ в отличие от запросов SQL, которые возвращают наборы строк.  
  
> [!NOTE]  
>  В схеме сопоставления чувствительность к регистру для указанных реляционных значений (таких как имя таблицы или столбца) зависит от того, использует ли SQL Server чувствительные к регистру параметры сортировки. Дополнительные сведения см. в статье [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="other-resources"></a>Другие ресурсы  
 Дополнительные сведения о языке XSD, языке XPath и преобразованиях XSLT находятся на следующих веб-сайтах.  
  
-   XML Schema Part 0: Учебник для начинающих, W3C рекомендации ()http://www.w3.org/TR/xmlschema-0/)  
  
-   XML Schema Part 1: Структуры, W3C (рекомендацияhttp://www.w3.org/TR/xmlschema-1/)  
  
-   Схема XML, часть 2: типы данных, W3C (рекомендацияhttp://www.w3.org/TR/xmlschema-2/)  
  
-   FOR XML Path Language (XPath) ()http://www.w3.org/TR/xpath)  
  
-   (XSL) преобразований (XSLT)http://www.w3.org/TR/xslt)  
  
## <a name="see-also"></a>См. также  
 [С заметками о безопасности схемы &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)   
 [Схемы XDR с заметками &#40;устарели в SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
