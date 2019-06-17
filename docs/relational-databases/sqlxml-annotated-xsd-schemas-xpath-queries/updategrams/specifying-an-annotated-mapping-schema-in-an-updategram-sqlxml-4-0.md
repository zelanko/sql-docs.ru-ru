---
title: Определение схемы с заметками сопоставления в диаграмме обновления (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, updategrams
- data types [SQLXML], mapping schema in updategrams
- updategrams [SQLXML], annotated mapping schemas
- annotated XDR schemas, updategrams
- inverse attribute
- parent-child relationships [SQLXML]
- mapping-schema attribute
- mapping schema [SQLXML], updategrams
- sql:inverse
ms.assetid: 2e266ed9-4cfb-434a-af55-d0839f64bb9a
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9e55ec7d8ed06914299f56b3d613186d8c612a05
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63025560"
---
# <a name="specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-40"></a>Определение схемы с заметками сопоставления в диаграмме обновления (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом разделе описывается использование схемы сопоставления (XSD или XDR), указанной в диаграмме обновления, для обработки обновлений. В диаграмме обновления, можно указать имя схемы с заметками сопоставления для использования при сопоставлении элементы и атрибуты в диаграмме обновления с таблицами и столбцами в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если в диаграмме обновления указана схема сопоставления, имена элементов и атрибутов, которые указаны в этой диаграмме обновления, должны сопоставляться с элементами и атрибутами в схеме сопоставления.  
  
 Чтобы указать схему сопоставления, используйте **схемы сопоставления** атрибут  **\<синхронизации >** элемент. В следующих примерах показаны две диаграммы обновления: в одной используется простая схема сопоставления, а в другой — более сложная схема сопоставления.  
  
> [!NOTE]  
>  Настоящая документация предназначена для тех, кто знаком с шаблонами и поддержкой схем сопоставления в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [введение в схемы XSD с заметками &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md). Для приложений прежних версий, которые используют XDR, см. в разделе [аннотированные схемы XDR &#40;в SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="dealing-with-data-types"></a>Работа с типами данных  
 Если схема указывает **изображение**, **двоичных**, или **varbinary** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных (с помощью **SQL: DataType**) и не делает Укажите тип данных XML, диаграмма обновления предполагает, что тип данных XML **двоичных base-64**. Если данные **bin.base** типа, необходимо явно указать тип (**dt:type=bin.base** или **тип = «XSD: hexBinary»** ).  
  
 Если схема указывает **dateTime**, **даты**, или **время** тип данных XSD, необходимо также указать соответствующий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных с помощью  **SQL: DataType = «dateTime»** .  
  
 При обработке параметров типа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **деньги** типа, необходимо явно указать **SQL: DataType = «деньги»** для соответствующего узла в схеме сопоставления.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы, используя следующие примеры, должны соответствовать требованиям, указанным в [требования для запуска примеров SQLXML](../../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-creating-an-updategram-with-a-simple-mapping-schema"></a>A. Создание диаграммы обновления с простой схемой сопоставления  
 Следующая схема XSD (SampleSchema.xml) является схемой сопоставления, которая сопоставляет  **\<клиента >** элемент с таблицей Sales.Customer:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
        <xsd:attribute name="CustID"    
                       sql:field="CustomerID"   
                       type="xsd:string" />  
        <xsd:attribute name="RegionID"    
                       sql:field="TerritoryID"    
                       type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Следующая диаграмма обновления вставляет запись в таблицу Sales.Customer и использует предыдущую схему сопоставления для сопоставления этих данных с таблицей. Обратите внимание на то, что диаграмма обновления использует то же имя элемента,  **\<клиента >** , как определено в схеме. Это является обязательным, поскольку диаграмма обновления указывает конкретную схему.  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем SampleUpdateSchema.xml.  
  
2.  Скопируйте приведенный ниже шаблон диаграммы обновления и вставьте его в текстовый файл. Сохраните файл под именем SampleUpdategram.xml в том же каталоге, где был сохранен файл SampleUpdateSchema.xml.  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleUpdateSchema.xml">  
        <updg:before>  
          <Customer CustID="1" RegionID="1"  />  
        </updg:before>  
        <updg:after>  
          <Customer CustID="1" RegionID="2" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
     Путь к каталогу задается для схемы сопоставления (SampleUpdateSchema.xml) относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Эквивалентная схема XDR:  
  
```  
<?xml version="1.0" ?>  
   <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
         xmlns:dt="urn:schemas-microsoft-com:datatypes"   
         xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
     <ElementType name="Customer" sql:relation="Sales.Customer" >  
       <AttributeType name="CustID" />  
       <AttributeType name="RegionID" />  
  
       <attribute type="CustID" sql:field="CustomerID" />  
       <attribute type="RegionID" sql:field="TerritoryID" />  
     </ElementType>  
   </Schema>   
```  
  
### <a name="b-inserting-a-record-by-using-the-parent-child-relationship-specified-in-the-mapping-schema"></a>Б. Вставка записи с помощью связи «родители-потомки», указанной в схеме сопоставления  
 Между элементами схемы можно устанавливать связь. **\<SQL: Relationship >** элемент указывает связь «родители потомки» между элементами схемы. Эти данные используются для обновления соответствующих таблиц, между которыми установлена связь «первичный-внешний ключ».  
  
 Следующая схема сопоставления (SampleSchema.xml) состоит из двух элементов,  **\<порядок >** и  **\<OD >** :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="OD"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOD" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID"   type="xsd:integer" />  
              <xsd:attribute name="ProductID" type="xsd:integer" />  
             <xsd:attribute name="UnitPrice"  type="xsd:decimal" />  
             <xsd:attribute name="OrderQty"   type="xsd:integer" />  
             <xsd:attribute name="UnitPriceDiscount"   type="xsd:decimal" />  
  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesOrderID"  type="xsd:integer" />  
        <xsd:attribute name="OrderDate"  type="xsd:date" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Следующая диаграмма обновления использует эту схему XSD для добавления новой записи сведения о порядке (  **\<OD >** элемент в  **\<после >** блок) для заказа 43860. **Схемы сопоставления** атрибут используется для указания схемы сопоставления в диаграмме обновления.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43860" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43860" >  
           <OD ProductID="753" UnitPrice="$10.00"  
               Quantity="5" Discount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем SampleUpdateSchema.xml.  
  
2.  Скопируйте приведенный выше шаблон диаграммы обновления и вставьте его в текстовый файл. Сохраните файл под именем SampleUpdategram.xml в том же каталоге, где был сохранен файл SampleUpdateSchema.xml.  
  
     Путь к каталогу задается для схемы сопоставления (SampleUpdateSchema.xml) относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Эквивалентная схема XDR:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="OD" sql:relation="Sales.SalesOrderDetail" >  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="ProductID" />  
    <AttributeType name="UnitPrice"  dt:type="fixed.14.4" />  
    <AttributeType name="OrderQty" />  
    <AttributeType name="UnitPriceDiscount" />  
  
    <attribute type="SalesOrderID" />  
    <attribute type="ProductID" />  
    <attribute type="UnitPrice" />  
    <attribute type="OrderQty" />  
    <attribute type="UnitPriceDiscount" />  
</ElementType>  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="OrderDate" />  
  
    <attribute type="CustomerID" />  
    <attribute type="SalesOrderID" />  
    <attribute type="OrderDate" />  
    <element type="OD" >  
             <sql:relationship   
                   key-relation="Sales.SalesOrderHeader"  
                   key="SalesOrderID"  
                   foreign-key="SalesOrderID"  
                   foreign-relation="Sales.SalesOrderDetail" />  
    </element>  
</ElementType>  
</Schema>  
```  
  
### <a name="c-inserting-a-record-by-using-the-parent-child-relationship-and-inverse-annotation-specified-in-the-xsd-schema"></a>В. Вставка записи с помощью связи «родители-потомки» и заметки INVERSE, указанных в схеме XSD  
 В этом примере показано, как в логике диаграммы обновления использует иерархические связи, указанной в XSD, для обработки обновлений и как **обратное** используется заметка. Дополнительные сведения о **обратное** заметки, см. в разделе [указания значения атрибута SQL: inverse для SQL: Relationship &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).  
  
 В этом примере предполагается, что следующие таблицы в **tempdb** базы данных:  
  
-   `Cust (CustomerID, CompanyName)`, где `CustomerID` — это первичный ключ;  
  
-   `Ord (OrderID, CustomerID)`, где `CustomerID` — это внешний ключ, который ссылается на первичный ключ `CustomerID` из таблицы `Cust`.  
  
 Для вставки записей в таблицы Cust и Ord в диаграмме обновления используется следующая схема XSD:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
       <sql:relationship name="OrdCust" inverse="true"  
                  parent="Ord"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Cust"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
<xsd:element name="Order" sql:relation="Ord">  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customer" sql:relationship="OrdCust"/>  
    </xsd:sequence>  
    <xsd:attribute name="OrderID"   type="xsd:int"/>  
    <xsd:attribute name="CustomerID" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
<xsd:element name="Customer" sql:relation="Cust">  
  <xsd:complexType>  
     <xsd:attribute name="CustomerID"  type="xsd:string"/>  
    <xsd:attribute name="CompanyName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
</xsd:schema>  
```  
  
 В этом примере схема XSD имеет  **\<клиента >** и  **\<порядок >** элементы и; она указывает отношение "родитель потомок" между двумя элементами. Он определяет  **\<порядок >** как родительский элемент и  **\<клиента >** как дочерний элемент.  
  
 Логика обработки диаграммы обновления использует данные о связи «родители-потомки» для определения порядка вставки записей в таблицы. В этом примере логика диаграммы обновления сначала пытается вставить запись в таблицу Ord (поскольку  **\<порядок >** является родительским) и пытается вставить запись в таблицу Cust (поскольку  **\<Клиента >** является дочерним элементом). Однако из-за данных «первичный-внешний ключ», которые содержатся в схеме таблицы базы данных, эта операция вставки ведет к нарушению внешнего ключа в базе данных и завершается неудачей.  
  
 Чтобы указать логике диаграммы обновления для отмены «родитель потомок» во время операции обновления, **обратное** задана заметка для  **\<связь >** элемент. В итоге записи будут сначала добавляться в таблицу Cust, а затем в таблицу Ord, и операция завершится успешно.  
  
 Следующая диаграмма обновления вставляет заказ (OrderID=2) в таблицу Ord, а клиента (CustomerID='AAAAA') — в таблицу Cust при помощи указанной схемы XSD:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before/>  
    <updg:after>  
      <Order OrderID="2" CustomerID="AAAAA" >  
        <Customer CustomerID="AAAAA" CompanyName="AAAAA Company" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Создайте следующие таблицы в **tempdb** базы данных:  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust(CustomerID varchar(5) primary key,   
                      CompanyName varchar(20))  
    GO  
    CREATE TABLE Ord (OrderID int primary key,   
                      CustomerID varchar(5) references Cust(CustomerID))  
    GO  
    ```  
  
2.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем SampleUpdateSchema.xml.  
  
3.  Скопируйте приведенный выше шаблон диаграммы обновления и вставьте его в текстовый файл. Сохраните файл под именем SampleUpdategram.xml в том же каталоге, где был сохранен файл SampleUpdateSchema.xml.  
  
     Путь к каталогу задается для схемы сопоставления (SampleUpdateSchema.xml) относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
4.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности диаграмм обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
