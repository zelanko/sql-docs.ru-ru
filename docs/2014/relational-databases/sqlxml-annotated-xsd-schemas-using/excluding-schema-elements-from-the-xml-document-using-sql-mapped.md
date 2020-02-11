---
title: 'Исключение элементов схемы из результирующего XML-документа с помощью SQL: сопоставлено (SQLXML 4,0) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- annotated XSD schemas, excluding schema elements
- mapped annotation
- table mapping [SQLXML], excluding schema elements
- sql:mapped
- excluding schema elements
- element mapping [SQLXML], excluding schema elements
- column mapping [SQLXML]
- XSD schemas [SQLXML], excluding schema elements
- attribute mapping [SQLXML], excluding schema elements
- table/view mapping [SQLXML], excluding schema elements
ms.assetid: 7d2649dd-0038-4a2c-b16d-f80f7c306966
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 865a9af892f948e77aa593d3713766e7860349b0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013862"
---
# <a name="excluding-schema-elements-from-the-resulting-xml-document-using-sqlmapped-sqlxml-40"></a>Исключение элементов схемы из результирующего XML-документа с помощью sql:mapped (SQLXML 4.0)
  В результате сопоставления по умолчанию каждый элемент и атрибут в схеме XSD будет сопоставлен с таблицей и столбцом в базе данных. Если в схеме XSD нужно создать элемент, не сопоставленный никакой таблице, никакому представлению или столбцу базы данных и не фигурирующий в XML, нужно создать для него заметку `sql:mapped`.  
  
 Заметка `sql:mapped` особенно полезна, если схему нельзя изменять или она используется для проверки XML из других источников (при этом содержит данные, не хранящиеся в вашей базе данных). Заметка `sql:mapped` отличается от `sql:is-constant` тем, что несопоставленные элементы и атрибуты не фигурируют в XML-документе.  
  
 Заметка `sql:mapped` имеет логическое значение (0 = false, 1 = true). Допустимые значения: 0, 1, true и false.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a>A. Задание заметки sql:mapped  
 Предположим, существует схема XSD, полученная из другого источника. Эта схема XSD состоит из элемента ** \<Person. Contact>** с атрибутами **ContactID**, **FirstName**, **LastName**и **HomeAddress** .  
  
 При сопоставлении этой схемы XSD с таблицей Person. Contact в базе данных `sql:mapped` AdventureWorks в атрибуте **HomeAddress** указывается, потому что в таблице Employees не хранятся домашние адреса сотрудников. В результате этот атрибут не сопоставлен с базой данных и не возвращается в результирующем XML-документе в ответ на запрос XPath к схеме сопоставления.  
  
 Для остальной части схемы используется сопоставление по умолчанию. Элемент ** \<Person. Contact>** сопоставляется с таблицей Person. Contact, а все атрибуты сопоставляются со столбцами с тем же именем в таблице Person. Contact.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:attribute name="ContactID"   type="xsd:string"/>  
      <xsd:attribute name="FirstName"    type="xsd:string" />  
      <xsd:attribute name="LastName"     type="xsd:string" />  
      <xsd:attribute name="HomeAddress" type="xsd:string"   
                     sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем sql-mapped.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните файл под именем sql-mappedT.xml в том же каталоге, где был сохранен файл sql-mapped.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-mapped.xml">  
            /Person.Contact[@ContactID < 10]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу для схемы сопоставления (MySchema.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\sql-mapped.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Результирующий набор:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel" />   
  <Person.Contact ContactID="3" FirstName="Kim" LastName="Abercrombie" />   
  <Person.Contact ContactID="4" FirstName="Humberto" LastName="Acevedo" />   
  <Person.Contact ContactID="5" FirstName="Pilar" LastName="Ackerman" />   
  <Person.Contact ContactID="6" FirstName="Frances" LastName="Adams" />   
  <Person.Contact ContactID="7" FirstName="Margaret" LastName="Smith" />   
  <Person.Contact ContactID="8" FirstName="Carla" LastName="Adams" />   
  <Person.Contact ContactID="9" FirstName="Jay" LastName="Adams" />   
</ROOT>  
```  
  
 Обратите внимание, что поля ContactID, FirstName и LastName присутствуют, а HomeAddress — нет, потому что в схеме сопоставления было задано значение 0 для атрибута `sql:mapped`.  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление элементов и атрибутов XSD с таблицами и столбцами по умолчанию &#40;SQLXML 4,0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
