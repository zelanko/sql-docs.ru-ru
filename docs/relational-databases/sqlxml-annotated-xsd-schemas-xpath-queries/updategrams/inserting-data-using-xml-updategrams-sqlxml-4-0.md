---
title: Вставка данных с помощью диаграмм обновления XML (SQLXML 4.0) | Документация Майкрософт
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
- xsi:nil attribute
- unique values
- <after> block
- id attribute
- data insertions [SQLXML]
- nil attribute
- <before> block
- updg:guid attribute
- multiple record insertions
- returnid attribute
- updategrams [SQLXML], inserting data
- updg:at-identity attribute
- invalid characters [SQLXML]
- updg:returnid attribute
- updg:id attribute
- namespaces [SQLXML], updategrams
- IDENTITY-type column
- guid attribute
- record insertion [SQLXML]
- null values [SQLXML]
- at-identity attribute
- xml data type [SQL Server], SQLXML
ms.assetid: 4dc48762-bc12-43fb-b356-ea1b9c1e287e
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0fd130aea0e3fbf3627eef0b5284c4543c090d4a
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43109270"
---
# <a name="inserting-data-using-xml-updategrams-sqlxml-40"></a>Вставка данных с помощью диаграмм обновления XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Диаграмма обновления обозначает операцию вставки, когда экземпляр записи появляется в  **\<после >** блок, но отсутствует в соответствующем  **\<перед >** блока. В этом случае диаграмма обновления вставляет запись в  **\<после >** блок в базу данных.  
  
 Ниже приведен формат диаграммы обновления для операции вставки:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   [<updg:before>  
   </updg:before>]  
    <updg:after [updg:returnid="x y ...] >  
       <ElementName [updg:id="value"]   
                   [updg:at-identity="x"]   
                   [updg:guid="y"]  
                   attribute="value"   
                   attribute="value"  
                   ...  
       />  
      [<ElementName .../>... ]  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
## <a name="before-block"></a>\<Прежде чем > блока  
 **\<Перед >** можно опустить блок для операции вставки. Если необязательный **схемы сопоставления** атрибут не указан,  **\<ElementName >** , указанный в диаграмме обновления, соответствует таблице базы данных, а также дочерние элементы или атрибуты сопоставляются столбцы в таблице.  
  
## <a name="after-block"></a>\<После > блока  
 Можно указать одну или несколько записей в  **\<после >** блока.  
  
 Если  **\<после >** блок не предоставляет значение для определенного столбца, в диаграмме обновления используется значение по умолчанию, который указан в схеме с заметками (если схема была определена). Если схема не содержит значение по умолчанию для столбца, то диаграмма обновления не задает никакие явные значения для этого столбца и, вместо этого назначает [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] значение по умолчанию (Если указано) к этому столбцу. Если не существует значения по умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и столбец допускает значение NULL, то диаграмма обновления задает для столбца значение NULL. Если столбец не имеет значения по умолчанию и не допускает значение NULL, команда завершается ошибкой и диаграмма обновления возвращает ошибку. Необязательный **updg: returnid** атрибут используется для возвращения значения идентификатора, который создается системой при добавлении записи в таблице со столбцом типа IDENTITY.  
  
## <a name="updgid-attribute"></a>Атрибут updg:id  
 Если диаграмма обновления только записи, то диаграмма обновления не требуется **updg: ID** атрибута. Дополнительные сведения о **updg: ID**, см. в разделе [обновление данных с помощью диаграмм обновления XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/updating-data-using-xml-updategrams-sqlxml-4-0.md).  
  
## <a name="updgat-identity-attribute"></a>Атрибут updg:at-identity  
 Если диаграмма обновления вставляет запись в таблицу со столбцом типа IDENTITY, она может зафиксировать назначенное системой значение с помощью необязательного **updg: в identity** атрибута. Диаграмма обновления может потом использовать это значение в последующих операциях. При выполнении диаграммы обновления, может возвращать значение идентификатора, который создается путем указания **updg: returnid** атрибута.  
  
## <a name="updgguid-attribute"></a>Атрибут updg:guid  
 **Updg: GUID** атрибут является необязательным атрибутом, который создает глобальный уникальный идентификатор. Это значение остается в области для всего  **\<синхронизации >** блока, в котором оно указано. Вы можете использовать в любом в  **\<синхронизации >** блока. Атрибут вызывает **NEWGUID()** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] функцию для создания уникального идентификатора.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы, используя следующие примеры, должны соответствовать требованиям, указанным в [требования для запуска примеров SQLXML](../../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
 При использовании примеров диаграмм обновления необходимо учитывать следующие моменты.  
  
-   В большинстве примеров используется сопоставление по умолчанию (то есть в диаграмме обновления схема сопоставления не задана). Дополнительные примеры диаграмм обновления, которые используются схемы сопоставления, см. в разделе [определение схемы с заметками сопоставления в диаграмме обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
-   В большинстве примеров задействован образец базы данных [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]. Все обновления применяются к таблицам в этой базе данных.  
  
### <a name="a-inserting-a-record-by-using-an-updategram"></a>A. Вставка записи с помощью диаграммы обновления  
 Эта диаграмма обновления с атрибутивной моделью вставляет запись в таблицу HumanResources.Employee в базе данных [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)].  
  
 В этом примере диаграмма обновления не указывает схему сопоставления. Следовательно, диаграмма обновления использует сопоставление по умолчанию, при котором имя элемента сопоставляется с именем таблицы, а атрибуты или дочерние элементы сопоставляются со столбцами таблицы.  
  
 Схема [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] для таблицы HumanResources.Department налагает ограничение «not null» на все столбцы. Следовательно, диаграмма обновления должна содержать значения, указанные для всех столбцов. Столбец DepartmentID является столбцом типа IDENTITY. Поэтому для него значения не указаны.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name="New Product Research"   
            GroupName="Research and Development"   
            ModifiedDate="2010-08-31"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенную выше диаграмму обновления и вставьте ее в текстовый файл. Сохраните файл под именем MyUpdategram.xml.  
  
2.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 При элементном сопоставлении диаграмма обновления выглядит следующим образом:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department>  
            <Name> New Product Research </Name>  
            <GroupName> Research and Development </GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 В диаграмме обновления со смешанной моделью (элементной и атрибутивной) элемент может иметь как атрибуты, так и вложенные элементы, как показано на следующей диаграмме обновления:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name=" New Product Research "   
            <GroupName>Research and Development</GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="b-inserting-multiple-records-by-using-an-updategram"></a>Б. Вставка нескольких записей с помощью диаграммы обновления  
 Данная диаграмма обновления добавляет две новые записи о сменах в таблицу HumanResources.Shift. Диаграмма обновления указывает необязательный  **\<перед >** блока.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенную выше диаграмму обновления и вставьте ее в текстовый файл. Сохраните файл под именем Updategram-AddShifts.xml.  
  
2.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Другая версия этого примера является диаграмма обновления, использующая два отдельных  **\<после >** блоки вместо одного для вставки двух сотрудников. Это допустимо и может быть закодировано следующим образом:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after >  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="c-working-with-valid-sql-server-characters-that-are-not-valid-in-xml"></a>В. Работа с допустимыми символами SQL Server, не являющимися допустимыми в XML  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имена таблиц могут содержать пробелы, как, например, таблица Order Details в базе данных Northwind. Тем не менее, не допускается в XML-символы, которые являются допустимыми [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] идентификаторов, однако не является допустимым идентификаторов XML можно закодировать с помощью "__xHHHH\_\_" как значение кодировки, где HHHH обозначает четырехразрядный шестнадцатеричный код UCS-2 для символа, в наиболее значимых порядке старшинства бит.  
  
> [!NOTE]  
>  В данном примере используется образец базы данных Northwind. Базы данных Northwind можно установить с помощью скрипта SQL доступны для загрузки из этого [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkId=30196).  
  
 Кроме того имя элемента должны быть заключены в квадратные скобки ([]). Поскольку символы [и] недопустимы в XML, их необходимо кодировать как _x005B\_ и _x005D\_, соответственно. Если используется схема сопоставления, то можно предоставить имена элементов, не содержащие недопустимых символов, таких как пробелы. Схема сопоставления выполняет необходимое сопоставление, следовательно, необязательно кодировать эти символы.  
  
 Эта диаграмма обновления добавляет запись в таблицу Order Details в базе данных Northwind:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <_x005B_Order_x0020_Details_x005D_ OrderID="1"  
            ProductID="11"  
            UnitPrice="$1.0"  
            Quantity="1"  
            Discount="0.0" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Столбец UnitPrice в таблице Order Details имеет **деньги** типа. Чтобы применить соответствующее преобразование типов (из **строка** тип **деньги** типа), знак доллара ($) должен быть добавлен как часть значения. Если диаграмма обновления не задана схема сопоставления, первый символ **строка** значение вычисляется. Если первый символ — символ доллара ($), применяется соответствующее преобразование.  
  
 Если диаграмма обновления указывает схему сопоставления, где столбец помечен соответственно как **dt:type="fixed.14.4»** или **SQL: DataType = «деньги»**, знак доллара ($) не является обязательным и Преобразование обрабатывается сопоставлением. Это рекомендуемый способ, который гарантирует, что соответствующее преобразование типов происходит.  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенную выше диаграмму обновления и вставьте ее в текстовый файл. Сохраните файл под именем UpdategramSpacesInTableName.xml.  
  
2.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="d-using-the-at-identity-attribute-to-retrieve-the-value-that-has-been-inserted-in-the-identity-type-column"></a>Г. Использование атрибута at-identity для получения значения, вставленного в столбец типа IDENTITY  
 Следующая диаграмма обновления вставляет две записи: одну в таблицу Sales.SalesOrderHeader, а другую — в таблицу Sales.SalesOrderDetail.  
  
 Сначала диаграмма обновления добавляет запись в таблицу Sales.SalesOrderHeader. В этой таблице столбец SalesOrderID является столбцом типа IDENTITY. Таким образом, при добавлении этой записи в таблицу, в диаграмме обновления используется **в identity** атрибут, определяющий присвоенное столбцу SalesOrderID значение как «x» (значение заполнителя). Затем диаграмма обновления указывает это **в identity** переменной в качестве значения атрибута SalesOrderID в \<Sales.SalesOrderDetail > элемента.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
   <Sales.SalesOrderHeader updg:at-identity="x"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00001111-2222-3333-4444-556677889900"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
      <Sales.SalesOrderDetail SalesOrderID="x"  
                LineNumber="1"  
                OrderQty="1"  
                ProductID="776"  
                SpecialOfferID="1"  
                UnitPrice="2429.9928"  
                UnitPriceDiscount="0.00"  
                rowguid="aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"  
                ModifiedDate="2001-07-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Если вы хотите возвратить значение идентификатора, созданного **updg: в identity** атрибут, можно использовать **updg: returnid** атрибута. Ниже показана измененная диаграмма обновления, которая возвращает значение идентификатора. Эта диаграмма обновления добавляет две записи заказа и две записи подробностей заказа, чтобы немного усложнить пример.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync>  
  <updg:before>  
  </updg:before>  
  <updg:after updg:returnid="x y" >  
       <HumanResources.Shift updg:at-identity="x" Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift updg:at-identity="y" Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:after>  
 </updg:sync>  
</ROOT>  
```  
  
 При выполнении диаграммы обновления она возвращает результат, подобный следующему, который содержит сформированное значение идентификатора (сформированное значение столбца ShiftID, используемого для идентификатора таблицы):  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">   
  <returnid>   
    <x>4</x>   
    <y>5</y>   
  </returnid>   
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенную выше диаграмму обновления и вставьте ее в текстовый файл. Сохраните файл под именем Updategram-returnId.xml.  
  
2.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="e-using-the-updgguid-attribute-to-generate-a-unique-value"></a>Д. Использование атрибута updg:guid для формирования уникального значения  
 В этом примере диаграмма обновления вставляет запись в таблицы Cust и CustOrder. Кроме того, диаграмма обновления формирует уникальное значение атрибута CustomerID с помощью **updg: GUID** атрибута.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after updg:returnid="x" >  
      <Cust updg:guid="x" >  
         <CustID>x</CustID>  
         <LastName>Fuller</LastName>  
      </Cust>  
      <CustOrder>  
         <CustID>x</CustID>  
         <OrderID>1</OrderID>  
      </CustOrder>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Диаграмма обновления указывает **returnid** атрибута. В результате возвращается сформированное значение GUID:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <returnid>  
    <x>7111BD1A-7F0B-4CEE-B411-260DADFEFA2A</x>   
  </returnid>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенную выше диаграмму обновления и вставьте ее в текстовый файл. Сохраните файл под именем Updategram-GenerateGuid.xml.  
  
2.  Создайте следующие таблицы.  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust (CustID uniqueidentifier, LastName varchar(20))  
    CREATE TABLE CustOrder (CustID uniqueidentifier, OrderID int)  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="f-specifying-a-schema-in-an-updategram"></a>Е. Указание схемы в диаграмме обновления  
 Диаграмма обновления в этом примере вставляет запись в следующую таблицу:  
  
```  
CustOrder(OrderID, EmployeeID, OrderType)  
```  
  
 В этой диаграмме обновления указана схема XSD (нет сопоставления по умолчанию элементов и атрибутов диаграммы обновления). Схема обеспечивает необходимое сопоставление элементов и атрибутов таблицам и столбцам базы данных.  
  
 Следующая схема (CustOrderSchema.xml) описывает  **\<CustOrder >** элемент, который состоит из **OrderID** и **EmployeeID** атрибуты. Чтобы сделать схему более интересной, назначается значение по умолчанию **EmployeeID** атрибута. В диаграмме обновления значение атрибута по умолчанию используется только для операций вставки, и только если диаграмма обновления не указывает этот атрибут.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="CustOrder" >  
   <xsd:complexType>  
        <xsd:attribute name="OrderID"     type="xsd:integer" />   
        <xsd:attribute name="EmployeeID"  type="xsd:integer" />  
        <xsd:attribute name="OrderType  " type="xsd:integer" default="1"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Эта диаграмма обновления вставляет записи в таблицу CustOrder. Диаграмма обновления указывает только значения атрибутов OrderID и EmployeeID. Она не указывает значение атрибута OrderType. Поэтому в диаграмме обновления используется значение по умолчанию для атрибута EmployeeID, указанное в предшествующей схеме.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
             xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync mapping-schema='CustOrderSchema.xml'>  
<updg:after>  
       <CustOrder OrderID="98000" EmployeeID="1" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 Дополнительные примеры диаграмм обновления, который указывает схему сопоставления, см. в разделе [определение схемы с заметками сопоставления в диаграмме обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Создайте следующую таблицу в **tempdb** базы данных:  
  
    ```  
    USE tempdb  
    CREATE TABLE CustOrder(  
                     OrderID int,   
                     EmployeeID int,   
                     OrderType int)  
    ```  
  
2.  Скопируйте приведенную выше схему и вставьте ее в текстовый файл. Сохраните файл под именем CustOrderSchema.xml.  
  
3.  Скопируйте приведенную выше диаграмму обновления и вставьте ее в текстовый файл. Сохраните файл под именем CustOrderUpdategram.xml в той же папке, которая используется в предыдущем шаге.  
  
4.  Создайте тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) и воспользуйтесь им для выполнения диаграммы обновления.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Эквивалентная схема XDR:  
  
```  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
 <ElementType name="CustOrder" >  
    <AttributeType name="OrderID" />  
    <AttributeType name="EmployeeID" />  
    <AttributeType name="OrderType" default="1" />  
    <attribute type="OrderID"  />  
    <attribute type="EmployeeID" />  
    <attribute type="OrderType" />  
  </ElementType>  
</Schema>  
```  
  
### <a name="g-using-the-xsinil-attribute-to-insert-null-values-in-a-column"></a>Ж. Использование атрибута xsi:nil для вставки в столбец значений NULL  
 Если вы хотите вставить значение null в соответствующем столбце в таблице, можно указать **xsi: nil** атрибут элемента в диаграмме обновления. В соответствующей схеме XSD, XSD **nillable** также должен быть задан атрибут.  
  
 В качестве примера рассмотрим следующую схему XSD.  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="Student" sql:relation="Students">  
  <xsd:complexType>  
    <xsd:all>  
      <xsd:element name="fname" sql:field="first_name"   
                                type="xsd:string"   
                                 nillable="true"/>  
    </xsd:all>  
    <xsd:attribute name="SID"   
                        sql:field="StudentID"  
                        type="xsd:ID"/>      
    <xsd:attribute name="lname"       
                        sql:field="last_name"  
                        type="xsd:string"/>  
    <xsd:attribute name="minitial"    
                        sql:field="middle_initial"   
                        type="xsd:string"/>  
    <xsd:attribute name="years"       
                         sql:field="no_of_years"  
                         type="xsd:integer"/>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 Схема XSD указывает **nillable = «true»** для  **\<fname >** элемент. Следующая диаграмма обновления использует эту схему:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
      xmlns:updg="urn:schemas-microsoft-com:xml-updategram"  
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  
<updg:sync mapping-schema='StudentSchema.xml'>  
  <updg:before/>  
  <updg:after>  
    <Student SID="S00004" lname="Elmaci" minitial="" years="2">  
      <fname xsi:nil="true">  
    </fname>  
    </Student>  
  </updg:after>  
</updg:sync>  
  
</ROOT>  
```  
  
 Диаграмма обновления указывает **xsi: nil** для  **\<fname >** элемент в  **\<после >** блока. Поэтому при выполнении этой диаграммы обновления значение NULL вставляется для столбца first_name таблицы.  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Создайте следующую таблицу в **tempdb** базы данных:  
  
    ```  
    USE tempdb  
    CREATE TABLE Students (  
       StudentID char(6)NOT NULL ,  
       first_name varchar(50),  
       last_name varchar(50),  
       middle_initial char(1),  
       no_of_years int NULL)  
    GO  
    ```  
  
2.  Скопируйте приведенную выше схему и вставьте ее в текстовый файл. Сохраните файл под именем StudentSchema.xml.  
  
3.  Скопируйте приведенную выше диаграмму обновления и вставьте ее в текстовый файл. Сохраните файл под именем StudentUpdategram.xml в той же папке, которая использовалась на предыдущем шаге для сохранения файла StudentSchema.xml.  
  
4.  Создайте тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) и воспользуйтесь им для выполнения диаграммы обновления.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="h-specifying-namespaces-in-an-updategram"></a>З. Указание пространств имен в диаграмме обновления  
 Диаграмма обновления может содержать элементы, которые принадлежат пространству имен, объявленному в этом же элементе диаграммы обновления. В этом случае соответствующая схема также должна объявлять то же пространство имен и элемент должен принадлежать этому целевому пространству имен.  
  
 Например, в следующей диаграмме обновления (именем UpdateGram-ElementHavingNamespace.xml)  **\<порядок >** элемент принадлежит пространству имен, объявленному в элементе.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema='XSD-ElementHavingNameSpace.xml'>  
    <updg:after>  
       <x:Order  xmlns:x="http://server/xyz/schemas/"  
             updg:at-identity="SalesOrderID"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00009999-8888-7777-6666-554433221100"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 В этом случае схема должна тоже объявлять пространство имен, как показано в следующей схеме:  
  
 Следующая схема (XSD-ElementHavingNamespace.xml) показывает, как должен быть декларирован соответствующий элемент и атрибуты.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns:dt="urn:schemas-microsoft-com:datatypes"   
     xmlns:sql="urn:schemas-microsoft-com:mapping-schema"    
     xmlns:x="http://server/xyz/schemas/"   
     targetNamespace="http://server/xyz/schemas/" >  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="x:Order_type"/>  
  <xsd:complexType name="Order_type">  
    <xsd:attribute name="SalesOrderID"  type="xsd:ID"/>  
    <xsd:attribute name="RevisionNumber" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OrderDate" type="xsd:dateTime"/>  
    <xsd:attribute name="DueDate" type="xsd:dateTime"/>  
    <xsd:attribute name="ShipDate" type="xsd:dateTime"/>  
    <xsd:attribute name="Status" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OnlineOrderFlag" type="xsd:boolean"/>  
    <xsd:attribute name="SalesOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="PurchaseOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="AccountNumber" type="xsd:string"/>  
    <xsd:attribute name="CustomerID" type="xsd:int"/>  
    <xsd:attribute name="ContactID" type="xsd:int"/>  
    <xsd:attribute name="SalesPersonID" type="xsd:int"/>  
    <xsd:attribute name="TerritoryID" type="xsd:int"/>  
    <xsd:attribute name="BillToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipMethodID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardApprovalCode" type="xsd:string"/>  
    <xsd:attribute name="CurrencyRateID" type="xsd:int"/>  
    <xsd:attribute name="SubTotal" type="xsd:decimal"/>  
    <xsd:attribute name="TaxAmt" type="xsd:decimal"/>  
    <xsd:attribute name="Freight" type="xsd:decimal"/>  
    <xsd:attribute name="TotalDue" type="xsd:decimal"/>  
    <xsd:attribute name="Comment" type="xsd:string"/>  
    <xsd:attribute name="rowguid" type="xsd:string"/>  
    <xsd:attribute name="ModifiedDate" type="xsd:dateTime"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенную выше схему и вставьте ее в текстовый файл. Сохраните файл под именем XSD-ElementHavingNamespace.xml.  
  
2.  Скопируйте приведенную выше диаграмму обновления и вставьте ее в текстовый файл. Сохраните файл под именем Updategram-ElementHavingNamespace.xml в той же папке, в которой был сохранен файл XSD-ElementHavingnamespace.xml.  
  
3.  Создайте тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) и воспользуйтесь им для выполнения диаграммы обновления.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="i-inserting-data-into-an-xml-data-type-column"></a>И. Вставка данных в столбец типа данных XML  
 **Xml** появился тип данных [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Диаграммы обновления можно использовать для вставки и обновления данных, хранящихся в **xml** типа данных столбцов при следующих условиях:  
  
-   **Xml** столбец не может использоваться для идентификации существующей строки. Таким образом, он не может быть включен в **updg: перед** раздел диаграммы обновления.  
  
-   Пространства имен, которые находятся в области видимости XML-фрагмент, вставленный на **xml** столбца будут сохранены и декларации пространства имен добавляются в верхний элемент вставленного фрагмента.  
  
 Например, в следующей диаграмме обновления (SampleUpdateGram.xml)  **\<Desc >** элемент обновляет столбец ProductDescription в рабочей среде > таблицы productModel в [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] образца базы данных. Эта диаграмма обновления образом, содержимое столбца ProductDescription XML обновления с содержимым XML  **\<Desc >** элемент.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
       <updg:before>  
<ProductModel ProductModelID="19">  
   <Name>Mountain-100</Name>  
</ProductModel>  
    </updg:before>  
    <updg:after>  
 <ProductModel>  
    <Name>Mountain-100</Name>  
    <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
        <p1:ProductDescription xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
              xmlns:wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
              xmlns:wf="http://www.adventure-works.com/schemas/OtherFeatures"   
              xmlns:html="http://www.w3.org/1999/xhtml"   
              xmlns="">  
  <p1:Summary>  
     <html:p>Insert Example</html:p>  
  </p1:Summary>  
  <p1:Manufacturer>  
    <p1:Name>AdventureWorks</p1:Name>  
    <p1:Copyright>2002</p1:Copyright>  
    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
  </p1:Manufacturer>  
  <p1:Features>These are the product highlights.   
    <wm:Warranty>  
       <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
       <wm:Description>parts and labor</wm:Description>  
    </wm:Warranty>  
    <wm:Maintenance>  
       <wm:NoOfYears>10 years</wm:NoOfYears>  
       <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
    </wm:Maintenance>  
    <wf:wheel>High performance wheels.</wf:wheel>  
    <wf:saddle>  
      <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle>  
    <wf:pedal>  
       <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal>  
    <wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter and wall-thickness required of a premium mountain frame. The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame>  
    <wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset>  
   </p1:Features>  
   <p1:Picture>  
      <p1:Angle>front</p1:Angle>  
      <p1:Size>small</p1:Size>  
      <p1:ProductPhotoID>118</p1:ProductPhotoID>  
   </p1:Picture>  
   <p1:Specifications> These are the product specifications.  
     <Material>Almuminum Alloy</Material>  
     <Color>Available in most colors</Color>  
     <ProductLine>Mountain bike</ProductLine>  
     <Style>Unisex</Style>  
     <RiderExperience>Advanced to Professional riders</RiderExperience>  
   </p1:Specifications>  
  </p1:ProductDescription>  
 </Desc>  
      </ProductModel>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Диаграмма обновления ссылается на следующую схему XSD с заметками (SampleSchema.xml).  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
     <xsd:complexType>  
       <xsd:sequence>  
          <xsd:element name="Name" type="xsd:string"></xsd:element>  
          <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
           <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="ProductDescription">  
                 <xsd:complexType>  
                   <xsd:sequence>  
                     <xsd:element name="Summary" type="xsd:anyType">  
                     </xsd:element>  
                   </xsd:sequence>  
                 </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>   
       </xsd:sequence>  
       <xsd:attribute name="ProductModelID" sql:field="ProductModelID"/>  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенную выше схему и вставьте ее в текстовый файл. Сохраните файл под именем XSD-SampleSchema.xml.  
  
    > [!NOTE]  
    >  Поскольку диаграмма обновления поддерживает сопоставление по умолчанию, нет способа идентифицировать начало и конец **xml** тип данных. Это фактически означает, что схема сопоставления является обязательным при вставке или обновлении таблиц с помощью **xml** столбцы с типом данных. Если схема не предоставляется, SQLXML возвращает ошибку, указывающую, что один из столбцов пропущен в таблице.  
  
2.  Скопируйте приведенную выше диаграмму обновления и вставьте ее в текстовый файл. Сохраните файл под именем SampleUpdategram.xml в том же каталоге, где был сохранен файл SampleSchema.xml.  
  
3.  Создайте тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) и воспользуйтесь им для выполнения диаграммы обновления.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности диаграмм обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
