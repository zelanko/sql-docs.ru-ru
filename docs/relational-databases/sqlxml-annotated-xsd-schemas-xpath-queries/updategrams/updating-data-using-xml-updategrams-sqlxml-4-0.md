---
title: Обновление данных с помощью диаграмм обновления XML (SQLXML 4.0) | Документы Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDREF type attribute [SQLXML]
- before attribute
- <sync> block
- <after> block
- id attribute
- <before> block
- updg:after attribute
- mapping-schema attribute
- IDREFS type attribute [SQLXML]
- updg:id attribute
- multiple record updates
- after attribute
- updategrams [SQLXML], updating data
- updg:before attribute
- record updates [SQLXML]
ms.assetid: 90ef8a33-5ae3-4984-8259-608d2f1d727f
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 613fe19b4cb3a63b1998cfa5ef2c6a7368481c6c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="updating-data-using-xml-updategrams-sqlxml-40"></a>Обновление данных при помощи диаграмм обновления XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  При обновлении существующих данных, то необходимо задать и  **\<перед >** и  **\<после >** блоков. Элементы, указанные в  **\<перед >** и  **\<после >** блоки описывают нужное изменение. Диаграмма обновления использует элементы, которые указаны в  **\<перед >** блока для идентификации существующих записей в базе данных. Соответствующие элементы в  **\<после >** блок указывают, как должна выглядеть запись после выполнения операции обновления. На основе данных, диаграмма обновления создает инструкцию SQL, который соответствует  **\<после >** блока. Затем диаграмма обновления использует эту инструкцию для обновления базы данных.  
  
 Ниже представлен формат диаграммы обновления для операции обновления.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
      <ElementName [updg:id="value"] .../>  
      [<ElementName [updg:id="value"] .../> ... ]  
   </updg:before>  
   <updg:after>  
      <ElementName [updg:id="value"] ... />  
      [<ElementName [updg:id="value"] .../> ...]  
   </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 **\<updg:before>**  
 Элементы в  **\<перед >** блок указывают существующие записи в таблицах базы данных.  
  
 **\<updg:after>**  
 Элементы в  **\<после >** блок описывают, как записи, указанные в  **\<перед >** блок должен выглядеть после применения обновлений.  
  
 **Схемы сопоставления** атрибут идентифицирует схему сопоставления для использования в диаграмме обновления. Если диаграмма обновления указывает схему сопоставления, имена элементов и атрибутов, указанные в  **\<перед >** и  **\<после >** блоки должны совпадать с именами в схеме. Схема сопоставления сопоставляет эти имена элементов или атрибутов с именами таблиц и столбцов в базе данных.  
  
 Если в диаграмме обновления не указана схема, используется сопоставление по умолчанию. При сопоставлении по умолчанию,  **\<ElementName >** указанный в диаграмме обновления, соответствует таблице базы данных и дочерние элементы или атрибуты сопоставляются со столбцами базы данных.  
  
 Элемент в  **\<перед >** блок должен соответствовать только одной строке таблицы в базе данных. Если элемент соответствует нескольким строкам таблицы или не соответствует ни одной строке, диаграмма обновления возвращает ошибку и отменяет весь  **\<синхронизации >** блока.  
  
 Диаграмма обновления может включать несколько  **\<синхронизации >** блоков. Каждый  **\<синхронизации >** блокировка, обрабатывается как транзакция. Каждый  **\<синхронизации >** блок может иметь несколько  **\<перед >** и  **\<после >** блоков. Например, при обновлении двух существующих записей, можно указать две  **\<перед >** и  **\<после >** пары, по одному для каждой обновляемой записи.  
  
## <a name="using-the-updgid-attribute"></a>Использование атрибута updg:id  
 Если указано несколько элементов в  **\<перед >** и  **\<после >** использовать блоки, **updg: ID** атрибута для отметки строк в  **\<перед >** и  **\<после >** блоков. Логика обработки использует эти сведения, чтобы определить, какие записи в  **\<перед >** блоках соответствие записей в  **\<после >** блока.  
  
 **Updg: ID** атрибут не требуется (хотя рекомендуется), если существует одно из следующих:  
  
-   Элементы в указанной схеме сопоставления имеют **SQL: Key-поля** определен атрибут.  
  
-   Для ключевых полей в диаграмме обновления указано одно или несколько значений.  
  
 Если либо выполняется, то диаграмма обновления использует ключевые столбцы, указанные в **SQL: Key-поля** для сопоставления элементов в  **\<перед >** и  **\< После >** блоков.  
  
 Если схема сопоставления не определяет ключевые столбцы (с помощью **SQL: Key-поля**) или если диаграмма обновления обновляет значение ключевого столбца, необходимо указать **updg: ID**.  
  
 Записи, которые определены в  **\<перед >** и  **\<после >** блоки не должны обязательно находиться в том же порядке. **Updg: ID** атрибут приводит связь между элементами, которые указаны в  **\<перед >** и  **\<после >** блокирует вызывающий поток.  
  
 Если указать один элемент в  **\<перед >** блок и только один соответствующий элемент в  **\<после >** блока с помощью **updg: ID** не является обязательным. Тем не менее, рекомендуется указывать **updg: ID** все равно во избежание неоднозначности.  
  
## <a name="examples"></a>Примеры  
 При использовании примеров диаграмм обновления необходимо учитывать следующие моменты.  
  
-   В большинстве примеров используется сопоставление по умолчанию (то есть в диаграмме обновления схема сопоставления не задана). Дополнительные примеры диаграмм обновления, которые используются схемы сопоставления см. в разделе [определение схемы с заметками сопоставления в диаграмме обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
-   В большинстве примеров задействован образец базы данных AdventureWorks. Все обновления применяются к таблицам в этой базе данных. Базу данных AdventureWorks можно восстановить.  
  
### <a name="a-updating-a-record"></a>A. Обновление записи  
 Следующая диаграмма обновления используется для изменения фамилии сотрудника в таблице Person.Contact базы данных AdventureWorks на Fuller. В диаграмме обновления не задана схема сопоставления, поэтому применяется сопоставление по умолчанию.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact LastName="Abel-Achong" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 Запись, описанная в  **\<перед >** блок представляет текущую запись в базе данных. Диаграмма обновления использует все значения столбца, указанного в  **\<перед >** блока для поиска записи. В данной диаграмме обновления  **\<перед >** блок предоставляет только столбец ContactID, таким образом, диаграмма обновления использует для поиска записи всего значение. Если добавить в этот блок значение LastName, то диаграмма обновления будет производить поиск по обоим значениям — ContactID и LastName.  
  
 В данной диаграмме обновления  **\<после >** блок предоставляет только значение столбца LastName, так как это единственное значение, которое необходимо изменить.  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенный выше шаблон диаграммы обновления и вставьте его в текстовый файл. Сохраните файл под именем UpdateLastName.xml.  
  
2.  Создайте тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) и воспользуйтесь им для выполнения диаграммы обновления.  
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="b-updating-multiple-records-by-using-the-updgid-attribute"></a>Б. Обновление нескольких записей с помощью атрибута updg:id  
 В данном примере диаграмма обновления выполняет два обновления в таблице HumanResources.Shift в базе данных AdventureWorks.  
  
-   Имя исходной дневной смены, начинающейся в 7:00, меняется с «Day» на «Early Morning».  
  
-   Также добавляется имя новой смены, «Late Morning», которая начинается в 10:00.  
  
 В диаграмме обновления **updg: ID** атрибут создает связи между элементами в  **\<перед >** и  **\<после >** блоков.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift updg:id="x" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift updg:id="y" Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
      <HumanResources.Shift updg:id="x" Name="Early Morning" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Обратите внимание как **updg: ID** пар «атрибут», первый экземпляр \<HumanResources.Shift > элемент в  **\<перед >** блок во втором экземпляре \< HumanResources.Shift > элемент в  **\<после >** блока.  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенный выше шаблон диаграммы обновления и вставьте его в текстовый файл. Сохраните файл под именем UpdateMultipleRecords.xml.  
  
2.  Создайте тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) и воспользуйтесь им для выполнения диаграммы обновления.  
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="c-specifying-multiple-before-and-after-blocks"></a>В. Указание нескольких \<перед > и \<после > блоков  
 Чтобы избежать неоднозначности, можно написать диаграмма обновления в примере Б с использованием нескольких  **\<перед >** и  **\<после >** пар блоков. Указание  **\<перед >** и  **\<после >** пары является одним из способов задать несколько изменений и избежать путаницы. Кроме того Если каждый из  **\<перед >** и  **\<после >** блоки указать не более одного элемента, необходимо использовать **updg: ID** атрибута .  
  
> [!NOTE]  
>  Для создания пары  **\<после >** тег должен следовать непосредственно за соответствующим  **\<перед >** тег.  
  
 В следующей диаграмме обновления первый  **\<перед >** и  **\<после >** пары обновления имени дневной смены. Вторая пара вставляет запись для новой смены.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Early Morning" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенный выше шаблон диаграммы обновления и вставьте его в текстовый файл. Сохраните файл под именем UpdateMultipleBeforeAfter.xml.  
  
2.  Создайте тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) и воспользуйтесь им для выполнения диаграммы обновления.  
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="d-specifying-multiple-sync-blocks"></a>Г. Указание нескольких \<синхронизации > блоков  
 Можно указать несколько  **\<синхронизации >** блоков в диаграмме обновления. Каждый  **\<синхронизации >** указанный блок представляет независимую транзакцию.  
  
 В следующей диаграмме обновления первый  **\<синхронизации >** блок обновляет запись в таблице Sales.Customer. Для простоты в диаграмме обновления указаны только обязательные значения столбцов: идентификатор (CustomerID) и обновляемое значение (SalesPersonID).  
  
 Второй  **\<синхронизации >** блок добавляет две записи в таблицу Sales.SalesOrderHeader. В этой таблице SalesOrderID является столбцом типа IDENTITY. Таким образом, диаграмма обновления не указывает значение SalesOrderID в каждом из \<Sales.SalesOrderHeader > элементов.  
  
 Указание нескольких  **\<синхронизации >** блоки полезно, поскольку если второй  **\<синхронизации >** блока (транзакция) не сможет добавить записи в таблицу Sales.SalesOrderHeader, Первый  **\<синхронизации >** блок все равно можете обновить запись клиента в таблице Sales.Customer.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
      <Sales.Customer CustomerID="1" SalesPersonID="280" />  
    </updg:before>  
    <updg:after>  
      <Sales.Customer CustomerID="1" SalesPersonID="283" />  
    </updg:after>  
  </updg:sync>  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
   <Sales.SalesOrderHeader   
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="01010101-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-08 00:00:00.000" />  
   <Sales.SalesOrderHeader  
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="1000.0000"  
             TaxAmt="0.0000"  
             Freight="0.0000"  
             rowguid="10101010-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-09 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенный выше шаблон диаграммы обновления и вставьте его в текстовый файл. Сохраните файл под именем UpdateMultipleSyncs.xml.  
  
2.  Создайте тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) и воспользуйтесь им для выполнения диаграммы обновления.  
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="e-using-a-mapping-schema"></a>Д. Использование схемы сопоставления  
 В этом примере диаграмма обновления указывает схему сопоставления с помощью **схемы сопоставления** атрибута. (сопоставление по умолчанию отсутствует; это означает, что сопоставление элементов и атрибутов в диаграмме обновления с таблицами и столбцами базы данных производится согласно схеме сопоставления).  
  
 Элементы и атрибуты диаграммы обновления ссылаются на элементы и атрибуты схемы сопоставления.  
  
 Следующая схема сопоставления XSD содержит  **\<клиента >**,  **\<порядок >**, и  **\<OD >** элементы, которые сопоставляются Таблицы Sales.Customer, Sales.SalesOrderHeader и Sales.SalesOrderDetail в базе данных.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustomerOrder"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustomerOrder" >  
           <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OD"   
                             sql:relation="Sales.SalesOrderDetail"  
                             sql:relationship="OrderOD" >  
                 <xsd:complexType>  
                  <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                  <xsd:attribute name="ProductID" type="xsd:integer" />  
                  <xsd:attribute name="UnitPrice" type="xsd:decimal" />  
                  <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  <xsd:attribute name="UnitPriceDiscount" type="xsd:decimal" />   
                 </xsd:complexType>  
                </xsd:element>  
              </xsd:sequence>  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
           </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Эта диаграмма сопоставления (UpdategramMappingSchema.xml) указывается в следующей диаграмме обновления. Диаграмма обновления добавляет элемент, содержащий сведения об определенном заказе, в таблицу Sales.SalesOrderDetail. Диаграмма обновления содержит следующие вложенные элементы:  **\<OD >** внутри  **\<порядок >** элемента. Связь «первичный ключ-внешний ключ» между этими элементами указывается в схеме сопоставления.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="UpdategramMappingSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43659" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43659" >  
          <OD ProductID="776" UnitPrice="2329.0000"  
              OrderQty="2" UnitPriceDiscount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенную выше схему сопоставления и вставьте ее в текстовый файл. Сохраните файл под именем UpdategramMappingSchema.xml.  
  
2.  Скопируйте приведенный выше шаблон диаграммы обновления и вставьте его в текстовый файл. Сохраните файл под именем UpdateWithMappingSchema.xml в той же папке, в которой сохранена схема сопоставления (UpdategramMappingSchema.xml).  
  
3.  Создайте тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) и воспользуйтесь им для выполнения диаграммы обновления.  
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Дополнительные примеры диаграмм обновления, которые используются схемы сопоставления см. в разделе [определение схемы с заметками сопоставления в диаграмме обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
### <a name="f-using-a-mapping-schema-with-idrefs-attributes"></a>Е. Использование схемы сопоставления с атрибутами IDREFS  
 В данном примере показано, каким образом диаграммы обновления используют атрибуты IDREFS в схеме сопоставления для обновления записей в нескольких таблицах. В этом примере предполагается, что база данных состоит из следующих таблиц.  
  
-   Student(StudentID, LastName)  
  
-   Course(CourseID, CourseName)  
  
-   Enrollment(StudentID, CourseID)  
  
 Поскольку один студент может быть записан на несколько разных курсов, а на курс может быть записано много студентов, третья таблица Enrollment должна представлять связь M:N.  
  
 Следующая схема сопоставления XSD предоставляет XML-представление таблицы с помощью  **\<Student >**,  **\<Course >**, и  **\<регистрации >** элементов. **IDREFS** атрибуты в схеме сопоставления указывают отношения между этими элементами. **StudentIDList** атрибут  **\<Course >** элемент **IDREFS** атрибутом типа, который относится к столбцу StudentID в таблице Enrollment. Аналогичным образом **EnrolledIn** атрибут  **\<Student >** элемент **IDREFS** атрибутом типа, который относится к столбцу CourseID в регистрации Таблица.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="StudentEnrollment"  
          parent="Student"  
          parent-key="StudentID"  
          child="Enrollment"  
          child-key="StudentID" />  
  
    <sql:relationship name="CourseEnrollment"  
          parent="Course"  
          parent-key="CourseID"  
          child="Enrollment"  
          child-key="CourseID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Course" sql:relation="Course"   
                             sql:key-fields="CourseID" >  
    <xsd:complexType>  
    <xsd:attribute name="CourseID"  type="xsd:string" />   
    <xsd:attribute name="CourseName"   type="xsd:string" />   
    <xsd:attribute name="StudentIDList" sql:relation="Enrollment"  
                 sql:field="StudentID"  
                 sql:relationship="CourseEnrollment"   
                                     type="xsd:IDREFS" />  
  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name="Student" sql:relation="Student" >  
    <xsd:complexType>  
    <xsd:attribute name="StudentID"  type="xsd:string" />   
    <xsd:attribute name="LastName"   type="xsd:string" />   
    <xsd:attribute name="EnrolledIn" sql:relation="Enrollment"  
                 sql:field="CourseID"  
                 sql:relationship="StudentEnrollment"   
                                     type="xsd:IDREFS" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Если указать эту схему в диаграмме обновления и добавить запись в таблицу Course, то диаграмма обновления вставит новую запись о курсе в таблицу Course. Если указать один или несколько идентификаторов студентов в атрибуте StudentIDList, то диаграмма обновления также добавит запись в таблицу Enrollment для каждого нового студента. Диаграмма обновления обеспечивает отсутствие повторяющих друг друга записей в таблицу Enrollment.  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Создайте эти таблицы в базе данных в виртуальном корневом каталоге:  
  
    ```  
    CREATE TABLE Student(StudentID varchar(10) primary key,   
                         LastName varchar(25))  
    CREATE TABLE Course(CourseID varchar(10) primary key,   
                        CourseName varchar(25))  
    CREATE TABLE Enrollment(StudentID varchar(10)   
                                      references Student(StudentID),  
                           CourseID varchar(10)   
                                      references Course(CourseID))  
    ```  
  
2.  Добавьте следующий образец данных:  
  
    ```  
    INSERT INTO Student VALUES ('S1','Davoli')  
    INSERT INTO Student VALUES ('S2','Fuller')  
  
    INSERT INTO Course VALUES  ('CS101', 'C Programming')  
    INSERT INTO Course VALUES  ('CS102', 'Understanding XML')  
  
    INSERT INTO Enrollment VALUES ('S1', 'CS101')  
    INSERT INTO Enrollment VALUES ('S1', 'CS102')  
    ```  
  
3.  Скопируйте приведенную выше схему сопоставления и вставьте ее в текстовый файл. Сохраните файл под именем SampleSchema.xml.  
  
4.  Сохраните диаграмму обновления (SampleUpdategram) в той же папке, что и схему сопоставления в предыдущем шаге (эта диаграмма обновления удаляет студента с идентификатором StudentID="1" из курса CS102).  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
5.  Создайте тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) и воспользуйтесь им для выполнения диаграммы обновления.  
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
6.  Сохраните и выполните следующую диаграмму обновления, как описано на предыдущих шагах. Диаграмма обновления снова записывает студента с идентификатором StudentID="1" на курс CS102 путем добавления записи в таблицу Enrollment.  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
7.  Сохраните и выполните следующую диаграмму обновления, как описано на предыдущих шагах. Эта диаграмма обновления добавляет трех новых студентов и регистрирует их на курс CS101. Связь IDREFS вставляет запись в таблицу Enrollment.  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
           <Course updg:id="y" CourseID="CS101"   
                               CourseName="C Programming" />  
        </updg:before>  
        <updg:after >  
           <Student updg:id="x1" StudentID="S3" LastName="Leverling" />  
           <Student updg:id="x2" StudentID="S4" LastName="Pecock" />  
           <Student updg:id="x3" StudentID="S5" LastName="Buchanan" />  
           <Course updg:id="y" CourseID="CS101"  
                               CourseName="C Programming"  
                               StudentIDList="S3 S4 S5" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
 Эквивалентная схема XDR:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ElementType name="Enrollment" sql:relation="Enrollment" sql:key-fields="StudentID CourseID">  
    <AttributeType name="StudentID" dt:type="id" />  
    <AttributeType name="CourseID" dt:type="id" />  
  
    <attribute type="StudentID" />  
    <attribute type="CourseID" />  
  </ElementType>  
  <ElementType name="Course" sql:relation="Course" sql:key-fields="CourseID">  
    <AttributeType name="CourseID" dt:type="id" />  
    <AttributeType name="CourseName" />  
  
    <attribute type="CourseID" />  
    <attribute type="CourseName" />  
  
    <AttributeType name="StudentIDList" dt:type="idrefs" />  
    <attribute type="StudentIDList" sql:relation="Enrollment" sql:field="StudentID" >  
        <sql:relationship  
                key-relation="Course"  
                key="CourseID"  
                foreign-relation="Enrollment"  
                foreign-key="CourseID" />  
    </attribute>  
  
  </ElementType>  
  <ElementType name="Student" sql:relation="Student">  
    <AttributeType name="StudentID" dt:type="id" />  
     <AttributeType name="LastName" />  
  
    <attribute type="StudentID" />  
    <attribute type="LastName" />  
  
    <AttributeType name="EnrolledIn" dt:type="idrefs" />  
    <attribute type="EnrolledIn" sql:relation="Enrollment" sql:field="CourseID" >  
        <sql:relationship  
                key-relation="Student"  
                key="StudentID"  
                foreign-relation="Enrollment"  
                foreign-key="StudentID" />  
    </attribute>  
  
    <element type="Enrollment" sql:relation="Enrollment" >  
        <sql:relationship key-relation="Student"  
                          key="StudentID"  
                          foreign-relation="Enrollment"  
                          foreign-key="StudentID" />  
    </element>  
  </ElementType>  
  
</Schema>  
```  
  
 Дополнительные примеры диаграмм обновления, которые используются схемы сопоставления см. в разделе [определение схемы с заметками сопоставления в диаграмме обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности диаграмм обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
