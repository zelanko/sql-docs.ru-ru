---
title: VisualTotals (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- VisualTotals
dev_langs:
- kbMDX
helpviewer_keywords:
- VisualTotals function
ms.assetid: 8ec529c2-729a-4a5b-892e-750849ab4013
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3270bf4f47b4ceafe6d5e1479e870d0492c7c37b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="visualtotals-mdx"></a>VisualTotals (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает множество, созданное динамически объединенными дочерними участниками в указанном множестве, по выбору используя образец имени родительского элемента для результирующего набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
VisualTotals(Set_Expression[,Pattern])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Шаблон*  
 Допустимое строковое выражение для родительского элемента набора, включающее в себя звездочку (*) как подстановочный символ для имени родительского объекта.  
  
## <a name="remarks"></a>Remarks  
 Заданное выражение набора может определять набор, включающий в себя элементы любого уровня внутри одного измерения, в основном элементы со связями «предок-потомок». **VisualTotals** функция подсчитывает значения дочерних элементов указанного набора и пропускает дочерние элементы, не входящие в набор, при вычислении суммарного результата. Итоги наглядно представляются для наборов, упорядоченных иерархически. Если порядок элементов в наборах не соответствует иерархии, результаты не подсчитываются визуально. Например, выражение VisualTotals (USA, WA, CA, Seattle) не возвращает для WA значение Seattle, но возвращает значения для WA, CA и Seattle, затем данные значения суммируются в наглядную сумму USA, при этом продажи в Сиэтле (Seattle) учитываются дважды, так как он находится в штате Вашингтон (WA).  
  
> [!NOTE]  
>  Применение **VisualTotals** функция для элементов измерения, которые не связаны с мерой или находятся ниже уровня гранулярности группы мер вызовет значения будут заменены значением null.  
  
 *Шаблон*, который является необязательным, формат для метки итогов. *Шаблон* требует звездочки (*) как подстановочного символа для родительского элемента и оставшаяся часть текста в строке отображается в результате сцепленной с именем родительского. Чтобы воспроизвести символ звездочки, введите две звездочки (\*\*).  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются визуальные итоги третьего квартала 2001 календарного года, основываясь на единственном заданном потомке, месяце июле.  
  
```  
SELECT VisualTotals  
   ({[Date].[Calendar].[Calendar Quarter].&[2001]&[3]  
      ,[Date].[Calendar].[Month].&[2001]&[7]}) ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере возвращается элемент «Все» в иерархии атрибута Category в измерении Product вместе с двумя из четырех дочерних элементов. Итог, возвращаемый элементом «Все» для меры Internet Sales Amount, — сумма только для элементов Accessories и Clothing. Также аргумент шаблона используется для задания метки столбца All Products.  
  
```  
SELECT  
   VisualTotals  
   ({[Product].[Category].[All Products]  
      ,[Product].[Category].[Accessories]  
      ,[Product].[Category].[Clothing]}  
      , '* - Visual Total'  
   ) ON Columns  
, [Measures].[Internet Sales Amount] ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
