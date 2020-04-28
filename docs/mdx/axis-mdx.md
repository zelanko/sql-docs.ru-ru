---
title: Axis (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fa65c1531be29273c0a838b978109bbd1c8a2b18
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68016982"
---
# <a name="axis-mdx"></a>Axis (многомерные выражения)


  Возвращает набор кортежей по заданной оси.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Axis(Axis_Number)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Axis_Number*  
 Допустимое числовое выражение, указывающее номер оси.  
  
## <a name="remarks"></a>Remarks  
 Функция **Axis** использует Отсчитываемая от нуля координату оси для возврата набора кортежей по оси. Так, функция `Axis(0)` возвращает ось COLUMNS, функция `Axis(1)` — ось ROWS и т.д. Функцию **Axis** нельзя использовать на оси фильтра. С помощью этих функций можно сообщить вычисляемым элементам контекст выполняемого запроса. Например, может понадобиться вычисляемый элемент, который предоставляет сумму элементов, выбранных только по оси строк. С помощью функции также можно сделать определение одной оси зависимым от определения другой. Например, когда содержимое оси строк упорядочивается в соответствии со значением первого элемента по оси столбцов.  
  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
