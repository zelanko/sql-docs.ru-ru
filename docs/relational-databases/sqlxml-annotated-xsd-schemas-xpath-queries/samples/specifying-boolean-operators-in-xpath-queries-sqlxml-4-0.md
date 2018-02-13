---
title: "Указание логических операторов в запросах XPath (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- XPath operators [SQLXML]
- OR operator
- Boolean operators
- XPath queries [SQLXML], Boolean operators
- operators [SQLXML]
ms.assetid: 9928cff5-62ac-42aa-96bf-2e09a1df0bc3
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 90e324d5d10d7043bb95471e87c2b664a46d0398
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="specifying-boolean-operators-in-xpath-queries-sqlxml-40"></a>Указание логических операторов в запросах XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
В следующем примере показано, каким образом логические операторы задаются в запросах XPath. В этом примере задается запрос XPath к схеме сопоставления, содержащейся в файле SampleSchema1.xml. Сведения об этом образце схемы см. в разделе [образец аннотированные схемы XSD для примеров XPath &#40; SQLXML 4.0 &#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-specify-the-or-boolean-operator"></a>A. Указание логического оператора OR  
 Этот запрос XPath возвращает  **\<клиента >** дочерние элементы узла контекста с **CustomerID** значение 13 или 31 атрибута:  
  
```  
/child::Customer[attribute::CustomerID="13" or attribute::CustomerID="31"]  
```  
  
 Ярлык для **атрибута** оси (@) можно указать, а потому, что **дочерних** оси используется по умолчанию, ее можно опустить:  
  
```  
/Customer[@CustomerID="13" or @CustomerID="31"]  
```  
  
 В этом предикате `attribute` является осью и `CustomerID` является проверкой узла (значение TRUE, если **CustomerID** —  **\<атрибут >** узла, так как  **\<атрибут >** узел является основным узлом для **атрибута** оси). Фильтры предикатов  **\<клиента >** элементов и возвращает только те, которые удовлетворяют условию, заданному в предикате.  
  
##### <a name="to-test-the-xpath-queries-against-the-mapping-schema"></a>Проверка запросов XPath к схеме сопоставления  
  
1.  Копировать [образец кода схемы](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) и вставьте его в текстовый файл. Сохраните файл с именем SampleSchema1.xml.  
  
2.  Создайте следующий шаблон (BooleanOperatorsA.xml) и сохраните его в каталоге, в котором сохранен файл SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="13" or @CustomerID="31"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл SampleSchema1.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Далее приведен результирующий набор, полученный в результате выполнения этого шаблона.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="31" SalesPersonID="286" TerritoryID="7" AccountNumber="31" CustomerType="S" Orders="Ord-51803 Ord-69427">  
    <Order SalesOrderID="Ord-51803" SalesPersonID="286" OrderDate="2003-08-01T00:00:00" DueDate="2003-08-13T00:00:00" ShipDate="2003-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-718" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-838" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    <Order SalesOrderID="Ord-69427" SalesPersonID="286" OrderDate="2004-05-01T00:00:00" DueDate="2004-05-13T00:00:00" ShipDate="2004-05-08T00:00:00">  
      <OrderDetail ProductID="Prod-835" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
  </Customer>  
</ROOT>  
```  
  
  
