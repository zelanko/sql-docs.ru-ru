---
title: Lag (многомерные Выражения) | Документация Майкрософт
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63205824"
---
# <a name="lag-mdx"></a>Lag (многомерные выражения)


  Возвращает элемент, который находится на указанное количество позиций ранее заданного элемента на его уровне.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.Lag(Index)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Index*  
 Допустимое числовое выражение, указывающее количество позиций между элементами.  
  
## <a name="remarks"></a>Примечания  
 Позиции элементов на уровне определяются естественным порядком иерархии атрибутов. Нумерация позиций начинается с нуля.  
  
 Если указан промежуток, равный нулю, **Lag** функция возвращает сам элемент.  
  
 Если заданное число периодов отрицательно, **Lag** функция возвращает последующего члена.  
  
 `Lag(1)` эквивалентно [PrevMember](../mdx/prevmember-mdx.md) функции. `Lag(-1)` эквивалентно [NextMember](../mdx/nextmember-mdx.md) функции.  
  
 **Lag** функция аналогична [привести](../mdx/lead-mdx.md) за тем исключением, которое **привести** функция ищет в обратном направлении для **Lag** функция. Таким образом, вызов `Lag(n)` эквивалентен вызову `Lead(-n)`.  
  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
