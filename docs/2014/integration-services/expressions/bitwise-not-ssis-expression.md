---
title: ~ (битовое НЕ) (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fd0226e3f96e2a2d77b80fc36e5ee41b949094da
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85429111"
---
# <a name="-bitwise-not-ssis-expression"></a>~ (битовое НЕ) (выражение служб SSIS)
  Выполняет битовую инверсию целого числа. Этот оператор может быть применен к целочисленному типу данных со знаком или без знака.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *integer_expression*  
 Любое допустимое выражение целочисленного типа данных. *integer*_*expression* — целое число, которое преобразуется в двоичное число для побитовой операции. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Возвращает тип данных *integer_expression*.  
  
## <a name="remarks"></a>Remarks  
 None  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример выполняет операцию битового ~ (NOT) над числом 170 (0000 0000 1010 1010). Число целого типа со знаком.  
  
```  
  
~ 170  
```  
  
 Результат вычисления выражения — 170 (1111111101010101).  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## <a name="see-also"></a>См. также:  
 [Очередность и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](operators-ssis-expression.md)  
  
  
