---
title: "* (Умножение) (Выражение служб SSIS) | Документы Microsoft"
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
- '* (multiply operator)'
- multiply operator (*)
ms.assetid: d457f052-ffbb-4485-833f-f4bed4349b69
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bb439e9221a1bcb169776eec1f6251b49ed4b861
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="-multiply-ssis-expression"></a>* (умножение) (выражение служб SSIS)
  Умножает два числовых выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
numeric_expression1 * numeric_expression2  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression1, numeric_expression2*  
 Любое допустимое выражение числовых типов данных. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Замечания  
 Если один из операндов равен NULL, то результатом является значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример умножает числовые литералы.  
  
```  
5 * 6.09  
```  
  
 Этот пример увеличивает значения столбца **ListPrice** на 10 процентов.  
  
```  
ListPrice * .10  
```  
  
 Этот пример вычитает результат выражения из столбца **ListPrice** . Переменная **Discount%** должна быть заключена в квадратные скобки, поскольку имя включает символ %. Дополнительные сведения см. в статье [Идентификаторы (службы SSIS)](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a>См. также:  
 [Приоритет и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

