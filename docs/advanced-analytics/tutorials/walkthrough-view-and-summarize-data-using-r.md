---
title: Просмотр и анализ данных SQL Server, с помощью функций R - машинного обучения SQL Server
description: Учебник, в котором показано, как визуализировать и создать статистические сводки, использование функций R для анализа в базе данных в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 368caa21545e534c393aca29ce8fd3a59f9d9837
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53644563"
---
# <a name="view-and-summarize-sql-server-data-using-r-walkthrough"></a>Просмотр и анализ данных SQL Server, с помощью языка R (Пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом уроке рассматривается функций в **RevoScaleR** пакета, а также действия по следующие задачи:

> [!div class="checklist"]
> * Подключение к SQL Server
> * Определите запрос, содержащий нужные данные, либо укажите таблицу или представление.
> * определить один или несколько контекстов вычислений для использования при выполнении кода R;
> * При необходимости определите преобразований, применяемых к источнику данных во время чтения из источника

## <a name="define-a-sql-server-compute-context"></a>Определение контекста вычислений SQL Server

Выполните следующие инструкции R в среде R на клиентской рабочей станции. В этом разделе предполагается [рабочую станцию обработки и анализа данных с помощью Microsoft R Client](../r/set-up-a-data-science-client.md), так как он включает все пакеты RevoScaleR, а также базовый "," упрощенный набор средств R. Например Rgui.exe можно использовать для выполнения сценария r. в этом разделе.

1. Если **RevoScaleR** пакет не загружен, запустите эту строку кода R:

    ```R
    library("RevoScaleR")
    ```

     Кавычки являются необязательными, таким образом, хотя рекомендуется.
     
     Если отобразится сообщение об ошибке, убедитесь, что среду разработки R используется библиотека, включающая пакет RevoScaleR. Например, используйте команду `.libPaths()` Чтобы просмотреть текущий путь к библиотеке.

2. Создайте строку подключения для SQL Server и сохраните его в переменной r. *connStr*.

   Заполнитель «имя_вашего_сервера» необходимо изменить на допустимое имя экземпляра SQL Server. Для имени сервера можно использовать только имя экземпляра, или может потребоваться полное имя, в зависимости от вашей сети.
    
   Для проверки подлинности SQL Server синтаксис соединения выглядит следующим образом:

    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Uid=your-sql-login;Pwd=your-login-password"
    ```

    Для проверки подлинности Windows синтаксис немного отличается:
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Trusted_Connection=True"
    ```

    Как правило рекомендуется использовать проверку подлинности Windows, где это возможно, чтобы не сохранять пароли в коде R.

3. Определите переменные для использования при создании нового *контекста вычислений*. После создания объекта контекста вычислений, его можно использовать для запуска кода R в экземпляре SQL Server.

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - R использует временный каталог при сериализации объектов R между рабочей станцией и компьютером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Вы можете указать локальный каталог, используемый в качестве *sqlShareDir*, или принять значение по умолчанию.
  
    - Используйте *sqlWait* для указания, нужно ли R ожидать результатов с сервера.  Описание ожидания и без ожидания заданий, см. в разделе [распределенные и параллельные вычисления с помощью RevoScaleR в Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).
  
    - Используйте аргумент *sqlConsoleOutput* для указания, что вы не хотите просмотреть выходные данные консоли R.

4. Вы вызываете [RxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver) конструктор для создания объекта контекста вычислений с переменными и строками подключения и сохраните новый объект в переменной R *sqlcc*.
  
    ```R
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

5. По умолчанию контекст вычислений является локальным. Поэтому необходимо явно задать *active* контекста вычислений.

    ```R
    rxSetComputeContext(sqlcc)
    ```

    + [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) незаметно возвращает предыдущий активный контекст вычисления, которые можно использовать
    + [rxGetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) возвращает активный контекст вычисления
    
    Обратите внимание на то, что задание контекста вычислений влияет только на операции, использующие функции из **RevoScaleR** пакета; он не влияет на контекст, как выполняются операции R открытым исходным кодом.

## <a name="create-a-data-source-using-rxsqlserver"></a>Создать источник данных, с помощью RxSqlServer

При использовании библиотек Microsoft R, как RevoScaleR и MicrosoftML, *источника данных* — это объект, созданный с помощью функций RevoScaleR. Объект источника данных определяет некоторый набор данных, который вы хотите использовать для задач, таких как модели обучения или извлечение признаков. Можно получить данные из различных источников, включая SQL Server. Список поддерживаемых в настоящее время источников, см. в разделе [RxDataSource](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource).

Ранее определенные строки подключения и сохранили сведения в переменной R. Кроме того, можно повторно использовать сведения о подключении для указания данных, что вы хотите получить.

1. Сохраните запрос SQL как строковую переменную. Запрос определяет данные для обучения модели.

    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

    Мы использовали предложение TOP, чтобы заставить все работать быстрее, но фактические строки, возвращаемые запросом, зависит от порядка. Таким образом сводки результатов, также может отличаться от перечисленных ниже. Вы можете удалить предложение TOP.

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
  
    + Аргумент *rowsPerRead* важен для управления использованием памяти и обеспечения эффективных вычислений.  Большинство расширенных аналитических функций в[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] обрабатывают данные блоками и накапливают промежуточные результаты, возвращая итоговые результаты вычислений после считывания всех данных.  Добавив *rowsPerRead* параметр, можно указать, сколько строк данных считывается в каждый обрабатываемый блок.  Если значение этого параметра слишком велико, доступ к данным может снижаться, поскольку у вас нет достаточно памяти для эффективной обработки такого большого блока данных.  В некоторых системах установка *rowsPerRead* слишком маленькое значение может обеспечить снижение производительности.

3. На этом этапе вы создали *inDataSource* объект, но он не содержит никаких данных. Данные не извлекаются из SQL-запроса в локальную среду до запуска функции, такие как [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) или [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary).

    Однако теперь, когда вы определили объекты данных, можно использовать его в качестве аргумента для других функций.

## <a name="use-the-sql-server-data-in-r-summaries"></a>Использование данных SQL Server в R сводки

В этом разделе вы испытаете несколько функций, предоставленных в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] , которые поддерживают удаленные контексты вычисления. Применение функций R к источнику данных, можно изучить, суммировать и диаграммы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных.

1. Вызовите функцию [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) для получения списка переменных в источнике данных и их типы данных.

    **rxGetVarInfo** является удобную функцию; его можно вызвать для любой кадр данных или на набор данных в удаленном объекте данных, чтобы получить сведения, такие как минимальное и максимальное значения, тип данных, а также количество уровней в столбцах факторов.
    
    Ее рекомендуется использовать после любой операции ввода данных, преобразования функций или создания функций. Таким образом, можно убедитесь, что все функции, которые вы хотите использовать в модели ожидаемые данные введите и избежать ошибок.
  
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

2. Теперь вызовите функцию RevoScaleR [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary) можно получить более подробную статистику по отдельным переменным.

    rxSummary основан на R `summary` работать, но имеет некоторые дополнительные возможности и преимущества. rxSummary работает в нескольких контекстах вычислений и поддерживает фрагментацию.  Можно также использовать rxSummary для преобразования значения или суммировать основаны на уровне идентификации.
    
    В этом примере необходимо создать сводку по на основе количества пассажиров.
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + Первый аргумент rxSummary определяет формулу или термин, чтобы получить сводку по. Здесь `F()` функция используется для преобразования значений в _пассажиров\_число_ в факторы перед созданием сводки. Также необходимо указать минимальное значение (1) и максимальное значение (6) для _пассажиров\_число_ фактором в переменной.
    + Если вы не укажете статистические данные, по умолчанию rxSummary выводит Mean, StDev, Min, Max и число допустимых и отсутствующих наблюдений.
    + В этом примере также есть код для отслеживания времени начала и завершения выполнения функции, что позволяет сравнить производительность.
  
    **Результаты**

    Если функция rxSummary выполняется успешно, вы увидите результаты наподобие следующих, за которым следует список статистических данных по категориям. 

    ```R
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    ```

### <a name="bonus-exercise-on-big-data"></a>Дополнительное упражнение для больших данных

Попробуйте определение строку запроса со всеми строками. Мы рекомендуем настроить новый объект источника данных для этого эксперимента. Можно также попытаться изменение *rowsToRead* параметр, чтобы увидеть, как это влияет на пропускную способность.

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
> Пока выполняется, можно использовать такой инструмент, как [Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) или SQL Profiler, чтобы увидеть, каким образом будет предоставляться подключение и код R выполняется с использованием служб SQL Server.
> 
> Другой вариант — для отслеживания заданий R в SQL Server, используя эти [пользовательские отчеты](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Создание диаграмм и графиков с помощью языка R](walkthrough-create-graphs-and-plots-using-r.md)