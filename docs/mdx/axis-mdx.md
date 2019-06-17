---
title: Оси (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2802422f7d50c0a504a0c42eec940d81e89e66b8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181643"
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
  
## <a name="remarks"></a>Примечания  
 **Оси** функция использует нулевое положение оси для получения набора кортежей по оси. Так, функция `Axis(0)` возвращает ось COLUMNS, функция `Axis(1)` — ось ROWS и т.д. **Оси** функция не может использоваться для оси фильтра. С помощью этих функций можно сообщить вычисляемым элементам контекст выполняемого запроса. Например, может понадобиться вычисляемый элемент, который предоставляет сумму элементов, выбранных только по оси строк. С помощью функции также можно сделать определение одной оси зависимым от определения другой. Например, когда содержимое оси строк упорядочивается в соответствии со значением первого элемента по оси столбцов.  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
