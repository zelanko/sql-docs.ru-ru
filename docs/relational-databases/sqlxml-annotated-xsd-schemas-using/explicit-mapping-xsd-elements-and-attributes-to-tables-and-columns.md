---
title: Явное сопоставление элементов и атрибутов XSD с таблицами и столбцами | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- sql:field
- row mapping [SQLXML]
- attribute mapping [SQLXML], explicit mapping
- field annotation
- XSD schemas [SQLXML], mapping attributes and elements
- names [SQLXML]
- relation annotation
- table/view mapping [SQLXML], explicit mapping
- sql:relation
- mapping schema [SQLXML], explicit mapping
- annotated XSD schemas, mapping attributes and elements
- column mapping [SQLXML]
- element mapping [SQLXML], explicit mapping
- table mapping [SQLXML], explicit mapping
- element/attribute mapping [SQLXML]
ms.assetid: 7a5ebeb6-7322-4141-a307-ebcf95976146
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 40bbbe05f2476a922844943d2388890bc2851527
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39544314"
---
# <a name="explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns"></a>Явное сопоставление элементов и атрибутов XSD с таблицами и столбцами
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  При использовании схемы XSD для представления реляционных баз данных в виде XML элементы и атрибуты схемы должны быть сопоставлены с таблицами и столбцами базы данных. Строки таблицы или представления базы данных будут сопоставлены с элементами в XML-документе. Значения столбцов базы данных сопоставляются с атрибутами и элементами.  
  
 При запросах XPath к схеме XSD c заметками данные для элементов и атрибутов схемы берутся из таблиц и столбцов, которым они сопоставлены.  Для получения единичного значения из базы данных сопоставление, заданное схемой XSD, должно содержать спецификации и связей, и полей.  Если имя элемента или атрибута не совпадает с именем имя таблицы или представления или столбца, к которому оно сопоставлено, **SQL: Relation** и **SQL: field** заметки используются для сопоставления элемента или атрибут в XML-документ и таблицы (представления) или столбца в базе данных.  
  
## <a name="sql-relation"></a>sql-relation  
 **SQL: Relation** добавляется заметка, для сопоставления узла XML в схеме XSD с таблицей базы данных. Имя таблицы (представления) указан в качестве значения **SQL: Relation** заметки.  
  
 Когда **SQL: Relation** указана для элемента, все атрибуты и дочерние элементы, описанные в определении сложного типа этого элемента, тем самым ярлык в письменной область этой заметки заметки.  
  
 **SQL: Relation** заметки также полезен, когда идентификаторы, допустимые в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не являются допустимыми в XML. Например, «Order Details» — допустимое имя таблицы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но не в XML. В таких случаях **SQL: Relation** заметки можно использовать для указания сопоставления, например:  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a>sql-field  
 **Поле sql** заметка сопоставляет элемент или атрибут со столбцом базы данных. **SQL: field** добавляется заметка, для сопоставления узла XML в схеме со столбцом базы данных. Нельзя указать **SQL: field** на пустой элемент содержимого.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a>A. Задание заметок sql:relation и sql:field  
 В этом примере схема XSD состоит из  **\<контакт >** элемент сложного типа с  **\<FName >** и  **\<LName >** дочерние элементы и **ContactID** атрибута.  
  
 **SQL: Relation** карты заметки  **\<контакт >** элемент с таблицей Person.Contact в базе данных AdventureWorks. **SQL: field** карты заметки  **\<FName >** элемента для столбца FirstName и  **\<LName >** элемент Фамилия столбец.  
  
 Не задано заметок для **ContactID** атрибута. Поэтому атрибут по умолчанию сопоставляется со столбцом с тем же именем.  
  
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
        <xsd:attribute name="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем MySchema-annotated.xml.  
  
2.  Скопируйте приведенный ниже шаблон и вставьте его в текстовый файл. Сохраните файл под именем MySchema-annotatedT.xml в том же каталоге, где был сохранен файл MySchema-annotated.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="MySchema-annotated.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл MySchema-annotated.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema-annotated.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Частичный результирующий набор:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
 <Contact ContactID="1">   
    <FName>Gustavo</FName>   
    <LName>Achong</LName>   
 </Contact>   
  .....  
</ROOT>  
```  
  
  
