---
title: DrillupLevel (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 19d6443857d53d835db4c395ddd43dc4a305ad8c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579456"
---
# <a name="drilluplevel-mdx"></a>DrillupLevel (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Детализирует обобщением элементы набора, находящиеся ниже указанного уровня.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DrillupLevel(Set_Expression [ , Level_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
## <a name="remarks"></a>Примечания  
 **DrillupLevel** функция возвращает набор элементов, иерархически организованных на основе элементов, включенные в указанный набор. Порядок элементов в указанном наборе сохраняется.  
  
 Если выражение уровня указано, **DrillupLevel** функция формирует набор путем получения только элементы, расположенные выше указанного уровня. Если выражение уровня указано, но набор не содержит элементов на данном уровне, возвращается указанный набор.  
  
 Если выражение уровня не задано, функция извлекает элементы, расположенные на один уровень выше самого нижнего уровня первого измерения, на которое ссылается указанный набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается набор элементов первого набора, которые расположены выше уровня Subcategory.  
  
```  
SELECT DrillUpLevel   
  ({[Product].[Product Categories].[All Products]  
    ,[Product].[Product Categories].[Subcategory].&[32],  
    [Product].[Product Categories].[Product].&[215]},  
  [Product].[Product Categories].[Subcategory]  
    )  
  ON 0  
  FROM [Adventure Works]  
  WHERE [Measures].[Internet Order Quantity]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
