---
title: ИМЕЕТ (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: aaf4151d8291ccd4249892c6ef8fce8a3d280f6b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
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
 Логическое значение, возвращающее **значение true** , если оба аргумента ссылаются на один и тот же объект. в противном случае — **значение false**. Если указано ключевое слово **null** , оператор возвращает **true** , если *expression1* имеет **значение NULL**; в противном случае — **значение false**.  
  
## <a name="remarks"></a>Remarks  
 Оператор **is** часто используется для определения того, являются ли кортежи и элементы идемпотентными, то есть они точно эквивалентны.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как использовать оператор **is** для проверки того, является ли текущий элемент на оси конкретным элементом:  
  
 `With`  
  
 `//Returns TRUE if the currentmember is Bikes`  
  
 `Member [Measures].[IsBikes?] AS`  
  
 `[Product].[Category].CurrentMember IS [Product].[Category].&[1]`  
  
 `SELECT`  
  
 `{[Measures].[IsBikes?]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-operator-reference-mdx.md)  
  
  
