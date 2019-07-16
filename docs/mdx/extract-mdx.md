---
title: Extract (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 26edefab1a81aebaa9bf63e69e24067428266de1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67906043"
---
# <a name="extract-mdx"></a>Extract (многомерные выражения)


  Возвращает набор кортежей из извлеченных элементов иерархии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Extract(Set_Expression, Hierarchy_Expression1 [,Hierarchy_Expression2, ...n] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Hierarchy_Expression1*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
 *Hierarchy_Expression2*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
## <a name="remarks"></a>Примечания  
 **Извлечь** функция возвращает набор, состоящий из кортежей из извлеченных элементов иерархии. Для каждого кортежа из указанного набора элементы из указанных иерархий извлекаются в новые кортежи результирующего набора. Эта функция всегда удаляет повторяющиеся кортежи.  
  
 **Извлечь** Функция противоположна из [Crossjoin](../mdx/crossjoin-mdx.md) функции.  
  
## <a name="examples"></a>Примеры  
 Следующий запрос показывает, как использовать **извлечь** функцию применительно к набору кортежей, возвращенных **NonEmpty** функции:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `//Returns the distinct combinations of Customer and Date for all purchases`  
  
 `//of Bike Racks or Bike Stands`  
  
 `EXTRACT(`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `*`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `*`  
  
 `{[Product].[Product Categories].[Subcategory].&[26],[Product].[Product Categories].[Subcategory].&[27]}`  
  
 `*`  
  
 `{[Measures].[Internet Sales Amount]}`  
  
 `)`  
  
 `,  [Customer].[Customer], [Date].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
