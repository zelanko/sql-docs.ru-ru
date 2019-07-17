---
title: Определение оси (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 29d97b92f6979a7e5bbc67185f6e5a47ff82af68
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073284"
---
# <a name="specifying-an-axis-sqlxml-40"></a>Определение оси (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
    
-   Ось определяет древовидную связь между узлами, которые выбираются шагом доступа, и контекстными узлами. Поддерживаются следующие оси: **дочерних**  
  
     Содержит дочерний элемент узла контекста.  
  
     Следующее выражение XPath (путь доступа) выбирает из текущего контекстного узла все  **\<клиента >** дочерние элементы:  
  
    ```  
    child::Customer  
    ```  
  
     В следующем запросе XPath `child` является осью. `Customer` является проверкой узла.  
  
-   **parent**  
  
     Содержит родительский элемент контекстного узла.  
  
     Следующее выражение XPath выбирает все  **\<клиента >** родителям  **\<порядок >** дочерние элементы:  
  
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
  
-   **SELF**  
  
     Содержит сам узел контекста.  
  
     Следующее выражение XPath выбирает текущий узел, если это  **\<порядок >** узла:  
  
    ```  
    self::Order  
    ```  
  
     В следующем запросе XPath `self` является осью, а `Order` — проверкой узла.  
  
  
