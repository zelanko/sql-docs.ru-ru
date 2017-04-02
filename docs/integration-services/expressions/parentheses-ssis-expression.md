---
title: "() (скобки) (выражение служб SSIS) | Microsoft Docs"
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
  - "() (оператор «скобки»)"
  - "порядок вычисления [службы Integration Services]"
  - "оператор «скобки» ()"
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
caps.latest.revision: 36
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 36
---
# () (скобки) (выражение служб SSIS)
  Определяет порядок вычисления выражений. Выражения, взятые в скобки, имеют самый высокий приоритет вычисления. Вложенные выражения в скобках вычисляются от внутреннего к внешнему.  
  
 Кроме того, скобки применяются для того, чтобы облегчить чтение сложных выражений.  
  
## Синтаксис  
  
```  
  
(expression)  
  
```  
  
## Аргументы  
 *expression*  
 Любое допустимое выражение.  
  
## Типы результата  
 Тип данных *expression*. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Примеры выражений  
 В этом примере показано изменение приоритета операторов с помощью скобок. Значение для первого выражения — 100, для второго — 31.  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## См. также  
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  