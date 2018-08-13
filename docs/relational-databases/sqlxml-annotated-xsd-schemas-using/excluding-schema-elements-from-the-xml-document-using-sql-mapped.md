---
title: 'Исключение элементов схемы из XML-документа с помощью sql: сопоставлены | Документация Майкрософт'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
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
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b5153c59e1f803231ab80692579bb09b56a5ef32
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555864"
---
# <a name="excluding-schema-elements-from-the-xml-document-using-sqlmapped"></a>Исключение элементов схемы из XML-документа с помощью sql:mapped
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В результате сопоставления по умолчанию каждый элемент и атрибут в схеме XSD будет сопоставлен с таблицей и столбцом в базе данных. Если вы хотите создать элемент в схеме XSD, который не сопоставляется любой таблицы базы данных (представления) или столбца и не фигурирующий в XML, можно указать **sql: сопоставлены** заметки.  
  
 **Sql: сопоставлены** заметки особенно полезен, если схема не может быть изменена или если схема используется для проверки XML из других источников и еще содержит данные, которые не хранятся в базе данных. **Sql: сопоставлены** заметки отличается от **sql: является константа** тем, что несопоставленные элементы и атрибуты не отображаются в документе XML.  
  
 **Sql: сопоставлены** заметка имеет логическое значение (0 = false, 1 = true). Допустимые значения: 0, 1, true и false.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a>A. Задание заметки sql:mapped  
 Предположим, существует схема XSD, полученная из другого источника. Эта схема XSD состоит из  **\<Person.Contact >** элемент с **ContactID**, **FirstName**, **LastName**, и **HomeAddress** атрибуты.  
  
 При сопоставлении этой схемы XSD с таблицей Person.Contact в базе данных AdventureWorks, **sql: сопоставлены** заметка указывается для **HomeAddress** атрибут, поскольку таблица Employees не хранятся дома адреса сотрудников. В результате этот атрибут не сопоставлен с базой данных и не возвращается в результирующем XML-документе в ответ на запрос XPath к схеме сопоставления.  
  
 Для остальной части схемы используется сопоставление по умолчанию. **\<Person.Contact >** элемент сопоставляется с таблицей Person.Contact, а все атрибуты сопоставляются со столбцами с тем же именем в таблице Person.Contact.  
  
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
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
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
  
 Обратите внимание, что ContactID, FirstName и LastName присутствуют, но не HomeAddress, поскольку в схеме сопоставления задано значение 0 для **sql: сопоставлены** атрибута.  
  
## <a name="see-also"></a>См. также  
 [По умолчанию осуществляется сопоставление элементов и атрибутов с таблицами и столбцами XSD &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
