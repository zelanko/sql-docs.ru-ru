---
title: Визуализация данных SQL Server, с помощью RevoScaleR rxHistogram - машинного обучения SQL Server
description: Руководство о том, как визуализировать данные с помощью языка R в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 4092de07d19d4d33bd56025076e606269c2b04e8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962152"
---
#  <a name="visualize-sql-server-data-using-r-sql-server-and-revoscaler-tutorial"></a>Визуализация данных SQL Server, с помощью языка R (руководство по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом занятии использовать функции R, чтобы просмотреть распределение значений в *creditLine* столбца по полу.

> [!div class="checklist"]
> * Создание минимальных и максимальных переменные для входных данных гистограммы
> * Визуализация данных в гистограмму с помощью **rxHistogram** из **RevoScaleR**
> * Визуализация с помощью точечных диаграмм с помощью **levelplot** из **lattice** включенные в базовое распределение R

Как на этом занятии рассматривается, открытым исходным кодом и характерные для Майкрософт функции, в том же сценарии можно объединять.

## <a name="add-maximum-and-minimum-values"></a>Добавить максимальное и минимальное значения

Исходя из вычисляемые сводные статистические данные на предыдущем занятии, вы ознакомились с некоторые полезные сведения о данных, которые можно вставить в источник данных для дальнейшего вычисления. Например минимальное и максимальное значения можно использовать для построения гистограмм. В этом упражнении добавить верхние и нижние значения **RxSqlServerData** источника данных.

1. Сначала создайте ряд временных переменных.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Используйте эту переменную *ccColInfo* , созданного на предыдущем занятии, для определения столбцов в источнике данных.
  
   Добавление новых вычисляемых столбцов (*numTrans*, *numIntlTrans*, и *creditLine*) в коллекцию столбцов, которая переопределяет исходное определение. Приведенный ниже сценарий добавляет факторы, на основе минимального и максимального значений, полученный из sumOut, которая сохраняет выходные данные в памяти **rxSummary**. 
  
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
  
3. Обновив коллекцию столбцов, применить следующую инструкцию, чтобы создать обновленную версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных, который вы задали ранее.
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    Источник данных sqlFraudDS теперь содержит новые столбцы, добавленные с помощью *ccColInfo*.
  
На этом этапе изменения касаются только объекта источника данных в R; новые данные не будет записана в таблицу базы данных еще. Тем не менее данные, записанные в переменную sumOut можно использовать для создания визуализаций и сводок. 

> [!TIP]
> Если вы забудете, какой контекст вычисления, вы используете, выполните **rxGetComputeContext()** . Возвращаемое значение, равное «Контекст вычислений RxLocalSeq» указывает, что вы работаете в локальном контексте вычисления.

## <a name="visualize-data-using-rxhistogram"></a>Визуализация данных с помощью rxHistogram

1. Используйте следующий код R, чтобы вызвать функцию [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) и передать формулу и источник данных. Сначала эту операцию можно выполнить локально, чтобы оценить результаты и продолжительность.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Сама по себе функция **rxHistogram** вызывает функцию [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) , которая включена в пакет **RevoScaleR** . **rxCube** выводит один список (или кадр данных) содержит по одному столбцу для каждой переменной, указанной в формуле, а также столбец counts.
    
2. Теперь задайте контекст вычислений на удаленный компьютер SQL Server и запустите **rxHistogram** еще раз.
  
    ```R
    rxSetComputeContext(sqlCompute)
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
3. Результаты одинаковы, так как вы используете тот же источник данных, но на втором шаге, вычисления выполняются на удаленном сервере. Затем результаты возвращаются на локальную рабочую станцию для построения графика.
   
  ![Результаты в виде гистограммы](media/rsql-sue-histogramresults.jpg "Результаты в виде гистограммы")


## <a name="visualize-with-scatter-plots"></a>Визуализация с помощью точечных диаграмм

Точечных диаграмм часто используются во время просмотра данных для сравнения отношения между двумя переменными. Для этой цели можно использовать встроенные пакеты R с входными данными, предоставляемые **RevoScaleR** функции.

1. Вызовите [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) функции для вычисления среднего значения *fraudRisk* для каждой комбинации *numTrans* и *numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Чтобы указать группы, используемые для вычисления средних значений по группам, используйте нотацию `F()` . В этом примере `F(numTrans):F(numIntlTrans)` указывает, что целочисленные значения переменных `numTrans` и `numIntlTrans` следует рассматривать как категориальные переменные с уровнем каждое целочисленное значение.
  
    Возвращаемое значение по умолчанию **rxCube** — *rxCube объекта*, который представляет перекрестное табулирование. 
  
2. Вызовите [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) функция для преобразования результатов в кадр данных, который можно легко использовать в одном из стандартных функций построения диаграмм.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    **RxCube** функция имеет необязательный аргумент, *returnDataFrame* = **TRUE**, что можно использовать для преобразования результатов в кадр данных напрямую. Пример:
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Тем не менее выходные данные **rxResultsDF** чище и понятнее и в них сохраняются имена исходных столбцов. Можно запустить `head(cube1)` следуют `head(cubePlot)` сравнение вывода.
  
3. Создать тепловую карту с помощью **levelplot** функции из **lattice** пакета, в состав всех дистрибутивов r.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Результаты**
  
    ![Результаты в виде точечной диаграммы](media/rsql-sue-scatterplotresults.jpg "Результаты в виде точечной диаграммы")
  
Из такой быстрый анализ вы увидите, что риск мошенничества возрастает количество транзакций и числа международных транзакций.

Дополнительные сведения о **rxCube** функции и перекрестных таблицах в целом, см. в разделе [сводки данных, с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Создание моделей R, используя данные SQL Server](../../advanced-analytics/tutorials/deepdive-create-models.md)