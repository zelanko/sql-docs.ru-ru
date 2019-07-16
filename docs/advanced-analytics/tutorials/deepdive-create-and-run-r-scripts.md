---
title: Вычислить сводную статистику руководстве RevoScaleR - машинного обучения SQL Server
description: Руководство о том, как вычислить статистические сводную статистику, используя язык R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 945b7cb32c64c343ca7bb5ab2aab4169fd7bea24
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962281"
---
# <a name="compute-summary-statistics-in-r-sql-server-and-revoscaler-tutorial"></a>Вычислить сводную статистику в R (руководство по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Он использует источники данных и контекстов вычислений, созданных в предыдущих уроках для выполнения сложных скриптов R в нем. На этом занятии будет использовать сервер локальных и удаленных контекстов вычислений для выполнения следующих задач:

> [!div class="checklist"]
> * Переключить контекст вычисления для SQL Server
> * Получить сводные статистические данные о объекты удаленных данных
> * Вычисления локальной сводки

Если вы выполнили уроки, необходимо иметь эти удаленные контексты вычисления: sqlCompute и sqlComputeTrace. Продвигаясь вперед, используется будет sqlCompute и локального контекста вычислений на следующих занятиях.

Использование среды IDE R или **Rgui** для запуска скрипта R на этом занятии.

## <a name="compute-summary-statistics-on-remote-data"></a>Вычислить сводную статистику на удаленных данных

Прежде чем код R можно выполнять удаленно, необходимо указать удаленного контекста вычислений. Все последующие вычисления выполняются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютере, указанном в *sqlCompute* параметра.

Контекст вычисления остается активным, пока вы не измените его. Однако скрипты R, которые *нельзя* выполнения в контексте удаленного сервера будет автоматически запускаться локально.

Чтобы увидеть, как работает контекст вычисления, создайте сводную статистику для источника данных sqlFraudDS на удаленный экземпляр SQL Server. Этот объект источника данных был создан в [урок два](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) и представляющий таблицу в базе данных RevoDeepDive ccFraudSmall. 

1. Перейдите контекст вычисления для sqlCompute, созданные на предыдущем занятии:
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```

2. Вызовите [rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) функции и передайте требуемые аргументы, такие как формула и источник данных и присвоить переменной результаты `sumOut`.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Язык R предоставляет множество функций сводки, но **rxSummary** в **RevoScaleR** поддерживает выполнение в различных контекстах удаленных вычислений, включая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о схожих функциях см. в разделе [сводки данных, с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).
  
3. Печать содержимого sumOut на консоль.
  
    ```R
    sumOut
    ```
    > [!NOTE]
    > Если отобразится сообщение об ошибке, подождите несколько минут для выполнения перед повторным выполнением команды.

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
  
2. При извлечении данных из SQL Server, можно часто получить более высокую производительность, увеличивая количество строк, извлекаемых каждой операцией чтения, при условии, что размер блока увеличение может быть размещено в памяти. Выполните следующую команду, чтобы увеличить значение для *rowsPerRead* параметр в источнике данных. Ранее значение параметра *rowsPerRead* было равно 5000.
  
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
  
   Фактические результаты должны совпадать с результатами, получаемыми при запуске функции **rxSummary** в контексте компьютера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако операция может выполняться быстрее или медленнее. Во многом это зависит от подключения к базе данных, так как данные передаются на локальный компьютер для анализа.

4. Вернитесь на удаленного контекста вычислений для следующего несколько занятий.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Визуализация данных SQL Server с помощью языка R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)