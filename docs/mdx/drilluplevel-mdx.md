---
title: DrillupLevel (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e00851557b502bda3a98763eff4bac9c3abdccff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62690780"
---
# <a name="drilluplevel-mdx"></a>DrillupLevel (многомерные выражения)


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
 **DrillupLevel** функция возвращает набор элементов, иерархически организованных на основе элементов, включенных в указанном наборе. Порядок элементов в указанном наборе сохраняется.  
  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
