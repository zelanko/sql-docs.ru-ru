---
title: "&amp;(Побитовое и) (Выражение служб SSIS) | Документы Microsoft"
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
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 06d2958e-66a5-44d8-8bc4-56209ebe1ff2
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6d5dad9457bbafe0218c1e71358d2c9c445f79a8
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="amp-bitwise-and-ssis-expression"></a>&amp;(Побитовое и) (Выражение служб SSIS)
  Выполняет побитовую операцию И для двух целочисленных значений. Она сравнивает каждый бит первого операнда с соответствующим битом второго операнда. Если оба бита равны 1, соответствующий бит результата равен 1. В противном случае соответствующий бит результата равен 0.  
  
 Оба значения должны принадлежать целочисленному типу со знаком или без знака.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
integer_expression1 & integer_expression2  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *integer_expression1, integer_expression2*  
 Любое допустимое выражение: либо целое число со знаком, либо беззнаковое целое число. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Замечания  
 Если значение любого из условий — NULL, то результат выражения тоже будет NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример выполняет битовую операцию И над столбцами **NumberA** и **NumberB**. Столбец**NumberA** содержит значение 3 (0000011), а столбец **NumberB** содержит значение 7 (00000111).  
  
```  
NumberA & NumberB  
```  
  
 Результат вычисления выражения равен 3 (00000011).  
  
 00000011  
  
 00000111  
  
 ----------\-  
  
 00000011  
  
 Этот пример выполняет побитовую операцию И между столбцами **ReorderPoint** и **SafetyStockLevel** .  
  
```  
ReorderPoint & SafetyStockLevel  
```  
  
 Если **ReorderPoint** имеет значение 10, а **SafetyStockLevel** имеет значение 8, результат вычисления выражения равен 8 (00001000).  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00001000  
  
 Этот пример выполняет побитовую операцию И между двумя целыми числами.  
  
```  
3 & 5   
```  
  
 Результат вычисления выражения равен 1(00000001).  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000001  
  
## <a name="see-also"></a>См. также  
 [& & &#40; Логическое и &#41; &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/logical-and-ssis-expression.md)   
 [Приоритет и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
