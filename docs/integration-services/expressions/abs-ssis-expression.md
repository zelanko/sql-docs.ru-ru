---
title: "ABS (выражение служб SSIS) | Microsoft Docs"
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
  - "ABS, функция"
  - "абсолютное положительное значение"
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# ABS (выражение служб SSIS)
  Возвращает абсолютное положительное значение числового выражения.  
  
## Синтаксис  
  
```  
  
ABS(numeric_expression)  
```  
  
## Аргументы  
 *numeric_expression*  
 Является числовым выражением со знаком или без знака.  
  
## Типы результата  
 Тип данных числового выражения, переданного функции.  
  
## Замечания  
 Функция ABS возвращает NULL, если аргумент имеет значение NULL.  
  
## Примеры выражений  
 В этих примерах функция ABS применяется к положительному и отрицательному числам. В обоих случаях возвращается 1,23.  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 В этом примере функция ABS применяется к разности значений переменных **HighTemperature** и **LowTempature**.  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## См. также  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  