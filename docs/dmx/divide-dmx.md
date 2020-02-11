---
title: Деление (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 17f1233310ce8b070e12fbf25dca0e256ff34664
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070738"
---
# <a name="divide-dmx"></a>(деление) (расширение интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет арифметическую операцию, которая делит одно число на другое.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>Параметры  
 *Делимое*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
 *Делитель*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение с типом данных параметра, имеющего более высокий приоритет.  
  
## <a name="remarks"></a>Remarks  
 Значение, возвращаемое оператором, представляет собой частное от деления первого выражения на второе.  
  
 Оба выражения должны иметь одинаковый тип данных, или одно из выражений должно допускать неявное преобразование к типу данных другого выражения. Если делитель возвращает значение NULL, оператор выдает ошибку. Если как делитель, так и делимое возвращают значения NULL, оператор возвращает значение NULL.  
  
## <a name="see-also"></a>См. также:  
 [Арифметические операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-arithmetic.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-dmx.md)   
 [Разделение &#40;выражений служб SSIS&#41;](../integration-services/expressions/divide-ssis-expression.md)   
 [&#40;деление&#41; &#40;Transact-SQL&#41;](../t-sql/language-elements/divide-transact-sql.md)  
  
  
