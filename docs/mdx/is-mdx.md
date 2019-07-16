---
title: IS (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: aaf4151d8291ccd4249892c6ef8fce8a3d280f6b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905982"
---
# <a name="is-mdx"></a>IS (многомерные выражения)


  Выполняет логическое сравнение двух выражений объектов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Expression1 IS ( Expression2 | NULL )  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое многомерное выражение, возвращающее ссылку на многомерный объект.  
  
 *Expression2*  
 Допустимое многомерное выражение, возвращающее ссылку на многомерный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, возвращающее **true** Если оба аргумента ссылаются на один и тот же объект; в противном случае **false**. Если **NULL** указывается ключевое слово, оператор возвращает **true** Если *Expression1* — **null**; в противном случае **false** .  
  
## <a name="remarks"></a>Примечания  
 **IS** оператор часто используется для определения кортежи и элементы идемпотентными, это означает, что они полностью эквивалентны.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как использовать **IS** оператор для проверки того, является ли текущий элемент на оси конкретный элемент:  
  
 `With`  
  
 `//Returns TRUE if the currentmember is Bikes`  
  
 `Member [Measures].[IsBikes?] AS`  
  
 `[Product].[Category].CurrentMember IS [Product].[Category].&[1]`  
  
 `SELECT`  
  
 `{[Measures].[IsBikes?]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
