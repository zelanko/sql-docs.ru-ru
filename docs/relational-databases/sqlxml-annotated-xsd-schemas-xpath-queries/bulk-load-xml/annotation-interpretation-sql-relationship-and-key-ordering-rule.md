---
title: 'SQL: отношение и правило упорядочивания ключей (SQLXML 4,0) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- key ordering rules [SQLXML]
- relationship annotation
ms.assetid: 914cb152-09f5-4b08-b35d-71940e4e9986
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cb8807e5a5fe63ee18e6932d6e102175e3d6cc63
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72908740"
---
# <a name="annotation-interpretation---sqlrelationship-and-key-ordering-rule"></a>Интерпретация заметки — sql:relationship и правило упорядочения ключа
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Поскольку при массовой загрузке XML записи создаются в момент включения узлов в область действия, а затем отправляются в Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], то при их выходе из области действия данные для этих записей должны находиться в пределах области действия узла.  
  
 Рассмотрим следующую схему XSD, в которой отношение "один ко многим" между **\<клиент >** и **\<порядок >** элементов (один клиент может поместить много заказов) указывается с помощью **\<SQL: relationship >** элемент:  
  
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
  
 Когда **\<клиентский элемент >** входит в область, при выполнении групповой загрузки XML создается запись о клиенте. Эта запись остается до тех пор, пока не будет выполнена операция загрузки XML **\</Customer >** . При обработке узла элемента **> порядка\<** , при выполнении групповой загрузки XML используется **\<sql: relationship >** для получения значения столбца внешнего ключа CustomerID таблицы CustOrder из **\<ого родительского элемента Customer >** . Поскольку элемент **> порядка\<** не указывает атрибут **CustomerID** . Это означает, что при определении элемента **\<Customer >** необходимо указать атрибут **CustomerID** в схеме, прежде чем указать **\<SQL: relationship >** . В противном случае, когда элемент **\<порядок >** входит в область, при выполнении групповой загрузки XML создается запись для таблицы CustOrder, а при выполнении групповой загрузки xml — **\</Order >** закрывающий тег, он отправляет запись в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] без Значение столбца внешнего ключа CustomerID.  
  
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
  
     В результате массовая загрузка XML вставит значение NULL во внешний ключевой столбец CustomerID в таблице CustOrder. Если вы пересмотрите образец XML-данных, чтобы **\<элемент CustomerID >** дочерним элементом **\<** дочернего элемента, вы получаете ожидаемый результат: при выполнении операции XML-загрузки в столбец вставляется указанное значение внешнего ключа.  
  
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
  
  
