---
title: Ancestor (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 385206d4a94362831e0949bafe5a11c1ce48d7bd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68017129"
---
# <a name="ancestor-mdx"></a>Ancestor (многомерные выражения)


  Функция, возвращающая предок заданного элемента на заданном уровне или заданном расстоянии от элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Level syntax  
Ancestor(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestor(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Distance*  
 Допустимое числовое выражение, указывающее расстояние от заданного элемента.  
  
## <a name="remarks"></a>Remarks  
 С помощью функции- **предка** вы предоставляете функцию с многомерным выражением элемента, а затем ПРЕДОСТАВЛЯЕТе многомерное выражение уровня, который является предком элемента, или числовое выражение, представляющее количество уровней выше этого элемента. С этой информацией функция **предков** Возвращает элемент предка на этом уровне.  
  
> [!NOTE]  
>  Чтобы получить набор, содержащий элемент-предок, а не только элемент-предок, используйте функцию- [предки &#40;многомерные функции&#41;](../mdx/ancestors-mdx.md) .  
  
 Если выражение уровня задано, функция- **предок** Возвращает предка указанного элемента на указанном уровне. Если заданный элемент не входит в ту же иерархию, что и заданный уровень, функция вернет ошибку.  
  
 Если задано расстояние, функция- **предок** Возвращает предка указанного элемента, который является числом шагов, указанных в иерархии, заданной выражением элемента. Элемент может быть определен как элемент иерархии атрибута, пользовательской иерархии или при некоторых обстоятельствах иерархии типа «родители-потомки». Число 1 возвращает родительский объект элемента, а число 2 возвращает прародительский объект элемента (если такой существует). Число 0 вернет сам элемент.  
  
> [!NOTE]  
>  Используйте эту форму функции- **предка** для случаев, когда уровень родителя неизвестен или не может быть именован.  
  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
