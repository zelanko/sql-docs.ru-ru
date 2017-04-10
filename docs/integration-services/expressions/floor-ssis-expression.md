---
title: "FLOOR (выражение службы SSIS) | Microsoft Docs"
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
  - "наибольшее целое число, меньшее или равное выражению"
  - "FLOOR, функция [службы SSIS]"
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# FLOOR (выражение службы SSIS)
  Возвращает наибольшее целое число, меньшее или равное числовому выражению.  
  
## Синтаксис  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## Аргументы  
 *numeric_expression*  
 Допустимое числовое выражение.  
  
## Типы результата  
 Числовой тип данных выражения аргумента. Результат представляет собой целую часть вычисляемого значения и имеет тот же тип данных, что и *numeric_expression.*  
  
## Замечания  
 Функция FLOOR возвращает NULL, если аргумент имеет значение NULL.  
  
## Примеры выражений  
 В этих примерах функция FLOOR применяется к положительному, отрицательному и нулевому значениям.  
  
```  
FLOOR(123.45)  
```  
  
 Возвращает значение 123,00  
  
```  
FLOOR(-123.45)  
```  
  
 Возвращает значение −124,00  
  
```  
FLOOR(0.00)  
```  
  
 Возвращает значение 0,00  
  
## См. также  
 [CEILING (выражение служб SSIS)](../../integration-services/expressions/ceiling-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  