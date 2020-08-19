---
description: Wtd (многомерные выражения)
title: WTD (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b45e583da6f7fc18712e432a0c504c3bc813141e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421888"
---
# <a name="wtd-mdx"></a>Wtd (многомерные выражения)


  Возвращает набор элементов с общим родителем, находящихся на том же уровне, что и данный элемент, начиная с первого такого элемента и заканчивая данным элементом, в соответствии с ограничениями уровня Week в измерении Time.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Wtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Комментарии  
 Если выражение элемента не указано, по умолчанию используется текущий элемент первой иерархии с уровнем Weeks в первом измерении типа Time (**time. CurrentMember**) в группе мер.  
  
 Функция **WTD** является сочетанием клавиш для функции [PeriodsToDate](../mdx/periodstodate-mdx.md) , в которой уровень установлен равным *weeks*. Таким образом, вызов `Wtd(Member_Expression)` эквивалентен вызову `PeriodsToDate(Week_Level_Expression,Member_Expression)`.  
  
## <a name="see-also"></a>См. также  
 [Текущему кварталу &#40;&#41;многомерных выражений ](../mdx/qtd-mdx.md)   
 [MTD &#40;&#41;многомерных выражений ](../mdx/mtd-mdx.md)   
 [&#40;с начала года&#41;многомерных выражений ](../mdx/ytd-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
