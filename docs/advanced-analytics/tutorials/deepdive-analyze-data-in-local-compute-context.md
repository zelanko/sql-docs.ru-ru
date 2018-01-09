---
title: "Анализ данных в локальный контекст вычислений (SQL и R глубокое погружение) | Документы Microsoft"
ms.date: 12/18/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: 787bb526-4a13-40fa-9343-75d3bf5ba6a2
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 0705d7253979dd5b688a0ca5f78720304a368e3d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="analyze-data-in-local-compute-context-sql-and-r-deep-dive"></a>Анализ данных в локальный контекст вычислений (SQL и R глубокое погружение)

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

В этом разделе вы узнаете, как для переключения обратно в локальный контекст вычислений и перемещение данных между контекстами для оптимизации производительности.

Несмотря на то, что i можно ускорить процесс для выполнения сложных код R, используя контекст сервера, иногда удобнее для получения данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и проанализируйте его на локальной рабочей станции.

## <a name="create-a-local-summary"></a>Создание локального сводки

1. Измените контекст вычисления так, чтобы все задачи выполнялись локально.
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. При извлечении данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]часто можно добиться более высокой производительности, увеличив число строк, извлекаемых каждой операцией чтения.  Для этого увеличьте значение параметра *rowsPerRead* в источнике данных. Ранее значение параметра *rowsPerRead* было равно 5000.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. Вызовите **rxSummary** на новый источник данных.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
    Фактические результаты должны совпадать с результатами, получаемыми при запуске функции **rxSummary** в контексте компьютера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Однако операция может выполняться быстрее или медленнее. Во многом это зависит от подключения к базе данных, так как данные передаются на локальный компьютер для анализа.

## <a name="next-step"></a>Следующий шаг

[Перемещение данных между SQL Server и файлом XDF.](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)

## <a name="previous-step"></a>Предыдущий шаг

[Выполнение фрагментирующего анализа с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
