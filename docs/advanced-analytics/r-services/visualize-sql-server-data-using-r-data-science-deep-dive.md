---
title: "Визуализация данных SQL Server с помощью языка R (глубокое погружение в обработку и анализ данных) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 10def0b3-9b09-4df9-b8aa-69516f7d7659
caps.latest.revision: 14
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Визуализация данных SQL Server с помощью языка R (глубокое погружение в обработку и анализ данных)
Расширенные пакеты в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] включают несколько функций, которые оптимизированы для масштабируемости и параллельной обработки. Обычно эти функции начинаются с префикса *rx* или *Rx*.  
  
В этом пошаговом руководстве функция *rxHistogram* будет использоваться для просмотра распределения значений в столбце _creditLine_ по полу.  
  
## Визуализация данных с помощью функций rxHistogram и rxCube  
  
1.  Используйте следующий код R, чтобы вызвать функцию *rxHistogram* и передать формулу и источник данных. Сначала эту операцию можно выполнить локально, чтобы оценить результаты и продолжительность.
  
    ```R  
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")   
    ```  
 
    Сама по себе функция *rxHistogram* вызывает функцию *rxCube*, которая включена в пакет **RevoScaleR**. Функция *rxCube* создает один список (или кадр данных), в котором каждой заданной в формуле переменной отведен один столбец плюс столбец с указанием количества.
    
2. Теперь задайте в качестве контекста вычислений удаленный компьютер с SQL Server и запустите *rxHistogram* еще раз.
  
    ```R  
    rxSetComputeContext(sqlCompute)  
    ```  
 
3.    Результаты будут такими же, поскольку вы используете тот же источник данных; однако вычисления выполняются на компьютере с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Затем результаты возвращаются на локальную рабочую станцию для построения графика.  
   
![histogram results](../../advanced-analytics/r-services/media/rsql-sue-histogramresults.jpg "histogram results")  

  
4.  Можно также вызвать функцию *rxCube* и передать результаты функциям формирования диаграмм языка R.  Например, в следующем примере функция *rxCube* используется для вычисления среднего значения *fraudRisk* для каждого сочетания значений *numTrans* и *numIntlTrans*:  
  
    ```R  
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)   
    ```  
  
    Чтобы указать группы, используемые для вычисления средних значений по группам, используйте нотацию `F()`. В этом примере `F(numTrans):F(numIntlTrans)` указывает на то, что целочисленные значения переменных _numTrans_ и _numIntlTrans_ должны обрабатываться как категориальные переменные (каждое целочисленное значение имеет свой уровень).  
  
    Так как нижний и верхний уровни уже были добавлены в источник данных *sqlFraudDS* (параметром *colInfo*), уровни будут автоматически использоваться в гистограмме.  
  
5.  Возвращаемое значение *rxCube* по умолчанию является объектом *rxCube*, представляющим перекрестное табулирование. Однако при помощи функции *rxResultsDF* можно преобразовать результаты в кадр данных, который можно легко использовать в одной из стандартных функций формирования диаграмм языка R.  
  
    ```R  
    cubePlot <- rxResultsDF(cube1)   
    ```  
  
    > [!TIP]  
    > Обратите внимание, что функция *rxCube* имеет необязательный аргумент (*returnDataFrame* = TRUE), который можно использовать для преобразования результатов непосредственно в кадр данных. Например:  
    >   
    > `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`  
    >   
    > Однако выходные данные функции *rxResultsDF* более понятны, и в них сохраняются имена исходных столбцов.  
  
6.  Наконец, выполните приведенный ниже код, чтобы создать тепловую карту при помощи функции *levelplot* из пакета **lattice**, который входит в состав всех дистрибутивов R.  
  
    ```R  
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)   
    ```  
  
    **Результаты**  
  
    ![scatterplot results](../../advanced-analytics/r-services/media/rsql-sue-scatterplotresults.jpg "scatterplot results")  
  
Даже выполнив такой быстрый анализ, можно заметить, что риск мошенничества растет с увеличением как числа обычных транзакций, так и числа международных транзакций.

Дополнительные сведения о функции *rxCube* и перекрестных таблицах в целом см. в разделе [Сводки по данным](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries).  
  
## Следующий шаг  
[Создание моделей (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/create-models-data-science-deep-dive.md)  
  
## Предыдущий шаг  
[Занятие 2. Создание и выполнение скриптов R (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
## См. также:  
[Глубокое погружение в обработку и анализ данных: использование пакетов RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
