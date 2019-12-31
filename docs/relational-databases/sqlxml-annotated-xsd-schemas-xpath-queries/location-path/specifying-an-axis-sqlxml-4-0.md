---
title: Указание оси (SQLXML)
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
ms.openlocfilehash: a219c2093832b979171584d5559da359b574552e
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75253056"
---
# <a name="specifying-an-axis-sqlxml-40"></a>Определение оси (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
    
-   Ось определяет древовидную связь между узлами, которые выбираются шагом доступа, и контекстными узлами. Поддерживаются следующие оси: **дочерний элемент**  
  
     Содержит дочерний элемент узла контекста.  
  
     Следующее выражение XPath (путь расположения) выбирает из текущего контекстного узла все дочерние элементы ** \<>клиента** :  
  
    ```  
    child::Customer  
    ```  
  
     В следующем запросе XPath `child` является осью. 
  `Customer` является проверкой узла.  
  
-   **источника**  
  
     Содержит родительский элемент контекстного узла.  
  
     Следующее выражение XPath выбирает все ** \<пользовательские>** родительских элементов ** \<заказа>** потомков:  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     Это аналогично указанию `child::Customer`. В данном запросе XPath `child` и `parent` являются осями. 
  `Customer` и `Order` являются проверками узла.  
  
-   **версию**  
  
     Содержит атрибут узла контекста.  
  
     Следующее выражение XPath выбирает атрибут **CustomerID** узла контекста:  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   **самообслуживания**  
  
     Содержит сам узел контекста.  
  
     Следующее выражение XPath выбирает текущий узел, если это узел ** \<Order>** .  
  
    ```  
    self::Order  
    ```  
  
     В следующем запросе XPath `self` является осью, а `Order` — проверкой узла.  
  
  
