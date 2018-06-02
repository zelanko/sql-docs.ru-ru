---
title: Lag (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c5e019312eacc2cf3f842721054ad5e39ea75d4b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578866"
---
# <a name="lag-mdx"></a>Lag (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
  
