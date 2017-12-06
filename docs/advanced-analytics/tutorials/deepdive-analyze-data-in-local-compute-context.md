---
title: "Анализ данных в локальном контексте | Документы Microsoft"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 787bb526-4a13-40fa-9343-75d3bf5ba6a2
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d8e6516b7d203180d5c2a605db1099b1dcbae708
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="analyze-data-in-local-compute-context-data-science-deep-dive"></a>Анализ данных в локальный контекст вычислений (данных обработки и анализа глубокое погружение)

Несмотря на то, что можно ускорить процесс для выполнения сложных код R, используя контекст сервера, иногда удобнее просто для получения данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и проанализируйте его на рабочей станции закрытый.

В этом разделе вы узнаете, как переключиться обратно на локальный контекст вычисления и переносить данные между контекстами для оптимизации производительности.

## <a name="create-a-local-summary"></a>Создание локальной сводки

1. Измените контекст вычисления так, чтобы все задачи выполнялись локально.
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. При извлечении данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]часто можно добиться более высокой производительности, увеличив число строк, извлекаемых каждой операцией чтения.  Для этого увеличьте значение параметра *rowsPerRead* в источнике данных.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```
  
    Ранее значение параметра *rowsPerRead* было равно 5000.
  
3. Теперь вызовите функцию **rxSummary** в новом источнике данных.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
    Фактические результаты должно быть таким же, как при выполнении в контексте rxSummary [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера.  Однако операция может выполняться быстрее или медленнее. Во многом это зависит от подключения к базе данных, так как данные передаются на локальный компьютер для анализа.


## <a name="next--step"></a>Следующий шаг

[Перемещение данных между SQL Server и XDF-файла](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)

## <a name="previous-step"></a>Предыдущий шаг

[Выполнять анализ фрагментации, с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)


