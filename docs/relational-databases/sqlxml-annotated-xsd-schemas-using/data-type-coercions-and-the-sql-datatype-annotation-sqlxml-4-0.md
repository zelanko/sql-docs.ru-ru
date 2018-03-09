---
title: "Приведение типов данных и SQL: DataType заметки (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c4c5d33454cebe84fb14a5bb154f7ee30a57de51
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a>Приведение типов данных и заметка sql:datatype (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
В схеме XSD **заметки xsd: Type** атрибут задает тип данных XSD элемент или атрибут. Если схема XSD используется для получения данных из базы данных, указанный тип данных используется для форматирования данных.  
  
 Помимо указания XSD-типа в схеме, можно также указать Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных с помощью **SQL: DataType** заметки. **Заметки xsd: Type** и **SQL: DataType** атрибуты определяют сопоставление типов данных XSD и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.  
  
## <a name="xsdtype-attribute"></a>Атрибут xsd:type  
 Можно использовать **заметки xsd: Type** атрибут для указания типа данных XML атрибута или элемента, который сопоставляется со столбцом. **Заметки xsd: Type** влияет на документ, возвращенный сервером, а также выполняемый запрос XPath. При выполнении запроса XPath к схеме сопоставления, которая содержит **xsd: тип**, XPath использует заданный тип данных при обработке запроса. Дополнительные сведения об использовании XPath **заметки xsd: Type**, в разделе [сопоставление типов данных XSD для типов данных XPath &#40; SQLXML 4.0 &#41; ](../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md).  
  
 В возвращенном документе все типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] преобразуются в строковые представления. Для некоторых типов данных необходимо дополнительное преобразование. В следующей таблице перечислены преобразования, которые используются для различных **заметки xsd: Type** значения.  
  
|Тип данных XSD|Преобразование SQL Server|  
|-------------------|---------------------------|  
|Boolean|CONVERT(bit, COLUMN)|  
|Дата|LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)|  
|Decimal|CONVERT(money, COLUMN)|  
|id/idref/idrefs|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|nmtoken/nmtokens|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|Time|SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)|  
|Все остальные|Дополнительное преобразование не выполняется|  
  
> [!NOTE]  
>  Некоторые значения, возвращаемые методом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут оказаться несовместимыми с типами данных XML, заданные с помощью **заметки xsd: Type**, так как преобразование не поддерживается (например, преобразование «XYZ» в  **десятичное число** тип данных) или из-за превышения диапазона этого типа данных (например,-100000 преобразуется в **UnsignedShort** типа XSD). Преобразования несовместимых типов может привести к недопустимым XML-документам или ошибкам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a>Сопоставление типов данных SQL Server с типами данных XSD  
 Следующая таблица показывает очевидные сопоставления типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типам данных XSD. Если известен тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в данной таблице показан соответствующий XSD-тип, который можно указать в схеме XSD.  
  
|Тип данных SQL Server|Тип данных XSD|  
|--------------------------|-------------------|  
|**bigint**|**long**|  
|**binary**|**base64Binary**|  
|**бит**|**boolean**|  
|**char**|**строка**|  
|**datetime**|**dateTime**|  
|**decimal**|**decimal**|  
|**float**|**double**|  
|**image**|**base64Binary**|  
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
|**varbinary**|**base64Binary**|  
|**varchar**|**строка**|  
|**uniqueidentifier**|**строка**|  
  
## <a name="sqldatatype-annotation"></a>Заметка sql:datatype  
 **SQL: DataType** заметка используется для указания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных, эта заметка должен быть указан, если:  
  
-   Выполняется Массовая загрузка в **dateTime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбец из XSD **dateTime**, **даты**, или **время** типа. В этом случае необходимо определить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных столбца с помощью **SQL: DataType = «dateTime»**. Это правило применяется только для диаграмм обновления.  
  
-   Выполняется Массовая загрузка в столбец [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **uniqueidentifier** тип и значение XSD представляет собой идентификатор GUID, который включает фигурные скобки ({и}). При указании **SQL: DataType = «uniqueidentifier»**, фигурные скобки удаляются из значения перед вставкой в столбце. Если **SQL: DataType** не указан, значение пересылается с фигурными скобками и вставка или обновление завершается неудачей.  
  
-   Тип данных XML **base64Binary** сопоставляется различным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных (**двоичных**, **изображения**, или **varbinary**). Чтобы сопоставить тип данных XML **base64Binary** с определенным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных, используйте **SQL: DataType** заметки. Эта заметка указывает явный тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбца, которому сопоставляется атрибут. Это полезно, если данные сохраняются в базах данных. Указав **SQL: DataType** заметки, можно определить явные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.  
  
 Обычно рекомендуется указывать **SQL: DataType** в схеме.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для выполнения примеров SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-xsdtype"></a>A. Указание заметки xsd:type  
 В этом примере показано, как XSD **даты** типа, заданного с помощью **заметки xsd: Type** атрибут в схеме, влияет на результирующий XML-документ. Схема обеспечивает XML-представление таблицы Sales.SalesOrderHeader в базе данных AdventureWorks.  
  
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
  
-   Указывает **заметки xsd: Type = время** на **ShipDate** атрибут часть времени значения, возвращаемого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для **ShipDate** атрибут отображается.  
  
-   Не указывайте **заметки xsd: Type** на **DueDate** атрибута, то же значение, возвращенный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображается.  
  
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
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML 4.0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
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
 Работающий пример см. в разделе примере Е в [примеры массовой загрузки XML &#40; SQLXML 4.0 &#41; ](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md). В этом примере выполняется массовая загрузка значения идентификатора GUID, включая "{" и "}". В этом примере схема задает **SQL: DataType** для идентификации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типа данных как **uniqueidentifier**. В этом примере показано, когда **SQL: DataType** должен быть указан в схеме.  
  
  
