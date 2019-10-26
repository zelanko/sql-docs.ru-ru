---
title: Указание арифметических операторов в запросах XPath (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- arithmetic operators
- XPath operators [SQLXML]
- XPath queries [SQLXML], arithmetic operators
- operators [SQLXML]
ms.assetid: fdfbc87d-759f-4abc-acf5-a21de01f78d3
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2fa1bf6dd7d5652e33eb5fa7c75a86268f31129a
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72907765"
---
# <a name="specifying-arithmetic-operators-in-xpath-queries-sqlxml-40"></a>Задание арифметических операторов в запросах XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В следующем примере показано, как в запросах XPath указывать арифметические операторы. В этом примере задается запрос XPath к схеме сопоставления, содержащейся в файле SampleSchema1.xml. Сведения об этом образце схемы см. в статье [Пример схемы XSD с заметками &#40;для&#41;XPath примеры SQLXML 4,0](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-specify-the--arithmetic-operator"></a>A. Указание арифметического оператора *  
 Этот запрос XPath возвращает **\<OrderDetail >** элементов, которые соответствуют заданному предикату:  
  
```  
/child::OrderDetail[@UnitPrice * @Quantity = 12.350]  
```  
  
 В запросе `child` — это ось, а `OrderDetail` — это проверка узла (TRUE, если **OrderDetail** является **\<ным узлом элемента >** , поскольку\<**элемент** > является основным узлом для **дочерней** оси). Для всех узлов элементов **\<OrderDetail >** применяется тест в предикате и возвращаются только те узлы, которые соответствуют условию.  
  
> [!NOTE]  
>  Числа в языке XPath являются числами с плавающей запятой двойной точности, и сравнение чисел с плавающей запятой, как указано в примере, приводит к округлению.  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Проверка запроса XPath к схеме сопоставления  
  
1.  Скопируйте [пример кода схемы](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) и вставьте его в текстовый файл. Сохраните файл с именем SampleSchema1.xml.  
  
2.  Создайте следующий шаблон (ArithmeticOperatorA.xml) и сохраните его в каталоге, где содержится файл SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /OrderDetail[@UnitPrice * @OrderQty = 12.350]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл SampleSchema1.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  

     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
```  
Here is the partial result set of the template execution:    
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-710" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
   ...  
</ROOT>  
```  
  
  
