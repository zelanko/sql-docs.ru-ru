---
title: "+ (Добавить) (СЛУЖБЫ SSIS) | Документы Microsoft"
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
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 04596cf4762f2473da1555f4ce5f9cd210678986
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="-add-ssis"></a>+ (Сложение) (службы SSIS)
  Складывает два числовых выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression1, numeric_expression2*  
 Любое допустимое выражение числовых типов данных.  
  
## <a name="result-types"></a>Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="remarks"></a>Замечания  
 Если один из операндов равен NULL, то результатом является значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере суммируются числовые литералы.  
  
```  
5 + 6.09 + 7.0  
```  
  
 В примере суммируются значения столбцов **VacationHours** и **SickLeaveHours** .  
  
```  
VacationHours + SickLeaveHours  
```  
  
 В примере вычисленное значение прибавляется к столбцу **StandardCost** . Переменная **Profit%** должна быть заключена в квадратные скобки, поскольку имя включает символ %. Дополнительные сведения см. в статье [Идентификаторы (службы SSIS)](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a>См. также:  
 [Приоритет и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

