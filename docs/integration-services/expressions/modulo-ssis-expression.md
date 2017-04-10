---
title: "(Остаток от деления) (выражение служб SSIS) | Microsoft Docs"
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
  - "% (оператор остатка от деления)"
  - "остаток от операции деления"
  - "оператор остатка от деления (%)"
ms.assetid: e2920821-2f5b-4c76-8db8-8b9eddf4606f
caps.latest.revision: 34
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 34
---
# (Остаток от деления) (выражение служб SSIS)
  Вычисляет целочисленный остаток после деления первого числового выражения на второе.  
  
## Синтаксис  
  
```  
  
dividend % divisor  
  
```  
  
## Аргументы  
 *dividend*  
 Делимое числовое выражение. *dividend* может быть любым допустимым числовым выражением. Дополнительные сведения см. в разделе [Типы данных служб Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 *divisor*  
 Числовое выражение, на которое делится делимое. *divisor* может быть любым допустимым числовым выражением, отличным от нуля.  
  
## Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## Замечания  
 Оба выражения должны соответствовать целочисленному типу данных со знаком или без знака.  
  
 Если один из операндов равен NULL, то результатом является значение NULL.  
  
 Нулевой остаток от деления — недопустимый аргумент.  
  
## Примеры выражений  
 Этот пример вычисляет модули из двух числовых литералов. Результат 3.  
  
```  
42 % 13  
```  
  
 Этот пример вычисляет модуль от столбца **SalesQuota** и числового литерала.  
  
```  
SalesQuota % 12  
```  
  
 Этот пример вычисляет модуль из двух числовых переменных **Sales$** и **Month**. Переменная **Sales$** должна быть заключена в квадратные скобки, так как имя включает символ $. Дополнительные сведения см. в разделе [Идентификаторы (службы SSIS)](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
@[Sales$] % @Month  
```  
  
 Этот пример использует оператор остатка от деления, чтобы определить, является ли значение переменной **Value** четным или нечетным, и использует оператор условия, чтобы вернуть строку, описывающую результат. Дополнительные сведения см. в разделе [? : (условный) (выражение служб SSIS)](../../integration-services/expressions/conditional-ssis-expression.md).  
  
```  
@Value % 2 == 0? "even":"odd"  
```  
  
## См. также  
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  