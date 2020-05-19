---
title: Указание оси (SQLXML 4,0) | Документация Майкрософт
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 05891576872818e0d15d7bcae728dd3f19cdc252
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703094"
---
# <a name="specifying-an-axis-sqlxml-40"></a>Определение оси (SQLXML 4.0)
    
-   Ось определяет древовидную связь между узлами, которые выбираются шагом доступа, и контекстными узлами. Поддерживаются следующие оси:`child`  
  
     Содержит дочерний элемент узла контекста.  
  
     Следующее выражение XPath (путь расположения) выбирает из текущего контекстного узла все дочерние элементы ** \<>клиента** :  
  
    ```  
    child::Customer  
    ```  
  
     В следующем запросе XPath `child` является осью. `Customer` является проверкой узла.  
  
-   `parent`  
  
     Содержит родительский элемент контекстного узла.  
  
     Следующее выражение XPath выбирает все ** \< пользовательские>** родительских элементов ** \< заказа>** потомков:  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     Это аналогично указанию `child::Customer`. В данном запросе XPath `child` и `parent` являются осями. `Customer` и `Order` являются проверками узла.  
  
-   `attribute`  
  
     Содержит атрибут узла контекста.  
  
     Следующее выражение XPath выбирает атрибут **CustomerID** узла контекста:  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   `self`  
  
     Содержит сам узел контекста.  
  
     Следующее выражение XPath выбирает текущий узел, если это узел ** \< Order>** .  
  
    ```  
    self::Order  
    ```  
  
     В следующем запросе XPath `self` является осью, а `Order` — проверкой узла.  
  
  
