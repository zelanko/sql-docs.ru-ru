---
title: LOG (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- base-10 logarithms
- LOG function
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 77e50116aee1dfc144e5175de7cc56077d205e86
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65725239"
---
# <a name="log-ssis-expression"></a>LOG (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Возвращает десятичный логарифм числового выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LOG(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Допустимое ненулевое и неотрицательное числовое выражение.  
  
## <a name="result-types"></a>Типы результата  
 DT_R8  
  
## <a name="remarks"></a>Remarks  
 Перед вычислением логарифма аргумент *numeric_expression* приводится к типу DT_R8. Дополнительные сведения см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Если вычисленное значение *numeric_expression* является нулем или отрицательным значением, возвращается результат NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере используется числовой литерал. Функция возвращает значение 1,988291341907488.  
  
```  
LOG(97.34)  
```  
  
 Этот пример использует столбец **Length**. Если значением столбца является 101,24, функция возвращает 2,005352136486217.  
  
```  
LOG(Length)   
```  
  
 Этот пример использует переменную **Length**. Тип данных переменной должен быть numeric либо выражение должно включать явное приведение к типу данных [!INCLUDE[ssIS](../../includes/ssis-md.md)] numeric. При параметре **Length** равном 234,567 функция возвращает 2,370266913465859.  
  
```  
LOG(@Length)   
```  
  
## <a name="see-also"></a>См. также:  
 [EXP (выражение служб SSIS)](../../integration-services/expressions/exp-ssis-expression.md)   
 [LN (выражение служб SSIS)](../../integration-services/expressions/ln-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
