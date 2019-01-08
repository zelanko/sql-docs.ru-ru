---
title: 'Получение невостребованных данных с помощью SQL: Overflow-field (SQLXML 4.0) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- unconsumed data
- storing unconsumed data
- retrieving unconsumed data
- annotated XSD schemas, unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: 8526998d-b47d-4a32-8dc2-7f50a8d11097
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4193f98f4431ae5d73cfeadb1ef9898bd330a078
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52522177"
---
# <a name="retrieving-unconsumed-data-using-the-sqloverflow-field-sqlxml-40"></a>Получение невостребованных данных с помощью sql:overflow-field (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Когда в базу данных с помощью функции OPENXML [!INCLUDE[tsql](../../includes/tsql-md.md)] вставляются записи из XML-документа, все невостребованные данные из исходного XML-документа могут быть сохранены в столбце. При получении данных из базы данных с использованием аннотированных схем, можно указать **SQL: Overflow-поле** атрибут для идентификации столбца в таблице, в котором хранятся данные переполнения. **SQL: Overflow-поле** атрибут может быть указан в  **\<элемент >**.  
  
 Затем эти данные можно получить одним из трех способов.  
  
-   Атрибуты, сохраненные в столбце переполнения, добавляются к элементу, который содержит **SQL: Overflow-поле** заметки.  
  
-   Дочерние элементы и их потомки, хранимые в столбце переполнения базы данных, добавляются в качестве дочерних элементов вслед за содержимым, которое явным образом указывается в схеме. (Порядок не сохраняется.)  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqloverflow-field-for-an-element"></a>A. Указание sql:overflow-field для элемента  
 В данном примере предполагается, что был выполнен следующий скрипт, а значит, в базе данных tempdb имеется таблица Customers2:  
  
```  
USE tempdb  
CREATE TABLE Customers2 (  
CustomerID       VARCHAR(10),   
ContactName    VARCHAR(30),   
AddressOverflow    NVARCHAR(500))  
  
GO  
INSERT INTO Customers2 VALUES (  
'ALFKI',   
'Joe',  
'<Address>  
  <Address1>Maple St.</Address1>  
  <Address2>Apt. E105</Address2>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98147</Zip>  
 </Address>')  
GO  
```  
  
 Кроме того, необходимо создать виртуальный каталог для базы данных tempdb- и виртуальное имя шаблона из **шаблона** тип с именем «template».  
  
 В следующем примере схема сопоставления получает невостребованные данные, которые сохраняются в столбце AddressOverflow таблицы Customers2:  
  
```  
<xsd:schema xmlns:xsd="https://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customers2" sql:overflow-field="AddressOverflow" >  
    <xsd:complexType>  
      <xsd:attribute name="CustomerID"  type="xsd:integer"/>  
      <xsd:attribute name="ContactName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните этот файл под именем Overflow.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните файл под именем OverflowT.xml в том же каталоге, где был сохранен файл Overflow.xml. Запрос из шаблона выбирает все записи из таблицы Customers2.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Overflow.xml">  
            /Customers2  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу для схемы сопоставления (Overflow.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\Overflow.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Результирующий набор:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers2 CustomerID="ALFKI" ContactName="Joe">  
    <Address1>Maple St.</Address1>   
    <Address2>Apt. E105</Address2>   
    <City>Seattle</City>   
    <State>WA</State>   
    <Zip>98147</Zip>   
  </Customers2>  
</ROOT>  
```  
  
  
