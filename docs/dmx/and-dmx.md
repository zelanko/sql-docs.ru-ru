---
title: "И (DMX) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: AND
dev_langs: DMX
helpviewer_keywords: AND, DMX
ms.assetid: d337b20c-f80e-48be-9354-371367e53735
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 4acd3c33863e8e8c198480e4cc90e4661f7acf94
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="and-dmx"></a>AND (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет логическое умножение двух числовых выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
 *Expression2*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение принимает значение TRUE, если оба аргумента имеют значение TRUE, в противном случае возвращает значение FALSE.  
  
## <a name="remarks"></a>Remarks  
 Оба аргумента приводятся к значениям логического типа (0 — FALSE; любое ненулевое значение — TRUE), прежде чем оператор выполнит логическое умножение. В приведенной ниже таблице показаны результаты, соответствующие различным сочетаниям значений аргументов:  
  
|Если Expression1 равно|Если Expression2 равно|Возвращается значение|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|FALSE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Логические операторы &#40; расширений интеллектуального анализа данных &#41;](../dmx/operators-logical.md)   
 [Операторы &#40; расширений интеллектуального анализа данных &#41;](../dmx/operators-dmx.md)  
  
  
