---
title: Явное сопоставление элементов и атрибутов с таблицами и столбцами (SQLXML 4.0) XSD | Документы Microsoft
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
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba2b9df8e9104afe0dc7c1645cc4cc64dd01d2ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099742"
---
# <a name="explicit-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a>Явное сопоставление элементов и атрибутов XSD с таблицами и столбцами (SQLXML 4.0)
  При использовании схемы XSD для представления реляционных баз данных в виде XML элементы и атрибуты схемы должны быть сопоставлены с таблицами и столбцами базы данных. Строки таблицы или представления базы данных будут сопоставлены с элементами в XML-документе. Значения столбцов базы данных сопоставляются с атрибутами и элементами.  
  
 При запросах XPath к схеме XSD c заметками данные для элементов и атрибутов схемы берутся из таблиц и столбцов, которым они сопоставлены.  Для получения единичного значения из базы данных сопоставление, заданное схемой XSD, должно содержать спецификации и связей, и полей.  Если имя элемента или атрибута не совпадает с именем таблицы, представления или столбца, которому оно сопоставлено, для задания сопоставления элемента или атрибута в XML-документе и таблицы (представления) или столбца базы данных используются заметки `sql:relation` и `sql:field`.   
  
## <a name="sql-relation"></a>sql-relation  
 Заметка `sql:relation` добавляется для сопоставления узла XML в схеме XSD и таблицы базы данных. Имя таблицы (представления) задано как значение заметки `sql:relation`.  
  
 Если для элемента задана заметка `sql:relation`, ее область действия охватывает все атрибуты и дочерние элементы, описанные в определении сложного типа этого элемента, сокращая, таким образом, усилия по написанию заметок.  
  
 `sql:relation` Заметка также полезна, когда идентификаторы, допустимые в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не являются допустимыми в XML. Например, «Order Details» — допустимое имя таблицы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но не в XML. В этих случаях заметка `sql:relation` может использоваться для указания сопоставления, например следующим образом.  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a>sql-field  
 Заметка `sql-field` сопоставляет атрибут или элемент столбцу базы данных. Заметка `sql:field` добавляется для сопоставления узла XML в схеме и столбца базы данных. Нельзя задавать заметку `sql:field` на элементе с пустым содержимым.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для выполнения примеров SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a>A. Задание заметок sql:relation и sql:field  
 В этом примере схема XSD состоит из  **\<контакт >** элемент сложного типа с  **\<FName >** и  **\<LName >** дочерние элементы и **ContactID** атрибута.  
  
 `sql:relation` Maps заметки  **\<контакт >** элемент с таблицей Person.Contact в базе данных AdventureWorks. `sql:field` Maps заметки  **\<FName >** элемента для столбца FirstName и  **\<LName >** элемент к столбцу LastName.  
  
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
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
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
  
  