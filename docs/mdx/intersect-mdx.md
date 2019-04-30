---
title: Intersect (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b24049cb81982075fa9234c6fa792db273d404db
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63224865"
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
  
## <a name="remarks"></a>Примечания  
 **Intersect** функция возвращает пересечение двух наборов. По умолчанию эта функция удаляет дубликаты из обоих наборов до проведения операции над наборами. Оба набора должны иметь одинаковую размерность.  
  
 Необязательный **все** флаг сохраняет повторяющиеся значения. Если **все** указано, **Intersect** функция пересечение неповторяющихся элементов как обычно и пересечение повторяющихся в первом наборе, имеющий повторяются во втором наборе. Оба набора должны иметь одинаковую размерность.  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
