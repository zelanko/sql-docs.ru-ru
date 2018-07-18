---
title: Lag (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3c5479aa3ce855b554f34f72c5c86aa86eb04b9f
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740883"
---
# <a name="lag-mdx"></a>Lag (многомерные выражения)


  Возвращает элемент, который находится на указанное количество позиций ранее заданного элемента на его уровне.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.Lag(Index)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Index*  
 Допустимое числовое выражение, указывающее количество позиций между элементами.  
  
## <a name="remarks"></a>Примечания  
 Позиции элементов на уровне определяются естественным порядком иерархии атрибутов. Нумерация позиций начинается с нуля.  
  
 Если указан промежуток, равный нулю, **запаздывания** функция возвращает сам элемент.  
  
 Если указан промежуток, является отрицательной, **запаздывания** функция возвращает предыдущий элемент.  
  
 `Lag(1)` эквивалентно [PrevMember](../mdx/prevmember-mdx.md) функции. `Lag(-1)` эквивалентно [NextMember](../mdx/nextmember-mdx.md) функции.  
  
 **Запаздывания** функция подобна [привести](../mdx/lead-mdx.md) за тем исключением, которое **привести** функция выглядит в направлении, противоположном направлению **запаздывания** функции. Таким образом, вызов `Lag(n)` эквивалентен вызову `Lead(-n)`.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается значения для декабря 2001 г.:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(2) ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается значения для марта 2002 г.:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(-1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
