---
title: "EXP (выражение служб SSIS) | Microsoft Docs"
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
  - "экспоненциальные функции"
  - "EXP, функция"
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
caps.latest.revision: 34
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 34
---
# EXP (выражение служб SSIS)
  Возвращает значение экспоненты основания е числового выражения. Функция EXP дополняет действие функции LN и иногда называется обратным логарифмом.  
  
## Синтаксис  
  
```  
  
EXP(numeric_expression)  
```  
  
## Аргументы  
 *numeric_expression*  
 Допустимое числовое выражение.  
  
## Типы результата  
 DT_R8  
  
## Замечания  
 Перед вычислением степени числовое выражение приводится к типу данных DT_R8. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Возвращаемый результат всегда является положительным числом.  
  
## Примеры выражений  
 В этих примерах функция EXP применяется к положительным значениям, отрицательным значениям и к нулю.  
  
```  
EXP(74)  
```  
  
 Возвращает 1.373382979540176E+32.  
  
```  
EXP(-27)  
```  
  
 Возвращает 1.879528816539083E-12.  
  
```  
EXP(0)  
```  
  
 Возвращает значение 1.  
  
## См. также  
 [LOG (выражение служб SSIS)](../../integration-services/expressions/log-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  