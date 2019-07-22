---
title: Просмотр и обобщение данных SQL Server с помощью функций R
description: Руководство, в котором показано, как визуализировать и формировать статистические сводки с помощью функций R для аналитики в базе данных в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 52ba1a8f036037ade42c8483b1735c84cc72867e
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345783"
---
# <a name="view-and-summarize-sql-server-data-using-r-walkthrough"></a>Просмотр и обобщение данных SQL Server с помощью языка R (пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом занятии рассказывается о функциях в пакете **RevoScaleR** и описываются следующие задачи.

> [!div class="checklist"]
> * Подключение к SQL Server
> * Определите запрос, содержащий нужные данные, либо укажите таблицу или представление.
> * определить один или несколько контекстов вычислений для использования при выполнении кода R;
> * При необходимости определите преобразования, применяемые к источнику данных при его считывании из источника.

## <a name="define-a-sql-server-compute-context"></a>Определение SQL Server контекста вычислений

Выполните следующие инструкции R в среде R на клиентской рабочей станции. В этом разделе предполагается [Рабочая станция обработки и анализа данных с Microsoft R Client](../r/set-up-a-data-science-client.md), так как она включает все пакеты RevoScaleR, а также базовый, упрощенный набор средств R. Например, можно использовать RGUI. exe для выполнения скрипта R в этом разделе.

1. Если пакет **RevoScaleR** еще не загружен, выполните следующую строку кода R:

    ```R
    library("RevoScaleR")
    ```

     В нашем примере кавычки являются необязательными, хотя и рекомендуется.
     
     При возникновении ошибки убедитесь, что среда разработки R использует библиотеку, содержащую пакет RevoScaleR. Используйте команду, например `.libPaths()` , для просмотра текущего пути к библиотеке.

2. Создайте строку подключения для SQL Server и сохраните ее в переменной R *коннстр*.

   Необходимо изменить заполнитель "your_server_name" на допустимое имя экземпляра SQL Server. В качестве имени сервера можно использовать только имя экземпляра, иначе в зависимости от сети может потребоваться полное имя.
    
   Для SQL Server проверки подлинности используется следующий синтаксис соединения:

    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Uid=your-sql-login;Pwd=your-login-password"
    ```

    Для проверки подлинности Windows синтаксис имеет несколько отличий.
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Trusted_Connection=True"
    ```

    Как правило, рекомендуется по возможности использовать проверку подлинности Windows, чтобы не сохранять пароли в коде R.

3. Определите переменные для использования при создании нового *контекста вычислений*. После создания объекта контекста вычислений его можно использовать для выполнения кода R на экземпляре SQL Server.

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - R использует временный каталог при сериализации объектов R между рабочей станцией и компьютером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Вы можете указать локальный каталог, используемый в качестве *sqlShareDir*, или принять значение по умолчанию.
  
    - Используйте *sqlWait* , чтобы указать, должен ли R ожидать результаты на сервере.  Обсуждение ожидающих и неожидающих заданий см. в статье [распределенные и параллельные вычисления с помощью RevoScaleR в Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).
  
    - Используйте аргумент *sqlConsoleOutput* , чтобы указать, что вы не хотите видеть выходные данные в консоли R.

4. Конструктор [RxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver) вызывается для создания объекта контекста вычислений с уже определенными переменными и строками подключения и сохранения нового объекта в переменной R *sqlcc*.
  
    ```R
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

5. По умолчанию контекст вычислений является локальным, поэтому необходимо явно задать *Активный* контекст вычислений.

    ```R
    rxSetComputeContext(sqlcc)
    ```

    + [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) возвращает невидимый ранее активный контекст вычислений, чтобы его можно было использовать
    + [рксжеткомпутеконтекст](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) Возвращает активный контекст вычислений
    
    Обратите внимание, что установка контекста вычислений влияет только на операции, использующие функции в пакете **RevoScaleR** . контекст вычислений не влияет на способ выполнения операций R с открытым кодом.

## <a name="create-a-data-source-using-rxsqlserver"></a>Создание источника данных с помощью RxSqlServer

При использовании таких библиотек Microsoft R, как RevoScaleR и MicrosoftML, *источник данных* — это объект, создаваемый с помощью функций RevoScaleR. Объект источника данных определяет некоторый набор данных, которые необходимо использовать для задачи, например обучение модели или извлечение компонентов. Вы можете получать данные из различных источников, включая SQL Server. Список поддерживаемых в настоящее время источников см. в разделе [рксдатасаурце](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource).

Ранее вы определили строку подключения и сохранили эту информацию в переменной R. Эти сведения о соединении можно повторно использовать для указания данных, которые необходимо получить.

1. Сохранение SQL-запроса в виде строковой переменной. Запрос определяет данные для обучения модели.

    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

    Мы использовали предложение TOP, чтобы сделать работу быстрее, но фактические строки, возвращаемые запросом, могут различаться в зависимости от порядка. Таким образом, результаты сводных данных также могут отличаться от перечисленных ниже. Вы можете удалить предложение TOP.

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
  
    + Аргумент *rowsPerRead* важен для управления использованием памяти и эффективных вычислений.  Большинство расширенных аналитических функций в[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] обрабатывают данные блоками и накапливают промежуточные результаты, возвращая итоговые результаты вычислений после считывания всех данных.  Добавив параметр *rowsPerRead* , можно управлять тем, сколько строк данных считывается в каждый блок для обработки.  Если значение этого параметра слишком велико, доступ к данным может оказаться слишком большим из-за отсутствия достаточного объема памяти для эффективной обработки такого большого фрагмента данных.  В некоторых системах установка *rowsPerRead* на чрезмерно небольшое значение может также обеспечить более низкую производительность.

3. На этом этапе вы создали объект *DataSource* , но он не содержит данных. Данные не извлекаются из SQL-запроса в локальную среду до тех пор, пока не будет выполнена функция, например [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) или [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary).

    Однако теперь, когда вы определили объекты данных, их можно использовать в качестве аргумента для других функций.

## <a name="use-the-sql-server-data-in-r-summaries"></a>Использование данных SQL Server в сводках R

В этом разделе вы исследуете несколько функций, предоставляемых в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] , поддерживающих удаленные контексты вычислений. Применяя функции R к источнику данных, можно просматривать, суммировать и запланировать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данные.

1. Вызовите функцию [функцию rxgetvarinfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) , чтобы получить список переменных в источнике данных и их типы данных.

    **функцию rxgetvarinfo** — это удобная функция; его можно вызвать для любого кадра данных или для набора данных в удаленном объекте данных, чтобы получить такие сведения, как максимальное и минимальное значения, тип данных и число уровней в столбцах коэффициента.
    
    Ее рекомендуется использовать после любой операции ввода данных, преобразования функций или создания функций. Это позволит гарантировать, что все функции, которые вы хотите использовать в модели, имеют ожидаемый тип данных и избежать ошибок.
  
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

2. Теперь вызовите функцию RevoScaleR [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary) , чтобы получить более подробную статистику по отдельным переменным.

    rxSummary основан на функции R `summary` , но обладает некоторыми дополнительными функциями и преимуществами. rxSummary работает в нескольких контекстах вычислений и поддерживает фрагментацию.  Можно также использовать rxSummary для преобразования значений или суммирования на основе уровней коэффициента.
    
    В этом примере вы суммируете сумму FARE на основе числа пассажиров.
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + Первый аргумент для rxSummary указывает формулу или термин, по которому производится суммирование. Здесь функция используется для преобразования значений в _пассажиров\_Count_ в факторы перед обобщением. `F()` Кроме того, необходимо указать минимальное значение (1) и максимальное значение (6) для переменной коэффициента _числа пассажиров\__ .
    + Если статистика не указана для вывода, по умолчанию rxSummary выходные данные имеют значение, StDev, min, Max и число допустимых и пропущенных наблюдений.
    + В этом примере также есть код для отслеживания времени начала и завершения выполнения функции, что позволяет сравнить производительность.
  
    **Результаты**

    Если функция rxSummary выполняется успешно, должны отобразиться такие результаты, за которыми следует список статистических данных по категориям. 

    ```R
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    ```

### <a name="bonus-exercise-on-big-data"></a>Премиальные упражнения на большие данные

Попробуйте определить новую строку запроса со всеми строками. Мы рекомендуем настроить новый объект источника данных для этого эксперимента. Вы также можете попробовать изменить параметр *ровстореад* , чтобы увидеть, как он влияет на пропускную способность.

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
> Во время выполнения этого действия можно использовать такие средства, как [Обозреватель процессов](https://technet.microsoft.com/sysinternals/processexplorer.aspx) или приложение SQL Profiler, чтобы узнать, как устанавливается соединение и код R выполняется с помощью SQL Server Services.
> 
> Другой вариант — мониторинг заданий R, выполняемых на SQL Server с помощью [пользовательских отчетов](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Создание диаграмм и графиков с помощью языка R](walkthrough-create-graphs-and-plots-using-r.md)