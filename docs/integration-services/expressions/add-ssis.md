---
title: + (сложение) (службы SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e7f51d8027bcb65b1f9e3596748778baed36759e
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58270948"
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
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="remarks"></a>Remarks  
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
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
