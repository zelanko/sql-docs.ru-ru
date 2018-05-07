---
title: Инструкция CREATE CELL CALCULATION (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CELL CALCULATION
- CREATE
- CALCULATION
- CELL
- CREATE_CELL_CALCULATION
- CREATE CELL
- CREATE CELL CALCULATION
dev_langs:
- kbMDX
helpviewer_keywords:
- calculations [Analysis Services], creating
- CREATE CELL CALCULATION statement
- cubes [Analysis Services], calculations
ms.assetid: 01ced1b3-ada1-4b55-b350-e4255c3cc679
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: ca01b454906ddb5c51a6cd96e8c49190bfda9998
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---create-cell-calculation"></a>Определения данных многомерных Выражений — Создание ВЫЧИСЛЕНИЯ ЯЧЕЙКИ.
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
 *Строковые значения*  
 Допустимое строковое значение.  
  
 *MDX_Expression*  
 Допустимое многомерное выражение.  
  
 *Logical_Expression*  
 Допустимое логическое многомерное выражение.  
  
 *Целочисленный*  
 Допустимое целое значение.  
  
 *Calculation_Name*  
 Допустимая строка, представляющая имя свойства вычисления ячейки.  
  
 *Scalar_Expression*  
 Допустимое скалярное многомерное выражение.  
  
## <a name="remarks"></a>Замечания  
 Используя вычисляемые ячейки, клиентское приложение может определить значение свертки для определенного набора ячеек вместо выполнения операции над всем набором ячеек, как в случае c формулой пользовательской свертки или вычисляемым элементом. Например, можно указать, что любая ячейка в наборе, определяемом выражением `{[Canada],[Time].[2000]}`, может содержать значение, определяемое некоторой формулой. Все другие ячейки, которые не входят в этот набор, вычисляются как обычно.  
  
> [!NOTE]  
>  Форма Бэкуса-Наура (BNF) `{*(<comment> | <whitespace> | <newline>)}` будет проанализирована как `{*}` для обратной совместимости.  
  
## <a name="see-also"></a>См. также  
 [Создание вычисляемых ячеек с областью действия сеанса](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells.md)   
 [Создание вычислений ячеек с областью действия запроса & #40; Многомерные Выражения & #41;](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations.md)   
 [Построение вычислений значений ячеек в многомерном Выражении &#40;многомерных Выражений&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations.md)   
 [С помощью свойства ячейки & #40; Многомерные Выражения & #41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)   
 [Строка формата Format_string & #40; Многомерные Выражения & #41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)   
 [Свойства ячеек FORE_COLOR и Back_color &#40;многомерных Выражений&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)   
 [Инструкции определения данных многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
