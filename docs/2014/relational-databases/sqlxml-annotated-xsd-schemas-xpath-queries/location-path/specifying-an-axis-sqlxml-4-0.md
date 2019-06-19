---
title: Определение оси (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 8da239fd8a6bbf559f89ba5fd1b0fa0ab10ec190
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66012651"
---
# <a name="specifying-an-axis-sqlxml-40"></a>Определение оси (SQLXML 4.0)
    
-   Ось определяет древовидную связь между узлами, которые выбираются шагом доступа, и контекстными узлами. Поддерживаются следующие оси:  `child`  
  
     Содержит дочерний элемент узла контекста.  
  
     Следующее выражение XPath (путь доступа) выбирает из текущего контекстного узла все  **\<клиента >** дочерние элементы:  
  
    ```  
    child::Customer  
    ```  
  
     В следующем запросе XPath `child` является осью. `Customer` является проверкой узла.  
  
-   `parent`  
  
     Содержит родительский элемент контекстного узла.  
  
     Следующее выражение XPath выбирает все  **\<клиента >** родителям  **\<порядок >** дочерние элементы:  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     Это аналогично указанию `child::Customer`. В данном запросе XPath `child` и `parent` являются осями. `Customer` и `Order` являются проверками узла.  
  
-   `attribute`  
  
     Содержит атрибут узла контекста.  
  
     Следующее выражение XPath выбирает **CustomerID** атрибут узла контекста:  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   `self`  
  
     Содержит сам узел контекста.  
  
     Следующее выражение XPath выбирает текущий узел, если это  **\<порядок >** узла:  
  
    ```  
    self::Order  
    ```  
  
     В следующем запросе XPath `self` является осью, а `Order` — проверкой узла.  
  
  
