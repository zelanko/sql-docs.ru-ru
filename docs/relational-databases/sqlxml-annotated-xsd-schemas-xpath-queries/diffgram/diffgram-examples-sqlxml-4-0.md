---
title: Примеры дельт (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], examples
- examples [SQLXML], DiffGram
- diffgr:parentID
- parentID annotation
ms.assetid: fc148583-dfd3-4efb-a413-f47b150b0975
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c3738a54ab06b6dd3f0a63f79c53ee46d8c1664
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43104726"
---
# <a name="diffgram-examples-sqlxml-40"></a>Примеры дельт (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Примеры в данном разделе состоят из нескольких дельт (DiffGram), которые выполняют операции вставки, обновления и удаления в базе данных. При использовании этих примеров необходимо учитывать следующие моменты.  
  
-   Примеры используют две таблицы (Cust и Ord), которые необходимо создать, если требуется проверить примеры дельт:  
  
    ```  
    Cust(CustomerID, CompanyName, ContactName)  
    Ord(OrderID, CustomerID)  
    ```  
  
-   Большинство примеров в данном разделе используют следующую схему XSD:  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
    <xsd:annotation>  
      <xsd:documentation>  
        Diffgram Customers/Orders Schema.  
      </xsd:documentation>  
      <xsd:appinfo>  
           <sql:relationship name="CustomersOrders"   
                      parent="Cust"  
                      parent-key="CustomerID"  
                      child-key="CustomerID"  
                      child="Ord"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
    <xsd:element name="Customer" sql:relation="Cust">  
      <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="CompanyName"    type="xsd:string"/>  
          <xsd:element name="ContactName"    type="xsd:string"/>  
           <xsd:element name="Order" sql:relation="Ord" sql:relationship="CustomersOrders">  
            <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:int" sql:field="OrderID"/>  
              <xsd:attribute name="CustomerID" type="xsd:string"/>  
            </xsd:complexType>  
          </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID" type="xsd:string" sql:field="CustomerID"/>  
      </xsd:complexType>  
    </xsd:element>  
  
    </xsd:schema>     
    ```  
  
     Сохраните данную схему под именем DiffGramSchema.xml в той же папке, где находятся остальные файлы, используемые в примерах.  
  
## <a name="a-deleting-a-record-by-using-a-diffgram"></a>A. Удаление записи с помощью дельты  
 Дельта в этом примере удаляет запись пользователя (с атрибутом CustomerID, имеющим значение ALFKI) из таблицы Cust и удаляет соответствующую запись заказа (с атрибутом OrderID со значением 1) из таблицы Ord.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance/>  
  
    <diffgr:before>  
        <Order diffgr:id="Order1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI"   
               OrderID="1"/>  
        <Customer diffgr:id="Customer1"   
                  msdata:rowOrder="0"   
                  CustomerID="ALFKI">  
           <CompanyName>Alfreds Futterkiste</CompanyName>  
           <ContactName>Maria Anders</ContactName>  
        </Customer>  
    </diffgr:before>  
    <msdata:errors/>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 В  **\<перед >** block, имеется  **\<порядок >** элемент (**diffgr: ID = «Order1»**) и  **\< Customer >** элемент (**diffgr: ID = «Customer1»**). Данные элементы представляют существующие записи в базе данных. **\<DataInstance >** элемент не имеет соответствующих записей (с тем же **diffgr: ID**). Это указывает на операцию удаления.  
  
#### <a name="to-test-the-diffgram"></a>Проверка дельты  
  
1.  Создайте следующие таблицы в **tempdb** базы данных.  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  Добавьте следующий образец данных:  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquería', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  Скопируйте приведенную выше дельту и вставьте ее в текстовый файл. Сохраните файл с именем MyDiffGram.xml в папке, которая использовалась на предыдущем шаге.  
  
4.  Скопируйте схему DiffGramSchema, приведенную ранее в этом разделе, и вставьте ее в текстовый файл. Сохраните файл с именем DiffGramSchema.xml.  
  
5.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить дельту.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="b-inserting-a-record-by-using-a-diffgram"></a>Б. Вставка записи с помощью дельты  
 В этом примере дельта вставляет по одной записи в таблицы Cust и Ord.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"   
      sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
          xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
          xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
       <Customer diffgr:id="Customer1" msdata:rowOrder="0"    
                 diffgr:hasChanges="inserted" CustomerID="ALFKI">  
        <CompanyName>C3Company</CompanyName>  
        <ContactName>C3Contact</ContactName>  
        <Order diffgr:id="Order1"   
               msdata:rowOrder="0"  
               diffgr:hasChanges="inserted"   
               CustomerID="ALFKI" OrderID="1"/>  
      </Customer>  
    </DataInstance>  
  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 В данной Дельте  **\<перед >** блок не указывается (не существующие записи базы данных определены). Существуют два экземпляра записи (определяется  **\<клиента >** и  **\<порядок >** элементов в  **\<DataInstance >** блока), которые соответствуют таблицам Cust и Ord, соответственно. Оба эти элемента укажите **diffgr: HasChanges** атрибут (**hasChanges = «inserted»**). Это указывает на операцию вставки. В данной Дельте, если указать **hasChanges = «modified»**, вы указываете, что вы хотите изменить запись, которая не существует, который приводит к ошибке.  
  
#### <a name="to-test-the-diffgram"></a>Проверка дельты  
  
1.  Создайте следующие таблицы в **tempdb** базы данных.  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  Добавьте следующий образец данных:  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquería', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  Скопируйте приведенную выше дельту и вставьте ее в текстовый файл. Сохраните файл с именем MyDiffGram.xml в папке, которая использовалась на предыдущем шаге.  
  
4.  Скопируйте схему DiffGramSchema, приведенную ранее в этом разделе, и вставьте ее в текстовый файл. Сохраните файл с именем DiffGramSchema.xml.  
  
5.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить дельту.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="c-updating-an-existing-record-by-using-a-diffgram"></a>В. Обновление существующей записи с помощью дельты  
 В этом примере дельта обновляет CompanyName и ContactName для клиента ALFKI.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer1"   
                msdata:rowOrder="0" diffgr:hasChanges="modified"   
                CustomerID="ALFKI">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Antonio Moreno</ContactName>  
      </Customer>  
    </DataInstance>  
  
    <diffgr:before>  
     <Customer diffgr:id="Customer1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
    </diffgr:before>  
  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 **\<Перед >** блок содержит  **\<клиента >** элемент (**diffgr: ID = «Customer1»**). **\<DataInstance >** блок содержит соответствующий  **\<клиента >** элемент с таким же **идентификатор**.  **\<Клиента >** элемент в  **\<NewDataSet >** также указывает **diffgr: HasChanges = «modified»**. Он означает операции обновления, а также запись о заказчике в **Cust** таблица обновляется соответствующим образом. Обратите внимание, что если **diffgr: HasChanges** атрибут не указан, то логика обработки дельты пропустит этот элемент и обновления не выполняются.  
  
#### <a name="to-test-the-diffgram"></a>Проверка дельты  
  
1.  Создайте следующие таблицы в **tempdb** базы данных.  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  Добавьте следующий образец данных:  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquería', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  Скопируйте приведенную выше дельту и вставьте ее в текстовый файл. Сохраните файл с именем MyDiffGram.xml в папке, которая использовалась на предыдущем шаге.  
  
4.  Скопируйте схему DiffGramSchema, приведенную ранее в этом разделе, и вставьте ее в текстовый файл. Сохраните файл с именем DiffGramSchema.xml.  
  
5.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить дельту.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="d-inserting-updating-and-deleting-records-by-using-a-diffgram"></a>Г. Вставка, обновление и удаление записей с помощью дельты  
 В этом примере относительно сложная дельта используется для выполнения операций вставки, обновления и удаления.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer2" msdata:rowOrder="1"   
                diffgr:hasChanges="modified"   
                CustomerID="ANATR">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Elizabeth Lincoln</ContactName>  
          <Order diffgr:id="Order2" msdata:rowOrder="1"   
               msdata:hiddenCustomerID="ANATR"   
               CustomerID="ANATR" OrderID="2"/>  
      </Customer>  
  
      <Customer diffgr:id="Customer3" msdata:rowOrder="2"   
                CustomerID="ANTON">  
         <CompanyName>Chop-suey Chinese</CompanyName>  
         <ContactName>Yang Wang</ContactName>  
         <Order diffgr:id="Order3" msdata:rowOrder="2"   
               msdata:hiddenCustomerID="ANTON"   
               CustomerID="ANTON" OrderID="3"/>  
      </Customer>  
      <Customer diffgr:id="Customer4" msdata:rowOrder="3"   
                diffgr:hasChanges="inserted"   
                CustomerID="AROUT">  
         <CompanyName>Around the Horn</CompanyName>  
         <ContactName>Thomas Hardy</ContactName>  
         <Order diffgr:id="Order4" msdata:rowOrder="3"   
                diffgr:hasChanges="inserted"   
                msdata:hiddenCustomerID="AROUT"   
               CustomerID="AROUT" OrderID="4"/>  
      </Customer>  
    </DataInstance>  
    <diffgr:before>  
      <Order diffgr:id="Order1" msdata:rowOrder="0"   
             msdata:hiddenCustomerID="ALFKI"   
             CustomerID="ALFKI" OrderID="1"/>  
      <Customer diffgr:id="Customer1" msdata:rowOrder="0"   
                CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
      <Customer diffgr:id="Customer2" msdata:rowOrder="1"   
                CustomerID="ANATR">  
        <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
        <ContactName>Ana Trujillo</ContactName>  
      </Customer>  
    </diffgr:before>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 Логика работы с дельтами обрабатывает эту дельту следующим образом.  
  
-   В соответствии с логикой обработки дельт все элементы верхнего уровня в  **\<перед >** block карте определенным таблицам, как описано в схеме сопоставления.  
  
-   **\<Перед >** блок содержит  **\<порядок >** элемент (**dffgr:id = «Order1»**) и  **\<клиента >** элемент (**diffgr: ID = «Customer1»**), для которого отсутствует соответствующий элемент в  **\<DataInstance >** блоке (с одинаковым Идентификатором). Это указывает на операцию удаления, во время которой записи удаляются из таблиц Cust и Ord.  
  
-   **\<Перед >** блок содержит  **\<клиента >** элемент (**diffgr: ID = «Customer2»**) для которого существует соответствующий  **\<Клиента >** элемент в  **\<DataInstance >** блоке (с одинаковым Идентификатором). Элемент в  **\<DataInstance >** указывает блок **diffgr: HasChanges = «modified»**. Это операция обновления, в которой для пользователя anatr, CompanyName и ContactName данные обновляются в таблице Cust, с помощью значений, указанных в  **\<DataInstance >** блока.  
  
-   **\<DataInstance >** блок содержит  **\<клиента >** элемент (**diffgr: ID = «Customer3»**) и  **\<Порядок >** элемент (**diffgr: ID = «Order3»**). Ни один из этих элементов укажите **diffgr: HasChanges** атрибута. Таким образом, логика обработки дельт не учитывает эти элементы.  
  
-   **\<DataInstance >** блок содержит  **\<клиента >** элемент (**diffgr: ID = «Customer4»**) и  **\<Порядок >** элемент (**diffgr: ID = «Order4»**) для которых существует соответствующий элемент в \<перед > блока. Эти элементы в  **\<DataInstance >** указать блок **diffgr: HasChanges = «inserted»**. Таким образом, в таблицы Cust и Ord добавляется новая запись.  
  
#### <a name="to-test-the-diffgram"></a>Проверка дельты  
  
1.  Создайте следующие таблицы в **tempdb** базы данных.  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  Добавьте следующий образец данных:  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquería', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  Скопируйте приведенную выше дельту и вставьте ее в текстовый файл. Сохраните файл с именем MyDiffGram.xml в папке, которая использовалась на предыдущем шаге.  
  
4.  Скопируйте схему DiffGramSchema, приведенную ранее в этом разделе, и вставьте ее в текстовый файл. Сохраните файл с именем DiffGramSchema.xml.  
  
5.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить дельту.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="e-applying-updates-by-using-a-diffgram-with-the-diffgrparentid-annotation"></a>Д. Применение обновлений с помощью дельты с заметкой diffgr:parentID  
 В этом примере показано, как **parentID** заметка, указанная в  **\<перед >** блок DiffGram используется в применении обновлений.  
  
```  
<NewDataSet />  
<diffgr:before>  
   <Order diffgr:id="Order1" msdata:rowOrder="0" OrderID="2" />  
   <Order diffgr:id="Order3" msdata:rowOrder="2" OrderID="4" />  
  
   <OrderDetail diffgr:id="OrderDetail1"   
                diffgr:parentId="Order1"   
                msdata:rowOrder="0"   
                ProductID="13"   
                OrderID="2" />  
   <OrderDetail diffgr:id="OrderDetail3"   
                diffgr:parentId="Order3"  
                ProductID="77"  
                OrderID="4"/>  
</diffgr:before>  
</diffgr:diffgram>  
```  
  
 Данный объект DiffGram указывает операцию удаления, так как имеется только  **\<перед >** блока. В Дельте **parentID** Определение отношения родитель потомок между заказами и сведения о заказе, используется заметка. При удалении записей посредством SQLXML они удаляются из дочерней таблицы, указанной этой связью, а после этого из соответствующей родительской таблицы.  
  
  
