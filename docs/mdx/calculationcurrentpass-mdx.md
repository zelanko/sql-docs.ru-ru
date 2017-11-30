---
title: "CalculationCurrentPass (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: CALCULATIONCURRENTPASS
dev_langs: kbMDX
helpviewer_keywords: CalculationCurrentPass function
ms.assetid: 7069f7a0-8ec8-4293-8db3-b35b9327f437
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f2ad2b55c956ed0a161adf1ac54ce8fec48a8be6
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="calculationcurrentpass-mdx"></a>CalculationCurrentPass (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает текущий этап вычисления куба для указанного контекста запроса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CalculationCurrentPass()  
```  
  
## <a name="remarks"></a>Замечания  
 **CalculationCurrentPass** функция возвращает отсчитываемый от нуля индекс этапа вычисления для контекста текущего запроса. Автоматическое разрешение рекурсии в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], эта функция имеет практически не используется.  
  
## <a name="see-also"></a>См. также:  
 [CalculationPassValue &#40; Многомерные Выражения &#41;](../mdx/calculationpassvalue-mdx.md)   
 [IIf &#40; Многомерные Выражения &#41;](../mdx/iif-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
