---
title: "Unorder (многомерные Выражения) | Документы Microsoft"
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
f1_keywords: UNORDER
dev_langs: kbMDX
helpviewer_keywords: Unorder function
ms.assetid: a805df2a-6320-45bc-989f-90e85faf027f
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2593c6f22915cbe5615f8d104b718fd4b3a7d6a5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="unorder-mdx"></a>Unorder (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Удаляет принудительное упорядочивание заданного набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Remarks  
 **Unorder** функция удаляет упорядочение кортежей в наборе с любой другой функцией или инструкцией, такой как [порядок](../mdx/order-mdx.md) функции. Порядок кортежей в наборе, возвращаемом **Unorder** функции не определено.  
  
 **Unorder** функция используется в качестве подсказки для [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] для оптимизации запросов для обработки набора. Если порядок кортежей в наборе не важен для вычислений запроса, с помощью **Unorder** функции может улучшить производительность в таких случаях. Например [NonEmpty (многомерные Выражения)](../mdx/nonempty-mdx.md) может выполняться лучше, если предоставленный набор для этой функции неупорядочен, чем если [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] требуется сохранять порядок, хотя с [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], обработчик запросов пытается выполнить эту функцию автоматически для многих функций, таких как **сумма** и **статистические**. Увеличение производительности с помощью **Unorder** , вероятнее всего только заметно с очень большими наборами, состоящими из миллионов кортежей.  
  
## <a name="example"></a>Пример  
 Следующий псевдокод иллюстрирует синтаксис для этой функции.  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
