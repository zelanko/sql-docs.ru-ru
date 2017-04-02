---
title: "ROUND (выражение служб SSIS) | Microsoft Docs"
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
  - "округление выражений"
  - "ROUND, функция [службы SSIS]"
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# ROUND (выражение служб SSIS)
  Возвращает числовое выражение, округленное до указанной длины или точности. Параметр длины должен иметь целочисленное значение.  
  
## Синтаксис  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## Аргументы  
 *numeric_expression*  
 Является выражением допустимого числового типа. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 *длина*  
 Является целочисленным выражением. Это точность, до которой должно быть округлено значение *numeric_expression*.  
  
## Типы результата  
 Того же типа, что и *numeric*_*expression.*  
  
## Замечания  
 Аргумент *length* должен иметь положительное целочисленное значение либо ноль.  
  
 ROUND возвращает результат NULL, если аргумент имеет значение NULL.  
  
## Примеры выражений  
 Эти примеры округляют числовые величины до трех знаков. Первый возвращенный результат — 137.1570, второй — 137.1580.  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## См. также  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  