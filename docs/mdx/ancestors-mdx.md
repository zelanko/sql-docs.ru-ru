---
title: "Ancestors (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ANCESTORS
dev_langs:
- kbMDX
helpviewer_keywords:
- Ancestors function
ms.assetid: abdf2e9c-72c8-4f2e-a823-d42efc4cc7d5
caps.latest.revision: 46
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b2d6304b9a87bcdb87a98a8351d4e60074ebb4d8
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="ancestors-mdx"></a>Ancestors (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Функция, возвращающая набор предков заданного элемента на заданном уровне или заданном расстоянии от элемента. С [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], возвращаемый набор всегда будет содержать один элемент — [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживают нескольких родителей для одного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Level syntax  
Ancestors(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestors(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Расстояние*  
 Допустимое числовое выражение, указывающее расстояние от заданного элемента.  
  
## <a name="remarks"></a>Замечания  
 С **предков** функции, задать функцию с Многомерным выражением элемента, а затем задать Многомерное выражение уровня, являющегося предком элемента, или числовое выражение, представляющее число уровней над данным элементом. С этой информацией **предков** функция возвращает набор элементов (который будет набором, состоящим из одного элемента) этого уровня.  
  
> [!NOTE]  
>  Для возвращения предка элемента вместо набора предков используется [предка](../mdx/ancestor-mdx.md) функции.  
  
 Если выражение уровня указано, **предков** функция возвращает набор предков заданного элемента на заданном уровне. Если заданный элемент не входит в ту же иерархию, что и заданный уровень, функция вернет ошибку.  
  
 Если задано расстояние, **предков** функция возвращает набор всех элементов, которые находятся вверх по иерархии на заданном расстоянии. Элемент может быть определен как элемент иерархии атрибута, пользовательской иерархии или при некоторых обстоятельствах иерархии типа «родители-потомки». Число 1 возвращает набор элементов на родительском уровне, а число 2 возвращает набор элементов на прародительском уровне (если такой существует). Число 0 вернет набор, включающий только сам элемент.  
  
> [!NOTE]  
>  Используйте эту форму для **предков** функции для случаев, когда уровень родительского элемента неизвестен или не может иметь имя.  
  
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
  
 В следующем примере используется **предков** функция возвращает меру Internet Sales Amount для родителя элемента иерархии атрибута. В этом пример используются числовые выражения для определения уровня, который должен быть возвращен. Поскольку элемент в выражении элемента является элементом иерархии атрибута, его родителем является уровень «Все».  
  
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
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

