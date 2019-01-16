---
title: Обработка базы данных проблем параллелизма в диаграммах обновления (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <before> block
- low concurrency protection
- database concurrency [SQLXML]
- timestamp column [SQLXML]
- updategrams [SQLXML], database concurrency
- high concurrency protection [SQLXML]
- optimistic concurrency control
- concurrency [SQLXML]
- intermediate concurrency protection [SQLXML]
ms.assetid: d4b908d1-b25b-4ad9-8478-9cd882e8c44e
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f7ded788c5aecff2445d7f3257f7c56957b9d0bd
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54256839"
---
# <a name="handling-database-concurrency-issues-in-updategrams-sqlxml-40"></a>Решение проблем с параллелизмом обработки в базе данных в диаграммах обновления (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Как и другие механизмы обновления базы данных, диаграммы обновления должны иметь дело с одновременными обновлениями данных в многопользовательской среде. В диаграммах обновления используется оптимистическое управление параллелизмом, которое использует сравнение данных в выбранных полях как моментальных снимков, чтобы данные, которые нужно обновить, не были изменены другим пользовательским приложением после чтения из базы данных. Диаграммы обновления включают эти значения моментальных снимков в  **\<перед >** блок диаграмм обновления. Перед обновлением базы данных, диаграмма обновления сопоставляет значения, заданные в  **\<перед >** блок с текущими значениями в базе данных, чтобы убедиться, что обновление является допустимым.  
  
 Управление оптимистичным параллелизмом обеспечивает три уровня защиты в диаграмме обновления: низкий (нет), промежуточный и высокий. Можно выбрать нужный уровень защиты, указав соответствующую диаграмму обновления.  
  
## <a name="lowest-level-of-protection"></a>Самый низкий уровень защиты  
 Этот уровень обеспечивает «слепое» обновление, при котором обновление обрабатывается без учета других обновлений, сделанных со времени последнего чтения базы данных. В этом случае указываются только первичные ключевые столбцы в  **\<перед >** блокировать для идентификации записи, и указываются обновленные сведения в  **\<после >** блок.  
  
 Например, новый номер телефона для связи в следующей диаграмме обновления верен, независимо от предыдущего значения телефонного номера. Обратите внимание, что как  **\<перед >** блока указывает только первичный ключевой столбец (ContactID).  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="intermediate-level-of-protection"></a>Промежуточный уровень защиты  
 На этом уровне защиты диаграмма обновления сравнивает текущие значения обновляемых данных со значениями в столбцах базы данных, чтобы проверить, что значения не были изменены другой транзакцией после чтения записи данной транзакцией.  
  
 Этот уровень защиты можно получить, указав первичные ключевые столбцы и обновляемые столбцы при обновлении в  **\<перед >** блока.  
  
 Например, данная диаграмма обновления изменяет значение в столбце Phone таблицы Person.Person для контактного лица со значением ContactID, равным 1.  **\<Перед >** указывает блок **Phone** атрибута, чтобы гарантировать, что это значение атрибута соответствует значению в соответствующем столбце в базе данных перед применением обновленного значения .  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" Phone="398-555-0132" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="high-level-of-protection"></a>Высокий уровень защиты  
 Высокий уровень защиты гарантирует, что запись остается неизменной со времени последнего чтения записи приложением (то есть после чтения записи приложением она не была изменена никакой другой транзакцией).  
  
 Существует два способа получить высокий уровень защиты от одновременных обновлений.  
  
-   Укажите дополнительные столбцы в таблице в  **\<перед >** блока.  
  
     Если указаны дополнительные столбцы в  **\<перед >** блока, то диаграмма обновления сравнивает значения, заданные для этих столбцов со значениями, которые были в базе данных перед применением обновления. Если какие-нибудь столбцы записи изменились после чтения записи транзакцией, диаграмма обновления не выполняет обновление.  
  
     Например, следующая диаграмма обновления обновляет название рабочей смены, но указывает дополнительные столбцы (StartTime, EndTime) в  **\<перед >** блока, тем самым запрашивая более высокий уровень защиты от одновременных обновления.  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1"   
                 Name="Day"   
                 StartTime="1900-01-01 07:00:00.000"   
                 EndTime="1900-01-01 15:00:00.000" />  
    </updg:before>  
    <updg:after>  
       <HumanResources.Shift Name="Morning" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
     В этом примере указывает самый высокий уровень защиты, указав все значения столбцов для записи в  **\<перед >** блока.  
  
-   Указать столбец отметки времени (если доступно) в  **\<перед >** блока.  
  
     Вместо указания всех столбцов записи в  **\<перед**> блока, можно просто указать столбец отметки времени (если есть в таблице) наряду с первичными ключевыми столбцами в  **\<перед >** блока. База данных обновляет столбец отметки времени уникальным значением после каждого обновления записи. В этом случае диаграмма обновления сравнивает значения отметок времени с соответствующим значением в базе данных. Значение отметки времени, сохраненное в базе данных, является двоичным значением. Таким образом, необходимо указать столбец отметки времени в схеме как **dt:type="bin.hex»**, **dt:type="bin.base64»**, или **SQL: DataType = «timestamp»**. (Можно указать либо **xml** тип данных или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.)  
  
#### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Создайте следующую таблицу в **tempdb** базы данных:  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (  
                 CustomerID  varchar(5),  
                 ContactName varchar(20),  
                 LastUpdated timestamp)  
    ```  
  
2.  Добавьте следующий образец записи:  
  
    ```  
    INSERT INTO Customer (CustomerID, ContactName) VALUES   
                         ('C1', 'Andrew Fuller')  
    ```  
  
3.  Скопируйте и вставьте следующую схему XSD в приложение «Блокнот». Сохраните код в файл с именем ConcurrencySampleSchema.xml:  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="Customer" sql:relation="Customer" >  
       <xsd:complexType>  
            <xsd:attribute name="CustomerID"    
                           sql:field="CustomerID"   
                           type="xsd:string" />   
  
            <xsd:attribute name="ContactName"    
                           sql:field="ContactName"   
                           type="xsd:string" />  
  
            <xsd:attribute name="LastUpdated"   
                           sql:field="LastUpdated"   
                           type="xsd:hexBinary"   
                 sql:datatype="timestamp" />  
  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
4.  Скопируйте следующий код диаграммы обновления в приложении «Блокнот» и сохраните его в файле с именем ConcurrencySampleTemplate.xml в том же каталоге, в котором сохранена схема, созданная на предыдущем шаге. Обратите внимание, что указанное ниже значение отметки времени для столбца LastUpdated будет иным, нежели в примере таблицы Customer, поэтому скопируйте фактическое значение для LastUpdated из таблицы и вставьте его в диаграмму обновления.  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
    <updg:before>  
       <Customer CustomerID="C1"   
                 LastUpdated = "0x00000000000007D1" />  
    </updg:before>  
    <updg:after>  
       <Customer ContactName="Robert King" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
5.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Эквивалентная схема XDR:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<ElementType name="Customer" sql:relation="Customer" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="ContactName" />  
    <AttributeType name="LastUpdated"  dt:type="bin.hex"   
                                       sql:datatype="timestamp" />  
    <attribute type="CustomerID" />  
    <attribute type="ContactName" />  
    <attribute type="LastUpdated" />  
</ElementType>  
</Schema>  
```  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности диаграмм обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
