---
title: Указание проверки узла в пути расположения (SQLXML)
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
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f94f155ee86df6daf0c039a18f27c30e294d57df
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "75254736"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Задание проверки узла в пути доступа (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Проверка узла задает тип узла, выбранного на шаге доступа. Каждая ось (**дочерний**, **родительский**, **атрибут**или **Self**) имеет тип основного узла. Для оси **атрибута** типом основного узла является ** \<атрибут>**. Для **родительских**, **дочерних**и **собственных** осей типом основного узла является ** \<>element **.  
  
> [!NOTE]  
>  Шаблон проверки узла * (например `child::*`) не поддерживается.  
  
## <a name="node-test-example-1"></a>Проверка узла: Пример 1  
 Путь к `child::Customer` расположению выбирает ** \<** дочерние элементы Customer>элемента контекстного узла.  
  
 В следующем примере элемент `child` является осью, а `Customer` является проверкой узла. Тип основного узла для **дочерней** оси — ** \<элемент>**. Поэтому проверка узла имеет значение true, если узел ** \<>клиента** является ** \<элементом>** узле. Если узел контекста не ** \<имеет клиентов>** потомков, возвращается пустой набор узлов.  
  
## <a name="node-test-example-2"></a>Проверка узла: пример 2  
 Путь к `attribute::CustomerID` расположению выбирает атрибут **CustomerID** узла контекста.  
  
 В этом примере элемент `attribute` является осью, а `CustomerID` является проверкой узла. Основной тип узла оси **атрибута** — ** \<атрибут>**. Поэтому проверка узла имеет значение true, если **CustomerID** является ** \<атрибутом>** узле. Если узел контекста не имеет **CustomerID**, возвращается пустой набор узлов.  
  
> [!NOTE]  
>  В этой реализации XPath, если шаг расположения ссылается на ** \<элемент>** или ** \<атрибут>** тип, не объявленный в схеме, создается ошибка. Это отличается от реализации XPath в MSXML, где возвращается пустое множество узлов.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Сокращенный синтаксис осей  
 Поддерживается следующий сокращенный синтаксис пути доступа.  
  
-   `attribute::` можно сократить до `@`.  
  
     Путь доступа `Customer[@CustomerID="ALFKI"]` аналогичен выражению `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` можно исключить из шага определения расположения данных.  
  
     Таким же значением является **дочерняя** ось по умолчанию. Путь доступа `Customer/Order` аналогичен выражению `child::Customer/child::Order`.  
  
-   `self::node()` можно сократить до одной точки (.), а `parent::node()` можно сократить до двух точек (..).  
  
  
