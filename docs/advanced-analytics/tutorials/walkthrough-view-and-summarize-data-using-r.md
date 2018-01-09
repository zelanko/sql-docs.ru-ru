---
title: "Просмотр и сведение данных с помощью R (Пошаговое руководство) | Документы Microsoft"
ms.date: 11/10/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 358e1431-8f47-4d32-a02f-f90e519eef49
caps.latest.revision: "22"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 86042ab737cf4471fa4286e44d12b40061289b04
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="view-and-summarize-data-using-r"></a>Просмотр и сведение данных с помощью R

Теперь давайте работать с теми же данными, с помощью кода R. На этом занятии вы узнаете, как использовать функции в **RevoScaleR** пакета.

К этому пошаговому руководству прилагается скрипт R, который содержит весь необходимый код для создания объекта данных, формирования сводок и построения моделей. Файл скрипта R **RSQL_RWalkthrough.R**находится в папке, в которой были установлены файлы скриптов.

+ Если у вас есть опыт работы с языком R, можно выполнить скрипт сразу.
+ Для людей, обучение работе с RevoScaleR этот учебник проходит через сценарий по одной строке.
+ Для запуска отдельных строк из скрипта можно выделить строку или строки в файле и нажать клавиши CTRL+ВВОД.

> [!TIP]
> Если вы хотите завершить остальную часть пошагового руководства позднее, сохраните рабочее пространство R.  В этом случае объекты данных и другие переменные готовы для повторного использования.

## <a name="define-a-sql-server-compute-context"></a>Определение контекста вычислений SQL Server

Microsoft R позволяет легко получать данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для использования в коде R. Применяется следующая обработка.
  
- Создайте подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
- Определите запрос, содержащий нужные данные, либо укажите таблицу или представление.
- определить один или несколько контекстов вычислений для использования при выполнении кода R;
- Также можно определите преобразования, которые применяются к источнику данных во время чтения из источника

Следующие шаги являются составными частями кода R и следует запускать в среде R. Мы использовали клиент Microsoft R, поскольку он включает все пакеты RevoScaleR, а также основные, упрощенный набор средств R.

1. Если **RevoScaleR** пакета не уже загружен, запустите эту строку кода R:

    ```R
    library("RevoScaleR")
    ```

     Кавычки являются необязательными, таким образом, хотя это рекомендуется.
     
     Возникает сообщение об ошибке, убедитесь, что среде разработки R использует библиотеку, которая содержит пакет RevoScaleR. Использовать команды, такие как `.libPaths()` Чтобы просмотреть текущий путь к библиотеке.

2. Создание строки подключения для SQL Server и сохраните его в переменной R _connStr_.
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=Your_Database_Name;Uid=Your_User_Name;Pwd=Your_Password"
    ```

    Для имени сервера можно использовать только имя экземпляра, или может потребоваться указать полное имя, в зависимости от сети.

    Для проверки подлинности Windows синтаксис немного отличается.
    
    ```R
    connStr <- "Driver=SQL Server;Server=SQL_instance_name;Database=database_name;Trusted_Connection=Yes"
    ```

    Скрипт R, доступный для загрузки, использует только имена входа SQL. Как правило рекомендуется использовать проверку подлинности Windows, где это возможно избежать хранение паролей в коде R. Тем не менее чтобы убедиться, что код в этом учебнике соответствует коды, загруженные из Github, мы будем использовать имя входа SQL для остальной части пошагового руководства.

3. Определение переменных, используемых для создания нового _контекста вычислений_. После создания объекта контекста вычислений, его можно использовать для выполнения кода R в экземпляре SQL Server.

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - R использует временный каталог при сериализации объектов R между рабочей станцией и компьютером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Вы можете указать локальный каталог, используемый в качестве *sqlShareDir*, или принять значение по умолчанию.
  
    - Используйте *sqlWait* для указания, следует ли R ожидания результатов от сервера.  Описание ожидания и без ожидания заданий см. в разделе [распределенных и параллельных вычислений с ScaleR в Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).
  
    - Используйте аргумент *sqlConsoleOutput* для указания, что вы не хотите увидеть результаты из консоли R:.


4. Можно вызвать [RxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver) конструктор для создания объекта контекста вычислений с переменными и строки подключения, которые уже определены и сохраните новый объект в переменной R *sqlcc*.
  
    ```R
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

5. По умолчанию контекст вычислений является локальным, поэтому необходимо явно задать *active* контекста вычислений.

    ```R
    rxSetComputeContext(sqlcc)
    ```

    + `rxSetComputeContext` возвращает предыдущий скрытый активный контекст вычислений для дальнейшего использования.
    + `rxGetComputeContext` возвращает активный контекст вычислений.
    
    Обратите внимание, что задание контекста вычислений влияет только на операции, использующие функции из пакета **RevoScaleR** . Контекст вычислений не влияет на то, как выполняются операции R с открытым исходным кодом.

## <a name="create-a-data-source-using-rxsqlserver"></a>Создать источник данных с помощью RxSqlServer

В Microsoft R *источника данных* — это объект, созданный с помощью функции RevoScaleR. Объект источника данных указывает некоторый набор данных, который вы хотите использовать для задачи, такие как модель извлечения обучающих или компонента. Можно получить данные из различных источников; Список поддерживаемых источников см. в разделе [RxDataSource](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource).

Ранее определенная строка соединения и сохранить эти данные в переменной R. Можно повторно использовать сведения о подключении для указания данных, что вы хотите получить.

1. Сохранение запроса SQL строковой переменной. Запрос определяет данные для обучения модели.

    ```R
    sampleDataQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

    Мы использовали предложение TOP, чтобы упростить выполняются быстрее, но зависит от порядка фактических строк, возвращаемых запросом. Таким образом Сводка результатов, также может отличаться от перечисленных ниже. Вы можете удалить предложение TOP.

2. Передайте определение запроса в качестве аргумента в функцию [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata).

    ```R
    inDataSource <- RxSqlServerData(
      sqlQuery = sampleDataQuery,
      connectionString = connStr,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
      dropoff_longitude = "numeric", dropoff_latitude = "numeric"),
      rowsPerRead=500
      )
    ```
    
    + Аргумент  *colClasses* определяет типы столбцов, используемые при переносе данных между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и средой R. Это важно, так как в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются типы данных, отличные от типов данных R, и этих типов больше. Дополнительные сведения см. в разделе [библиотеки R и типы данных](../r/r-libraries-and-data-types.md).
  
    + Аргумент *rowsPerRead* важно для управления памятью и эффективный вычислений.  Большинство расширенных аналитических функций в[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] обрабатывают данные блоками и накапливают промежуточные результаты, возвращая итоговые результаты вычислений после считывания всех данных.  Добавив *rowsPerRead* параметр, можно выбрать, сколько строк данных считываются в каждом блоке для обработки.  Если значение этого параметра слишком велико, доступ к данным может замедлиться из-за нехватки памяти для эффективной обработки такого большого блока данных.  В некоторых системах параметр *rowsPerRead* слишком малое значение также может предоставить более низкую производительность.

3. На этом этапе вы создали *inDataSource* , но не содержит никаких данных. Данные не изымается из SQL-запроса в локальной среде до запуска функции, такие как [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) или [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary).

    Однако теперь, когда вы определили объекты данных, можно использовать его в качестве аргумента для других функций.

## <a name="use-the-sql-server-data-in-r-summaries"></a>Использование данных SQL Server в R сводки

В этом разделе вы познакомитесь несколько функций, предоставляемых в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] контексты, поддержка удаленных вычислений. Применение функций R в источник данных, можно исследовать, обобщения и диаграммы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных.

1. Вызовите функцию [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) для получения списка переменных в источнике данных и их типы данных.

    **rxGetVarInfo** является функцией под рукой; его можно вызвать для любой кадр данных или на наборе данных в объекте удаленных данных, чтобы получить сведения, такие как минимальное и максимальное значения, тип данных и количество уровней в столбцах коэффициент.
    
    Ее рекомендуется использовать после любой операции ввода данных, преобразования функций или создания функций. Таким образом, можно убедитесь, что все компоненты, которые вы хотите использовать в модели находятся ожидаемые данные типа и избежать ошибок.
  
    ```R
    rxGetVarInfo(data = inDataSource)
    ```

    **Результаты**
    
    ```
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

2. Теперь, вызовите функцию RevoScaleR [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary) для получения более подробной статистики об отдельных переменных.

    rxSummary основан на R `summary` работать, но имеет некоторые дополнительные функции и преимущества. rxSummary работает в нескольких контекстах вычислений и поддерживает фрагментации.  Можно также использовать rxSummary для преобразования значений или обрабатывать на основе коэффициент уровней.
    
    В этом примере приведены тариф авиакомпании сумма, основанная на количество пассажиров.
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + Первый аргумент rxSummary указывает формулы или термин для подведения итогов с. Здесь `F()` функция используется для преобразования значения в _пассажира\_число_ в факторы перед суммирования. Также необходимо указать минимальное значение (1) и максимальное значение (6) для _пассажира\_число_ коэффициент переменной.
    + Если статистика для вывода не указан, по умолчанию rxSummary выводит среднее, StDev, Min, Max и число допустимых и отсутствуют наблюдений.
    + В этом примере также есть код для отслеживания времени начала и завершения выполнения функции, что позволяет сравнить производительность.
  
    **Результаты**

    В случае успешного выполнения функции rxSummary должны быть получены результаты, подобные, за которым следует список статистических данных по категориям. 

    ```
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    ```

### <a name="bonus-exercise-on-big-data"></a>Дополнительное упражнение на большие наборы данных

Попробуйте определение строку запроса со всеми строками. Мы рекомендуем настроить новый объект источника данных в этом эксперименте. Можно также попытаться изменение *rowsToRead* параметр, чтобы увидеть, как влияет на пропускную способность.

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
> Пока выполняется, можно воспользоваться инструментом [Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) или приложения SQL Profiler, чтобы увидеть, каким образом будет предоставляться соединения и код R выполняется с помощью служб SQL Server.
> 
> Другой вариант — для наблюдения за R заданий, выполняемых на сервере SQL Server, с их помощью [пользовательские отчеты](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="next-lesson"></a>Следующее занятие

[Создание диаграмм и графиков с помощью языка R](walkthrough-create-graphs-and-plots-using-r.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Изучение данных с использованием SQL](walkthrough-view-and-explore-the-data.md)
