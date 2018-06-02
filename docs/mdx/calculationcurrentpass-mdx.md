---
title: CalculationCurrentPass (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ec237237358203dc63639592894d1c3f9a48227
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578446"
---
# <a name="calculationcurrentpass-mdx"></a>CalculationCurrentPass (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает текущий этап вычисления куба для указанного контекста запроса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CalculationCurrentPass()  
```  
  
## <a name="remarks"></a>Примечания  
 **CalculationCurrentPass** функция возвращает отсчитываемый от нуля индекс этапа вычисления для контекста текущего запроса. Автоматическое разрешение рекурсии в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], эта функция имеет практически не используется.  
  
## <a name="see-also"></a>См. также  
 [CalculationPassValue &#40;многомерных Выражений&#41;](../mdx/calculationpassvalue-mdx.md)   
 [IIf &#40;многомерных Выражений&#41;](../mdx/iif-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
