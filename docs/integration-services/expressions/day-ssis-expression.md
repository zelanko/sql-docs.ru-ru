---
title: "DAY (выражение служб SSIS) | Microsoft Docs"
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
  - "DAY, функция"
  - "даты [службы Integration Services], DAY"
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# DAY (выражение служб SSIS)
  Возвращает целое число, представляющее день указанной даты.  
  
## Синтаксис  
  
```  
  
DAY(date)  
```  
  
## Аргументы  
 *date*  
 Выражение, возвращающее допустимую дату или строку в формате даты.  
  
## Типы результата  
 DT_I4  
  
## Замечания  
 Функция DAY возвращает значение NULL, если значение аргумента NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  Проверка выражения завершается ошибкой при явном приведении литерала даты к одному из следующих типов данных: DT_DBTIMESTAMPOFFSET и DT_DBTIMESTAMP2.  
  
 Использование функции DAY более компактно, но эквивалентно использованию функции DATEPART("Day", date).  
  
## Примеры выражений  
 В этом примере возвращается номер дня из литерала даты. Если дата имеет формат «мм/дд/гггг», будет возвращено значение 23.  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 Этот пример возвращает целое число, представляющее день в столбце **ModifiedDate** .  
  
```  
DAY(ModifiedDate)  
```  
  
 В этом примере возвращается целое число, представляющее день текущей даты.  
  
```  
DAY(GETDATE())  
```  
  
## См. также  
 [DATEADD (выражение служб SSIS)](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF (выражение служб SSIS)](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART (выражение служб SSIS)](../../integration-services/expressions/datepart-ssis-expression.md)   
 [MONTH (выражение служб SSIS)](../../integration-services/expressions/month-ssis-expression.md)   
 [YEAR (выражение служб SSIS)](../../integration-services/expressions/year-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  