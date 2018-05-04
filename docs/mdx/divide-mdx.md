---
title: Деление (многомерные Выражения) | Документы Microsoft
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
ms.assetid: 9fe4a47b-d5e8-4dc7-ad4a-3e47ab463f03
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 4bff8fd59df9aa01e88fcd5d8a71f209f48332eb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="divide-mdx"></a>Деление (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет деление и возвращает альтернативный результат или выражение BLANK() при делении на 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>Аргументы  
 *числитель*  
 Делимое число.  
  
 *знаменатель*  
 Делитель.  
  
 *alternateresult*  
 (Необязательно) Значение, возвращаемое когда деление на ноль приводит к ошибке. Если не указано, значение по умолчанию является выражением BLANK().  
  
## <a name="remarks"></a>Замечания  
 Альтернативный результат при делении на 0 должен быть константой.  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
