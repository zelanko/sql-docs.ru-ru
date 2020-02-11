---
title: Запаздывание (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c7e95af96249b64f86bb1466283e8a1a38a32d90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905780"
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
  
 *Номер*  
 Допустимое числовое выражение, указывающее количество позиций между элементами.  
  
## <a name="remarks"></a>Remarks  
 Позиции элементов на уровне определяются естественным порядком иерархии атрибутов. Нумерация позиций начинается с нуля.  
  
 Если заданная задержка равна нулю, функция **Lag** возвращает сам указанный элемент.  
  
 Если заданная задержка отрицательна, функция **Lag** возвращает последующий элемент.  
  
 `Lag(1)`функция эквивалентна функции [PrevMember](../mdx/prevmember-mdx.md) . `Lag(-1)`функция эквивалентна функции [NextMember](../mdx/nextmember-mdx.md) .  
  
 Функция **Lag** аналогична функции [Lead](../mdx/lead-mdx.md) , за исключением того, что функция **Lead** ищет в обратном направлении функцию **Lag** . Таким образом, вызов `Lag(n)` эквивалентен вызову `Lead(-n)`.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
