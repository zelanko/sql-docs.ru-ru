---
title: Lead (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cc4d362fbc7656e9427548a352b32d5d8297071e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905744"
---
# <a name="lead-mdx"></a>Lead (многомерные выражения)


  Возвращает элемент, который следует за заданным элементом через указанное число позиций на уровне элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Индекс*  
 Допустимое числовое выражение, указывающее число позиций элементов.  
  
## <a name="remarks"></a>Remarks  
 Позиции элементов на уровне определяются естественным порядком иерархии атрибутов. Нумерация позиций начинается с нуля.  
  
 Если указанный ведущий равен нулю (0), функция **Lead** Возвращает указанный элемент.  
  
 Если указанный интерес является отрицательным, функция **Lead** возвращает более ранний элемент.  
  
 `Lead(1)`функция эквивалентна функции [NextMember](../mdx/nextmember-mdx.md) . `Lead(-1)`функция эквивалентна функции [PrevMember](../mdx/prevmember-mdx.md) .  
  
 Функция- **интерес** похожа на функцию [Lag](../mdx/lag-mdx.md) , за исключением того, что функция **Lag** ищет в обратном направлении функцию, противоположную **интересу** . Таким образом, вызов `Lead(n)` эквивалентен вызову `Lag(-n)`.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается значения для декабря 2001 г.:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(-2) ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается значения для марта 2002 г.:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
