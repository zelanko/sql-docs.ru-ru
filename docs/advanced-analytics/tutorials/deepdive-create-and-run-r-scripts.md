---
title: "Создание и выполнение сценариев R | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 51e8e66f-a0a5-4e96-aa71-f5c870e6d0d4
caps.latest.revision: 18
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 08549ecffb6877fd160db62bb54c70dbe9347ce3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-and-run-r-scripts"></a>Создание и выполнение сценариев R

Теперь, когда вы настроили источники данных и создали контексты вычисления, можно приступать к выполнению более сложных скриптов R с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  На этом занятии вы используете серверный контекст вычисления для выполнения ряда распространенных задач машинного обучения:

- визуализация данных и получение сводных статистических данных;
- создание модели линейной регрессии;
- создание модели логистической регрессии;
- оценка новых данных и создание гистограммы оценок.

## <a name="change-compute-context-to-the-server"></a>Задание сервера в качестве контекста вычисления

Перед выполнением любого кода на языке R необходимо указать *текущий* или *активный* контекст вычисления.

1. Чтобы активировать контекст вычисления, который вы уже определили с помощью языка R, используйте функцию **rxSetComputeContext** , как показано ниже.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
    После выполнения этой инструкции все последующие вычисления будут производиться на сервере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , указанном в параметре *sqlCompute* .
  
2. Если вы считаете, что код на языке R лучше выполнять на рабочей станции, вы можете переключить контекст вычисления обратно на локальный компьютер с помощью ключевого слова  **local** .
  
    ```R
    rxSetComputeContext ("local")
    ```
  
    Чтобы просмотреть список других ключевых слов, поддерживаемых этой функцией, в командной строке R введите `help("rxSetComputeContext")` .
  
3. После задания контекста вычисления он будет оставаться активным, пока вы не измените его. Однако скрипты R, которые *не могут* выполняться в контексте удаленного сервера, будут выполняться локально.

## <a name="compute-summary-statistics"></a>Вычисление сводных статистических данных

Чтобы проверить правильность работы контекста вычисления, попытайтесь создать какие-нибудь сводные статистические данные с помощью источника данных *sqlFraudDS* .  Помните, что объект источника данных определяет только данные, которые вы будете использовать. Он не меняет контекст вычисления.

+ Для выполнения кода локально используйте **rxSetComputeContext** и укажите ключевое слово local.
+ Чтобы создать те же самые вычисления на сервере SQL Server, переключитесь в контекст вычисления SQL, определенный ранее.

1. Вызовите функцию **rxSummary** и передайте требуемые аргументы, такие как формула и источник данных, а также занесите результаты в переменную *sumOut*.
  
    ```R
    sumOut \<- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Язык R предоставляет множество функций сводки, но rxSummary поддерживает выполнение в различных контекстах удаленных вычислений, включая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Дополнительные сведения о схожих функциях см. в подразделе о [сводках](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries) в [справочнике по функциям ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler).
  
2. По завершении обработки можно вывести содержимое переменной *sumOut* на консоль.
  
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

## <a name="add-maximum-and-minimum-values"></a>Добавление максимального и минимального значений

Изучив сводные статистические данные, вы получили полезную информацию, которую хотите поместить в источник данных для использования в последующих вычислениях. Например можно использовать минимальное и максимальное значения для вычисления гистограммы, необходимо добавить к источнику данных RxSqlServerData большим и меньшим значениями.

К счастью, в службах [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] есть оптимизированные функции, которые эффективно преобразуют целочисленные данные в категориальные факторные данные.

1. Сначала создайте ряд временных переменных.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Используйте ранее созданную переменную *ccColInfo* для определения столбцов в источнике данных.
  
    Вы также добавите несколько новых вычисляемых столбцов (*numTrans*, *numIntlTrans*и *creditLine*) в коллекцию столбцов.
  
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
  
3. Обновив коллекцию столбцов, вы можете применить приведенную ниже инструкцию, чтобы создать обновленную версию источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который был определен ранее.
  
    ```R
    sqlFraudDS \<- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    Теперь источник данных *sqlFraudDS* содержит новые столбцы, добавленные в *ccColInfo*.
  
  Эти изменения касаются только объекта источника данных в среде R; в таблицу базы данных новые данные не записываются. Однако данные, записанные в переменную *sumOut* , можно использовать для создания визуализаций и сводок. На следующем шаге вы научитесь делать это при переключении контекста вычислений.

> [!TIP]
> Если вы забыли какой контекст вычислений, которые вы используете, запустите `rxGetComputeContext()`.  Возвращаемое значение `RxLocalSeq Compute Context` указывает, что выполняется в локальном контексте.

## <a name="next-step"></a>Следующий шаг

[Визуализация данных SQL Server с помощью R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)

## <a name="previous-step"></a>Предыдущий шаг

[Определение и использование контекстов вычислений](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)


