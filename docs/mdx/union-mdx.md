---
title: UNION (многомерные Выражения) | Документы Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- functions [MDX], Union
ms.assetid: cc083455-8b3b-46af-bb55-1e238376f162
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: ed3c4eac39b7ee34bc16063ad7671aa5a0175f9d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="union--mdx"></a>UNION (многомерные Выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор, порожденный объединением двух наборов, по желанию сохраняя повторяющиеся элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Standard syntax  
Union(Set_Expression1, Set_Expression2 [,...n][, ALL])  
  
Alternate syntax 1  
Set_Expression1 + Set_Expression2 [+...n]  
  
Alternate syntax 2  
{Set_Expression1 , Set_Expression2 [,...n]}  
```  
  
## <a name="arguments"></a>Аргументы  
 *Выражение набора 1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Выражение набора 2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Замечания  
 Эта функция возвращает объединение двух или более заданных наборов *.* При использовании стандартного синтаксиса и первого альтернативного варианта дубликаты исключаются по умолчанию. При использовании стандартного синтаксиса с помощью **все** флаг сохраняет дубликаты в объединенном наборе. Дубликаты удаляются из конца набора. При использовании второго альтернативного варианта синтаксиса дубликаты всегда сохраняются.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах демонстрируется поведение **объединения** функции с помощью каждого из синтаксисов.  
  
### <a name="standard-syntax-duplicates-eliminated"></a>Стандартный синтаксис, дубликаты исключаются  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="standard-syntax-duplicates-retained"></a>Стандартный синтаксис, дубликаты сохраняются  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   , ALL  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-1-duplicates-eliminated"></a>Первый альтернативный синтаксис, дубликаты исключаются  
  
```  
SELECT   
   [Date].[Calendar Year].children   
   + {[Date].[Calendar Year].[CY 2002]}   
   + {[Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-2-duplicates-retained"></a>Второй альтернативный синтаксис, дубликаты сохраняются  
  
```  
SELECT   
   {[Date].[Calendar Year].children  
   , [Date].[Calendar Year].[CY 2002]  
   , [Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [+ &#40;Объединения&#41; &#40;многомерных Выражений&#41;](../mdx/union-mdx-operator-reference.md)   
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
