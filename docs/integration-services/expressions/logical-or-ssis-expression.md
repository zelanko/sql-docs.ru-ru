---
title: "|| (Логическое или) (Выражение служб SSIS) | Документы Microsoft"
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
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c369d66dbfdfefa0249ef0e479266bf17cf8f7d6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="-logical-or-ssis-expression"></a>|| (логическое ИЛИ) (выражение служб SSIS)
  Выполняет логическую операцию ИЛИ. Выражение принимает значение TRUE, если одно или оба условия имеют значение TRUE.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a>Аргументы  
 *boolean_expression1, boolean_expression2*  
 Любое допустимое выражение, результатом которого являются TRUE, FALSE или NULL  
  
## <a name="result-types"></a>Типы результата  
 DT_BOOL  
  
## <a name="remarks"></a>Замечания  
 Следующая таблица демонстрирует результаты выполнения оператора ||:  
  
|Результат|Выражение|Выражение|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|TRUE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|TRUE|NULL|TRUE|  
|NULL|NULL|FALSE|  
  
## <a name="ssis-expression-examples"></a>Примеры выражений служб SSIS  
 В этом примере используются столбцы **StandardCost** и **ListPrice** . Пример возвращает значение TRUE, если значение столбца **StandardCost** меньше 300 или значение столбца **ListPrice** больше 500.  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 Этот пример использует переменные **SPrice** и **LPrice** вместо числовых литералов.  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>См. также  
 [&#124; &#40; Побитовое включающее или &#41; &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/bitwise-inclusive-or-ssis-expression.md)   
 [^ &#40; Побитовое исключающее или &#41; &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)   
 [Приоритет и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

