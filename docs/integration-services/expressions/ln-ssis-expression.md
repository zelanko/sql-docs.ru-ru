---
title: LN (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LN function
- natural logarithm of expression [Integration Services]
ms.assetid: 55d7b657-b5fd-4753-9c81-54ed7575e720
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ac9490abd45c37005fc77ed7733768fa6d7c35a9
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65725254"
---
# <a name="ln-ssis-expression"></a>LN (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Возвращает натуральный логарифм числового выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LN(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Допустимые положительные числовые выражения.  
  
## <a name="result-types"></a>Типы результата  
 DT_R8  
  
## <a name="remarks"></a>Remarks  
 Перед вычислением логарифма аргумент numeric expression приводится к типу DT_R8. Дополнительные сведения см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Если вычисленное значение *numeric_expression* является нулем или отрицательным значением, возвращается результат NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере используется числовой литерал. Функция возвращает значение 3,737766961828337.  
  
```  
LN(42)  
```  
  
 Этот пример использует столбец **Length**. Если значение столбца равно 53.99, функция возвращает значение 3.9887988442302.  
  
```  
LN(Length)   
```  
  
 Этот пример использует переменную **Length**. Переменная должна иметь числовой тип данных, или выражение должно содержать явное приведение к числовому типу данных. При параметре **Length** равном 234,567 функция возвращает 5,45774126708797.  
  
```  
LN(@Length)   
```  
  
## <a name="see-also"></a>См. также:  
 [LOG (выражение служб SSIS)](../../integration-services/expressions/log-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
