---
title: "() (Скобки) (выражение служб SSIS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6e1bcdc618477d4b4c3cee1dc07b01053335f745
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="-parentheses-ssis-expression"></a>() (скобки) (выражение служб SSIS)
  Определяет порядок вычисления выражений. Выражения, взятые в скобки, имеют самый высокий приоритет вычисления. Вложенные выражения в скобках вычисляются от внутреннего к внешнему.  
  
 Кроме того, скобки применяются для того, чтобы облегчить чтение сложных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
(expression)  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое выражение.  
  
## <a name="result-types"></a>Типы результата  
 Тип данных *expression*. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере показано изменение приоритета операторов с помощью скобок. Значение для первого выражения — 100, для второго — 31.  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a>См. также  
 [Приоритет и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

