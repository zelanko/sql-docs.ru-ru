---
title: DrillupLevel (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ef2f94eb843b3ffbfbb67eb6ca01f2114522e024
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68049217"
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
  
## <a name="remarks"></a>Remarks  
 Функция **DrillupLevel** возвращает набор элементов, организованных иерархически на основе элементов, включенных в указанный набор. Порядок элементов в указанном наборе сохраняется.  
  
 Если выражение уровня задано, функция **DrillupLevel** конструирует набор, получая только те элементы, которые находятся выше указанного уровня. Если выражение уровня указано, но набор не содержит элементов на данном уровне, возвращается указанный набор.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
