---
title: "MONTH (выражение служб SSIS) | Microsoft Docs"
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
  - "даты [службы Integration Services], MONTH"
  - "MONTH, функция"
ms.assetid: b5a47a11-c2ef-49bd-bd70-235632ff7bf6
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# MONTH (выражение служб SSIS)
  Возвращает целое число, представляющее месяц указанной даты.  
  
## Синтаксис  
  
```  
  
MONTH(date)  
```  
  
## Аргументы  
 *date*  
 Является датой в любом формате дат.  
  
## Типы результата  
 DT_I4  
  
## Замечания  
 Функция MONTH возвращает значение NULL, если значение аргумента NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  Проверка выражения завершается ошибкой при явном приведении литерала даты к одному из следующих типов данных: DT_DBTIMESTAMPOFFSET и DT_DBTIMESTAMP2.  
  
 Использование функции MONTH более компактно, но эквивалентно использованию функции DATEPART(«Month», date).  
  
## Примеры выражений  
 В этом примере возвращается номер месяца из литерала даты. Если дата имеет формат «мм/дд/гггг», то этот пример возвращает 11.  
  
```  
MONTH((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 В этом примере возвращается целое число, представляющее месяц в столбце **ModifiedDate** .  
  
```  
MONTH(ModifiedDate)  
```  
  
 В этом примере возвращается целое число, представляющее месяц текущей даты.  
  
```  
MONTH(GETDATE())  
```  
  
## См. также  
 [DATEADD (выражение служб SSIS)](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF (выражение служб SSIS)](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART (выражение служб SSIS)](../../integration-services/expressions/datepart-ssis-expression.md)   
 [DAY (выражение служб SSIS)](../../integration-services/expressions/day-ssis-expression.md)   
 [YEAR (выражение служб SSIS)](../../integration-services/expressions/year-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  