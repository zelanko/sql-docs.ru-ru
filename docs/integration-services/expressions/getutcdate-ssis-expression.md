---
title: "GETUTCDATE (выражение служб SSIS) | Microsoft Docs"
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
  - "даты [службы Integration Services], GETUTCDATE"
  - "текущая дата"
  - "UTC, время"
  - "GETUTCDATE, функция"
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# GETUTCDATE (выражение служб SSIS)
  Возвращает текущую дату системы в формате времени UTC (универсальное время, или время по Гринвичу), используя формат DT_DBTIMESTAMP. Функция GETUTCDATE не имеет аргументов.  
  
## Синтаксис  
  
```  
  
GETUTCDATE()  
```  
  
## Аргументы  
 Нет  
  
## Типы результата  
 DT_DBTIMESTAMP  
  
## Примеры выражений  
 Этот пример возвращает год текущей даты времени в формате UTC.  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 Этот пример возвращает количество дней между датой в столбце **ModifiedDate** и текущей датой в формате UTC.  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 Этот пример добавляет три месяца к текущей дате в формате UTC.  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## См. также раздел  
 [GETDATE (выражение служб SSIS)](../../integration-services/expressions/getdate-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  