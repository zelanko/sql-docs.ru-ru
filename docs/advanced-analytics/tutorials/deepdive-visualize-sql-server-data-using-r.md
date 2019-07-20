---
title: Визуализация данных SQL Server с помощью RevoScaleR rxHistogram
description: Пошаговое руководство по визуализации данных с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 210fade2820c53ba585043827e7e3d2c36315319
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344651"
---
#  <a name="visualize-sql-server-data-using-r-sql-server-and-revoscaler-tutorial"></a>Визуализация SQL Server данных с помощью R (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [учебника RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом занятии используйте функции R для просмотра распределения значений в столбце *creditLine* по полу.

> [!div class="checklist"]
> * Создание переменных min-max для входных данных гистограммы
> * Визуализация данных в гистограмме с помощью **rxHistogram** из **RevoScaleR**
> * Визуализация с точечными диаграммами с помощью **levelplot** из **Lattice** , входящей в базовое распределение R

Как показано на этом занятии, можно сочетать функции с открытым исходным кодом и корпорацией Майкрософт в одном скрипте.

## <a name="add-maximum-and-minimum-values"></a>Добавление максимальных и минимальных значений

На основе вычисленной сводной статистики из предыдущего занятия были обнаружены полезные сведения о данных, которые можно вставить в источник данных для последующих вычислений. Например, для вычислений гистограмм можно использовать минимальное и максимальное значения. В этом упражнении добавьте значения High и Low в источник данных **RxSqlServerData** .

1. Сначала создайте ряд временных переменных.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Используйте переменную *ccColInfo* , созданную на предыдущем занятии, чтобы определить столбцы в источнике данных.
  
   Добавьте новые вычисляемые столбцы (*numTrans*, *numIntlTrans*и *creditLine*) в коллекцию столбцов, которая переопределяет исходное определение. Приведенный ниже скрипт добавляет коэффициенты на основе минимального и максимального значений, полученных из sumOut, который сохраняет выходные данные в памяти из **rxSummary**. 
  
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
  
3. После обновления коллекции столбцов примените следующую инструкцию, чтобы создать обновленную версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных, которая была определена ранее.
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    Источник данных sqlFraudDS теперь включает новые столбцы, добавленные с помощью *ccColInfo*.
  
На этом этапе изменения затрагивают только объект источника данных в R; новые данные еще не записаны в таблицу базы данных. Однако можно использовать данные, захваченные в переменной sumOut, для создания визуализаций и сводок. 

> [!TIP]
> Если вы забыли, какой контекст вычислений вы используете, запустите **рксжеткомпутеконтекст ()** . Возвращаемое значение "Ркслокалсек вычислений context" указывает, что вы работаете в локальном контексте вычислений.

## <a name="visualize-data-using-rxhistogram"></a>Визуализация данных с помощью rxHistogram

1. Используйте следующий код R, чтобы вызвать функцию [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) и передать формулу и источник данных. Сначала эту операцию можно выполнить локально, чтобы оценить результаты и продолжительность.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Сама по себе функция **rxHistogram** вызывает функцию [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) , которая включена в пакет **RevoScaleR** . **rxCube** выводит один список (или кадр данных), содержащий один столбец для каждой переменной, указанной в формуле, а также столбец счетчиков.
    
2. Теперь задайте для контекста вычислений удаленный SQL Server компьютер и снова запустите **rxHistogram** .
  
    ```R
    rxSetComputeContext(sqlCompute)
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
3. Результаты идентичны, так как используется один и тот же источник данных, но на втором шаге вычисления выполняются на удаленном сервере. Затем результаты возвращаются на локальную рабочую станцию для построения графика.
   
  ![Результаты в виде гистограммы](media/rsql-sue-histogramresults.jpg "Результаты в виде гистограммы")


## <a name="visualize-with-scatter-plots"></a>Визуализация с точечными диаграммами

Точечные диаграммы часто используются при исследовании данных для сравнения связи между двумя переменными. Для этой цели можно использовать встроенные пакеты R с входными данными, предоставленными функциями **RevoScaleR** .

1. Вызовите функцию [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) , чтобы вычислить среднее значение *fraudRisk* для каждого сочетания *numTrans* и *numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Чтобы указать группы, используемые для вычисления средних значений по группам, используйте нотацию `F()` . В этом примере `F(numTrans):F(numIntlTrans)` указывает, что целые числа в переменных `numTrans` и `numIntlTrans` должны рассматриваться как переменные категории с уровнем для каждого целочисленного значения.
  
    Возвращаемое по умолчанию значение **rxCube** — это *объект rxCube*, представляющий перекрестную табличку. 
  
2. Вызовите функцию [рксресултсдф](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) , чтобы преобразовать результаты в кадр данных, который можно легко использовать в одной из стандартных функций построения диаграмм на языке R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    Функция **rxCube** включает необязательный аргумент, *ретурндатафраме* = **true**, который можно использовать для преобразования результатов непосредственно в кадр данных. Пример:
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Однако выходные данные **рксресултсдф** являются понятными и сохраняют имена исходных столбцов. После этого можно `head(cube1)` выполнить команду `head(cubePlot)` , чтобы сравнить выходные данные.
  
3. Создайте тепловую карту с помощью функции **levelplot** из пакета **Lattice** , который входит в состав всех дистрибутивов R.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Результаты**
  
    ![Результаты в виде точечной диаграммы](media/rsql-sue-scatterplotresults.jpg "Результаты в виде точечной диаграммы")
  
С помощью этого краткого анализа можно увидеть, что риск мошенничества увеличивается вместе с количеством транзакций и числом международных транзакций.

Дополнительные сведения о функции **rxCube** и подобную перекрестным в целом см. в разделе [сводки данных с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Создание моделей R с помощью SQL Server данных](../../advanced-analytics/tutorials/deepdive-create-models.md)