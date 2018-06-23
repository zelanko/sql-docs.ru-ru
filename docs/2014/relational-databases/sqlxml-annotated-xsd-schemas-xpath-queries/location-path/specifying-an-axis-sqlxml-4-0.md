---
title: Определение оси (SQLXML 4.0) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f3b9f58369cea876bc345300a945f85260b4326a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097475"
---
# <a name="specifying-an-axis-sqlxml-40"></a>Определение оси (SQLXML 4.0)
    
-   Ось определяет древовидную связь между узлами, которые выбираются шагом доступа, и контекстными узлами. Поддерживаются следующие оси:  `child`  
  
     Содержит дочерний элемент узла контекста.  
  
     Следующее выражение XPath (путь доступа) выбирает из текущего контекстного узла все  **\<клиента >** дочерних элементов:  
  
    ```  
    child::Customer  
    ```  
  
     В следующем запросе XPath `child` является осью. `Customer` является проверкой узла.  
  
-   `parent`  
  
     Содержит родительский элемент контекстного узла.  
  
     Следующее выражение XPath выбирает все  **\<клиента >** родительские объекты  **\<порядок >** дочерних элементов:  
  
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
  
  