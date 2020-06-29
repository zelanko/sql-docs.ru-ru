---
title: '&amp; (битовое И) (выражение служб SSIS) | Документы Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 06d2958e-66a5-44d8-8bc4-56209ebe1ff2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 409b5413c93cce0f58ecf1d6004d943b3a8d298f
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85429161"
---
# <a name="amp-bitwise-and-ssis-expression"></a>&amp; (битовое И) (выражение служб SSIS)
  Выполняет побитовую операцию И для двух целочисленных значений. Она сравнивает каждый бит первого операнда с соответствующим битом второго операнда. Если оба бита равны 1, соответствующий бит результата равен 1. В противном случае соответствующий бит результата равен 0.  
  
 Оба значения должны принадлежать целочисленному типу со знаком или без знака.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
integer_expression1 & integer_expression2  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *integer_expression1, integer_expression2*  
 Любое допустимое выражение: либо целое число со знаком, либо беззнаковое целое число. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Remarks  
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
  
## <a name="see-also"></a>См. также:  
 [&#124;&#124; (логическое И) (выражение служб SSIS)](logical-and-ssis-expression.md)   
 [Очередность и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](operators-ssis-expression.md)  
  
  
