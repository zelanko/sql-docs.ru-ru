---
title: KPIValue (многомерные Выражения) | Документы Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- KPIValue function
ms.assetid: c4f8532c-4c24-4ad5-8847-4522511e0039
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b7d1abcf4d0e5c1ca7c02267a1eac7434b616f53
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="kpivalue-mdx"></a>KPIValue (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает элемент, вычисляющий значение указанного ключевого показателя эффективности (KPI).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
KPIValue(KPI_Name)  
```  
  
## <a name="arguments"></a>Аргументы  
 *KPI_Name*  
 Допустимое строковое выражение, указывающее имя ключевого показателя эффективности.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="example"></a>Пример  
 В следующем примере возвращаются значение, цель, состояние и тренд ключевого показателя эффективности для меры доходов от продаж через партнерскую сеть для потомков трех элементов иерархии атрибута Fiscal Year.  
  
```  
SELECT  
   { KPIValue("Channel Revenue"),   
     KPIGoal("Channel Revenue"),  
     KPIStatus("Channel Revenue"),   
     KPITrend("Channel Revenue")  
   } ON Columns,  
Descendants  
   ( { [Date].[Fiscal].[Fiscal Year].&[2002],  
       [Date].[Fiscal].[Fiscal Year].&[2003],  
       [Date].[Fiscal].[Fiscal Year].&[2004]   
     }, [Date].[Fiscal].[Fiscal Quarter]  
   ) ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
