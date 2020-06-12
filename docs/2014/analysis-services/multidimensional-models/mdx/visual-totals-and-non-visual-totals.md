---
title: Визуальные итоги и не визуальные итоги | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ea9d02f2-a668-4547-ade5-e3d077a2e1bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79497b0fd84116ab69187bd7d1733101357ffbce
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546106"
---
# <a name="visual-totals-and-non-visual-totals"></a>Визуальные и невизуальные итоги
  Visual Totals — это итоги в конце столбца или строки, которые представляют собой сумму всех элементов, видимых в столбце или строке. Это поведение применяется по умолчанию при отображении большинства таблиц. Но иногда нужно, чтобы в таблице отображались только определенные столбцы, а итоги выводились для всей строки, в том числе для неотображаемых столбцов. Такие итоги принято называть `Non Visual Totals`, поскольку они складываются из видимых и невидимых значений.  
  
 Поведение итогов Non Visual демонстрируется в следующем сценарии. В первом шаге показано поведение по умолчанию для Visual Totals.  
  
 В следующем примере приведен запрос к [Adventure Works] для получения данных [Reseller Sales Amount] из таблицы, в которой категории товаров расположены по столбцам, а типы торговых посредников — по строкам. Обратите внимание, что в следующей инструкции SELECT предусмотрено получение итогов по товарам и по торговым посредникам:  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Она выдает следующие результаты.  
  
|||||||  
|-|-|-|-|-|-|  
||**Все продукты**|**Принадлежности**|**Велосипеды**|**Экипировка**|**Components**|  
|**All Resellers**|**$ 80 450 596,98**|**$ 571 297,93**|**$ 66 302 381,56**|**$ 1 777 840,84**|**$ 11 799 076,66**|  
|**Specialty Bike Shop**|**$ 6 756 166,18**|**$ 65 125,48**|**$ 6 080 117,73**|**$ 252 933,91**|**$ 357 989,07**|  
|**Value Added Reseller**|**$ 34 967 517,33**|**$ 175 002,81**|**$ 30 892 354,33**|**$ 592 385,71**|**$ 3 307 774,48**|  
|**Хранилище**|**$ 38 726 913,48**|**$ 331 169,64**|**$ 29 329 909,50**|**$ 932 521,23**|**$ 8 133 313,11**|  
  
## <a name="non-visual-on-rows-and-columns"></a>Применение режима Non Visual к строкам и столбцам  
 Чтобы получить таблицу с данными только по товарам Accessories и Clothing и торговым посредникам Value Added Reseller и Warehouse, сохраняя при этом полные итоги, можно написать следующую инструкцию, содержащую предложение NON VISUAL:  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Она выдает следующие результаты.  
  
|||||  
|-|-|-|-|  
||**Все продукты**|**Принадлежности**|**Экипировка**|  
|**All Resellers**|**$ 80 450 596,98**|**$ 571 297,93**|**$ 1 777 840,84**|  
|**Value Added Reseller**|**$ 34 967 517,33**|**$ 175 002,81**|**$ 592 385,71**|  
|**Хранилище**|**$ 38 726 913,48**|**$ 331 169,64**|**$ 932 521,23**|  
  
## <a name="non-visual-on-rows"></a>Применение режима Non Visual к строкам  
 Чтобы создать таблицу, которая визуально рассчитывает итоги столбцов, а для строк приводится истинный итог всех [Category], необходимо выполнить следующий запрос.  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Обратите внимание, что NON VISUAL применяется только к [Category].  
  
 Этот запрос выдаст следующий результат.  
  
|||||  
|-|-|-|-|  
||Все продукты|Принадлежности|Экипировка|  
|All Resellers|$ 73 694 430,80|$ 506 172,45|$ 1 524 906,93|  
|Value Added Reseller|$ 34 967 517,33|$ 175 002,81|$ 592 385,71|  
|Warehouse|$ 38 726 913,48|$ 331 169,64|$ 932 521,23|  
  
 При сравнении с предыдущими результатами можно заметить, что в строке [All Resellers] складываются отображаемые значения [Value Added Reseller] и [Warehouse], однако столбец [All Products] отображает общее значение для всех продуктов, включая те, которые не отображаются.  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия в Analysis Services &#40;многомерных выражений&#41;](../key-concepts-in-mdx-analysis-services.md)   
 [Автоматической проверки существования](autoexists.md)   
 [Работа с элементами, кортежами и наборами &#40;многомерных выражениях&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [Основные принципы запросов многомерных выражений &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)   
 [Базовый запрос многомерных выражений &#40;многомерные выражения&#41;](mdx-query-the-basic-query.md)   
 [Ограничьте запрос с помощью осей запроса и среза &#40;&#41;многомерных выражений](mdx-query-and-slicer-axes-restricting-the-query.md)   
 [Определение контекста куба в запросе (многомерные выражения)](establishing-cube-context-in-a-query-mdx.md)  
  
  
