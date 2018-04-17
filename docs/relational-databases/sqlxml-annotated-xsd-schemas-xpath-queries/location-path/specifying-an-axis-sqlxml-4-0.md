---
title: Определение оси (SQLXML 4.0) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-xml
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
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6265d47c51238b70c394d8f6dba1a9006cde4451
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-an-axis-sqlxml-40"></a>Определение оси (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
    
-   Ось определяет древовидную связь между узлами, которые выбираются шагом доступа, и контекстными узлами. Поддерживаются следующие оси: **дочерних**  
  
     Содержит дочерний элемент узла контекста.  
  
     Следующее выражение XPath (путь доступа) выбирает из текущего контекстного узла все  **\<клиента >** дочерних элементов:  
  
    ```  
    child::Customer  
    ```  
  
     В следующем запросе XPath `child` является осью. `Customer` является проверкой узла.  
  
-   **parent**  
  
     Содержит родительский элемент контекстного узла.  
  
     Следующее выражение XPath выбирает все  **\<клиента >** родительские объекты  **\<порядок >** дочерних элементов:  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     Это аналогично указанию `child::Customer`. В данном запросе XPath `child` и `parent` являются осями. `Customer` и `Order` являются проверками узла.  
  
-   **Атрибут**  
  
     Содержит атрибут узла контекста.  
  
     Следующее выражение XPath выбирает **CustomerID** атрибут узла контекста:  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   **Самообслуживания**  
  
     Содержит сам узел контекста.  
  
     Следующее выражение XPath выбирает текущий узел, если это  **\<порядок >** узла:  
  
    ```  
    self::Order  
    ```  
  
     В следующем запросе XPath `self` является осью, а `Order` — проверкой узла.  
  
  
