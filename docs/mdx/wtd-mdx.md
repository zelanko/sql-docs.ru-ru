---
title: WTD (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eee40829c72394bf95a1bc06540a434a1c74e166
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125813"
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
  
## <a name="remarks"></a>Remarks  
 Если выражение элемента не указано, по умолчанию используется текущий элемент первой иерархии с уровнем Weeks в первом измерении типа Time (**time. CurrentMember**) в группе мер.  
  
 Функция **WTD** является сочетанием клавиш для функции [PeriodsToDate](../mdx/periodstodate-mdx.md) , в которой уровень установлен равным *weeks*. Таким образом, вызов `Wtd(Member_Expression)` эквивалентен вызову `PeriodsToDate(Week_Level_Expression,Member_Expression)`.  
  
## <a name="see-also"></a>См. также:  
 [Текущему кварталу &#40;&#41;многомерных выражений](../mdx/qtd-mdx.md)   
 [MTD &#40;&#41;многомерных выражений](../mdx/mtd-mdx.md)   
 [&#40;с начала года&#41;многомерных выражений](../mdx/ytd-mdx.md)   
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
