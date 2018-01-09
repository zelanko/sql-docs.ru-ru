---
title: "Создание и выполнение R-скриптов (SQL и R глубокое погружение) | Документы Microsoft"
ms.date: 12/14/2017
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
ms.assetid: 51e8e66f-a0a5-4e96-aa71-f5c870e6d0d4
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 302068f7ee9f1fe04bc7a3b1558e510274b2bc0d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="create-and-run-r-scripts-sql-and-r-deep-dive"></a>Создание и выполнение R-скриптов (SQL и R глубокое погружение)

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Теперь, когда вы настроили источники данных и создали контексты вычисления, можно приступать к выполнению более сложных скриптов R с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  На этом занятии использовать контекст вычислений сервера делать некоторые распространенные машинного обучения задачи:

- визуализация данных и получение сводных статистических данных;
- создание модели линейной регрессии;
- создание модели логистической регрессии;
- оценка новых данных и создание гистограммы оценок.

## <a name="change-compute-context-to-the-server"></a>Изменение контекста на сервер вычислений

Перед выполнением любого кода на языке R необходимо указать *текущий* или *активный* контекст вычисления.

1. Чтобы активировать контекст вычисления, который вы уже определили с помощью языка R, используйте функцию **rxSetComputeContext** , как показано ниже.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
    Как только выполнении этой инструкции, все последующие вычисления выполняются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютере, указанном в *sqlCompute* параметра.
  
2. Если вы считаете, что код на языке R лучше выполнять на рабочей станции, вы можете переключить контекст вычисления обратно на локальный компьютер с помощью ключевого слова  **local** .
  
    ```R
    rxSetComputeContext ("local")
    ```
  
    Чтобы просмотреть список других ключевых слов, поддерживаемых этой функцией, в командной строке R введите `help("rxSetComputeContext")` .
  
3. После задания контекста вычисления он будет оставаться активным, пока вы не измените его. Однако скрипты R, которые *не могут* выполняться в контексте удаленного сервера, будут выполняться локально.

## <a name="compute-some-summary-statistics"></a>Вычисления сводных статистики

Чтобы посмотреть, как работает контекст вычислений. Попробуйте создания некоторых сводные статистические данные с помощью `sqlFraudDS` источника данных.  Обратите внимание, что объект источника данных определяет только данные, которые можно использовать; оно не изменяется контекст вычислений.

+ Для выполнения в сводке локально, используйте **rxSetComputeContext** и укажите _локального_ ключевое слово.
+ Чтобы создать те же самые вычисления на сервере SQL Server, переключитесь в контекст вычисления SQL, определенный ранее.

1. Вызовите [rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) функцией и передачи обязательных аргументов, например формулы и источнике данных и присвоить переменной результаты `sumOut`.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Язык R поддерживает множество функций сводки, но **rxSummary** поддерживает выполнение в различных контекстах удаленных вычислений, включая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функции, подобные см. в разделе [сводок по данным с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).
  
2. После завершения обработки можно печатать содержимое `sumOut` переменной на консоль.
  
    ```R
    sumOut
    ```
  
    > [!NOTE]
    > Если вы попытаетесь вывести результаты до того, как они будут возвращены с сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , может возникнуть ошибка.

**Результаты**

*Сводные статистические результаты для: ~gender + balance + numTrans +*

 *numIntlTrans + creditLine*

 *Данные: sqlFraudDS (RxSqlServerData Data Source)*

 *Число допустимых наблюдений: 10000*

 *Name  Mean    StdDev  Min Max ValidObs    MissingObs*

 *balance       4075,0318 3926,558714            0   25626 100000*

 *numTrans        29,1061   26,619923 0     100 10000    0           100000*

 *numIntlTrans     4,0868    8,726757 0      60 10000    0           100000*

 *creditLine 9.1856 9.870364 1 75 10000 0 100000*

 *Категория счетчиков gender*

 *Число категорий: 2*

 *Число допустимых наблюдений: 10000*

 *Число отсутствующих наблюдений: 0*

 *gender Число*

 *Male   6154*

  *Female 3846*

## <a name="add-maximum-and-minimum-values"></a>Добавить минимальное и максимальное значения

Изучив сводные статистические данные, вы получили полезную информацию, которую хотите поместить в источник данных для использования в последующих вычислениях. Например можно использовать минимальное и максимальное значения для вычисления гистограммы. По этой причине добавим большим и меньшим значениями для **RxSqlServerData** источника данных.

К счастью [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] включает оптимизированные функции, которые можно эффективно преобразовать целочисленные данные в коэффициент категориальные данные.

1. Сначала создайте ряд временных переменных.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Используйте ранее созданную переменную `ccColInfo` для определения столбцов в источнике данных.
  
    Кроме того, добавить некоторые новые вычисляемые столбцы (`numTrans`, `numIntlTrans`, и `creditLine`) в коллекцию столбцов.
  
    ```R 
    ccColInfo <- list(
        gender = list(type = "factor",
          levels = c("1", "2"), 
          newLevels = c("Male", "Female")),
        cardholder = list(type = "factor",
          levels = c("1", "2"), 
          newLevels = c("Principal", "Secondary")), 
        state = list(type = "factor", 
          levels = as.character(1:51), 
          newLevels = stateAbb), 
        balance  = list(type = "numeric"),
        numTrans = list(type = "factor", 
          levels = as.character(sumDF[var == "numTrans", "Min"]:sumDF[var == "numTrans", "Max"])),
        numIntlTrans = list(type = "factor",  
            levels = as.character(sumDF[var == "numIntlTrans", "Min"]:sumDF[var =="numIntlTrans", "Max"])),
        creditLine = list(type = "numeric")
            )
    ```
  
3. Обновления коллекции столбцов применить следующую инструкцию, чтобы создать обновленную версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных, которое было определено ранее.
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    `sqlFraudDS` Источник данных теперь включает новые столбцы, добавленные с помощью `ccColInfo`.
  

На этом этапе изменения на только объект источника данных в R; нет новых данных еще была записана в таблицу базы данных. Тем не менее, можно использовать данные, зафиксированные в `sumOut` переменной для создания визуализаций и сводки. В следующем шаге вы узнаете, как это сделать при переключении контекстов вычислений.

> [!TIP]
> Если вы забыли какой контекст вычислений, которые вы используете, запустите `rxGetComputeContext()`.  Возвращаемое значение «Контекст вычислений RxLocalSeq» указывает, выполняется в локальном контексте.

## <a name="next-step"></a>Следующий шаг

[Визуализация данных SQL Server с помощью языка R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)

## <a name="previous-step"></a>Предыдущий шаг

[Определение и использование контекстов вычисления](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)
