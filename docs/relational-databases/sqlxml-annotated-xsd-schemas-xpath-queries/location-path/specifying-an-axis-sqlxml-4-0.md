---
title: Указание оси (SQLXML)
description: Узнайте, как указать ось в запросе на языке SQLXML 4,0 XPath, указывающий связь дерева между узлами, выбранными на шаге расположение, и узлом контекста.
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- XPath queries [SQLXML], location paths
- self axis
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- location path for XPath query
- axes [SQLXML]
ms.assetid: 65631795-3389-40cf-90ea-85e9438956c5
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 43daf972eacd67dcd7e75eabd1aca87bb3f67932
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84882188"
---
# <a name="specifying-an-axis-sqlxml-40"></a>Определение оси (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
    
-   Ось определяет древовидную связь между узлами, которые выбираются шагом доступа, и контекстными узлами. Поддерживаются следующие оси: **дочерний элемент**  
  
     Содержит дочерний элемент узла контекста.  
  
     Следующее выражение XPath (путь расположения) выбирает из текущего контекстного узла все **\<Customer>** дочерние элементы.  
  
    ```  
    child::Customer  
    ```  
  
     В следующем запросе XPath `child` является осью. `Customer` является проверкой узла.  
  
-   **источника**  
  
     Содержит родительский элемент контекстного узла.  
  
     Следующее выражение XPath выбирает все **\<Customer>** родительские **\<Order>** элементы дочерних элементов:  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     Это аналогично указанию `child::Customer`. В данном запросе XPath `child` и `parent` являются осями. `Customer` и `Order` являются проверками узла.  
  
-   **версию**  
  
     Содержит атрибут узла контекста.  
  
     Следующее выражение XPath выбирает атрибут **CustomerID** узла контекста:  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   **самообслуживания**  
  
     Содержит сам узел контекста.  
  
     Следующее выражение XPath выбирает текущий узел, если он является **\<Order>** узлом:  
  
    ```  
    self::Order  
    ```  
  
     В следующем запросе XPath `self` является осью, а `Order` — проверкой узла.  
  
  
