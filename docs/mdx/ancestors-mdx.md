---
title: Ancestors (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0c108ea102e03000481d18bfc69f657e6bd8a0ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63313725"
---
# <a name="ancestors-mdx"></a>Ancestors (многомерные выражения)


  Функция, возвращающая набор предков заданного элемента на заданном уровне или заданном расстоянии от элемента. С помощью [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], возвращаемый набор всегда будет содержать один элемент — [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживают нескольких родителей для одного элемента.  
  
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
  
 *расстояние*  
 Допустимое числовое выражение, указывающее расстояние от заданного элемента.  
  
## <a name="remarks"></a>Примечания  
 С помощью **предков** функцию, задать функцию с Многомерным выражением элемента, а затем задать Многомерное выражение уровня, являющегося предком элемента, или числовое выражение, представляющее число уровней над данным элементом. Имея эту информацию **предков** функция возвращает набор элементов (который будет набором, состоящим из одного элемента) на этом уровне.  
  
> [!NOTE]  
>  Для возвращения предка элемента вместо набора предков используется [предка](../mdx/ancestor-mdx.md) функции.  
  
 Если выражение уровня указано, **предков** функция возвращает набор всех предков заданного элемента на заданном уровне. Если заданный элемент не входит в ту же иерархию, что и заданный уровень, функция вернет ошибку.  
  
 Если задано расстояние, **предков** функция возвращает набор всех элементов, которые находятся вверх по иерархии на заданном расстоянии. Элемент может быть определен как элемент иерархии атрибута, пользовательской иерархии или при некоторых обстоятельствах иерархии типа «родители-потомки». Число 1 возвращает набор элементов на родительском уровне, а число 2 возвращает набор элементов на прародительском уровне (если такой существует). Число 0 вернет набор, включающий только сам элемент.  
  
> [!NOTE]  
>  Используйте эту форму для **предков** функции для случаев, в которых уровень родительского элемента неизвестен или не может быть именован.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется **предков** функция возвращает меру Internet Sales Amount для элемента, его родителя и прародителя. В этом примере используются выражения уровня для определения уровней, которые должны быть возвращены. Уровни находятся в той же иерархии, что и заданный элемент в выражении элемента.  
  
```  
SELECT {  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Category]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Subcategory]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Product])  
    } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 В следующем примере используется **предков** функция возвращает меру Internet Sales Amount для элемента, его родителя и прародителя. В этом примере используются числовые выражения для определения уровней, которые должны быть возвращены. Уровни находятся в той же иерархии, что и заданный элемент в выражении элемента.  
  
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
  
 В следующем примере используется **предков** функция возвращает меру Internet Sales Amount для родителя элемента иерархии атрибутов. В этом пример используются числовые выражения для определения уровня, который должен быть возвращен. Поскольку элемент в выражении элемента является элементом иерархии атрибута, его родителем является уровень «Все».  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product].[Mountain-100 Silver, 38],1  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
