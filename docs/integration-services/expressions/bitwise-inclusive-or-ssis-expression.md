---
title: "| (битовое включающее ИЛИ) (выражение служб SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "| (битовое включающее ИЛИ)"
  - "битовое включающее ИЛИ (|)"
ms.assetid: 4dce9eb2-3680-4adc-81a3-816ea52cef49
caps.latest.revision: 39
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 39
---
# | (битовое включающее ИЛИ) (выражение служб SSIS)
  Выполняет побитовую операцию ИЛИ для двух целочисленных значений. Она сравнивает каждый бит первого операнда с соответствующим битом второго операнда. Если какой-либо из битов равен 1, соответствующий бит результата равен 1. В противном случае соответствующий бит результата равен нулю (0).  
  
 Оба условия должны относиться либо к целым числам со знаком, либо к беззнаковым целым числам.  
  
## Синтаксис  
  
```  
  
integer_expression1 | integer_expression2  
  
```  
  
## Аргументы  
 *integer_expression1, integer_expression2*  
 Любое допустимое выражение: либо целое число со знаком, либо беззнаковое целое число. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## Замечания  
 Если значение любого из условий — NULL, то результат выражения тоже будет NULL.  
  
## Примеры выражений  
 В данном примере выполняется операция битового ИЛИ над переменными **NumberA** и **NumberB**. **NumberA** содержит 3 (00000011) а **NumberB** содержит 9 (00001001).  
  
```  
@NumberA | @NumberB  
```  
  
 Результат устанавливается в 11 (00001011).  
  
 00000011  
  
 00001001  
  
 ----------\-  
  
 00001011  
  
 В данном примере выполняется операция побитового ИЛИ над столбцами **ReorderPoint** и **SafetyStockLevel** .  
  
```  
ReorderPoint | SafetyStockLevel  
```  
  
 Если **ReorderPoint** имеет значение 10, а **SafetyStockLevel** — 8, результат вычисления выражения равен 10 (00001010).  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00001010  
  
 В данном примере выполняется операция побитового ИЛИ над двумя целочисленными значениями.  
  
```  
3 | 5   
```  
  
 Значение устанавливается равным 7 (00000111).  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000111  
  
## См. также  
 [&#124;&#124; (логическое ИЛИ) (выражение служб SSIS)](../../integration-services/expressions/logical-or-ssis-expression.md)   
 [^ (битовое исключающее ИЛИ) (выражение служб SSIS)](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)   
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  