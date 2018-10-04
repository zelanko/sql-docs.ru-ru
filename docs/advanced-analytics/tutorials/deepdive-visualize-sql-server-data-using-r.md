---
title: Визуализация данных SQL Server, с помощью языка R (SQL и R глубокое погружение в обработку) | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0d34ece68c421dbb7aabd845e117c9f07e00d013
ms.sourcegitcommit: 2420c57d2952add3697dbe0467ee1d755c5c2ee5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47217519"
---
#  <a name="visualize-sql-server-data-using-r-sql-and-r-deep-dive"></a>Визуализация данных SQL Server, с помощью языка R (SQL и R глубокое погружение в обработку)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья входит углубленное рассмотрение обработки и анализа данных руководства по использованию [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Расширенные пакеты в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] включают несколько функций, которые оптимизированы для масштабируемости и параллельной обработки. Обычно эти функции начинаются с префикса **rx** или **Rx**.

В этом пошаговом руководстве используется **rxHistogram** функцию, чтобы просмотреть распределение значений в _creditLine_ столбца по полу.

## <a name="visualize-data-using-rxhistogram"></a>Визуализация данных с помощью rxHistogram

1. Используйте следующий код R, чтобы вызвать функцию [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) и передать формулу и источник данных. Сначала эту операцию можно выполнить локально, чтобы оценить результаты и продолжительность.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Сама по себе функция **rxHistogram** вызывает функцию [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) , которая включена в пакет **RevoScaleR** . **rxCube** выводит один список (или кадр данных) содержит по одному столбцу для каждой переменной, указанной в формуле, а также столбец counts.
    
2. Теперь задайте контекст вычислений на удаленный компьютер SQL Server и запустите **rxHistogram** еще раз.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
 
3. Результаты будут такими же, поскольку вы используете тот же источник данных; однако вычисления выполняются на компьютере с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Затем результаты возвращаются на локальную рабочую станцию для построения графика.
   
![Результаты в виде гистограммы](media/rsql-sue-histogramresults.jpg "Результаты в виде гистограммы")

4. Можно также вызвать **rxCube** функции и передать результаты построения диаграмм функция R.  Например, в следующем примере функция **rxCube** используется для вычисления среднего значения *fraudRisk* для каждого сочетания значений *numTrans* и *numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Чтобы указать группы, используемые для вычисления средних значений по группам, используйте нотацию `F()` . В этом примере `F(numTrans):F(numIntlTrans)` указывает, что целочисленные значения переменных `numTrans` и `numIntlTrans` следует рассматривать как категориальные переменные с уровнем каждое целочисленное значение.
  
    Так как нижний и верхний уровни уже были добавлены к источнику данных `sqlFraudDS` (с помощью `colInfo` параметр), уровни автоматически используются в гистограмме.
  
5. Возвращаемое значение по умолчанию **rxCube** — *rxCube объекта*, который представляет перекрестное табулирование. Однако при помощи функции [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) можно преобразовать результаты в кадр данных, который можно легко использовать в одной из стандартных функций формирования диаграмм языка R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    **RxCube** функция имеет необязательный аргумент, *returnDataFrame* = **TRUE**, что можно использовать для преобразования результатов в кадр данных напрямую. Пример:
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Однако выходные данные функции **rxResultsDF** более понятны, и в них сохраняются имена исходных столбцов.
  
6. Наконец, выполните следующий код, чтобы создать тепловую карту с помощью `levelplot` функции из **lattice** пакет, который входит в состав всех дистрибутивов r.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Результаты**
  
    ![Результаты в виде точечной диаграммы](media/rsql-sue-scatterplotresults.jpg "Результаты в виде точечной диаграммы")
  
Даже выполнив такой быстрый анализ, можно заметить, что риск мошенничества растет с увеличением как числа обычных транзакций, так и числа международных транзакций.

Дополнительные сведения о **rxCube** функции и перекрестных таблицах в целом, см. в разделе [сводки данных, с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-step"></a>Следующий шаг

[Создание моделей R, используя данные SQL Server](../../advanced-analytics/tutorials/deepdive-create-models.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание и выполнение скриптов R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
