---
title: LN (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LN function
- natural logarithm of expression [Integration Services]
ms.assetid: 55d7b657-b5fd-4753-9c81-54ed7575e720
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7aee1568e8afc8ab87304340d34b0352a56be2df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188287"
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
  
## <a name="remarks"></a>Примечания  
 Перед вычислением логарифма аргумент numeric expression приводится к типу DT_R8. Дополнительные сведения см. в статье [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
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
 [ЖУРНАЛ &#40;выражение служб SSIS&#41;](log-ssis-expression.md)   
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  