---
title: Руководство по вычислению сводных статистических показателей RevoScaleR
description: Пошаговое руководство по вычислению статистических сводных статистических показателей с использованием языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 5b1ec344a2ec9728a24d45c47dd80737e6155b01
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469817"
---
# <a name="compute-summary-statistics-in-r-sql-server-and-revoscaler-tutorial"></a>Сводная статистика вычислений в R (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Это занятие является частью [учебника RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

В нем используются установленные источники данных и контексты вычислений, созданные на предыдущих занятиях, для запуска сценариев R с высоким уровнем использования в этом. На этом занятии будут использоваться контексты вычислений для локальных и удаленных серверов для следующих задач:

> [!div class="checklist"]
> * Переключить контекст вычислений на SQL Server
> * Получить сводную статистику по удаленным объектам данных
> * Вычисление локальной сводки

Если вы выполнили предыдущие уроки, у вас должны быть следующие удаленные контексты вычислений: sqlCompute и Склкомпутетраце. В дальнейшем вы будете использовать sqlCompute и локальный контекст вычислений на последующих занятиях.

Используйте R IDE или **RGUI** для запуска скрипта r на этом занятии.

## <a name="compute-summary-statistics-on-remote-data"></a>Вычисление сводных статистических данных по удаленным данным

Перед удаленным запуском кода R необходимо указать удаленный контекст вычислений. Все последующие вычисления выполняются на компьютере, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указанном в параметре *sqlCompute* .

Контекст вычислений остается активным, пока вы не измените его. Однако скрипты R, которые *не могут* выполняться в контексте удаленного сервера, будут автоматически выполняться локально.

Чтобы увидеть, как работает контекст вычислений, создайте сводную статистику для источника данных sqlFraudDS на удаленном SQL Server. Этот объект источника данных был создан на [занятии 2](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) и представляет таблицу ccFraudSmall в базе данных реводипдиве. 

1. Переключить контекст вычислений на sqlCompute, созданный на предыдущем занятии:
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```

2. Вызовите функцию [rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) и передайте необходимые аргументы, такие как формула и источник данных, и присвойте результаты переменной `sumOut`.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Язык R предоставляет множество сводных функций, но **rxSummary** в **RevoScaleR** поддерживает выполнение в различных удаленных контекстах вычисления, включая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о схожих функциях см. в разделе [сводки данных с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).
  
3. Распечатайте содержимое sumOut в консоли.
  
    ```R
    sumOut
    ```
    > [!NOTE]
    > При возникновении ошибки подождите несколько минут, пока не завершится выполнение команды.

**Результаты**

```R
Summary Statistics Results for: ~gender + balance + numTrans + numIntlTrans + creditLine
Data: sqlFraudDS (RxSqlServerData Data Source)
Number of valid observations: 10000

 Name  Mean    StdDev  Min Max ValidObs    MissingObs
 balance       4075.0318 3926.558714            0   25626 100000
 numTrans        29.1061   26.619923 0     100 10000    0           100000
 numIntlTrans     4.0868    8.726757 0      60 10000    0           100000
 creditLine       9.1856    9.870364 1      75 10000    0          100000
 
 Category Counts for gender
 Number of categories: 2
 Number of valid observations: 10000
 Number of missing observations: 0

 gender Counts
  Male   6154
  Female 3846
```

## <a name="create-a-local-summary"></a>Создание локальной сводки

1. Измените контекст вычисления так, чтобы все задачи выполнялись локально.
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. При извлечении данных из SQL Server часто можно получить лучшую производительность, увеличив число строк, извлеченных для каждого считывания, предполагая, что увеличенный размер блока можно разместить в памяти. Выполните следующую команду, чтобы увеличить значение параметра *rowsPerRead* в источнике данных. Ранее значение параметра *rowsPerRead* было равно 5000.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. Вызовите **rxSummary** для нового источника данных.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
   Фактические результаты должны совпадать с результатами, получаемыми при запуске функции **rxSummary** в контексте компьютера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако операция может выполняться быстрее или медленнее. Во многом это зависит от подключения к базе данных, так как данные передаются на локальный компьютер для анализа.

4. Вернитесь к удаленному контексту вычислений для следующих нескольких уроков.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Визуализация данных SQL Server с помощью языка R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)