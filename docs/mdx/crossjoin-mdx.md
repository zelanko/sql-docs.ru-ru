---
title: Crossjoin (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CROSSJOIN
dev_langs:
- kbMDX
helpviewer_keywords:
- Crossjoin function
ms.assetid: 503b8376-d244-4855-8f44-a749764162e4
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 0529245668d3456af58e6907635c42570a70a882
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="crossjoin-mdx"></a>Crossjoin (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает перекрестное произведение двух или нескольких наборов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Standard syntax  
Crossjoin(Set_Expression1 ,Set_Expression2 [,...n] )  
  
Alternate syntax  
Set_Expression1 * Set_Expression2 [* ...n]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Замечания  
 **Crossjoin** функция возвращает перекрестное произведение двух или более заданных наборов. Порядок кортежей в результирующем наборе зависит от порядка соединяемых наборов и от порядка их элементов. Например, если первый набор содержит {x1, x2,..., x*n*}, а второй набор — {y1, y2,..., y*n*}, перекрестное произведение наборов:  
  
 {(x1, y1), (x1, y2) … (x1, y*n*), (x2, y1), (x2, y2)...  
  
 (x2, y*n*),..., (x*n*, y1), (x*n*, y2)... (xn, y*n*)}  
  
> [!IMPORTANT]  
>  Если наборы в перекрестном соединении состоят из кортежей из различных иерархий атрибутов одного измерения, функция вернет только те кортежи, которые действительно существуют. Дополнительные сведения см. в разделе [основные понятия многомерных выражений &#40;служб Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показаны простые примеры использования функции Crossjoin по осям Columns и Rows запроса:  
  
 `SELECT`  
  
 `[Customer].[Country].Members *`  
  
 `[Customer].[State-Province].Members`  
  
 `ON 0,`  
  
 `Crossjoin(`  
  
 `[Date].[Calendar Year].Members,`  
  
 `[Product].[Category].[Category].Members)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE Measures.[Internet Sales Amount]`  
  
 В следующем примере показана автоматическая фильтрация, которая выполняется при перекрестном соединении различных иерархий из одного измерения:  
  
 `SELECT`  
  
 `Measures.[Internet Sales Amount]`  
  
 `ON 0,`  
  
 `//Only the dates in Calendar Years 2003 and 2004 will be returned here`  
  
 `Crossjoin(`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]},`  
  
 `[Date].[Date].[Date].Members)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 В следующих трех примерах возвращается одинаковый результат — значение меры Internet Sales Amount по штатам в США. В первых двух примерах используются два синтаксиса перекрестного соединения, а в третьем демонстрируется применение предложения WHERE для извлечения тех же сведений.  
  
### <a name="example-1"></a>Пример 1  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
       [Customer].[State-Province].Members  
   ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
### <a name="example-2"></a>Пример 2  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
### <a name="example-3"></a>Пример 3  
  
```  
SELECT   
   [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
