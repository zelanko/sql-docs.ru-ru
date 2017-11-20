---
title: "&amp;&amp;(Логическое и) (Выражение служб SSIS) | Документы Microsoft"
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
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a52d1a0bf10aba48b1e628a9253c7f2361f58506
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="ampamp-logical-and-ssis-expression"></a>&amp;&amp;(Логическое и) (Выражение служб SSIS)
  Выполняет логическую операцию И. Выражение принимает значение TRUE, если все условия имеют значение TRUE.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a>Аргументы  
 *boolean_expression1, boolean_expression2*  
 Любое допустимое выражение, результатом которого являются TRUE, FALSE или NULL  
  
## <a name="result-types"></a>Типы результата  
 DT_BOOL  
  
## <a name="remarks"></a>Замечания  
 Следующая таблица демонстрирует результаты выполнения оператора &&.  
  
|Результат|Выражение|Выражение|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|NULL|NULL|TRUE|  
|FALSE|NULL|FALSE|  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере используются столбцы **StandardCost** и **ListPrice** . Пример возвращает значение TRUE, если значение столбца **StandardCost** меньше 300 или значение столбца **ListPrice** больше 500.  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 Этот пример использует переменные **SPrice** и **LPrice** вместо числовых литералов.  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>См. также  
 [& &#40; Побитовое и &#41; &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/bitwise-and-ssis-expression.md)   
 [Приоритет и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

