---
title: 'SQL: отношение и правило упорядочивания ключей (SQLXML 4,0) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- key ordering rules [SQLXML]
- relationship annotation
ms.assetid: 914cb152-09f5-4b08-b35d-71940e4e9986
author: rothja
ms.author: jroth
ms.openlocfilehash: 10e8dc24c3c9ce234314a793ecdc1c9b41c0f3dd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068222"
---
# <a name="sqlrelationship-and-the-key-ordering-rule-sqlxml-40"></a>sql:relationship и правило упорядочения ключа (SQLXML 4.0)
  Поскольку при массовой загрузке XML записи создаются в момент включения узлов в область действия, а затем отправляются в Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], то при их выходе из области действия данные для этих записей должны находиться в пределах области действия узла.  
  
 Рассмотрим следующую схему XSD, в которой связь "один ко многим" между **\<Customer>** **\<Order>** элементами и (один клиент может разместить много заказов) указывается с помощью `<sql:relationship>` элемента:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"<>   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Когда **\<Customer>** узел Element входит в область, при выполнении групповой загрузки XML создается запись о клиенте. Эта запись остается до тех пор, пока не будет выполнена операция загрузки XML-операций **\</Customer>** . При обработке **\<Order>** узла Element функция XML с массовым использованием использует `<sql:relationship>` для получения значения столбца внешнего ключа CustomerID таблицы CustOrder из **\<Customer>** родительского элемента, поскольку **\<Order>** элемент не указывает атрибут **CustomerID** . Это означает, что при определении **\<Customer>** элемента необходимо указать атрибут **CustomerID** в схеме перед тем, как указать `<sql:relationship>` . В противном случае, когда **\<Order>** элемент входит в область, при выполнении XML-загрузки с помощью операции «Автозагрузка» создается запись для таблицы CustOrder, а при выполнении групповой загрузки XML-данных **\</Order>** закрывающий тег отправляет запись [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] без значения столбца внешнего ключа CustomerID.  
  
 Сохраните схему, приведенную в этом примере, в файле SampleSchema.xml.  
  
### <a name="to-test-a-working-sample"></a>Проверка рабочего образца  
  
1.  Создайте следующие таблицы.  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
               CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
               CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
2.  Сохраните следующие образцы данных в файле SampleXMLData.xml.  
  
    ```  
    <ROOT>    
      <Customers>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
        <CustomerID>1111</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>    
        <Order OrderID="3" />  
        <CustomerID>1112</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
        <CustomerID>1113</CustomerID>  
      </Customers>  
    </ROOT>  
    ```  
  
3.  Чтобы выполнить массовую загрузку XML-данных, сохраните этот пример на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) в файле MySample.vbs и выполните его.  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
     В результате массовая загрузка XML вставит значение NULL во внешний ключевой столбец CustomerID в таблице CustOrder. Если вы пересмотрите образец XML-данных, чтобы **\<CustomerID>** дочерний элемент появился перед **\<Order>** дочерним элементом, будет получен ожидаемый результат: при выполнении операции XML-загрузки в столбец будет вставлено указанное значение внешнего ключа.  
  
 Эквивалентная схема XDR:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID"  />  
   <ElementType name="CompanyName" />  
   <ElementType name="City"        />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
                 <sql:relationship  
                        key-relation    ="Cust"  
                        key             ="CustomerID"  
                        foreign-key     ="CustomerID"  
                        foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
  
