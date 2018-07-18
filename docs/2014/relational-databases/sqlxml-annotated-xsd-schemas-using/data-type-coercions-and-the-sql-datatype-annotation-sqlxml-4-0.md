---
title: 'Приведение типов данных и заметка (SQLXML 4.0), SQL: DataType | Документация Майкрософт'
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
- mapping data types [SQLXML]
- type attribute
- sql:datatype
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- xsd:type
- datatype annotation
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XSD schemas [SQLXML], mapping data types
ms.assetid: db192105-e8aa-4392-b812-9d727918c005
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 095df15d5a917b54e1a518445f49a7ab1f351378
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297944"
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a>Приведение типов данных и заметка sql:datatype (SQLXML 4.0)
  В схеме XSD атрибут `xsd:type` указывает тип XSD-данных элемента или атрибута. Если схема XSD используется для получения данных из базы данных, указанный тип данных используется для форматирования данных.  
  
 Кроме указания XSD-типа в схеме, можно также указать тип данных Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью заметки `sql:datatype`. Атрибуты `xsd:type` и `sql:datatype` управляют сопоставлением между типами данных XSD и типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="xsdtype-attribute"></a>Атрибут xsd:type  
 Атрибут `xsd:type` позволяет задать тип данных XML атрибута или элемента, сопоставляемого со столбцом. Атрибут `xsd:type` влияет на документ, возвращаемый сервером, а также на выполняемый запрос XPath. При выполнении запроса XPath к схеме сопоставления, которая содержит атрибут `xsd:type`, XPath использует указанный тип данных при обработке запроса. Дополнительные сведения о способах использования XPath `xsd:type`, см. в разделе [сопоставление типов данных XSD с типами данных XPath &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md).  
  
 В возвращенном документе все типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] преобразуются в строковые представления. Для некоторых типов данных необходимо дополнительное преобразование. В следующей таблице перечислены виды преобразования, которые применяются для различных значений `xsd:type`.  
  
|Тип данных XSD|Преобразование SQL Server|  
|-------------------|---------------------------|  
|Логическое значение|CONVERT(bit, COLUMN)|  
|Дата|LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)|  
|Decimal|CONVERT(money, COLUMN)|  
|id/idref/idrefs|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|nmtoken/nmtokens|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|Time|SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)|  
|Все остальные|Дополнительное преобразование не выполняется|  
  
> [!NOTE]  
>  Некоторые значения, возвращаемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], могут быть несовместимыми с типами данных XML, указанными с помощью атрибута `xsd:type`, из-за невозможности преобразования (например, преобразование «XYZ» в тип данных `decimal`) или из-за превышения диапазона этого типа данных (например, преобразование -100000 в XSD-тип `UnsignedShort`). Преобразования несовместимых типов может привести к недопустимым XML-документам или ошибкам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a>Сопоставление типов данных SQL Server с типами данных XSD  
 Следующая таблица показывает очевидные сопоставления типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типам данных XSD. Если известен тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в данной таблице показан соответствующий XSD-тип, который можно указать в схеме XSD.  
  
|Тип данных SQL Server|Тип данных XSD|  
|--------------------------|-------------------|  
|`bigint`|`long`|  
|`binary`|`base64Binary`|  
|`bit`|`boolean`|  
|`char`|`string`|  
|`datetime`|`dateTime`|  
|`decimal`|`decimal`|  
|`float`|`double`|  
|`image`|`base64Binary`|  
|`int`|`int`|  
|`money`|`decimal`|  
|`nchar`|`string`|  
|`ntext`|`string`|  
|`nvarchar`|`string`|  
|`numeric`|`decimal`|  
|`real`|`float`|  
|`smalldatetime`|`dateTime`|  
|`smallint`|`short`|  
|`smallmoney`|`decimal`|  
|`sql_variant`|`string`|  
|`sysname`|`string`|  
|`text`|`string`|  
|`timestamp`|`dateTime`|  
|`tinyint`|`unsignedByte`|  
|`varbinary`|`base64Binary`|  
|`varchar`|`string`|  
|`uniqueidentifier`|`string`|  
  
## <a name="sqldatatype-annotation"></a>Заметка sql:datatype  
 Заметка `sql:datatype` используется, чтобы указать тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта заметка должна быть указана в следующих случаях.  
  
-   Выполняется Массовая загрузка в `dateTime` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбец из XSD `dateTime`, `date`, или `time` типа. В этом случае необходимо определить тип данных столбца [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью заметки `sql:datatype="dateTime"`. Это правило применяется только для диаграмм обновления.  
  
-   Выполняется Массовая загрузка в столбец [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `uniqueidentifier` тип и значение XSD представляет собой идентификатор GUID, который включает фигурные скобки ({и}). Если указана заметка `sql:datatype="uniqueidentifier"`, фигурные скобки удаляются из значения прежде, чем оно вставляется в столбец. Если заметка `sql:datatype` не указана, значение пересылается с фигурными скобками, и вставка или обновление завершается неудачей.  
  
-   Тип данных XML `base64Binary` сопоставляется различным типам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (`binary`, `image` или `varbinary`). Чтобы сопоставить тип данных XML `base64Binary` различным типам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используйте заметку `sql:datatype`. Эта заметка указывает явный тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбца, которому сопоставляется атрибут. Это полезно, если данные сохраняются в базах данных. Указав заметку `sql:datatype`, можно явным образом указать тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 В основном рекомендуется указывать заметку `sql:datatype` в схеме.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-xsdtype"></a>A. Указание заметки xsd:type  
 Этот пример показывает, как XSD-тип `date`, указанный с помощью атрибута `xsd:type` в схеме, влияет на результирующий XML-документ. Схема обеспечивает XML-представление таблицы Sales.SalesOrderHeader в базе данных AdventureWorks.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader">  
     <xsd:complexType>  
       <xsd:attribute name="SalesOrderID" type="xsd:string" />   
       <xsd:attribute name="CustomerID"   type="xsd:string" />   
       <xsd:attribute name="OrderDate"    type="xsd:date" />   
       <xsd:attribute name="DueDate"  />   
       <xsd:attribute name="ShipDate"  type="xsd:time" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 В этой схеме XSD существует три атрибута, которые возвращают значение данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если схема:  
  
-   Указывает `xsd:type=date` на **OrderDate** атрибут дату часть значения, возвращенного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для **OrderDate** атрибут отображается.  
  
-   Указывает `xsd:type=time` на **ShipDate** атрибут, часть времени значения, возвращенного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для **ShipDate** атрибут отображается.  
  
-   Не указывайте `xsd:type` на **DueDate** атрибута, значение, возвращается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображается.  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл с именем xsdType.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните файл под именем xsdTypeT.xml в том же каталоге, где был сохранен файл xsdType.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="xsdType.xml">  
        /Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл xsdType.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\xsdType.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Частичный результирующий набор:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43659"   
         CustomerID="676"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
  <Order SalesOrderID="43660"   
         CustomerID="117"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
 ...  
</ROOT>  
```  
  
 Эквивалентная схема XDR:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader">  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="CustomerID"  />  
    <AttributeType name="OrderDate" dt:type="date" />  
    <AttributeType name="DueDate" />  
    <AttributeType name="ShipDate" dt:type="time" />  
  
    <attribute type="SalesOrderID" sql:field="OrderID" />  
    <attribute type="CustomerID" sql:field="CustomerID" />  
    <attribute type="OrderDate" sql:field="OrderDate" />  
    <attribute type="DueDate" sql:field="DueDate" />  
    <attribute type="ShipDate" sql:field="ShipDate" />  
</ElementType>  
</Schema>  
```  
  
### <a name="b-specifying-sql-data-type-using-sqldatatype"></a>Б. Указание типа данных SQL с помощью заметки sql:datatype  
 Работающий пример см. в разделе в примере G [примеры массовой загрузки XML &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md). В этом примере выполняется массовая загрузка значения идентификатора GUID, включая "{" и "}". Схема в этом примере указывает заметку `sql:datatype`, чтобы определить тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как `uniqueidentifier`. В этом примере показано, когда необходимо указать `sql:datatype` в схеме.  
  
  
