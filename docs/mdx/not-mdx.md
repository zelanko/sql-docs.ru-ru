---
title: "НЕ (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft"
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
f1_keywords: NOT
dev_langs: kbMDX
helpviewer_keywords: NOT operator [MDX]
ms.assetid: c11bd3b0-54b3-4a6d-babc-6067722194db
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 08bfb5c70fe36e36b62482f51864adf20cc851e4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="not-mdx"></a>NOT (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет операцию логического отрицания над числовым выражением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, которое возвращает **false** Если аргумент принимает значение **true**; в противном случае **true**.  
  
## <a name="remarks"></a>Remarks  
 **Не** оператор рассматривает выражение как логическое значение (ноль, 0 — как **false**; в противном случае **true**), прежде чем оператор выполнит логическое отрицание. В следующей таблице показано, как **не** оператор выполнит логическое отрицание.  
  
|*Expression1*|Возвращаемое значение|  
|-------------------|------------------|  
|**true**|**false**|  
|**false**|**true**|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
