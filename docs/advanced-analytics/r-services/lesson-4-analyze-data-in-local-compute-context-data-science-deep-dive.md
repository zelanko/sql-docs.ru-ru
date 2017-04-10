---
title: "Занятие&#160;4. Анализ данных в локальном контексте вычисления (глубокое погружение в обработку и анализ данных) | Microsoft Docs"
ms.custom: ""
ms.date: "10/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 787bb526-4a13-40fa-9343-75d3bf5ba6a2
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Занятие&#160;4. Анализ данных в локальном контексте вычисления (глубокое погружение в обработку и анализ данных)
Хотя обычно сложный код на языке R гораздо быстрее выполняется в контексте сервера, иногда удобнее получать данные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и анализировать их на собственной рабочей станции.  
  
В этом разделе вы узнаете, как переключиться обратно на локальный контекст вычисления и переносить данные между контекстами для оптимизации производительности.  
  
## Создание локальной сводки  
  
1.  Измените контекст вычисления так, чтобы все задачи выполнялись локально.  
  
    ```R  
    rxSetComputeContext ("local")    
    ```  
  
2.  При извлечении данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] часто можно добиться более высокой производительности, увеличив число строк, извлекаемых каждой операцией чтения.  Для этого увеличьте значение параметра *rowsPerRead* в источнике данных.  
  
    ```R  
    sqlServerDS1 <- RxSqlServerData(  
       connectionString = sqlConnString,        
       table = sqlFraudTable,   
       colInfo = ccColInfo,   
       rowsPerRead = 10000)  
    ```  
  
    Ранее значение параметра *rowsPerRead* было равно 5000.  
  
3.  Теперь вызовите функцию *rxSummary* в новом источнике данных.  
  
    ```R  
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)    
    ```  
  
    Фактические результаты должны совпадать с результатами, получаемыми при запуске функции *rxSummary* в контексте компьютера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Однако операция может выполняться быстрее или медленнее. Во многом это зависит от подключения к базе данных, так как данные передаются на локальный компьютер для анализа.  
  

## Следующий шаг  
[Перенос данных между SQL Server и файлом XDF (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/move-data-between-sql-server-and-xdf-file-data-science-deep-dive.md)  
  
## Предыдущий шаг  
[Выполнение фрагментирующего анализа с помощью rxDataStep (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/perform-chunking-analysis-using-rxdatastep-data-science-deep-dive.md)  
  
  
  
