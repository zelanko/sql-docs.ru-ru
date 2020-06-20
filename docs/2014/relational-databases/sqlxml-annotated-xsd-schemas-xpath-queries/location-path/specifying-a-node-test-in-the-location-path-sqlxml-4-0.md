---
title: Указание проверки узла в пути расположения (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: rothja
ms.author: jroth
ms.openlocfilehash: 02f78577eab391f1774251ad2c6ca7b9a4bd2dab
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85015218"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Задание проверки узла в пути доступа (SQLXML 4.0)
  Проверка узла задает тип узла, выбранного на шаге доступа. Каждая ось (`child`, `parent`, `attribute` или `self`) имеет тип узла участника. Для `attribute` оси тип основного узла — **\<attribute>** . Для `parent` осей, `child` и `self` Тип основного узла — **\<element>** .  
  
> [!NOTE]  
>  Шаблон проверки узла * (например `child::*`) не поддерживается.  
  
## <a name="node-test-example-1"></a>Проверка узла: Пример 1  
 Путь к расположению `child::Customer` выбирает **\<Customer>** дочерние элементы узла контекста.  
  
 В следующем примере элемент `child` является осью, а `Customer` является проверкой узла. Тип основного узла для `child` оси — **\<element>** . Поэтому проверка узла имеет значение TRUE, если **\<Customer>** узел является **\<element>** узлом. Если узел контекста не имеет **\<Customer>** дочерних элементов, возвращается пустой набор узлов.  
  
## <a name="node-test-example-2"></a>Проверка узла: пример 2  
 Путь к расположению `attribute::CustomerID` выбирает атрибут **CustomerID** узла контекста.  
  
 В этом примере элемент `attribute` является осью, а `CustomerID` является проверкой узла. Тип основного узла `attribute` оси — **\<attribute>** . Поэтому проверка узла имеет значение TRUE, если **CustomerID** является **\<attribute>** узлом. Если узел контекста не имеет **CustomerID**, возвращается пустой набор узлов.  
  
> [!NOTE]  
>  В этой реализации XPath, если шаг расположения ссылается на **\<element>** или **\<attribute>** тип, который не объявлен в схеме, создается ошибка. Это отличается от реализации XPath в MSXML, где возвращается пустое множество узлов.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Сокращенный синтаксис осей  
 Поддерживается следующий сокращенный синтаксис пути доступа.  
  
-   `attribute::` можно сократить до `@`.  
  
     Путь доступа `Customer[@CustomerID="ALFKI"]` аналогичен выражению `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` можно исключить из шага определения расположения данных.  
  
     Таким образом, ось `child` является осью по умолчанию. Путь доступа `Customer/Order` аналогичен выражению `child::Customer/child::Order`.  
  
-   `self::node()` можно сократить до одной точки (.), а `parent::node()` можно сократить до двух точек (..).  
  
  
