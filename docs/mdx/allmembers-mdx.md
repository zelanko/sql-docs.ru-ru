---
title: AllMembers (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALLMEMBERS
dev_langs:
- kbMDX
helpviewer_keywords:
- AllMembers function
ms.assetid: 202e81d4-d2ee-4ec1-a019-4835eb19f446
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 8bd432037435ed2659587e0aeefdb939f0911989
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="allmembers-mdx"></a>AllMembers (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Вычисляет выражение иерархии или уровня и возвращает набор, содержащий все элементы заданной иерархии или уровня, включая все вычисляемые элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.AllMembers  
  
Level syntax  
Level_Expression.AllMembers  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
## <a name="remarks"></a>Замечания  
 **AllMembers** функция возвращает набор, содержащий все элементы, включая вычисляемые, заданной иерархии или уровня. **AllMembers** функция возвращает вычисляемые элементы, даже если заданной иерархии или уровне нет видимых элементов.  
  
> [!IMPORTANT]  
>  Если измерение содержит единственную видимую иерархию, на нее можно сослаться по имени измерения или по имени иерархии, поскольку имя измерения в этом случае разрешается в единственную видимую иерархию. Например, многомерное выражение `Measures.AllMembers` является допустимым, поскольку измерение Measures разрешается в единственную видимую иерархию.  
  
> [!NOTE]  
>  **AllMembers** функция семантически схожа с [AddCalculatedMembers (многомерные Выражения)](../mdx/addcalculatedmembers-mdx.md) функции.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает все элементы в [`Date].[Calendar Year]` иерархии атрибута по оси столбцов, это включает в себя вычисляемые элементы и набор всех потомков `[Product].[Model Name]` иерархии на оси строк из атрибута **Adventure Works** куба.  
  
```  
SELECT  
   [Date].[Calendar Year].AllMembers ON COLUMNS,  
   [Product].[Model Name].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
 Следующий пример возвращает все элементы в **меры** измерение по оси столбцов, это включает в себя все вычисляемые элементы и набор всех потомков `[Product].[Model Name]` иерархии на оси строк из атрибута **Adventure Works** куба.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [AddCalculatedMembers & #40; Многомерные Выражения & #41;](../mdx/addcalculatedmembers-mdx.md)   
 [Дочерние элементы &#40;многомерных Выражений&#41;](../mdx/children-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
