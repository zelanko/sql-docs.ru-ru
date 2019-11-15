---
title: Сводная статистика в RevoScaleR
description: Пошаговое руководство по вычислению сводных статистических данных с помощью языка R в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4ece8cdac4f39cfd5d4b93484f18b0d415cc2291
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727294"
---
# <a name="compute-summary-statistics-in-r-sql-server-and-revoscaler-tutorial"></a>Вычисление сводных статистических данных с помощью языка R (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Этот занятие входит в состав [учебника по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), в котором описывается использование функций [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

В нем используются установленные источники данных и контексты вычислений, созданные на предыдущих занятиях, для запуска мощного сценария R. На этом занятии вы будете использовать контексты вычислений для локальных и удаленных серверов для решения следующих задач:

> [!div class="checklist"]
> * Переключение контекста вычислений на SQL Server
> * Получение сводной статистики по удаленным объектам данных
> * Вычисление локальной сводки

Если вы выполнили предыдущие уроки, у вас должны быть следующие удаленные контексты вычислений: sqlCompute и sqlComputeTrace. Вы будете использовать sqlCompute и локальный контекст вычислений на последующих занятиях.

Используйте интегрированную среду разработки R или **Rgui** для запуска сценария R на этом занятии.

## <a name="compute-summary-statistics-on-remote-data"></a>Вычисление сводных статистических данных для удаленных данных

Перед удаленным выполнением любого кода на языке R необходимо указать удаленный контекст вычислений. Все последующие вычисления будут производиться на сервере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указанном в параметре *sqlCompute*.

Контекст вычислений будет оставаться активным, пока вы не измените его. Однако скрипты R, которые *не могут* выполняться в контексте удаленного сервера, будут автоматически выполняться локально.

Чтобы увидеть, как работает контекст вычислений, создайте сводную статистику для источника данных sqlFraudDS на удаленном экземпляре SQL Server. Этот объект источника данных был создан на [уроке 2](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) и представляет таблицу ccFraudSmall в базе данных RevoDeepDive. 

1. Переключите контекст вычислений на контекст sqlCompute, созданный на предыдущем занятии:
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```

2. Вызовите функцию [rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) и передайте требуемые аргументы, такие как формула и источник данных, а также занесите результаты в переменную `sumOut`.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    В языке R существует множество функций для получения сводных данных, однако функция **rxSummary** в **RevoScaleR** поддерживает выполнение в различных удаленных контекстах вычислений, например, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о подобных функциях см. в разделе [Получение сводок данных с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).
  
3. Введите содержимое переменной sumOut в консоли.
  
    ```R
    sumOut
    ```
    > [!NOTE]
    > Если возникла ошибка, подождите несколько минут, пока не завершится выполнение команды.

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
  
2. При извлечении данных из SQL Server часто можно повысить производительность, увеличив число строк, извлекаемых для каждой операции считывания, при условии того, что блок с увеличенным размером можно разместить в памяти. Выполните следующую команду, чтобы увеличить значение параметра *rowsPerRead* в источнике данных. Ранее значение параметра *rowsPerRead* было равно 5000.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. Вызовите функцию **rxSummary** в новом источнике данных.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
   Фактические результаты должны совпадать с результатами, получаемыми при запуске функции **rxSummary** в контексте компьютера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако операция может выполняться быстрее или медленнее. Во многом это зависит от подключения к базе данных, так как данные передаются на локальный компьютер для анализа.

4. Вернитесь к удаленному контексту вычислений для нескольких последующих уроков.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Визуализация данных SQL Server с помощью языка R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)