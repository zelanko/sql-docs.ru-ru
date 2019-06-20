---
title: Lead (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d72af1bf0b671eeb2bd4b84c194f129ed1ce6bfe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63205435"
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
  
 *Index*  
 Допустимое числовое выражение, указывающее число позиций элементов.  
  
## <a name="remarks"></a>Примечания  
 Позиции элементов на уровне определяются естественным порядком иерархии атрибутов. Нумерация позиций начинается с нуля.  
  
 Если заданная позиция равна нулю (0), **привести** функция возвращает указанный элемент.  
  
 Если заданная позиция отрицательна, **привести** функция возвращает предыдущий элемент.  
  
 `Lead(1)` эквивалентно [NextMember](../mdx/nextmember-mdx.md) функции. `Lead(-1)` эквивалентно [PrevMember](../mdx/prevmember-mdx.md) функции.  
  
 **Привести** функция аналогична [Lag](../mdx/lag-mdx.md) за тем исключением, которое **Lag** функция ищет в обратном направлении для **привести** функция. Таким образом, вызов `Lead(n)` эквивалентен вызову `Lag(-n)`.  
  
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
  
  
