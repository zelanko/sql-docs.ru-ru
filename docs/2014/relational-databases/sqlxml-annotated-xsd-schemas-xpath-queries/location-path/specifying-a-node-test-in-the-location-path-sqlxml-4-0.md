---
title: Установка проверки узла в пути доступа (SQLXML 4.0) | Документы Microsoft
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
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ca3eff7a8d915588d632dc12ff94e42d946d8aad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087569"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Задание проверки узла в пути доступа (SQLXML 4.0)
  Проверка узла задает тип узла, выбранного на шаге доступа. Каждая ось (`child`, `parent`, `attribute` или `self`) имеет тип узла участника. Для `attribute` является основным типом узла оси,  **\<атрибут >**. Для `parent`, `child`, и `self` является основным типом узла оси,  **\<элемент >**.  
  
> [!NOTE]  
>  Шаблон проверки узла * (например `child::*`) не поддерживается.  
  
## <a name="node-test-example-1"></a>Проверка узла: Пример 1.  
 Путь к расположению `child::Customer` выбирает  **\<клиента >** дочерние элементы узла контекста.  
  
 В следующем примере элемент `child` является осью, а `Customer` является проверкой узла. Основным типом узла для `child` ось  **\<элемент >**. Таким образом, проверка узла имеет значение TRUE, если  **\<клиента >** узел  **\<элемент >** узла. Если узел контекста не содержит  **\<клиента >** дочерних элементов, возвращается пустой набор узлов.  
  
## <a name="node-test-example-2"></a>Проверки узла: Пример 2  
 Путь к расположению `attribute::CustomerID` выбирает **CustomerID** атрибут узла контекста.  
  
 В этом примере элемент `attribute` является осью, а `CustomerID` является проверкой узла. Тип узла участника для `attribute` ось  **\<атрибут >**. Таким образом, проверка узла имеет значение TRUE, если **CustomerID** —  **\<атрибут >** узла. Если узел контекста не содержит **CustomerID**, возвращается пустой набор узлов.  
  
> [!NOTE]  
>  В данной реализации XPath, если ссылается шаге  **\<элемент >** или  **\<атрибут >** тип, который не объявлен в схеме, возникает ошибка. Это отличается от реализации XPath в MSXML, где возвращается пустое множество узлов.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Сокращенный синтаксис осей  
 Поддерживается следующий сокращенный синтаксис пути доступа.  
  
-   `attribute::` можно сократить до `@`.  
  
     Путь доступа `Customer[@CustomerID="ALFKI"]` аналогичен выражению `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` можно исключить из шага определения расположения данных.  
  
     Таким образом, ось `child` является осью по умолчанию. Путь доступа `Customer/Order` аналогичен выражению `child::Customer/child::Order`.  
  
-   `self::node()` можно сократить до одной точки (.), а `parent::node()` можно сократить до двух точек (..).  
  
  