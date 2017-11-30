---
title: "Оси (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: AXIS
dev_langs: kbMDX
helpviewer_keywords: Axis function
ms.assetid: a3a60a1e-e266-4fa1-ae13-bae73544de33
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f53246e6442f7aebc60bea3a4ccbdecd7423e60d
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="axis-mdx"></a>Axis (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор кортежей по заданной оси.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Axis(Axis_Number)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Axis_Number*  
 Допустимое числовое выражение, указывающее номер оси.  
  
## <a name="remarks"></a>Замечания  
 **Оси** функция опираясь на нулевое положение оси, возвращает набор кортежей по оси. Так, функция `Axis(0)` возвращает ось COLUMNS, функция `Axis(1)` — ось ROWS и т.д. **Оси** функцию нельзя использовать для оси фильтра. С помощью этих функций можно сообщить вычисляемым элементам контекст выполняемого запроса. Например, может понадобиться вычисляемый элемент, который предоставляет сумму элементов, выбранных только по оси строк. С помощью функции также можно сделать определение одной оси зависимым от определения другой. Например, когда содержимое оси строк упорядочивается в соответствии со значением первого элемента по оси столбцов.  
  
> [!NOTE]  
>  Ось может ссылаться только на предыдущую ось. Например, `Axis(0)` можно вызывать только после расчета оси COLUMNS, например по осям ROW или PAGE.  
  
## <a name="examples"></a>Примеры  
 Запрос в следующем примере показывает использование функции Axis:  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SETTOSTR(AXIS(1))`  
  
 `SELECT MEASURES.AXISDEMO ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 В следующем примере показано использование функции Axis внутри вычисляемого элемента:  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SUM(AXIS(1), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.AXISDEMO} ON 0,`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
