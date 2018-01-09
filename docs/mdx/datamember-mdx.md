---
title: "DataMember (многомерные Выражения) | Документы Microsoft"
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
f1_keywords: DATAMEMBER
dev_langs: kbMDX
helpviewer_keywords: DataMember function
ms.assetid: 65bf21e8-1cb2-4ae8-bfbe-bb4d72589557
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8ebc7c203eeb0ca365f7c61dbc827082c6bf9234
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="datamember-mdx"></a>DataMember (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает элемент данных, сформированный системой и связанный с неконечным элементом измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.DataMember  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Remarks  
 Эта функция работает с неконечными элементами любой иерархии и могут использоваться [UPDATE CUBE Statement (MDX)](../mdx/mdx-data-manipulation-update-cube.md) для обратной записи данных непосредственно в неконечные элементы, а не в потомки конечных элементов.  
  
> [!NOTE]  
>  Возвращает указанный элемент, если он является конечным или если с неконечным элементом не связан элемент данных.  
  
## <a name="example"></a>Пример  
 В следующем примере используется **DataMember** функции в вычисляемой мере для отображения квоты продаж для каждого отдельного работника:  
  
```  
WITH MEMBER measures.InvidualQuota AS   
([Employee].[Employees].currentmember.datamember, [Measures].[Sales Amount Quota])  
,FORMAT_STRING='Currency'  
SELECT {[Measures].[Sales Amount Quota],[Measures].InvidualQuota} ON COLUMNS,  
[Employee].[Employees].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Ключевые понятия многомерных Выражений &#40; Службы Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
  
