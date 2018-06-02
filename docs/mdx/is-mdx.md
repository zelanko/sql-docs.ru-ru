---
title: IS (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5c36a5f45e34d6d78043f6ce8a3e3fb040ecc9f6
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578596"
---
# <a name="is-mdx"></a>IS (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 Логическое значение, которое возвращает **true** , если оба аргумента ссылаются на один и тот же объект; в противном случае **false**. Если **NULL** указывается ключевое слово, оператор возвращает **true** Если *Expression1* — **null**; в противном случае **false**.  
  
## <a name="remarks"></a>Примечания  
 **IS** часто используется для определения кортежи и элементы идемпотентными, то есть полностью эквивалентными.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как использовать **IS** оператор, проверьте, является ли текущий элемент на оси конкретный элемент:  
  
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
 [Справочник по операторам Многомерных &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
