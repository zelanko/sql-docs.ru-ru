---
title: "Визуализация данных SQL Server с помощью языка R (глубокое погружение в обработку и анализ данных) | Документация Майкрософт"
ms.custom: SQL2016_New_Updated
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 10def0b3-9b09-4df9-b8aa-69516f7d7659
caps.latest.revision: "14"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fa42e69f1e376dc528b3385ca3c4be38fea4710b
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="visualize-sql-server-data-using-r"></a>Визуализация данных SQL Server с помощью языка R

Расширенные пакеты в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] включают несколько функций, которые оптимизированы для масштабируемости и параллельной обработки. Обычно эти функции начинаются с префикса *rx* или *Rx*.

В этом пошаговом руководстве функция **rxHistogram** будет использоваться для просмотра распределения значений в столбце _creditLine_ по полу.

## <a name="visualize-data-using-rxhistogram"></a>Визуализация данных с помощью rxHistogram

1. Используйте следующий код R для вызова функции rxHistogram и передайте формулу и источник данных. Сначала эту операцию можно выполнить локально, чтобы оценить результаты и продолжительность.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    На внутреннем уровне rxHistogram вызывает функцию rxCube, который включен в **RevoScaleR** пакета. Функция rxCube выводит один список (или кадра данных) содержит один столбец для каждой переменной, указанным в формуле, плюс количество столбец.
    
2. Теперь задайте для контекста вычислений удаленный компьютер SQL Server и запустите rxHistogram.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
 
3. Результаты будут такими же, поскольку вы используете тот же источник данных; однако вычисления выполняются на компьютере с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Затем результаты возвращаются на локальную рабочую станцию для построения графика.
   
![Результаты в виде гистограммы](media/rsql-sue-histogramresults.jpg "Результаты в виде гистограммы")

4. Можно также вызвать функцию rxCube и передать результаты построения функцию R.  Например, в следующем примере rxCube для вычисления среднего значения *fraudRisk* для каждой комбинации *numTrans* и *numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Чтобы указать группы, используемые для вычисления средних значений по группам, используйте нотацию `F()` . В этом примере `F(numTrans):F(numIntlTrans)` указывает на то, что целочисленные значения переменных _numTrans_ и _numIntlTrans_ должны обрабатываться как категориальные переменные (каждое целочисленное значение имеет свой уровень).
  
    Так как нижний и верхний уровни уже были добавлены в источник данных *sqlFraudDS* (параметром *colInfo* ), уровни будут автоматически использоваться в гистограмме.
  
5. Возвращаемое значение rxCube — по умолчанию *rxCube объекта*, который представляет перекрестные таблицы. Однако при помощи функции **rxResultsDF** можно преобразовать результаты в кадр данных, который можно легко использовать в одной из стандартных функций формирования диаграмм языка R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    > [!TIP]
    > 
    > Обратите внимание, что функция rxCube включает необязательный аргумент, *returnDataFrame* = TRUE, что можно использовать для преобразования результатов в кадр данных напрямую. Например:
    >   
    > `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
    >   
    > Тем не менее выходные данные rxResultsDF гораздо проще и сохраняет имена столбцов источника.
  
6. Наконец, выполните следующий код для создания тепловой карты с помощью `levelplot` функции из **решетки** пакет, который входит в состав все R распределения.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Результаты**
  
    ![Результаты в виде точечной диаграммы](media/rsql-sue-scatterplotresults.jpg "Результаты в виде точечной диаграммы")
  
Даже выполнив такой быстрый анализ, можно заметить, что риск мошенничества растет с увеличением как числа обычных транзакций, так и числа международных транзакций.

Дополнительные сведения о функции rxCube и перекрестным в целом см. в разделе [сводок по данным](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries).

## <a name="next-step"></a>Следующий шаг

[Создание моделей](../../advanced-analytics/tutorials/deepdive-create-models.md)

## <a name="previous-step"></a>Предыдущий шаг

[Занятие 2. Создание и выполнение скриптов R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)


