---
title: Указание предикатов выбора в пути доступа (SQLXML 4.0) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7e32ce8235adfe6774b339219ced7ecb6a38f505
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a>Указание предикатов выбора в пути доступа (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Предикат фильтрует набор узлов по отношению к оси (аналогично предложению WHERE в инструкции SELECT). Предикат указывается в квадратных скобках. Для каждого узла в фильтруемом наборе узлов выражение предиката вычисляется с этим узлом в качестве узла контекста, а количество узлов в наборе определяет размер контекста. Если для данного узла выражение предиката дает значение TRUE, то узел включается в результирующий набор узлов.  
  
 XPath также позволяет выполнять фильтрацию в зависимости от позиции. Выражение предиката, результатом оценки которого является число, выбирает этот исходный узел. Например, путь доступа `Customer[3]` возвращает третьего клиента. Такие числовые предикаты не поддерживаются. Поддерживаются только предикаты, которые возвращают логический результат.  
  
> [!NOTE]  
>  Сведения об ограничениях этой реализации XPath и различия между ним и спецификации W3C см. в разделе [Общие сведения о запросах XPath с помощью &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="selection-predicate-example-1"></a>Предикат выбора: Пример 1.  
 Следующее выражение XPath (путь доступа) выбирает из текущего контекстного узла все  **\<клиента >** дочерние элементы, имеющие **CustomerID** атрибут со значением «ALFKI»:  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 В этом запросе XPath `child` и `attribute` являются именами осей. `Customer` является проверкой узла (значение TRUE, если `Customer` —  **\<узел элемента >**, так как  **\<элемент >** является основным типом узла для `child` оси). `attribute::CustomerID="ALFKI"` является предикатом. В этом предикате `attribute` является осью и `CustomerID` является проверкой узла (значение TRUE, если **CustomerID** является атрибутом элемента узла контекста, так как  **\<атрибут >** участник Тип узла **атрибута** оси).  
  
 Запрос XPath также можно задать с использованием сокращенного синтаксиса:  
  
```  
/Customer[@CustomerID="ALFKI"]  
```  
  
## <a name="selection-predicate-example-2"></a>Предикат выбора: Пример 2  
 Следующее выражение XPath (путь доступа) выбирает из текущего контекстного узла все  **\<порядок >** внучатые элементы, имеющие **SalesOrderID** атрибут со значением 1:  
  
```  
/child::Customer/child::Order[attribute::SalesOrderID="1"]  
```  
  
 В этом выражении XPath `child` и `attribute` являются именами осей. `Customer`, `Order` и `SalesOrderID` являются проверками узла. `attribute::OrderID="1"` является предикатом.  
  
 Запрос XPath также можно задать с использованием сокращенного синтаксиса:  
  
```  
/Customer/Order[@SalesOrderID="1"]  
```  
  
## <a name="selection-predicate-example-3"></a>Предикат выбора: Пример 3.  
 Следующее выражение XPath (путь доступа) выбирает из текущего контекстного узла все  **\<клиента >** дочерние элементы, имеющие один или несколько  **\<ContactName >** дочерние элементы:  
  
```  
child::Customer[child::ContactName]  
```  
  
 В этом примере предполагается, что  **\<ContactName >** является дочерним элементом элемента  **\<клиента >** элемент XML-документа, который называется  *элементное сопоставление* в схеме XSD с заметками.  
  
 В этом выражении XPath `child` является именем оси. `Customer` является проверкой узла (значение TRUE, если `Customer` —  **\<элемент >** узла, так как  **\<элемент >** является основным типом узла для `child` оси). `child::ContactName` является предикатом. В этом предикате `child` является осью и `ContactName` является проверкой узла (значение TRUE, если `ContactName` —  **\<элемент >** узла).  
  
 Это выражение возвращает только  **\<клиента >** дочерний элемент контекстного узла, имеющего  **\<ContactName >** дочерние элементы.  
  
 Запрос XPath также можно задать с использованием сокращенного синтаксиса:  
  
```  
Customer[ContactName]  
```  
  
## <a name="selection-predicate-example-4"></a>Предикат выбора: Пример 4  
 Следующее выражение XPath выбирает  **\<клиента >** дочерние элементы узла контекста, у которых нет  **\<ContactName >** дочерние элементы:  
  
```  
child::Customer[not(child::ContactName)]  
```  
  
 В этом примере предполагается, что  **\<ContactName >** является дочерним элементом элемента  **\<клиента >** в элемент в XML-документе и поле ContactName не требуется База данных.  
  
 В этом примере `child` является осью. `Customer` является проверкой узла (значение TRUE, если `Customer` — \<элемент > узла). `not(child::ContactName)` является предикатом. В этом предикате `child` является осью и `ContactName` является проверкой узла (значение TRUE, если `ContactName` — \<элемент > узла).  
  
 Запрос XPath также можно задать с использованием сокращенного синтаксиса:  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a>Предикат выбора: Пример 5  
 Следующее выражение XPath выбирает из текущего контекстного узла все  **\<клиента >** дочерние элементы, имеющие **CustomerID** атрибута:  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 В этом примере `child` является осью и `Customer` — проверкой узла (значение TRUE, если `Customer` — \<элемент > узла). `attribute::CustomerID` является предикатом. В этом предикате `attribute` является осью и `CustomerID` является предикатом (значение TRUE, если `CustomerID` —  **\<атрибут >** узла).  
  
 Запрос XPath также можно задать с использованием сокращенного синтаксиса:  
  
```  
Customer[@CustomerID]  
```  
  
## <a name="selection-predicate-example-6"></a>Предикат выбора: Пример 6  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 включает поддержку запросов XPath, которые содержат в предикате перекрестное произведение, как показано в следующем примере:  
  
```  
Customer[Order/@OrderDate=Order/@ShipDate]  
```  
  
 Этот запрос выбирает всех клиентов с элементом `Order`, для которого `OrderDate` равен `ShipDate` `Order`.  
  
## <a name="see-also"></a>См. также  
 [Введение в схемы XSD с заметками &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)   
 [Форматирование XML на стороне клиента & #40; SQLXML 4.0 & #41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
