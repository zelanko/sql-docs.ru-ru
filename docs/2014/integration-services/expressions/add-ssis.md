---
title: + (сложение) (службы SSIS) | Документы Майкрософт
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
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b96a6e5c659925ea5eed876e1f7505997ea02b71
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189116"
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
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в статье [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="remarks"></a>Примечания  
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
  
 В примере вычисленное значение прибавляется к столбцу **StandardCost** . Переменная **Profit%** должна быть заключена в квадратные скобки, поскольку имя включает символ %. Дополнительные сведения см. в статье [Идентификаторы (службы SSIS)](identifiers-ssis.md).  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a>См. также  
 [Приоритет и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы &#40;выражение служб SSIS&#41;](operators-ssis-expression.md)  
  
  