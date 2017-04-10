---
title: "SIGN (выражение служб SSIS) | Microsoft Docs"
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
  - "положительные значения [службы Integration Services]"
  - "SIGN, функция"
  - "отрицательные значения"
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# SIGN (выражение служб SSIS)
  Возвращает знак числового выражения в виде положительного (+1), нулевого (0) или отрицательного (-1) числа.  
  
## Синтаксис  
  
```  
  
SIGN(numeric_expression)  
```  
  
## Аргументы  
 *numeric_expression*  
 Является допустимым числовым выражением со знаком. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Типы результата  
 DT_I4  
  
## Замечания  
 Функция SIGN возвращает результат NULL, если аргумент имеет значение NULL.  
  
## Примеры выражений  
 Этот пример возвращает знак числового литерала. Возвращается результат -1.  
  
```  
SIGN(-123.45)  
```  
  
 Этот пример возвращает знак результата вычитания значения столбца **StandardCost** из значения столбца **DealerPrice** .  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## См. также  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  