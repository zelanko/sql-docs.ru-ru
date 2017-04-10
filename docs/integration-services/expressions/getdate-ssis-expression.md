---
title: "GETDATE (выражение служб SSIS) | Microsoft Docs"
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
  - "текущая дата"
  - "GETDATE, функция"
  - "даты [службы Integration Services], GETDATE"
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# GETDATE (выражение служб SSIS)
  Возвращает текущее системное время в формате DT_DBTIMESTAMP. Функция GETDATE не имеет аргументов.  
  
> [!NOTE]  
>  Длина строки результата, возвращаемой функцией GETDATE, равна 29 символам.  
  
## Синтаксис  
  
```  
  
GETDATE()  
```  
  
## Аргументы  
 Нет  
  
## Типы результата  
 DT_DBTIMESTAMP  
  
## Примеры выражений  
 Этот пример возвращает текущий год.  
  
```  
DATEPART("year",GETDATE())  
```  
  
 Этот пример возвращает число дней от даты в столбце **ModifiedDate** до текущей даты.  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 Этот пример добавляет три месяца к текущей дате.  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## См. также раздел  
 [GETUTCDATE (выражение служб SSIS)](../../integration-services/expressions/getutcdate-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  