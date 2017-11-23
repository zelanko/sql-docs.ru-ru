---
title: "Установка проверки узла в пути доступа (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 026cc54ab05fa07dca6a668902e286d9903dd94c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Задание проверки узла в пути доступа (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Проверка узла задает тип узла, выбранного на шаге доступа. Каждая ось (**дочерних**, **родительского**, **атрибута**, или **self**) имеет основной тип узла. Для **атрибута** является основным типом узла оси,  **\<атрибут >**. Для **родительского**, **дочерних**, и **self** является основным типом узла оси,  **\<элемент >**.  
  
> [!NOTE]  
>  Шаблон проверки узла * (например `child::*`) не поддерживается.  
  
## <a name="node-test-example-1"></a>Проверка узла: Пример 1.  
 Путь к расположению `child::Customer` выбирает  **\<клиента >** дочерние элементы узла контекста.  
  
 В следующем примере элемент `child` является осью, а `Customer` является проверкой узла. Основным типом узла для **дочерних** ось  **\<элемент >**. Таким образом, проверка узла имеет значение TRUE, если  **\<клиента >** узел  **\<элемент >** узла. Если узел контекста не содержит  **\<клиента >** дочерних элементов, возвращается пустой набор узлов.  
  
## <a name="node-test-example-2"></a>Проверки узла: Пример 2  
 Путь к расположению `attribute::CustomerID` выбирает **CustomerID** атрибут узла контекста.  
  
 В этом примере элемент `attribute` является осью, а `CustomerID` является проверкой узла. Тип узла участника для **атрибута** ось  **\<атрибут >**. Таким образом, проверка узла имеет значение TRUE, если **CustomerID** —  **\<атрибут >** узла. Если узел контекста не содержит **CustomerID**, возвращается пустой набор узлов.  
  
> [!NOTE]  
>  В данной реализации XPath, если ссылается шаге  **\<элемент >** или  **\<атрибут >** тип, который не объявлен в схеме, возникает ошибка. Это отличается от реализации XPath в MSXML, где возвращается пустое множество узлов.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Сокращенный синтаксис осей  
 Поддерживается следующий сокращенный синтаксис пути доступа.  
  
-   `attribute::` можно сократить до `@`.  
  
     Путь доступа `Customer[@CustomerID="ALFKI"]` аналогичен выражению `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` можно исключить из шага определения расположения данных.  
  
     Таким образом **дочерних** является осью по умолчанию. Путь доступа `Customer/Order` аналогичен выражению `child::Customer/child::Order`.  
  
-   `self::node()` можно сократить до одной точки (.), а `parent::node()` можно сократить до двух точек (..).  
  
  
