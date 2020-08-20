---
description: Ancestors (многомерные выражения)
title: Предки (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d92f15f20c872fbe63db09a55356b5d1e35ff0d6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461686"
---
# <a name="ancestors-mdx"></a>Ancestors (многомерные выражения)


  Функция, возвращающая набор предков заданного элемента на заданном уровне или заданном расстоянии от элемента. В службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] возвращаемый набор всегда будет состоять из одного члена — не [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживает несколько родителей для одного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Level syntax  
Ancestors(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestors(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Друг*  
 Допустимое числовое выражение, указывающее расстояние от заданного элемента.  
  
## <a name="remarks"></a>Remarks  
 С помощью функции- **предков** вы предоставляете функцию с многомерным выражением элемента, а затем ПРЕДОСТАВЛЯЕТе многомерное выражение уровня, который является предком этого элемента, или числовое выражение, представляющее число уровней выше этого элемента. С этой информацией функция **предков** возвращает набор элементов (который будет набором, состоящим из одного элемента) на этом уровне.  
  
> [!NOTE]  
>  Чтобы получить элемент предка, а не набор предков, используйте функцию [предка](../mdx/ancestor-mdx.md) .  
  
 Если выражение уровня задано, функция **предков** возвращает набор всех предков указанного элемента на указанном уровне. Если заданный элемент не входит в ту же иерархию, что и заданный уровень, функция вернет ошибку.  
  
 Если задано расстояние, функция- **предки** возвращает набор всех элементов, которые являются количеством шагов, указанных в иерархии, указанной в выражении элемента. Элемент может быть определен как элемент иерархии атрибута, пользовательской иерархии или при некоторых обстоятельствах иерархии типа «родители-потомки». Число 1 возвращает набор элементов на родительском уровне, а число 2 возвращает набор элементов на прародительском уровне (если такой существует). Число 0 вернет набор, включающий только сам элемент.  
  
> [!NOTE]  
>  Используйте эту форму функции- **предков** для случаев, когда уровень родителя неизвестен или не может быть именован.  
  
## <a name="examples"></a>Примеры  
 В следующем примере функция **предков** используется для возврата меры Internet Sales Amount для элемента, его родителя и его бабушке. В этом примере используются выражения уровня для определения уровней, которые должны быть возвращены. Уровни находятся в той же иерархии, что и заданный элемент в выражении элемента.  
  
```  
SELECT {  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Category]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Subcategory]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Product])  
    } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 В следующем примере функция **предков** используется для возврата меры Internet Sales Amount для элемента, его родителя и его бабушке. В этом примере используются числовые выражения для определения уровней, которые должны быть возвращены. Уровни находятся в той же иерархии, что и заданный элемент в выражении элемента.  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],2  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],1  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],0  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM  [Adventure Works]  
```  
  
 В следующем примере функция **предков** используется для возврата меры Internet Sales Amount для родителя элемента иерархии атрибута. В этом пример используются числовые выражения для определения уровня, который должен быть возвращен. Поскольку элемент в выражении элемента является элементом иерархии атрибута, его родителем является уровень «Все».  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product].[Mountain-100 Silver, 38],1  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
