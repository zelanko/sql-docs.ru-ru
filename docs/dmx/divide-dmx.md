---
title: (Деление) (DMX) | Документы Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8ab2b355c551b868cec3ee4329460f8bb0532236
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842377"
---
# <a name="divide-dmx"></a>(Деление) (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет арифметическую операцию, которая делит одно число на другое.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>Параметры  
 *делимое*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
 *делитель*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение с типом данных параметра, имеющего более высокий приоритет.  
  
## <a name="remarks"></a>Примечания  
 Значение, возвращаемое оператором, представляет собой частное от деления первого выражения на второе.  
  
 Оба выражения должны иметь одинаковый тип данных, или одно из выражений должно допускать неявное преобразование к типу данных другого выражения. Если делитель возвращает значение NULL, оператор выдает ошибку. Если как делитель, так и делимое возвращают значения NULL, оператор возвращает значение NULL.  
  
## <a name="see-also"></a>См. также  
 [Арифметические операторы &#40;расширений интеллектуального анализа данных&#41;](../dmx/operators-arithmetic.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;расширений интеллектуального анализа данных&#41;](../dmx/operators-dmx.md)   
 [Разделите &#40;выражение служб SSIS&#41;](../integration-services/expressions/divide-ssis-expression.md)   
 [&#40;Разделите&#41; &#40;Transact-SQL&#41;](../t-sql/language-elements/divide-transact-sql.md)  
  
  
