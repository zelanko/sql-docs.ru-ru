---
title: CalculationPassValue (многомерные Выражения) | Документы Microsoft
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
- CALCULATIONPASSVALUE
dev_langs:
- kbMDX
helpviewer_keywords:
- CalculationPassValue function
ms.assetid: 1b4012cb-c8c7-441a-bb9c-59430703b189
caps.latest.revision: 45
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: bac34c96e9acaeeb480b12cd3acded7e08225093
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="calculationpassvalue-mdx"></a>CalculationPassValue (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      Numeric syntax  
CalculationPassValue(Numeric_Expression,Pass_Value [, ABSOLUTE | RELATIVE [,ALL]])  
String syntax  
CalculationPassValue(String_Expression ,Pass_Value [, ABSOLUTE | RELATIVE [,ALL]])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
 *String_Expression*  
 Допустимое строковое выражение (обычно многомерное выражение над координатами ячейки), возвращающее число, представленное в виде строки.  
  
 *Pass_Value*  
 Допустимое числовое выражение, указывающее номер этапа вычислений.  
  
 ABSOLUTE  
 Значение флага доступа, указывающее, что *Pass_Value* параметр содержит отсчитываемый от нуля индекс этапа вычисления. Если флаг доступа не указан, это значение используется по умолчанию.  
  
 RELATIVE  
 Значение флага доступа, указывающее, что *Pass_Value* параметр содержит относительное смещение этапа запущенного вычисления. Если смещение указывает на этап вычисления с отрицательным номером, используется этап с номером «0», и ошибка не возникает.  
  
 ALL  
 Если указан этот флаг, все значения, кроме тех, которые загружаются подсистемой хранилища, равны NULL. В противном случае рассчитывается статистическое значение без применения каких-либо вычислений.  
  
## <a name="remarks"></a>Замечания  
 Если числовое выражение указано, функция возвращает его числовое значение на заданном этапе вычисления посредством вычисления многомерного выражения, при необходимости изменяя его в соответствии с флагом доступа и модификатором флага доступа.  
  
 Если строковое выражение указано, функция возвращает строковое значение, оценивая указанного строкового выражения MDX в указанном этапе вычисления и при необходимости была изменена с флагом доступа и модификатором флага доступа *.*  
  
 Автоматическое разрешение рекурсии в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], эта функция имеет практически не используется.  
  
> [!NOTE]  
>  Только администраторы могут использовать **CalculationPassValue** функции в скрипте многомерных Выражений. Возникнет ошибка, если скрипт многомерных выражений, содержащий данную функцию, выполняется в контексте роли, не имеющей прав администратора.  
  
## <a name="see-also"></a>См. также  
 [CalculationCurrentPass & #40; Многомерные Выражения & #41;](../mdx/calculationcurrentpass-mdx.md)   
 [IIf &#40;многомерных Выражений&#41;](../mdx/iif-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
