---
title: Задание проверки узла в пути доступа (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 15d5389f9a16d676aa5d644b030455d4c63adf7b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62720003"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Задание проверки узла в пути доступа (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Проверка узла задает тип узла, выбранного на шаге доступа. Каждая ось (**дочерних**, **родительского**, **атрибут**, или **self**) имеет основной тип узла. Для **атрибут** является основным типом узла оси,  **\<атрибут >** . Для **родительского**, **дочерних**, и **self** является основным типом узла оси,  **\<элемент >** .  
  
> [!NOTE]  
>  Шаблон проверки узла * (например `child::*`) не поддерживается.  
  
## <a name="node-test-example-1"></a>Проверка узла. Пример 1  
 Путь к расположению `child::Customer` выбирает  **\<клиента >** дочерние элементы узла контекста.  
  
 В следующем примере элемент `child` является осью, а `Customer` является проверкой узла. Основным типом узла для **дочерних** ось является  **\<элемент >** . Таким образом, проверка узла возвращает значение TRUE Если  **\<клиента >** узел является  **\<элемент >** узла. Если узел контекста не имеет  **\<клиента >** дочерних элементов, возвращается пустой набор узлов.  
  
## <a name="node-test-example-2"></a>Проверка узла. Пример 2  
 Путь к расположению `attribute::CustomerID` выбирает **CustomerID** атрибут узла контекста.  
  
 В этом примере элемент `attribute` является осью, а `CustomerID` является проверкой узла. Тип узла участника **атрибут** ось является  **\<атрибут >** . Таким образом, проверка узла возвращает значение TRUE Если **CustomerID** —  **\<атрибут >** узла. Если узел контекста не имеет **CustomerID**, возвращается пустой набор узлов.  
  
> [!NOTE]  
>  В данной реализации XPath, если шаг определения расположения ссылается на  **\<элемент >** или  **\<атрибут >** тип, который не объявлен в схеме, формируется ошибка. Это отличается от реализации XPath в MSXML, где возвращается пустое множество узлов.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Сокращенный синтаксис осей  
 Поддерживается следующий сокращенный синтаксис пути доступа.  
  
-   `attribute::` можно сократить до `@`.  
  
     Путь доступа `Customer[@CustomerID="ALFKI"]` аналогичен выражению `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` можно исключить из шага определения расположения данных.  
  
     Таким образом **дочерних** является осью по умолчанию. Путь доступа `Customer/Order` аналогичен выражению `child::Customer/child::Order`.  
  
-   `self::node()` можно сократить до одной точки (.), а `parent::node()` можно сократить до двух точек (..).  
  
  
