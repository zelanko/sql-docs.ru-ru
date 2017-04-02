---
title: "+ (Сложение) (службы SSIS) | Microsoft Docs"
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
  - "+ (сложение)"
  - "оператор сложения (+)"
  - "добавление выражений"
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# + (Сложение) (службы SSIS)
  Складывает два числовых выражения.  
  
## Синтаксис  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## Аргументы  
 *numeric_expression1, numeric_expression2*  
 Любое допустимое выражение числовых типов данных.  
  
## Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Замечания  
 Если один из операндов равен NULL, то результатом является значение NULL.  
  
## Примеры выражений  
 В этом примере суммируются числовые литералы.  
  
```  
5 + 6.09 + 7.0  
```  
  
 В примере суммируются значения столбцов **VacationHours** и **SickLeaveHours** .  
  
```  
VacationHours + SickLeaveHours  
```  
  
 В примере вычисленное значение прибавляется к столбцу **StandardCost** . Переменная **Profit%** должна быть заключена в квадратные скобки, поскольку имя включает символ %. Дополнительные сведения см. в статье [Идентификаторы (службы SSIS)](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## См. также  
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  