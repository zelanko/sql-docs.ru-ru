---
title: ИЛИ (DMX) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- OR
dev_langs:
- DMX
helpviewer_keywords:
- OR operator
ms.assetid: 727a38a9-7f75-4963-8e8a-aa703c129d30
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f58bb4e4324d8932f14f5c1e87c021f373abc006
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="or-dmx"></a>OR (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Логический оператор, выполняющий логическое сложение (дизъюнкцию) двух числовых выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Expression1 OR Expression2  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
 *Expression2*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, возвращающее TRUE, если хотя бы один из аргументов возвращает TRUE, и FALSE в противном случае.  
  
## <a name="remarks"></a>Замечания  
 Оба аргумента считаются логическими значениями (0 — FALSE; любое ненулевое значение — TRUE), прежде чем оператор выполнит логическое сложение. Если хотя бы один аргумент возвращает TRUE, оператор возвращает TRUE. Если *Expression1* имеет значение TRUE и *Expression2* имеет значение FALSE, оператор возвращает TRUE.  
  
 В следующей таблице иллюстрируется выполнение логического сложения (дизъюнкции).  
  
|Если Expression1 равно|Если Expression2 равно|Возвращается значение|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|TRUE|  
|FALSE|TRUE|TRUE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Логические операторы &#40;расширений интеллектуального анализа данных&#41;](../dmx/operators-logical.md)   
 [Операторы &#40;расширений интеллектуального анализа данных&#41;](../dmx/operators-dmx.md)  
  
  
