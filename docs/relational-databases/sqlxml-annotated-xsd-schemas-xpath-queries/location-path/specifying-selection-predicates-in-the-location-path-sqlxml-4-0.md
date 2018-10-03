---
title: Указание предикатов выбора в пути доступа (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c19d5e43169142a8e3527fca48bb355e5f1e8f7d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713082"
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a>Указание предикатов выбора в пути доступа (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Предикат фильтрует набор узлов по отношению к оси (аналогично предложению WHERE в инструкции SELECT). Предикат указывается в квадратных скобках. Для каждого узла в фильтруемом наборе узлов выражение предиката вычисляется с этим узлом в качестве узла контекста, а количество узлов в наборе определяет размер контекста. Если для данного узла выражение предиката дает значение TRUE, то узел включается в результирующий набор узлов.  
  
 XPath также позволяет выполнять фильтрацию в зависимости от позиции. Выражение предиката, результатом оценки которого является число, выбирает этот исходный узел. Например, путь доступа `Customer[3]` возвращает третьего клиента. Такие числовые предикаты не поддерживаются. Поддерживаются только предикаты, которые возвращают логический результат.  
  
> [!NOTE]  
>  Сведения об ограничениях этой реализации XPath и отличиях от спецификации W3C, см. в разделе [введение в использование запросов XPath &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="selection-predicate-example-1"></a>Предикат выбора: Пример 1  
 Следующее выражение XPath (путь доступа) выбирает из текущего контекстного узла все  **\<клиента >** дочерние элементы, имеющие **CustomerID** атрибута значение «ALFKI»:  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 В этом запросе XPath `child` и `attribute` являются именами осей. `Customer` является проверкой узла (значение TRUE, если `Customer` —  **\<узла элемента >**, так как  **\<элемент >** является основным типом узла для `child` оси). `attribute::CustomerID="ALFKI"` является предикатом. В этом предикате `attribute` является осью и `CustomerID` является проверкой узла (значение TRUE, если **CustomerID** — это атрибут узла контекста, так как  **\<атрибут >** является участником Тип узла **атрибут** оси).  
  
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
  
## <a name="selection-predicate-example-3"></a>Предикат выбора: Пример 3  
 Следующее выражение XPath (путь доступа) выбирает из текущего контекстного узла все  **\<клиента >** дочерние элементы, имеющие один или несколько  **\<ContactName >** дочерние элементы:  
  
```  
child::Customer[child::ContactName]  
```  
  
 В этом примере предполагается, что  **\<ContactName >** является дочерним элементом элемента  **\<клиента >** элемент XML-документа, который называется  *элементное сопоставление* в аннотированной схеме XSD.  
  
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
  
 В этом примере предполагается, что  **\<ContactName >** является дочерним элементом элемента  **\<клиента >** элемент в XML-документе и поле ContactName не является обязательным в База данных.  
  
 В этом примере `child` является осью. `Customer` является проверкой узла (значение TRUE, если `Customer` является \<элемент > узла). `not(child::ContactName)` является предикатом. В этом предикате `child` является осью и `ContactName` является проверкой узла (значение TRUE, если `ContactName` является \<элемент > узла).  
  
 Запрос XPath также можно задать с использованием сокращенного синтаксиса:  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a>Предикат выбора: Пример 5  
 Следующее выражение XPath выбирает из текущего контекстного узла все  **\<клиента >** дочерние элементы, имеющие **CustomerID** атрибут:  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 В этом примере `child` является осью и `Customer` — проверкой узла (значение TRUE, если `Customer` является \<элемент > узла). `attribute::CustomerID` является предикатом. В этом предикате `attribute` является осью и `CustomerID` является предикатом (значение TRUE, если `CustomerID` —  **\<атрибут >** узла).  
  
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
 [Форматирование XML на стороне клиента &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
