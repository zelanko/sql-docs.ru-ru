---
title: 'Задание связей с помощью SQL: Relationship (SQLXML)'
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- parent attribute [SQLXML]
- element relationships [SQLXML]
- multiple element relationships
- attribute relationships [SQLXML]
- sql:relationship
- relationship chains [SQLXML]
- IDREF relationships [SQLXML]
- parent-child relationships [SQLXML]
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- relationships [SQLXML], specifying
- unnamed relationships
- ID relationships [SQLXML]
- hierarchical relationships [SQLXML]
- named relationships [SQLXML]
ms.assetid: 98820afa-74e1-4e62-b336-6111a3dede4c
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 02872a037e60fa3af58a70d3599b03c61d0cfb5e
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75257341"
---
# <a name="specifying-relationships-using-sqlrelationship-sqlxml-40"></a>Указание связей при помощи sql:relationship (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Элементы в XML-документе могут участвовать в связях. Элементы могут иметь иерархическую вложенность, и между ними могут быть заданы связи ID, IDREF или IDREFS.  
  
 Например, в схеме XSD элемент ** \<Customer>** содержит ** \<Order>** дочерние элементы. Когда схема сопоставляется с базой данных AdventureWorks, элемент ** \<Customer>** сопоставляется с таблицей Sales. Customer, а элемент ** \<Order>** сопоставляется с таблицей Sales. SalesOrderHeader. Базовые таблицы Sales.Customer и Sales.SalesOrderHeader связаны, так как заказчики размещают заказы. CustomerID в таблице Sales.SalesOrderHeader представляет собой внешний ключ, ссылающийся на первичный ключ CustomerID в таблице Sales.Customer. Эти связи можно установить между элементами схемы сопоставления с помощью аннотации **SQL: relationship** .  
  
 В схеме XSD с заметками схема **SQL: relationship** используется для иерархического вложения элементов схемы на основе связей первичного и внешнего ключей между базовыми таблицами, в которые сопоставляются элементы. При указании аннотации **SQL: relationship** необходимо определить следующее:  
  
-   Родительская таблица (Sales.Customer) и дочерняя таблица (Sales.SalesOrderHeader).  
  
-   Столбец или столбцы, представляющие связь между родительской и дочерней таблицами. Например, столбец CustomerID, который присутствует как в родительской, так и в дочерней таблицах.  
  
 Эти сведения используются для правильного создания иерархии.  
  
 Чтобы указать имена таблиц и необходимые сведения о соединении, в заметке **SQL: relationship** указаны следующие атрибуты. Эти атрибуты допустимы только с элементом ** \<SQL: relationship>** .  
  
 **Безымян**  
 Указывает уникальное имя связи.  
  
 **Родительский элемент**  
 Задает родительскую связь (таблицу). Это необязательный атрибут. Если он не указан, то имя родительской таблицы будет получено из дочерней иерархии в документе. Если в схеме указаны две иерархии «родители-потомки», использующие одну и ту же ** \<связь SQL:>** , но разные родительские элементы, то родительский атрибут не указывается в ** \<SQL: relationship>**. Эти сведения будут получены из иерархии в схеме.  
  
 **parent-key**  
 Указывает родительский ключ для родителя. Если родительский ключ состоит из нескольких столбцов, то они должны быть перечислены через пробелы. Между значениями, заданными для ключа, состоящего из нескольких столбцов, и соответствующего дочернего ключа, существует позиционное сопоставление.  
  
 **Дочерний**  
 Задает дочернюю связь (таблицу).  
  
 **child-key**  
 Задает дочерний ключ потомка, который ссылается на атрибут parent-key родителя. Если дочерний ключ состоит из нескольких атрибутов (столбцов), то значения атрибута child-key должны быть перечислены через пробелы. Между значениями, заданными для ключа, состоящего из нескольких столбцов, и соответствующего родительского ключа, существует позиционное сопоставление.  
  
 **Inverse**  
 Этот атрибут, указанный в ** \<SQL: relationship>** , используется диаграмм обновления. Дополнительные сведения см. в разделе [Указание атрибута SQL: инверсии в SQL: relationship](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).  
  
 Заметка **SQL: Key-Fields** должна быть указана в элементе, содержащем дочерний элемент, который имеет ** \<>SQL: relationship** , определенный между элементом и дочерним объектом и не предоставляющий первичный ключ таблицы, указанной в родительском элементе. Даже если схема не указывает ** \<SQL: relationship>**, необходимо указать **SQL: Key-Fields** , чтобы создать правильную иерархию. Дополнительные сведения см. в разделе [Определение ключевых столбцов с помощью SQL: Key-Fields](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md).  
  
 Чтобы создать правильное вложение в результате, рекомендуется, чтобы **поля SQL: Key-Field** были указаны во всех схемах.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlrelationship-annotation-on-an-element"></a>а. Определение заметки sql:relationship для элемента  
 Следующая схема XSD с заметками включает в себя ** \<>клиента** и ** \<порядок>** элементов. Элемент ** \<Order>** является дочерним элементом элемента ** \<>Customer** .  
  
 В схеме Аннотация **SQL: relationship** задана для дочернего элемента ** \<Order>** . Сама связь определяется в элементе ** \<XSD: appinfo>** .  
  
 Элемент ** \<Relationship>** идентифицирует CustomerID в таблице Sales. SalesOrderHeader как внешний ключ, который ссылается на первичный ключ CustomerID в таблице Sales. Customer. Таким образом, заказы, принадлежащие клиенту, отображаются как дочерний элемент элемента ** \<>Customer** .  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                    sql:relationship="CustOrders" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 В предыдущей схеме используется именованная связь. Можно также указать неименованную связь. Результаты будут одинаковы.  
  
 Ниже приведена новый вариант схемы, в которой определена неименованная связь.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer"  type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader">  
           <xsd:annotation>  
            <xsd:appinfo>  
              <sql:relationship   
                parent="Sales.Customer"  
                parent-key="CustomerID"  
                child="Sales.SalesOrderHeader"  
                child-key="CustomerID" />  
            </xsd:appinfo>  
           </xsd:annotation>  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем sql-relationship.xml.  
  
2.  Скопируйте приведенный ниже шаблон и вставьте его в текстовый файл. Сохраните файл под именем sql-relationshipT.xml в том же каталоге, где был сохранен файл sql-relationship.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-relationship.xml">  
            /Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл sql-relationship.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\sql-relationship.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Результирующий набор:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1">   
    <Order OrderID="43860" CustomerID="1" />   
    <Order OrderID="44501" CustomerID="1" />   
    <Order OrderID="45283" CustomerID="1" />   
    <Order OrderID="46042" CustomerID="1" />   
  </Customer>   
</ROOT>  
```  
  
### <a name="b-specifying-a-relationship-chain"></a>B. Указание цепочки связей  
 Для данного примера предположим, что в следующем XML-документе нужно использовать данные, полученные из базы данных AdventureWorks:  
  
```  
<Order SalesOrderID="43659">  
  <Product Name="Mountain Bike Socks, M"/>   
  <Product Name="Sport-100 Helmet, Blue"/>  
  ...  
</Order>  
...  
```  
  
 Для каждого заказа в таблице Sales. SalesOrderHeader XML-документ содержит один ** \<элемент>заказа** . Каждый ** \<элемент>заказа** имеет список дочерних элементов ** \<>продукта** , по одному для каждого продукта, запрошенного в заказе.  
  
 Чтобы указать схему XSD, которая будет создавать эту иерархию, необходимо указать две связи: Ордерод и ODProduct. Связь OrderOD определяет связь типа «родитель-потомок» между таблицами Sales.SalesOrderHeader и Sales.SalesOrderDetail. Связь ODProduct определяет связь между таблицами Sales.SalesOrderDetail и Production.Product.  
  
 В следующей схеме Аннотация **msdata: relationship** в элементе ** \<>Product** определяет два значения: ордерод и ODProduct. Порядок следования этих значений важен.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <msdata:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  
    <msdata:relationship name="ODProduct"  
          parent="Sales.SalesOrderDetail"  
          parent-key="ProductID"  
          child="Production.Product"  
          child-key="ProductID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID"  
                     msdata:relationship="OrderOD ODProduct">  
          <xsd:complexType>  
             <xsd:attribute name="Name" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
    </xsd:complexType>  
</xsd:schema>  
```  
  
 Вместо указания именованной связи можно задать анонимную связь. В этом случае все содержимое ** \<заметки>**... /аннотатион>, описывающие эти две связи, отображаются как дочерний элемент ** \<>продукта **. ** \< **  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID" >  
         <xsd:annotation>  
          <xsd:appinfo>  
           <msdata:relationship   
               parent="Sales.SalesOrderHeader"  
               parent-key="SalesOrderID"  
               child="Sales.SalesOrderDetail"  
               child-key="SalesOrderID" />  
  
           <msdata:relationship   
               parent="Sales.SalesOrderDetail"  
               parent-key="ProductID"  
               child="Production.Product"  
               child-key="ProductID" />  
         </xsd:appinfo>  
       </xsd:annotation>  
       <xsd:complexType>  
          <xsd:attribute name="Name" type="xsd:string" />  
       </xsd:complexType>  
     </xsd:element>  
   </xsd:sequence>  
   <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
  </xsd:complexType>  
 </xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем relationshipChain.xml.  
  
2.  Скопируйте приведенный ниже шаблон и вставьте его в текстовый файл. Сохраните файл под именем relationshipChainT.xml в том же каталоге, где был сохранен файл relationshipChain.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationshipChain.xml">  
            /Order  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу для схемы сопоставления (файл relationshipChain.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\relationshipChain.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Результирующий набор:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Order SalesOrderID="43659">  
    <Product Name="Mountain Bike Socks, M" />   
    <Product Name="Sport-100 Helmet, Blue" />   
    <Product Name="AWC Logo Cap" />   
    <Product Name="Long-Sleeve Logo Jersey, M" />   
    <Product Name="Long-Sleeve Logo Jersey, XL" />   
    ...  
  </Order>  
  ...  
</ROOT>  
```  
  
### <a name="c-specifying-the-relationship-annotation-on-an-attribute"></a>C. Задание заметки relationship для атрибута  
 Схема в этом примере включает элемент \<Customer> с дочерним \<элементом CustomerID> и атрибутом ордеридлист типа IDREFS. Элемент \<Customer> сопоставляется с таблицей Sales. Customer в базе данных AdventureWorks. По умолчанию область этого сопоставления применяется ко всем дочерним элементам или атрибутам, если только в дочернем элементе или атрибуте не задано значение **SQL: relation** , и в этом случае соответствующая связь типа "первичный ключ — \<внешний ключ" должна быть определена с помощью элемента> связи. И дочерний элемент или атрибут, указывающий другую таблицу с помощью аннотации **связи** , должен также указывать заметку **Relationship** .  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="CustomerID"   type="xsd:string" />   
     </xsd:sequence>  
     <xsd:attribute name="OrderIDList"   
                     type="xsd:IDREFS"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:field="SalesOrderID"  
                     sql:relationship="CustOrders" >  
        </xsd:attribute>  
    </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем relationship-on-attribute.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в файл. Сохраните файл под именем relationship-on-attributeT.xml в том же каталоге, где был сохранен файл relationship-on-attribute.xml. Запрос в шаблоне выберет клиента со значением идентификатора ContactID, равным 1.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-on-attribute.xml">  
        /Customer[CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл relationship-on-attribute.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\relationship-on-attribute.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Результирующий набор:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer OrderIDList="43860 44501 45283 46042">  
    <CustomerID>1</CustomerID>   
  </Customer>  
</ROOT>  
```  
  
### <a name="d-specifying-sqlrelationship-on-multiple-elements"></a>D. Задание sql:relationship для нескольких элементов  
 В этом примере схема XSD с заметками содержит элементы " ** \<клиент>**, ** \<" порядок>**"и ** \<" OrderDetail>** ".  
  
 Элемент ** \<Order>** является дочерним элементом элемента ** \<>Customer** . ** \<** **SQL: relationship>задано для дочернего \<** элемента Order>; Таким образом, заказы, принадлежащие клиенту, отображаются как дочерние элементы ** \<>клиента **.  
  
 Элемент ** \<Order>** включает дочерний элемент ** \<OrderDetail>** . ** \<** ** \<SQL: relationship>** задано для дочернего элемента OrderDetail>, поэтому сведения о заказе, относящиеся к заказу, отображаются как дочерние элементы этого ** \<порядка>** элемента.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
        parent="Sales.Customer"  
        parent-key="CustomerID"  
        child="Sales.SalesOrderHeader"  
        child-key="CustomerID" />  
  
    <sql:relationship name="OrderOrderDetail"  
        parent="Sales.SalesOrderHeader"  
        parent-key="SalesOrderID"  
        child="Sales.SalesOrderDetail"  
        child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"    
              sql:relationship="CustOrders" maxOccurs="unbounded" >  
          <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OrderDetail"   
                             sql:relation="Sales.SalesOrderDetail"   
                             sql:relationship="OrderOrderDetail"   
                             maxOccurs="unbounded" >  
                  <xsd:complexType>  
                    <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                    <xsd:attribute name="ProductID" type="xsd:string" />  
                    <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  </xsd:complexType>  
                </xsd:element>  
              </xsd:sequence>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем relationship-multiple-elements.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните файл под именем relationship-multiple-elementsT.xml в том же каталоге, где был сохранен файл relationship-multiple-elements.xml. Запрос в шаблоне возвращает сведения о заказчиках со значением CustomerID, равным 1, и SalesOrderID, равным 43860.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-multiple-elements.xml">  
        /Customer[@CustomerID=1]/Order[@SalesOrderID=43860]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл relationship-multiple-elements.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\relationship-multiple-elements.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Результирующий набор:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1">  
     <OrderDetail SalesOrderID="43860" ProductID="761" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="770" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="758" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="765" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="762" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="768" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="763" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="756" OrderQty="1" />   
  </Order>  
</ROOT>  
```  
  
### <a name="e-specifying-the-sqlrelationship-without-the-parent-attribute"></a>E. Указание> \<SQL: relationship без родительского атрибута  
 В этом примере показано, ** \<как задать>SQL: relationship** без **родительского** атрибута. Предположим, имеется следующая таблица сотрудников.  
  
```  
Emp1(SalesPersonID, FirstName, LastName, ReportsTo)  
Emp2(SalesPersonID, FirstName, LastName, ReportsTo)  
```  
  
 Следующее XML-представление содержит элементы ** \<Emp1>** и ** \<Emp2>** , сопоставленные с таблицами Sales. Emp1 и Sales. Emp2:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="EmpOrders"  
          parent-key="SalesPersonID"  
          child="Sales.SalesOrderHeader"  
          child-key="SalesPersonID" />  
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Emp1" sql:relation="Sales.Emp1" type="EmpType" />  
  <xsd:element name="Emp2" sql:relation="Sales.Emp2" type="EmpType" />  
   <xsd:complexType name="EmpType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:relationship="EmpOrders" >  
          <xsd:complexType>  
             <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesPersonID"   type="xsd:integer" />   
        <xsd:attribute name="LastName"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 В схеме элемент ** \<Emp1>** и ** \<Emp2>** имеют тип **емптипе**. Тип **емптипе** описывает ** \<заказ>** дочерний элемент и соответствующую ** \<>SQL: relationship **. В этом случае отсутствует один родительский элемент, который может быть идентифицирован в ** \<SQL: relationship>** с помощью **родительского** атрибута. В этом случае **родительский** атрибут не указывается в ** \<SQL: relationship>**. сведения о **родительском** атрибуте получаются из иерархии схемы.  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Создайте следующие таблицы в базе данных AdventureWorks.  
  
    ```  
    USE AdventureWorks  
    CREATE TABLE Sales.Emp1 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    CREATE TABLE Sales.Emp2 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    ```  
  
2.  Добавьте следующий образец данных в таблицы.  
  
    ```  
    INSERT INTO Sales.Emp1 values (279, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Sales.Emp1 values (282, 'Andrew', 'Fuller',1)  
    INSERT INTO Sales.Emp1 values (276, 'Janet', 'Leverling',1)  
    INSERT INTO Sales.Emp2 values (277, 'Margaret', 'Peacock',3)  
    INSERT INTO Sales.Emp2 values (283, 'Steven', 'Devolio',4)  
    INSERT INTO Sales.Emp2 values (275, 'Nancy', 'Buchanan',5)  
    INSERT INTO Sales.Emp2 values (281, 'Michael', 'Suyama',6)  
    ```  
  
3.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем relationship-noparent.xml.  
  
4.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните файл под именем relationship-noparentT.xml в том же каталоге, где был сохранен файл relationship-noparent.xml. Запрос в шаблоне выбирает все элементы> \<Emp1 (таким образом, родительским элементом является Emp1).  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationship-noparent.xml">  
            /Emp1  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл relationship-noparent.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\relationship-noparent.xml"  
    ```  
  
5.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Вот частичный результирующий набор:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<Emp1 SalesPersonID="276" LastName="Leverling">  
  <Order SalesOrderID="43663" CustomerID="510" />   
  <Order SalesOrderID="43666" CustomerID="511" />   
  <Order SalesOrderID="43859" CustomerID="259" />  
  ...  
</Emp1>  
```  
  
  
