---
title: Анализ данных в локальный контекст вычислений (SQL и R глубокое погружение) | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 598abd5e8da1bc8a5a6fdc844fe4133c27e87efa
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="analyze-data-in-local-compute-context-sql-and-r-deep-dive"></a>Анализ данных в локальный контекст вычислений (SQL и R глубокое погружение)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

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
