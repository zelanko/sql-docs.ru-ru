---
title: UNION (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe80d94be42a9ea953a5829de43bcab3cb30955f
ms.sourcegitcommit: d9c5b9ab3c282775ed61712892eeb3e150ccc808
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67597384"
---
# <a name="union--mdx"></a>UNION (многомерные Выражения)


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
  
## <a name="remarks"></a>Примечания  
 Эта функция возвращает объединение двух или более заданных наборов. С помощью стандартного синтаксиса и альтернативный синтаксис 1 дубликаты исключаются по умолчанию. При использовании стандартного синтаксиса с помощью **все** флаг сохраняет дубликаты в объединенном наборе. Дубликаты удаляются из конца набора. При использовании второго альтернативного варианта синтаксиса дубликаты всегда сохраняются.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показано поведение **объединения** функцию при помощи каждого из синтаксисов.  
  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
