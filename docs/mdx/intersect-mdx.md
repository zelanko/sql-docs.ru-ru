---
title: Intersect (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f253dad526c509edff5c837b61ae2faae07d5758
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105361"
---
# <a name="intersect-mdx"></a>Intersect (многомерные выражения)


  Возвращает пересечение двух входных наборов, при необходимости сохраняя повторяющиеся элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Intersect(Set_Expression1 , Set_Expression2 [ , ALL ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Remarks  
 Функция **Intersect** возвращает пересечение двух наборов. По умолчанию эта функция удаляет дубликаты из обоих наборов до проведения операции над наборами. Оба набора должны иметь одинаковую размерность.  
  
 Необязательный флаг **ALL** оставляет дубликаты. Если указан параметр **ALL** , функция **Intersect** пересекает недублированные элементы как обычно, а также пересекает каждый дубликат в первом наборе, который имеет совпадающие дубликаты во втором наборе. Оба набора должны иметь одинаковую размерность.  
  
## <a name="example"></a>Пример  
 Следующий запрос возвращает значения 2003 и 2004 годов. Эти два элемента присутствуют в обоих указанных наборах.  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001], [Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003]}`  
  
 `, {[Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 Следующий запрос завершается ошибкой, поскольку два заданных набора содержат элементы из различных иерархий.  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001]}`  
  
 `, {[Customer].[City].&[Abingdon]&[ENG]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
