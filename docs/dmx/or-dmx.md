---
title: ИЛИ (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 76b1f8ac9a5f7ad584f42110f2c3b22e5c1918ff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008140"
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
  
## <a name="remarks"></a>Примечания  
 Оба аргумента считаются логическими значениями (0 — FALSE; любое ненулевое значение — TRUE), прежде чем оператор выполнит логическое сложение. Если хотя бы один аргумент возвращает TRUE, оператор возвращает TRUE. Если *Expression1* возвращает значение TRUE, и *Expression2* оценивается как FALSE, оператор возвращает TRUE.  
  
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
  
  
