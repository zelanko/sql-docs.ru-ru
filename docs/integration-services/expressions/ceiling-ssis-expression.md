---
title: "CEILING (выражение служб SSIS) | Microsoft Docs"
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
  - "наименьшее целое число, которое больше или равно выражению"
  - "CEILING, функция [службы SSIS]"
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# CEILING (выражение служб SSIS)
  Возвращает наименьшее целое число, большее или равное данному числовому выражению.  
  
## Синтаксис  
  
```  
  
CEILING(numeric_expression)  
```  
  
## Аргументы  
 *numeric_expression*  
 Допустимое числовое выражение.  
  
## Типы результата  
 Тип данных числового выражения, переданного функции.  
  
## Замечания  
 Функция CEILING возвращает NULL, если аргумент имеет значение NULL.  
  
## Примеры выражений  
 В этих примерах функция CEILING применяется к положительным, отрицательным значениям и к нулю.  
  
```  
CEILING(123.74)  
```  
  
 Возвращает значение 124,00  
  
```  
CEILING(-124.27)  
```  
  
 Возвращает значение −124,00  
  
```  
CEILING(0.00)  
```  
  
 Возвращает значение 0,00  
  
## См. также  
 [FLOOR (выражение служб SSIS)](../../integration-services/expressions/floor-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  