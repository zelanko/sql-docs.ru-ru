---
title: "! (Логическое не) (Выражение служб SSIS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 003e0fcc98a267342aaf7c77bf344cdfdc71880b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="-logical-not-ssis-expression"></a>! (логическое НЕ) (выражение служб SSIS)
  Инвертирует логический операнд.  
  
> [!NOTE]  
>  ! Оператор «!» не может использоваться вместе с другими операторами. Например, нельзя объединить оператор «!» и оператор > в один оператор «!>» .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *boolean_expression*  
 Является любое допустимое выражение, результатом которого является логическое значение. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 DT_BOOL  
  
## <a name="remarks"></a>Замечания  
 Следующая таблица демонстрирует результаты выполнения «!» операции.  
  
|Исходное логическое выражение|После выполнения оператора «!» оператор|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## <a name="expression-examples"></a>Примеры выражений  
 В результате выполнения данного выражения получается значение FALSE, если столбец **Color** имеет значение "red".  
  
```  
!(Color == "red")  
```  
  
 В результате выполнения данного выражения получается значение TRUE, если значение переменной **MonthNumber** совпадает со значением переменной, представляющей номер текущего месяца. Дополнительные сведения см. в разделе [MONTH (выражение служб SSIS)](../../integration-services/expressions/month-ssis-expression.md) and [GETDATE (выражение служб SSIS)](../../integration-services/expressions/getdate-ssis-expression.md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>См. также:  
 [Приоритет и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

