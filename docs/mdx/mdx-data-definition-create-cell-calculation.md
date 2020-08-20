---
description: Определение данных многомерных выражений — CREATE CELL CALCULATION
title: Инструкция CREATE для вычисления ЯЧЕЙКИ (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5080e6bfa0f7a0ac942c3c5aa65bd1883b3050ee
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494877"
---
# <a name="mdx-data-definition---create-cell-calculation"></a>Определение данных многомерных выражений — CREATE CELL CALCULATION


  Формирует вычисление для расчета многомерных выражений по указанному набору кортежей в кубе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
[WITH <CELL CALCULATION clause> Calculation_Name  
   [,WITH <CELL CALCULATION clause> Calculation_Name...n]  
CREATE CELL CALCULATION CURRENTCUBE | Cube_Name.Calculation_Name   
  
<CELL CALCULATION clause> ::=  
   FOR Set_Expression AS 'MDX_Expression'   
      [ [ CONDITION = 'Logical_Expression' ]   
    | [ DISABLED = { TRUE | FALSE } ]   
    | [ DESCRIPTION =String ]   
    | [ CALCULATION_PASS_NUMBER = Integer]   
    | [ CALCULATION_PASS_DEPTH = Integer]   
    | [ SOLVE_ORDER = Integer]   
    | [ Calculation_Name= Scalar_Expression ], ...n]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимая строка, представляющая имя куба.  
  
 *Calculation_Name*  
 Допустимая строка, представляющая имя вычисления ячейки.  
  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *String*  
 Допустимое строковое значение.  
  
 *MDX_Expression*  
 Допустимое многомерное выражение.  
  
 *Logical_Expression*  
 Допустимое логическое многомерное выражение.  
  
 *Целое число*  
 Допустимое целое значение.  
  
 *Calculation_Name*  
 Допустимая строка, представляющая имя свойства вычисления ячейки.  
  
 *Scalar_Expression*  
 Допустимое скалярное многомерное выражение.  
  
## <a name="remarks"></a>Комментарии  
 Используя вычисляемые ячейки, клиентское приложение может определить значение свертки для определенного набора ячеек вместо выполнения операции над всем набором ячеек, как в случае c формулой пользовательской свертки или вычисляемым элементом. Например, можно указать, что любая ячейка в наборе, определяемом выражением `{[Canada],[Time].[2000]}`, может содержать значение, определяемое некоторой формулой. Все другие ячейки, которые не входят в этот набор, вычисляются как обычно.  
  
> [!NOTE]  
>  Форма Бэкуса-Наура (BNF) `{*(<comment> | <whitespace> | <newline>)}` будет проанализирована как `{*}` для обратной совместимости.  
  
## <a name="see-also"></a>См. также  
 [Создание вычисляемых ячеек с областью действия сеанса](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells)   
 [Создание вычислений ячеек с областью действия запроса &#40;многомерных выражениях&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations)   
 [Создание вычислений ячеек в МНОГОМЕРных выражениях &#40;многомерных выражениях&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations)   
 [Использование свойств ячеек &#40;&#41;многомерных выражений ](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties)   
 [FORMAT_STRING содержимого &#40;многомерных выражений&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents)   
 [FORE_COLOR и BACK_COLOR содержимое &#40;&#41;многомерных выражений ](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents)   
 [Инструкции определения данных многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
