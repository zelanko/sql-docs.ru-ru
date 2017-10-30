---
title: "Ancestor (многомерные Выражения) | Документы Microsoft"
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
- ANCESTOR
dev_langs:
- kbMDX
helpviewer_keywords:
- Ancestor function
ms.assetid: b5bf2ce4-20df-4ebc-97eb-e44a6f64cc50
caps.latest.revision: 46
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a9aad080913e792291f8d72281afe522704042e5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="ancestor-mdx"></a>Ancestor (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Функция, возвращающая предок заданного элемента на заданном уровне или заданном расстоянии от элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Level syntax  
Ancestor(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestor(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Расстояние*  
 Допустимое числовое выражение, указывающее расстояние от заданного элемента.  
  
## <a name="remarks"></a>Замечания  
 С **предка** функции, задать функцию с Многомерным выражением элемента, а затем задать Многомерное выражение уровня, являющегося предком элемента, или числовое выражение, представляющее число уровней над данным элементом. С этой информацией **предков** функция возвращает предка элемента на этом уровне.  
  
> [!NOTE]  
>  Чтобы вернуть набор, содержащий элемент-предок, а не просто элемент-предок, используйте [предков &#40; Многомерные Выражения &#41; ](../mdx/ancestors-mdx.md) функции.  
  
 Если выражение уровня указано, **предка** функция возвращает предок заданного элемента на заданном уровне. Если заданный элемент не входит в ту же иерархию, что и заданный уровень, функция вернет ошибку.  
  
 Если задано расстояние, **предка** функция возвращает предок указанного элемента, который имеет несколько этапов, указываемой по иерархии на заданном расстоянии. Элемент может быть определен как элемент иерархии атрибута, пользовательской иерархии или при некоторых обстоятельствах иерархии типа «родители-потомки». Число 1 возвращает родительский объект элемента, а число 2 возвращает прародительский объект элемента (если такой существует). Число 0 вернет сам элемент.  
  
> [!NOTE]  
>  Используйте эту форму для **предка** функции для случаев, когда уровень родительского элемента неизвестен или не может иметь имя.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется выражение уровня и возвращается Internet Sales Amount для каждой административно-территориальной единицы (State-Province) Австралии (Australia), возвращается также процентное соотношение относительно общего значения Internet Sales Amount в Австралии (Australia).  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
   [Measures].[Internet Sales Amount],    
      Ancestor   
         (  
         [Customer].[Customer Geography].CurrentMember,  
            [Customer].[Customer Geography].[Country]  
         )  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
        [Customer].[Customer Geography].[Country].&[Australia],  
           [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
 В следующем примере используется числовое выражение уровня и возвращается Internet Sales Amount для каждой административно-территориальной единицы (State-Province) Австралии (Australia), возвращается также процентное соотношение относительно общего значения Internet Sales Amount во всех странах.  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
      [Measures].[Internet Sales Amount],  
         Ancestor   
            ([Customer].[Customer Geography].CurrentMember, 2)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
         [Customer].[Customer Geography].[Country].&[Australia],  
            [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

