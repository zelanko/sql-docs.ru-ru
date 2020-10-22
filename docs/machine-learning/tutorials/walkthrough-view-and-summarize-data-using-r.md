---
title: Учебник по R. Анализ данных
description: В этом учебнике показано, как визуализировать и формировать статистические сводки с помощью функций R для аналитики в базе данных в SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7e48e25444acc2f84794afc487c95bdd5af64f30
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195076"
---
# <a name="view-and-summarize-sql-server-data-using-r-walkthrough"></a>Просмотр и сведение данных SQL Server с помощью R (пошаговое руководство)
[!INCLUDE [SQL Server 2016](../../includes/applies-to-version/sqlserver2016.md)]

На этом занятии приводятся сведения о функциях в пакете **RevoScaleR** и даются пошаговые инструкции по выполнению следующих задач.

> [!div class="checklist"]
> * Подключение к SQL Server
> * Определите запрос, содержащий нужные данные, либо укажите таблицу или представление.
> * определить один или несколько контекстов вычислений для использования при выполнении кода R;
> * При необходимости определение преобразований, применяемых к источнику данных во время чтения из источника.

## <a name="define-a-sql-server-compute-context"></a>Определение контекста вычислений SQL Server

Выполните следующие инструкции R в среде R на клиентской рабочей станции. В этом разделе предполагается, что используется [рабочая станция для обработки и анализа данных с Microsoft R Client](../r/set-up-a-data-science-client.md), так как она включает все пакеты RevoScaleR, а также базовый, упрощенный набор средств R. Например, для выполнения скрипта R в этом разделе можно использовать Rgui.exe.

1. Если пакет **RevoScaleR** еще не загружен, выполните следующую строку кода R:

    ```R
    library("RevoScaleR")
    ```

     В нашем примере кавычки не обязательны, хотя и рекомендуются.
     
     Если возникает ошибка, убедитесь, что используемая в среде разработки R библиотека содержит пакет RevoScaleR. Увидеть текущий путь к библиотеке можно с помощью такой команды, как `.libPaths()`.

2. Создайте строку подключения для SQL Server и сохраните ее в переменной R *connStr*.

   Необходимо заменить заполнитель "your_server_name" на допустимое имя экземпляра SQL Server. В зависимости от сети в качестве имени сервера может быть разрешено использовать только имя экземпляра, но может требоваться и указание полного имени.
    
   Для проверки подлинности SQL Server используется следующий синтаксис подключения:

    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Uid=your-sql-login;Pwd=your-login-password"
    ```

    Для проверки подлинности Windows синтаксис немного отличается:
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Trusted_Connection=True"
    ```

    Рекомендуется по возможности использовать проверку подлинности Windows, чтобы не сохранять пароли в коде R.

3. Определите переменные, которые будут использоваться при создании нового *контекста вычислений*. После создания объекта контекста вычислений его можно использовать для выполнения кода R в экземпляре SQL Server.

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - R использует временный каталог при сериализации объектов R между рабочей станцией и компьютером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Вы можете указать локальный каталог, используемый в качестве *sqlShareDir*, или принять значение по умолчанию.
  
    - С помощью *sqlWait* можно указать, следует ли R ожидать результаты с сервера.  Обсуждение заданий с ожиданием и без ожидания см. в статье [Распределенные и параллельные вычисления с помощью RevoScaleR в Microsoft R](/r-server/r/how-to-revoscaler-distributed-computing).
  
    - С помощью аргумента *sqlConsoleOutput* укажите, что не нужно выводить результаты на консоли R.

4. Далее вызывается конструктор [RxInSqlServer](/r-server/r-reference/revoscaler/rxinsqlserver) для создания объекта контекста вычислений с уже заданными переменными и строками подключения, и этот новый объект сохраняется в переменной R *sqlcc*.
  
    ```R
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

5. По умолчанию контекст вычислений является локальным. Поэтому *активный* контекст вычислений необходимо задавать явным образом.

    ```R
    rxSetComputeContext(sqlcc)
    ```

    + [rxSetComputeContext](/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) скрыто возвращает предыдущий активный контекст вычислений для дальнейшего использования;
    + [rxGetComputeContext](/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) возвращает активный контекст вычислений.
    
    Обратите внимание, что задание контекста вычислений влияет только на операции, использующие функции из пакета **RevoScaleR**. Контекст вычислений не влияет на то, как выполняются операции R с открытым исходным кодом.

## <a name="create-a-data-source-using-rxsqlserver"></a>Создание источника данных с помощью RxSqlServer

При использовании таких библиотек Microsoft R, как RevoScaleR и MicrosoftML, *источник данных*  является объектом, создаваемым с помощью функций RevoScaleR. Объект источника данных определяет некоторый набор данных, который требуется использовать для задачи, например, для обучения модели или извлечения функций. Вы можете получать данные из множества разных источников, включая SQL Server. Список поддерживаемых в настоящее время источников см. в разделе [RxDataSource](/r-server/r-reference/revoscaler/rxdatasource).

Ранее вы определили строку подключения и сохранили эту информацию в переменной R. Эти сведения о подключении можно использовать многократно для указания данных, которые требуется получить.

1. Сохраните SQL-запрос в виде строковой переменной. Этот запрос определяет данные для обучения модели.

    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

    Здесь используется предложение TOP, чтобы ускорить выполнение, но фактические строки, возвращаемые запросом, могут отличаться в зависимости от порядка. Таким образом, сводные результаты тоже могут отличаться от приведенных ниже. При желании предложение TOP можно удалить.

2. Передайте определение запроса в качестве аргумента в функцию [RxSqlServerData](/r-server/r-reference/revoscaler/rxsqlserverdata).

    ```R
    inDataSource <- RxSqlServerData(
      sqlQuery = sampleDataQuery,
      connectionString = connStr,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
      dropoff_longitude = "numeric", dropoff_latitude = "numeric"),
      rowsPerRead=500
      )
    ```
    
    + Аргумент  *colClasses* определяет типы столбцов, используемые при переносе данных между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и средой R. Это важно, так как в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются типы данных, отличные от типов данных R, и этих типов больше. Дополнительные сведения см. в разделе [Библиотеки R и типы данных](../r/r-libraries-and-data-types.md).
  
    + Аргумент *rowsPerRead* важен для управления использованием памяти и обеспечения эффективных вычислений.  Большинство расширенных аналитических функций в[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] обрабатывают данные блоками и накапливают промежуточные результаты, возвращая итоговые результаты вычислений после считывания всех данных.  С помощью параметра *rowsPerRead* можно управлять количеством строк данных, считываемых в каждый блок для обработки.  Если значение этого параметра слишком велико, доступ к данным может замедлиться из-за нехватки памяти для эффективной обработки такого большого блока данных.  В некоторых системах слишком низкое значение параметра *rowsPerRead* также может снизить производительность.

3. На данном этапе объект *inDataSource* создан, но в нем отсутствуют какие-либо данные. Данные не переносятся из SQL-запроса в локальную среду, пока не будут выполнены такие функции, как [rxImport](/r-server/r-reference/revoscaler/rxdatastep) или [rxSummary](/r-server/r-reference/revoscaler/rxsummary).

    Однако теперь, когда объект данных определен, его можно использовать в качестве аргумента в других функциях.

## <a name="use-the-sql-server-data-in-r-summaries"></a>Использование данных SQL Server в сводках R

В этом разделе вы попробуете использовать несколько функций, имеющихся в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], которые поддерживают удаленные контексты вычислений. Применяя функции R к источнику данных, можно исследовать данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], формировать сводки и строить диаграммы на их основе.

1. Вызовите функцию [rxGetVarInfo](/r-server/r-reference/revoscaler/rxgetvarinfo), чтобы получить список переменных в источнике данных и их типы данных.

    Функция **rxGetVarInfo** очень удобна; ее можно вызывать с любым кадром или набором данных в удаленном объекте данных для получения таких сведений, как максимальные и минимальные значения, тип данных и число уровней в столбцах факторов.
    
    Ее рекомендуется использовать после любой операции ввода данных, преобразования функций или создания функций. Таким образом можно обеспечить требуемый тип данных всех компонентов, которые планируется использовать в модели, и избежать ошибок.
  
    ```R
    rxGetVarInfo(data = inDataSource)
    ```

    **Результаты**
    
    ```R
    Var 1: tipped, Type: integer
    Var 2: fare_amount, Type: numeric
    Var 3: passenger_count, Type: integer
    Var 4: trip_time_in_secs, Type: numeric, Storage: int64
    Var 5: trip_distance, Type: numeric
    Var 6: pickup_datetime, Type: character
    Var 7: dropoff_datetime, Type: character
    Var 8: pickup_longitude, Type: numeric
    Var 9: pickup_latitude, Type: numeric
    Var 10: dropoff_longitude, Type: numeric
    ```

2. Теперь вызовите функцию [rxSummary](/r-server/r-reference/revoscaler/rxsummary) из пакета RevoScaleR для получения более подробной статистики по отдельным переменным.

    Функция rxSummary построена на функции R `summary`, но имеет некоторые дополнительные возможности и преимущества. rxSummary работает в нескольких контекстах вычислений и поддерживает фрагментирование.  Можно также использовать rxSummary для преобразования значений или подведения итогов на основе уровней коэффициентов.
    
    В данном примере создается сводка по размеру оплаты в зависимости от количества пассажиров.
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + Первый аргумент rxSummary определяет формулу или термин, по которому создается сводка. Здесь с помощью функции `F()` выполняется преобразование значений из _passenger\_count_ в коэффициенты перед созданием сводки. Необходимо также указать минимальное (1) и максимальное (6) значения для переменной коэффициента _passenger\_count_.
    + Если не указать статистические данные для вывода, по умолчанию функция rxSummary выводит Mean, StDev, Min, Max, а также число допустимых и пропущенных наблюдений.
    + В этом примере также есть код для отслеживания времени начала и завершения выполнения функции, что позволяет сравнить производительность.
  
    **Результаты**

    Если функция rxSummary выполняется успешно, вы должны увидеть результаты, подобные приведенным ниже, за которыми следует список статистических данных по категориям. 

    ```R
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    ```

### <a name="bonus-exercise-on-big-data"></a>Дополнительное упражнение с большими данными

Попробуйте задать новую строку запроса со всеми записями. Для этого эксперимента рекомендуется настроить новый объект источника данных. Можно также попробовать изменить параметр *rowsToRead*, чтобы посмотреть, как он влияет на пропускную способность.

```R
bigDataQuery  <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"

bigDataSource <- RxSqlServerData(
      sqlQuery = bigDataQuery,
      connectionString = connStr,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
      dropoff_longitude = "numeric", dropoff_latitude = "numeric"),
      rowsPerRead=500
      )

start.time <- proc.time()
rxSummary(~fare_amount:F(passenger_count,1,6), data = bigDataSource)
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
  Elapsed Time=", round(used.time[3],2),
  " seconds to summarize the inDataSource.", sep=""))
```

> [!TIP]
> Пока это выполняется, вы можете использовать такой инструмент, как [Process Explorer](/sysinternals/downloads/process-explorer) или SQL Profiler, чтобы с помощью служб SQL Server увидеть, как устанавливается соединение, и как выполняется код R.

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Создание диаграмм и графиков с помощью языка R](walkthrough-create-graphs-and-plots-using-r.md)