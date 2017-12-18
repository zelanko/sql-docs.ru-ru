---
title: "LN (выражение служб SSIS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LN function
- natural logarithm of expression [Integration Services]
ms.assetid: 55d7b657-b5fd-4753-9c81-54ed7575e720
caps.latest.revision: "34"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b89bf2f76561f997dd8def5522c342095714c74
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="ln-ssis-expression"></a>LN (выражение служб SSIS)
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
  
## <a name="remarks"></a>Замечания  
 Перед вычислением логарифма аргумент numeric expression приводится к типу DT_R8. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [LOG (выражение служб SSIS)](../../integration-services/expressions/log-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
