---
title: "Изменение КОЛЛЕКЦИИ XML-СХЕМ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_XML_SCHEMA_COLLECTION_TSQL
- ALTER XML SCHEMA COLLECTION
dev_langs:
- TSQL
helpviewer_keywords:
- schema collections [SQL Server], altering
- xml_schema_namespace function
- adding schema components
- ALTER XML SCHEMA COLLECTION statement
- XML schemas [SQL Server], adding
- XML schema collections [SQL Server], modifying
- schema collections [SQL Server], adding components
- XML schema collections [SQL Server], adding components
- importing schemas
- XML schema collections [SQL Server], altering
- schema collections [SQL Server], modifying
- multiple schema namespaces
ms.assetid: e311c425-742a-4b0d-b847-8b974bf66d53
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1f4d5a54d304aba3da37be9d73159060aaf2e794
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-xml-schema-collection-transact-sql"></a>ALTER XML SCHEMA COLLECTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет новые компоненты схемы в существующую коллекцию XML-схем.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER XML SCHEMA COLLECTION [ relational_schema. ]sql_identifier ADD 'Schema Component'  
```  
  
## <a name="arguments"></a>Аргументы  
 *relational_schema*  
 Определяет имя реляционной схемы. Если не задано, предполагается использование реляционной схемы по умолчанию.  
  
 *sql_identifier*  
 Идентификатор SQL для коллекции XML-схем.  
  
 **"** *Компонент схемы* **"**  
 Компонент схемы для вставки.  
  
## <a name="remarks"></a>Замечания  
 Чтобы добавить новые XML-схемы с пространствами имен, которые еще не присутствуют в коллекции XML-схем, или добавить новые компоненты к существующим пространствам имен в коллекции, используйте инструкцию ALTER XML SCHEMA COLLECTION.  
  
 В следующем примере добавляется новый \<элемент > к существующему пространству имен `http://MySchema/test_xml_schema` в коллекции `MyColl`.  
  
```  
-- First create an XML schema collection.  
CREATE XML SCHEMA COLLECTION MyColl AS '  
   <schema   
    xmlns="http://www.w3.org/2001/XMLSchema"   
    targetNamespace="http://MySchema/test_xml_schema">  
      <element name="root" type="string"/>   
  </schema>'  
-- Modify the collection.   
ALTER XML SCHEMA COLLECTION MyColl ADD '  
  <schema xmlns="http://www.w3.org/2001/XMLSchema"   
         targetNamespace="http://MySchema/test_xml_schema">   
     <element name="anotherElement" type="byte"/>   
 </schema>';  
```  
  
 Инструкция `ALTER XML SCHEMA` добавляет элемент `<anotherElement>` к ранее определенному пространству имен `http://MySchema/test_xml_schema`.  
  
 Обратите внимание на то, что если некоторые компоненты, добавляемые в коллекцию, ссылаются на уже существующие в данной коллекции компоненты, необходимо использовать команду `<import namespace="referenced_component_namespace" />`.  Однако в команде `<xsd:import>` не допускается использование пространств имен текущей схемы и, следовательно, компонентов из одного и того же целевого пространства имен, поскольку пространство имен текущей схемы импортируется автоматически.  
  
 Чтобы удалить коллекции, используйте [DROP XML SCHEMA COLLECTION &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-xml-schema-collection-transact-sql.md).  
  
 Если коллекция схем уже содержит шаблон нестрогой проверки или элемент типа **xs: anyType**, Добавление нового глобального элемента, типа или объявлении атрибута в коллекции схем приведет к повторной проверке всех сохраненного данные, который ограничен коллекцией схем.  
  
## <a name="permissions"></a>Permissions  
 Чтобы изменить коллекцию XML SCHEMA COLLECTION, необходимо разрешение ALTER для коллекции.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-xml-schema-collection-in-the-database"></a>A. Создание коллекции схем XML в базе данных  
 Следующие примеры создают коллекцию XML-схем `ManuInstructionsSchemaCollection`. Коллекция имеет только одно пространство имен схемы.  
  
```  
-- Create a sample database in which to load the XML schema collection.  
CREATE DATABASE SampleDB;  
GO  
USE SampleDB;  
GO  
CREATE XML SCHEMA COLLECTION ManuInstructionsSchemaCollection AS  
N'<?xml version="1.0" encoding="UTF-16"?>  
<xsd:schema targetNamespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"   
   xmlns          ="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"   
   elementFormDefault="qualified"   
   attributeFormDefault="unqualified"  
   xmlns:xsd="http://www.w3.org/2001/XMLSchema" >  
  
    <xsd:complexType name="StepType" mixed="true" >  
        <xsd:choice  minOccurs="0" maxOccurs="unbounded" >   
            <xsd:element name="tool" type="xsd:string" />  
            <xsd:element name="material" type="xsd:string" />  
            <xsd:element name="blueprint" type="xsd:string" />  
            <xsd:element name="specs" type="xsd:string" />  
            <xsd:element name="diag" type="xsd:string" />  
        </xsd:choice>   
    </xsd:complexType>  
  
    <xsd:element  name="root">  
        <xsd:complexType mixed="true">  
            <xsd:sequence>  
                <xsd:element name="Location" minOccurs="1" maxOccurs="unbounded">  
                    <xsd:complexType mixed="true">  
                        <xsd:sequence>  
                            <xsd:element name="step" type="StepType" minOccurs="1" maxOccurs="unbounded" />  
                        </xsd:sequence>  
                        <xsd:attribute name="LocationID" type="xsd:integer" use="required"/>  
                        <xsd:attribute name="SetupHours" type="xsd:decimal" use="optional"/>  
                        <xsd:attribute name="MachineHours" type="xsd:decimal" use="optional"/>  
                        <xsd:attribute name="LaborHours" type="xsd:decimal" use="optional"/>  
                        <xsd:attribute name="LotSize" type="xsd:decimal" use="optional"/>  
                    </xsd:complexType>  
                </xsd:element>  
            </xsd:sequence>  
        </xsd:complexType>  
    </xsd:element>  
</xsd:schema>' ;  
GO  
-- Verify - list of collections in the database.  
SELECT *  
FROM sys.xml_schema_collections;  
-- Verify - list of namespaces in the database.  
SELECT name  
FROM sys.xml_schema_namespaces;  
  
-- Use it. Create a typed xml variable. Note the collection name   
-- that is specified.  
DECLARE @x xml (ManuInstructionsSchemaCollection);  
GO  
--Or create a typed xml column.  
CREATE TABLE T (  
        i int primary key,   
        x xml (ManuInstructionsSchemaCollection));  
GO  
-- Clean up.  
DROP TABLE T;  
GO  
DROP XML SCHEMA COLLECTION ManuInstructionsSchemaCollection;  
Go  
USE master;  
GO  
DROP DATABASE SampleDB;  
```  
  
 В качестве альтернативы можно связать коллекцию схем с переменной и указать переменную в инструкции `CREATE XML SCHEMA COLLECTION` следующим образом:  
  
```  
DECLARE @MySchemaCollection nvarchar(max);  
SET @MySchemaCollection  = N' copy the schema collection here';  
CREATE XML SCHEMA COLLECTION AS @MySchemaCollection;   
```  
  
 Переменная в примере принадлежит к типу `nvarchar(max)`. Переменная также может быть **xml** тип данных, в этом случае она неявно преобразуется в строку.  
  
 Дополнительные сведения см. в разделе [Просмотр хранимой коллекции схем XML](../../relational-databases/xml/view-a-stored-xml-schema-collection.md).  
  
 Можно хранить коллекции схем в **xml** тип столбца. В этом случае, чтобы создать коллекцию XML-схем, выполните следующие действия.  
  
1.  Получить коллекцию схем из столбца с помощью инструкции SELECT и присвоить его переменной **xml** типа, или **varchar** типа.  
  
2.  Укажите имя переменной в инструкции CREATE XML SCHEMA COLLECTION.  
  
 Инструкция CREATE XML SCHEMA COLLECTION сохраняет только компоненты схем, которые понятны для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не все компоненты XML-схемы хранятся в базе данных. Таким образом, если нужно получить коллекцию XML-схем в том виде, в котором она была предоставлена, рекомендуется сохранять XML-схемы в столбце базы данных или в другой папке компьютера.  
  
### <a name="b-specifying-multiple-schema-namespaces-in-a-schema-collection"></a>Б. Указание нескольких пространств имен схем в коллекции схем  
 Можно указать несколько XML-схем при создании коллекции XML-схем. Например:  
  
```  
CREATE XML SCHEMA COLLECTION N'  
<xsd:schema>....</xsd:schema>  
<xsd:schema>...</xsd:schema>';  
```  
  
 В следующем примере создается коллекция XML-схем `ProductDescriptionSchemaCollection`, которая включает два пространства имен XML-схем.  
  
```  
CREATE XML SCHEMA COLLECTION ProductDescriptionSchemaCollection AS   
'<xsd:schema targetNamespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"  
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
    elementFormDefault="qualified"   
    xmlns:xsd="http://www.w3.org/2001/XMLSchema" >  
    <xsd:element name="Warranty"  >  
        <xsd:complexType>  
            <xsd:sequence>  
                <xsd:element name="WarrantyPeriod" type="xsd:string"  />  
                <xsd:element name="Description" type="xsd:string"  />  
            </xsd:sequence>  
        </xsd:complexType>  
    </xsd:element>  
</xsd:schema>  
 <xs:schema targetNamespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
    elementFormDefault="qualified"   
    xmlns:mstns="http://tempuri.org/XMLSchema.xsd"   
    xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns:wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain" >  
    <xs:import   
namespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain" />  
    <xs:element name="ProductDescription" type="ProductDescription" />  
        <xs:complexType name="ProductDescription">  
            <xs:sequence>  
                <xs:element name="Summary" type="Summary" minOccurs="0" />  
            </xs:sequence>  
            <xs:attribute name="ProductModelID" type="xs:string" />  
            <xs:attribute name="ProductModelName" type="xs:string" />  
        </xs:complexType>  
        <xs:complexType name="Summary" mixed="true" >  
            <xs:sequence>  
                <xs:any processContents="skip" namespace="http://www.w3.org/1999/xhtml" minOccurs="0" maxOccurs="unbounded" />  
            </xs:sequence>  
        </xs:complexType>  
</xs:schema>'  
;  
GO   
-- Clean up  
DROP XML SCHEMA COLLECTION ProductDescriptionSchemaCollection;  
GO  
```  
  
### <a name="c-importing-a-schema-that-does-not-specify-a-target-namespace"></a>В. Импорт схемы, не указывающей целевое пространство имен  
 Если схема, не содержит **targetNamespace** импортируется в коллекцию, ее компоненты связываются с целевым пространством имен пустую строку, как показано в следующем примере. Обратите внимание на то, что сопоставление одной или нескольких схем, импортированных в коллекцию, приводит к сопоставлению нескольких компонентов схемы (потенциально не связанных) с пустым строковым пространством имен по умолчанию.  
  
```  
-- Create a collection that contains a schema with no target namespace.  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  xmlns:ns="http://ns">  
<element name="e" type="dateTime"/>  
</schema>';  
GO  
-- query will return the names of all the collections that   
--contain a schema with no target namespace  
SELECT sys.xml_schema_collections.name   
FROM   sys.xml_schema_collections   
JOIN   sys.xml_schema_namespaces   
ON     sys.xml_schema_collections.xml_collection_id =   
       sys.xml_schema_namespaces.xml_collection_id   
WHERE  sys.xml_schema_namespaces.name='';  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание КОЛЛЕКЦИИ XML-СХЕМ &#40; Transact-SQL &#41;](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [DROP XML SCHEMA COLLECTION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-xml-schema-collection-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Требования и ограничения для коллекций схем XML на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  

