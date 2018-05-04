---
title: Визуальные и невизуальные итоги | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0df374422d7879bf88404371de4ba728482181e7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="visual-totals-and-non-visual-totals"></a>Визуальные и невизуальные итоги
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Visual Totals — это итоги в конце столбца или строки, которые представляют собой сумму всех элементов, видимых в столбце или строке. Это поведение применяется по умолчанию при отображении большинства таблиц. Но иногда нужно, чтобы в таблице отображались только определенные столбцы, а итоги выводились для всей строки, в том числе для неотображаемых столбцов. Такие итоги принято называть **невизуальными итогами**, так как они складываются из видимых и невидимых значений.  
  
 Поведение итогов Non Visual демонстрируется в следующем сценарии. В первом шаге показано поведение по умолчанию для Visual Totals.  
  
 В следующем примере приведен запрос к [Adventure Works] для получения данных [Reseller Sales Amount] из таблицы, в которой категории товаров расположены по столбцам, а типы торговых посредников — по строкам. Обратите внимание, что в следующей инструкции SELECT предусмотрено получение итогов по товарам и по торговым посредникам:  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Она выдает следующие результаты.  
  
|||||||  
|-|-|-|-|-|-|  
||**All Products**|**Accessories**|**Bikes**|**Clothing**|**Components**|  
|**All Resellers**|**$ 80 450 596,98**|**$ 571 297,93**|**$ 66 302 381,56**|**$ 1 777 840,84**|**$ 11 799 076,66**|  
|**Specialty Bike Shop**|**$ 6 756 166,18**|**$ 65 125,48**|**$ 6 080 117,73**|**$ 252 933,91**|**$ 357 989,07**|  
|**Value Added Reseller**|**$ 34 967 517,33**|**$ 175 002,81**|**$ 30 892 354,33**|**$ 592 385,71**|**$ 3 307 774,48**|  
|**Warehouse**|**$ 38 726 913,48**|**$ 331 169,64**|**$ 29 329 909,50**|**$ 932 521,23**|**$ 8 133 313,11**|  
  
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
||**All Products**|**Accessories**|**Clothing**|  
|**All Resellers**|**$ 80 450 596,98**|**$ 571 297,93**|**$ 1 777 840,84**|  
|**Value Added Reseller**|**$ 34 967 517,33**|**$ 175 002,81**|**$ 592 385,71**|  
|**Warehouse**|**$ 38 726 913,48**|**$ 331 169,64**|**$ 932 521,23**|  
  
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
||All Products|Accessories|Clothing|  
|All Resellers|$ 73 694 430,80|$ 506 172,45|$ 1 524 906,93|  
|Value Added Reseller|$ 34 967 517,33|$ 175 002,81|$ 592 385,71|  
|Warehouse|$ 38 726 913,48|$ 331 169,64|$ 932 521,23|  
  
 При сравнении с предыдущими результатами можно заметить, что в строке [All Resellers] складываются отображаемые значения [Value Added Reseller] и [Warehouse], однако столбец [All Products] отображает общее значение для всех продуктов, включая те, которые не отображаются.  
  
## <a name="see-also"></a>См. также  
 [Ключевые понятия многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [Автоматическая проверка существования](../../../analysis-services/multidimensional-models/mdx/autoexists.md)   
 [Работа с членами, кортежей и наборов & #40; Многомерные Выражения & #41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Основные принципы запросов многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [Базовый запрос многомерных Выражений & #40; Многомерные Выражения & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query.md)   
 [Ограничение запроса с & #40; запросов и осей среза Многомерные Выражения & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-restricting-the-query.md)   
 [Определение контекста куба в запросе & #40; Многомерные Выражения & #41;](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)  
  
  
