---
title: "DATEPART (выражение служб SSIS) | Microsoft Docs"
ms.custom: 
  - "ssisdev020617"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "даты [службы Integration Services], DATEPART"
  - "DATEPART, функция"
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# DATEPART (выражение служб SSIS)
  Возвращает целое число, обозначающее раздел даты.  
  
## Синтаксис  
  
```  
  
DATEPART(datepart, date)  
```  
  
## Аргументы  
 *часть_даты*  
 Параметр, который указывает, для какой части даты вернуть новое значение.  
  
 *date*  
 Выражение, возвращающее допустимую дату или строку в формате даты.  
  
## Типы результата  
 DT_I4  
  
## Замечания  
 DATEPART возвращает NULL при аргументе NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 В следующей таблице перечислены части дат и сокращения, распознаваемые средством оценки выражений. Имена частей даты обрабатываются без учета регистра.  
  
|Часть даты|Сокращения|  
|--------------|-------------------|  
|Год|yy, yyyy|  
|Квартал|qq, q|  
|Месяц|mm, m|  
|День года|dy, y|  
|День|dd, d|  
|Неделя|wk, ww|  
|День недели|dw|  
|Час|Hh|  
|Минута|mi, n|  
|Вторая|ss, s|  
|Миллисекунда|Ms|  
  
## Примеры выражений служб SSIS  
 Этот пример возвращает целое число, которое представляет месяц в литерале даты. Если формат даты «мм/дд/гггг», то этот пример возвращает 11.  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 Этот пример возвращает целое число, представляющее день в столбце **ModifiedDate** .  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 Этот пример возвращает целое число, представляющее год в текущей дате.  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## См. также  
 [DATEADD (выражение служб SSIS)](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF (выражение служб SSIS)](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DAY (выражение служб SSIS)](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH (выражение служб SSIS)](../../integration-services/expressions/month-ssis-expression.md)   
 [YEAR (выражение служб SSIS)](../../integration-services/expressions/year-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  