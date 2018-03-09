---
title: "DefaultMember (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DefaultMember
dev_langs: kbMDX
helpviewer_keywords: DefaultMember function
ms.assetid: c1b53b3a-6e73-4c41-a4fe-9f5c96da5463
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 756f099281a884c168a304cf4d27dfbf8f1f03e0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="defaultmember-mdx"></a>DefaultMember (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает элемент иерархии по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchy_Expression.DefaultMember  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
## <a name="remarks"></a>Remarks  
 Элемент по умолчанию атрибута используется для оценки выражений, когда атрибут не включен в запрос.  
  
## <a name="example"></a>Пример  
 В следующем примере используется **DefaultMember** функции вместе с **имя** функцию для возвращения элемента по умолчанию для измерения Destination Currency в кубе Adventure Works. В примере возвращается **доллара США**. **Имя** функция используется для возвращения имени меры, а не свойство по умолчанию для меры, которое является **значение**.  
  
```  
WITH MEMBER Measures.x AS   
   [Destination Currency].[Destination Currency].DefaultMember.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Определяет элемент по умолчанию](../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
