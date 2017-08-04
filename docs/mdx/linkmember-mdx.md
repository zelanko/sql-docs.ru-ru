---
title: "LinkMember (многомерные Выражения) | Документы Microsoft"
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
- LINKMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- LinkMember function
ms.assetid: b9106f07-8ea2-4933-aed3-ee9c63acf7ac
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c87723c4d7db370b46b2e41cf2d67064f1978f91
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="linkmember-mdx"></a>LinkMember (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает элемент, эквивалентный заданному элементу в указанной иерархии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LinkMember(Member_Expression, Hierarchy_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
## <a name="remarks"></a>Замечания  
 **LinkMember** функция возвращает элемент из заданной иерархии, соответствующий значениям ключа на каждом уровне указанного элемента в связанной иерархии. Атрибуты каждого уровня должны иметь одинаковое количество элементов ключа и тип данных. В искусственных иерархиях, если имеется более чем одно совпадение значения ключа атрибута, будет возвращена ошибка или неопределенный результат.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется **LinkMember** функцию для возвращения меры по умолчанию в кубе Adventure Works для предков элемента 1 июля 2002 иерархии атрибута Date.Date в иерархии «календарь».  
  
```  
SELECT  Hierarchize  
   (Ascendants   
      (LinkMember   
         ([Date].[Date].[July 1, 2002], [Date].[Calendar]  
         )  
       )  
    ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Hierarchize &#40; Многомерные Выражения &#41;](../mdx/hierarchize-mdx.md)   
 [Предки &#40; Многомерные Выражения &#41;](../mdx/ascendants-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

