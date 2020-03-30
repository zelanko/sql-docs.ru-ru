---
title: Визуализация данных с помощью RevoScaleR
description: Учебник по RevoScaleR, часть 6. Визуализация данных с помощью языка R в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 887c5790a7de70cf111f004be65e3a41748b47bf
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "74947370"
---
#  <a name="visualize-sql-server-data-using-r-sql-server-and-revoscaler-tutorial"></a>Визуализация данных SQL Server с помощью языка R (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта часть 6 входит в состав [серии учебников по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), посвященной использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

В этом учебнике вы примените функции R для просмотра распределения значений по полу в столбце *creditLine*.

> [!div class="checklist"]
> * Создание переменных с минимальными и максимальными значениями для входных данных гистограммы
> * Визуализация данных на гистограмме с помощью функции **rxHistogram** из пакета **RevoScaleR**
> * Визуализация данных на точечных диаграммах с помощью функции **levelplot** из пакета **lattice**, входящего в состав базового дистрибутива R

Как показано в этом учебнике, в одном скрипте можно сочетать функции с открытым кодом и функции корпорации Майкрософт.

## <a name="add-maximum-and-minimum-values"></a>Добавление максимального и минимального значений

Изучив сводные статистические данные из предыдущего учебника, вы получили полезную информацию о данных, которые можно добавить в источник данных для последующих вычислений. Например, минимальное и максимальное значения можно использовать для построения гистограмм. В этом упражнении вы добавите максимальное и минимальное значения в источник данных **RxSqlServerData**.

1. Сначала создайте ряд временных переменных.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Используйте созданную в предыдущем учебнике переменную *ccColInfo* для определения столбцов в источнике данных.
  
   Добавьте новые вычисляемые столбцы (*numTrans*, *numIntlTrans* и *creditLine*) в коллекцию столбцов, переопределяющую исходное определение. Приведенный ниже скрипт добавляет коэффициенты на основе минимального и максимального значений, полученных из переменной sumOut, предназначенной для сохранения в памяти выходных данных из **rxSummary**. 
  
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
  
3. Обновив коллекцию столбцов, примените приведенную ниже инструкцию, чтобы создать обновленную версию источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который был определен ранее.
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    Теперь источник данных sqlFraudDS содержит новые столбцы, добавленные с помощью *ccColInfo*.
  
На данный момент эти изменения касаются только объекта источника данных в среде R; в таблицу базы данных новые данные еще не записаны. Однако данные, записанные в переменную sumOut, можно использовать для создания визуализаций и сводок. 

> [!TIP]
> Если вы не помните, какой контекст вычисления используете, выполните **rxGetComputeContext()** . Возвращаемое значение "RxLocalSeq Compute Context" указывает, что вы работаете в локальном контексте вычисления.

## <a name="visualize-data-using-rxhistogram"></a>Визуализация данных с помощью функций rxHistogram

1. Используйте следующий код R, чтобы вызвать функцию [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) и передать формулу и источник данных. Сначала эту операцию можно выполнить локально, чтобы оценить результаты и продолжительность.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Сама по себе функция **rxHistogram** вызывает функцию [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) , которая включена в пакет **RevoScaleR** . Функция **rxCube** выводит единый список (или кадр данных), который содержит по одному столбцу для каждой переменной, указанной в формуле, а также столбец counts.
    
2. Теперь задайте в качестве контекста вычисления удаленный компьютер SQL Server и выполните **rxHistogram** еще раз.
  
    ```R
    rxSetComputeContext(sqlCompute)
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
3. Результаты будут такими же, так как вы используете тот же источник данных. Однако на втором шаге вычисления выполняются на удаленном сервере. Затем результаты возвращаются на локальную рабочую станцию для построения графика.
   
  ![Результаты в виде гистограммы](media/rsql-sue-histogramresults.jpg "Результаты в виде гистограммы")


## <a name="visualize-with-scatter-plots"></a>Визуализация с помощью точечных диаграмм

Точечные диаграммы часто используются при исследовании данных для представления взаимосвязи между двумя переменными. Для этой цели можно использовать встроенные пакеты R с входными данными, предоставляемыми функциями **RevoScaleR**.

1. Вызовите функцию [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) для вычисления среднего значения *fraudRisk* для каждого сочетания значений *numTrans* и *numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Чтобы указать группы, используемые для вычисления средних значений по группам, используйте нотацию `F()` . В этом примере `F(numTrans):F(numIntlTrans)` указывает на то, что целочисленные значения переменных `numTrans` и `numIntlTrans` должны обрабатываться как категориальные переменные (каждое целочисленное значение имеет свой уровень).
  
    Возвращаемое значение **rxCube** по умолчанию является объектом *rxCube*, представляющим перекрестное табулирование. 
  
2. Вызовите функцию [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf), чтобы преобразовать результаты в кадр данных, который можно легко использовать в одной из стандартных функций формирования диаграмм языка R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    Функция **rxCube** имеет необязательный аргумент (*returnDataFrame* = **TRUE**), который можно использовать для преобразования результатов непосредственно в кадр данных. Пример:
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Однако выходные данные функции **rxResultsDF** более понятны, и в них сохраняются имена исходных столбцов. Вы можете выполнить `head(cube1)`, а затем `head(cubePlot)`, чтобы сравнить выходные данные.
  
3. Создайте тепловую карту с помощью функции **levelplot** из пакета **lattice**, который входит в состав всех дистрибутивов R.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Результаты**
  
    ![Результаты в виде точечной диаграммы](media/rsql-sue-scatterplotresults.jpg "Результаты в виде точечной диаграммы")
  
Выполнив такой быстрый анализ, можно заметить, что риск мошенничества растет с увеличением числа как обычных, так и международных транзакций.

Дополнительные сведения о функции **rxCube** и перекрестных таблицах в целом см. в статье [Сведение данных с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Создание моделей R с помощью данных SQL Server](../../advanced-analytics/tutorials/deepdive-create-models.md)