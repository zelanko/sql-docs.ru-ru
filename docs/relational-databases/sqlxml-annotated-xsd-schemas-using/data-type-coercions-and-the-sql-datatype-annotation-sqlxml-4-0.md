---
title: 'Приведение типов данных и заметка (SQLXML 4.0), SQL: DataType | Документация Майкрософт'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: be710df7b54fa7019b5700a7789885ee10519d67
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067191"
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a>Приведение типов данных и заметка sql:datatype (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В схеме XSD **заметки xsd: Type** атрибут указывает тип данных XSD элемента или атрибута. Если схема XSD используется для получения данных из базы данных, указанный тип данных используется для форматирования данных.  
  
 Помимо указания типа XSD в схеме, можно также указать Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных с помощью **SQL: DataType** заметки. **Заметки xsd: Type** и **SQL: DataType** атрибуты управляют сопоставлением между типами данных XSD и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.  
  
## <a name="xsdtype-attribute"></a>Атрибут xsd:type  
 Можно использовать **заметки xsd: Type** атрибут для указания типа данных XML атрибута или элемента, который сопоставляется со столбцом. **Заметки xsd: Type** влияет на документ, возвращаемый сервером, а также выполняемый запрос XPath. При выполнении запроса XPath к схеме сопоставления, которая содержит **заметки xsd: Type**, XPath использует указанный тип данных при обработке запроса. Дополнительные сведения о способах использования XPath **заметки xsd: Type**, см. в разделе [сопоставление типов данных XSD с типами данных XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md).  
  
 В возвращенном документе все типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] преобразуются в строковые представления. Для некоторых типов данных необходимо дополнительное преобразование. В следующей таблице перечислены преобразования, которые используются для различных **заметки xsd: Type** значения.  
  
|Тип данных XSD|Преобразование SQL Server|  
|-------------------|---------------------------|  
|Логическое значение|CONVERT(bit, COLUMN)|  
|Date|LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)|  
|Decimal|CONVERT(money, COLUMN)|  
|id/idref/idrefs|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|nmtoken/nmtokens|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|Time|SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)|  
|Все остальные|Дополнительное преобразование не выполняется|  
  
> [!NOTE]  
>  Некоторые значения, возвращаемые методом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может оказаться несовместимым с типами данных XML, которые указываются с помощью **заметки xsd: Type**, из-за преобразование не поддерживается (например, преобразование «XYZ» в  **Decimal** тип данных) или из-за превышения диапазона этого типа данных (например,-100000 в **типа UnsignedShort** тип XSD). Преобразования несовместимых типов может привести к недопустимым XML-документам или ошибкам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a>Сопоставление типов данных SQL Server с типами данных XSD  
 Следующая таблица показывает очевидные сопоставления типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типам данных XSD. Если известен тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в данной таблице показан соответствующий XSD-тип, который можно указать в схеме XSD.  
  
|Тип данных SQL Server|Тип данных XSD|  
|--------------------------|-------------------|  
|**bigint**|**Long**|  
|**binary**|**Base64Binary**|  
|**bit**|**boolean**|  
|**char**|**строка**|  
|**datetime**|**dateTime**|  
|**decimal**|**decimal**|  
|**float**|**double**|  
|**image**|**Base64Binary**|  
|**int**|**int**|  
|**money**|**decimal**|  
|**nchar**|**строка**|  
|**ntext**|**строка**|  
|**nvarchar**|**строка**|  
|**numeric**|**decimal**|  
|**real**|**float**|  
|**smalldatetime**|**dateTime**|  
|**smallint**|**short**|  
|**smallmoney**|**decimal**|  
|**sql_variant**|**строка**|  
|**sysname**|**строка**|  
|**text**|**строка**|  
|**timestamp**|**dateTime**|  
|**tinyint**|**unsignedByte**|  
|**varbinary**|**Base64Binary**|  
|**varchar**|**строка**|  
|**uniqueidentifier**|**строка**|  
  
## <a name="sqldatatype-annotation"></a>Заметка sql:datatype  
 **SQL: DataType** заметка используется для указания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; эту заметку в тип данных должен быть указан, если:  
  
-   Выполняется Массовая загрузка в **dateTime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбец из XSD **dateTime**, **даты**, или **время** типа. В этом случае необходимо определить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных столбца с помощью **SQL: DataType = «dateTime»** . Это правило применяется только для диаграмм обновления.  
  
-   Выполняется Массовая загрузка в столбец [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **uniqueidentifier** тип и значение XSD представляет собой идентификатор GUID, который включает фигурные скобки ({и}). При указании **SQL: DataType = «uniqueidentifier»** , фигурные скобки удаляются из значения, прежде чем оно вставляется в столбец. Если **SQL: DataType** не указан, значение пересылается с фигурными скобками и вставка или обновление завершается неудачей.  
  
-   Тип данных XML **base64Binary** сопоставляется различным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных (**двоичных**, **изображение**, или **varbinary**). Чтобы сопоставить тип данных XML **base64Binary** с конкретными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных, используйте **SQL: DataType** заметки. Эта заметка указывает явный тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбца, которому сопоставляется атрибут. Это полезно, если данные сохраняются в базах данных. Путем указания **SQL: DataType** заметки, можно определить явный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.  
  
 Обычно рекомендуется указывать **SQL: DataType** в схеме.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-xsdtype"></a>A. Указание заметки xsd:type  
 В этом примере показано, как XSD- **даты** типа, заданного с помощью **заметки xsd: Type** атрибут в схеме, влияет на итоговый документ XML. Схема обеспечивает XML-представление таблицы Sales.SalesOrderHeader в базе данных AdventureWorks.  
  
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
  
-   Указывает **заметки xsd: Type = Дата** на **OrderDate** атрибут дату часть значения, возвращенного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для **OrderDate** атрибут отображается.  
  
-   Указывает **заметки xsd: Type = время** на **ShipDate** атрибут, часть времени значения, возвращенного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для **ShipDate** атрибут отображается.  
  
-   Не указывайте **заметки xsd: Type** на **DueDate** атрибута, значение, возвращается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображается.  
  
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

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
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
 Работающий пример см. в разделе в примере G [примеры массовой загрузки XML &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md). В этом примере выполняется массовая загрузка значения идентификатора GUID, включая "{" и "}". В этом примере схема указывает **SQL: DataType** для идентификации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как тип данных **uniqueidentifier**. В этом примере показано, когда **SQL: DataType** должен быть указан в схеме.  
  
  
