---
title: Указание предикатов с логическими значениями в запросах XPath (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- nested predicates
- successive predicates
- predicates [SQLXML]
- top-level predicates
- Boolean-valued predicates
- multiple predicates
ms.assetid: 5f6e7219-6911-4bca-a54b-56b95e0b43dd
author: rothja
ms.author: jroth
ms.openlocfilehash: 6eef537f60e6e2bccfe5fea77aeb2afe2c1468ac
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "84996247"
---
# <a name="specifying-boolean-valued-predicates-in-xpath-queries-sqlxml-40"></a>Определение предикатов с логическим значением в запросах XPath (SQLXML 4.0)
  В следующем примере показано, как предикаты с логическим значением указываются в запросах XPath. В данных примерах запросы XPath определены в соответствии со схемой сопоставления, которая содержится в файле SampleSchema1.xml. Дополнительные сведения об этом образце схемы см. в разделе [Пример схемы XSD с заметками для XPath-примеров &#40;SQLXML 4,0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-specify-multiple-predicates"></a>A. Указание нескольких предикатов  
 Следующий запрос XPath использует несколько предикатов для поиска сведений о заказе для данного идентификатора заказа и идентификатора клиента:  
  
```  
/child::Customer[attribute::CustomerID="1"]/child::Order[attribute::OrderID="Ord-43860"]  
```  
  
 Может быть задано сокращенное обозначение оси `attribute` (@), а поскольку ось `child` является осью по умолчанию, в запросе ее можно опустить.  
  
```  
/Customer[@CustomerID="1"]/Order[@SalesOrderID="Ord-43860"]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Проверка запроса XPath к схеме сопоставления  
  
1.  Скопируйте [пример кода схемы](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) и вставьте его в текстовый файл. Сохраните файл с именем SampleSchema1.xml.  
  
2.  Создайте следующий шаблон (BooleanValuedPredicatesA.xml) и сохраните его в каталоге, где содержится файл SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="1"]/Order[@SalesOrderID="Ord-43860"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл SampleSchema1.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
     Результат:  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <Order SalesOrderID="Ord-43860" SalesPersonID="280" OrderDate="2001-08-01T00:00:00" DueDate="2001-08-13T00:00:00" ShipDate="2001-08-08T00:00:00">  
        <OrderDetail ProductID="Prod-729" UnitPrice="226.8571" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-738" UnitPrice="220.2496" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-761" UnitPrice="503.3507" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-762" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-763" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-765" UnitPrice="503.3507" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-768" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-770" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
      </Order>  
    </ROOT>  
    ```  
  
### <a name="b-specify-successive-and-nested-predicates"></a>Б. Указание последовательных и вложенных предикатов  
 В следующем запросе показано использование последовательных предикатов. Запрос возвращает все **\<Customer>** дочерние элементы контекстного узла, которые имеют атрибут **SalesPersonID** со значением 277 и атрибутом **территорид** со значением 3:  
  
```  
/child::Customer[attribute::SalesPersonID="277"][attribute::TerritoryID="3"]  
```  
  
 Запрос возвращает **\<Customer>** элементы, которые соответствуют условиям, заданным в предикатах.  
  
 Может быть задано сокращенное обозначение оси `attribute` (@), а поскольку ось `child` является осью по умолчанию, в запросе ее можно опустить.  
  
```  
/Customer[@SalesPersonID="277"][@TerritoryID="3"]  
```  
  
 В следующем запросе XPath показано использование вложенных предикатов. Запрос возвращает все **\<Customer>** дочерние элементы контекстного узла, которые содержат **\<Order>** дочерние элементы по крайней мере с одним **\<Order>** элементом, имеющим значение атрибута **SalesPersonID** , равное 2.  
  
```  
/Customer[Order[@SalesPersonID=2]]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Проверка запроса XPath к схеме сопоставления  
  
1.  Скопируйте [пример кода схемы](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) и вставьте его в текстовый файл. Сохраните файл с именем SampleSchema1.xml.  
  
2.  Создайте следующий шаблон (nestedSuccessive.xml) и сохраните его в каталоге, где содержится файл SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
             /Customer[@SalesPersonID="277"][@TerritoryID="3"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл SampleSchema1.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Далее показан частичный результат:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="22" SalesPersonID="277" TerritoryID="3"   
            AccountNumber="22" CustomerType="S"   
            Orders="Ord-43874 Ord-44519 Ord-46989 Ord-48013 Ord-49130 Ord-50274 Ord-51807 Ord-57113 Ord-63162 Ord-69495">  
    <Order SalesOrderID="Ord-43874" SalesPersonID="277"   
           OrderDate="2001-08-01T00:00:00"   
           DueDate="2001-08-13T00:00:00"   
           ShipDate="2001-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
                   OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    ...  
  </Customer>  
  <Customer CustomerID="39" SalesPersonID="277" TerritoryID="3"   
            AccountNumber="39" CustomerType="S"   
            Orders="Ord-47428 Ord-48367 Ord-49529 Ord-50742 Ord-53591 Ord-59051 Ord-65301 Ord-71912">    <Order SalesOrderID="Ord-47428" SalesPersonID="277"   
           OrderDate="2002-09-01T00:00:00"   
           DueDate="2002-09-13T00:00:00"   
           ShipDate="2002-09-08T00:00:00">  
      <OrderDetail ProductID="Prod-759" UnitPrice="563.7528" OrderQty="2" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-769" UnitPrice="563.7528" OrderQty="1" UnitPriceDiscount="0" />   
      ...  
    </Order>  
    ...  
  </Customer>  
  ...  
</ROOT>  
```  
  
### <a name="c-specify-a-top-level-predicate"></a>В. Указание предиката верхнего уровня  
 Следующий запрос возвращает **\<Customer>** дочерние узлы элементов контекстного узла, которые имеют **\<Order>** дочерние элементы. В этом запросе проверяется, является ли путь доступа предикатом верхнего уровня:  
  
```  
/child::Customer[child::Order]  
```  
  
 Ось `child` является осью по умолчанию. Поэтому запрос можно определить следующим образом.  
  
```  
/Customer[Order]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Проверка запроса XPath к схеме сопоставления  
  
1.  Скопируйте [пример кода схемы](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) и вставьте его в текстовый файл. Сохраните файл с именем SampleSchema1.xml.  
  
2.  Создайте следующий шаблон (TopLevelPredicate.xml) и сохраните его в каталоге, где содержится файл SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл SampleSchema1.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Частичный результат:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" SalesPersonID="280" TerritoryID="1" AccountNumber="1" CustomerType="S" Orders="Ord-43860 Ord-44501 Ord-45283 Ord-46042">  
    <Order SalesOrderID="Ord-43860" SalesPersonID="280" OrderDate="2001-08-01T00:00:00" DueDate="2001-08-13T00:00:00" ShipDate="2001-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-729" UnitPrice="226.8571" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-738" UnitPrice="220.2496" OrderQty="1" UnitPriceDiscount="0" />   
      ...  
    </Order>  
    <Order SalesOrderID="Ord-44501" SalesPersonID="280" OrderDate="2001-11-01T00:00:00" DueDate="2001-11-13T00:00:00" ShipDate="2001-11-08T00:00:00">  
      <OrderDetail ProductID="Prod-725" UnitPrice="226.8571" OrderQty="3" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-726" UnitPrice="226.8571" OrderQty="2" UnitPriceDiscount="0" />   
      ...  
    </Order>    ...  
  </Customer>  
  ...  
</ROOT>  
```  
  
  
