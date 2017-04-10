---
title: "Просмотр и обобщение данных с помощью языка R (пошаговое руководство по обработке и анализу данных) | Microsoft Docs"
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
ms.assetid: 358e1431-8f47-4d32-a02f-f90e519eef49
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Просмотр и обобщение данных с помощью языка R (пошаговое руководство по обработке и анализу данных)
Теперь вы будете работать с теми же данными с помощью кода на языке R. Вы также научитесь использовать функции из пакета **RevoScaleR**, входящего в состав [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], для формирования сводок данных в контексте сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отправлять результаты обратно в среду R.  

К этому пошаговому руководству прилагается скрипт R, который содержит весь необходимый код для создания объекта данных, формирования сводок и построения моделей. Файл скрипта R **RSQL_RWalkthrough.R**находится в папке, в которой были установлены файлы скриптов.  
+ Если у вас есть опыт работы с языком R, можно выполнить скрипт сразу.
+ Для тех, кто учится использовать RevoScaleR, в этом руководстве скрипт разбит по строкам.
+ Для запуска отдельных строк из скрипта можно выделить строку или строки в файле и нажать клавиши CTRL+ВВОД.    
  
> [!TIP]  Если вы хотите завершить остальную часть пошагового руководства позднее, сохраните рабочее пространство R.  Таким образом объекты данных и другие переменные будут готовы для повторного использования.   

## <a name="defining-sql-server-data-sources-and-compute-contexts"></a>Определение источников данных и контекстов вычислений SQL Server
Чтобы получить данные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для использования в коде R, сделайте следующее:  
  
- Создайте подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
- Определите запрос, содержащий нужные данные, либо укажите таблицу или представление.    
- Определите один или несколько контекстов вычислений для использования при выполнении кода R.    
-   При необходимости определите функции, которые можно применить к источнику данных.  
 

### <a name="load-the-revoscaler-library"></a>Загрузка библиотеки RevoScaleR

+  Если пакет **RevoScaleR** еще не загружен, выполните следующую строку:
    ```R
    library("RevoScaleR")`.  
    ```  
    Если возникает ошибка, убедитесь в том, что в среде разработки R используется библиотека, включающая пакет RevoScaleR. Просмотрите текущий путь с помощью такой команды, как `.libPaths())`.  

    Если пакет **RevoScaleR** используется впервые, вы можете получить справку в среде R, введя команду `help("RevoScaleR")` или `help("RxSqlServerData")`.  

### <a name="create-connection-strings"></a>Создание строк подключения


1. Определите строки подключения. В этом пошаговом руководстве приведены примеры имен входа SQL и использования встроенной проверки подлинности Windows. Мы рекомендуем по возможности использовать проверку подлинности Windows, чтобы не сохранять пароли в коде R.

    Используемая учетная запись должна иметь разрешения на чтение данных и создание таблиц в указанной базе данных. Сведения о добавлении пользователей к базе данных SQL и назначении им соответствующих разрешений см. в разделе [Настройка сервера после установки (службы SQL Server R Services)](../Topic/Post-Installation%20Server%20Configuration%20(SQL%20Server%20R%20Services).md). 

    ```R  
    # SQL authentication  
    connStrSql <- "Driver=SQL Server;Server=<SQL_instance_name>;Database=<database_name>;    Uid=<user_name>;Pwd=<user password>"  

    # Windows authentication  
    connStrWin <- "Driver=SQL Server;Server=<SQL_instance_name>;Database=<database_name>;Trusted_Connection=Yes" 
    
    # Use one of the connection strings
    connStr <- connStrWin 
    ```
    > [!NOTE] Измените имя сервера, имя базы данных, имя пользователя и пароль на необходимые. 
      
  
### <a name="define-and-set-a-compute-context"></a>Определение и задание контекста вычислений  

Далее вы определите *контекст вычислений*, с помощью которого код R можно запустить на компьютере SQL Server. Как правило, при использовании языка R все операции выполняются в памяти вашего компьютера. Тем не менее, если указать, что операции R должны выполняться в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], некоторые задачи можно выполнять в параллельном режиме. При этом вы можете воспользоваться преимуществами ресурсов сервера.  

По умолчанию контекст вычислений является локальным. Поэтому в зависимости от операции его необходимо задавать явным образом.  


1.  Сначала нужно определить ряд переменных, которые служат для создания контекста вычисления.  
  
    ```R    
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")  
    sqlWait <- TRUE  
    sqlConsoleOutput <- FALSE    
    ```    
    -   R использует временный каталог при сериализации объектов R между рабочей станцией и компьютером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Вы можете указать локальный каталог, используемый в качестве *sqlShareDir*, или принять значение по умолчанию.  
  
    -   Используйте *sqlWait*, чтобы указать, нужно ли R ожидать результатов.  Описание заданий с ожиданием и без ожидания см. в статье [ScaleR Distributed Computing](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing) (Распределенные вычисления ScaleR).
  
    -   Используйте аргумент *sqlConsoleOutput*, чтобы указать, что не нужно выводить результаты из консоли R.  
  
2.  Создайте объект контекста вычислений с определенными переменными и строками подключения и сохраните его в переменной R *sqlcc*.  
  
    ```  
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir,   
                        wait = sqlWait, consoleOutput = sqlConsoleOutput)  
    ```  

4. Задайте контекст вычислений.
    ```R
    rxSetComputeContext(sqlcc)  
    ```  
   + `rxSetComputeContext` возвращает предыдущий скрытый активный контекст вычислений для дальнейшего использования.
   + `rxGetComputeContext` возвращает активный контекст вычислений.  
  
    Обратите внимание, что задание контекста вычислений влияет только на операции, использующие функции из пакета **RevoScaleR**. Контекст вычислений не влияет на то, как выполняются операции R с открытым исходным кодом.  
  
### <a name="create-an-rxsqlserver-data-object"></a>Создание объекта данных RxSqlServer  

Определив подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которым вы будете работать, можно использовать этот объект подключения к данным в качестве основы для определения различных источников данных. *Источник данных* определяет некоторый набор данных, который нужно использовать для задания, например для обучения, изучения, оценки или создания функций.  
    
Наборы данных SQL Server можно определить, использовав функцию *RxSqlServer* и передав строку подключения и определение данных для получения.  
  
1. Сохраните инструкцию SQL в качестве строковой переменной. Этот запрос определяет данные, которые будут использоваться для обучения модели.    
    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, 
           passenger_count,trip_time_in_secs,trip_distance,   
           pickup_datetime, dropoff_datetime, pickup_longitude, 
           pickup_latitude, dropoff_longitude,    
           dropoff_latitude 
           FROM nyctaxi_sample"  
    ```

2. Передайте определение запроса в качестве аргумента в источник данных SQL Server. Аргумент *colClasses* определяет схему данных, которые следует вернуть, путем сопоставления SQL. 

    ```R  
    inDataSource <- RxSqlServerData(sqlQuery = sampleDataQuery, 
         connectionString = connStr,
         colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
         dropoff_longitude = "numeric", dropoff_latitude = "numeric"),  
         rowsPerRead=500)  
    ```
    
    + Аргумент *colClasses* определяет типы столбцов, используемые при переносе данных между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и средой R. Это важно, так как в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются типы данных, отличные от типов данных R, и этих типов больше. Дополнительные сведения см. в разделе [Работа с типами данных R](../../advanced-analytics/r-services/working-with-r-data-types.md).  
  
    + Аргумент *rowsPerRead* важен для управления использованием памяти и обеспечения эффективных вычислений.  Большинство расширенных аналитических функций в[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] обрабатывают данные блоками и накапливают промежуточные результаты, возвращая итоговые результаты вычислений после считывания всех данных.  Добавив параметр `rowsPerRead` , можно управлять тем, сколько строк данных считывается в каждый обрабатываемый блок.  Если значение этого параметра слишком велико, доступ к данным может замедлиться из-за нехватки памяти для эффективной обработки такого большого блока данных.  В некоторых системах слишком малое значение параметра `rowsPerRead` также может снизить производительность.  

> [!TIP] После создания объекта данных *inDataSource* его можно применять сколько угодно раз для получения основных сведений об используемых данных и переменных, выполнения операций с данными и их преобразования, а также для обучения модели.  Тем не менее в объекте *inDataSource* пока отсутствуют данные из SQL-запроса. Данные не переносятся в локальную среду, пока не будут выполнены такие функции, как *rxImport* или *rxSummary*.          
  
## <a name="using-the-sql-server-data-in-r"></a>Использование данных SQL Server в R  
Теперь к источнику данных можно применять функции R для изучения данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , формирования сводок и построения диаграмм на их основе. В этом разделе вы испытаете несколько функций, имеющихся в службах [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] , которые поддерживают удаленные контексты вычисления.  
  
-   `rxGetVarInfo`. Эту функцию можно использовать с любым кадром или набором данных в удаленном объекте данных (а также с некоторыми списками и матрицами) для получения таких сведений, как максимальное и минимальное значения, тип данных и число уровней в столбцах факторов.  
  
    Ее рекомендуется использовать после любой операции ввода данных, преобразования функций или создания функций. Таки образом можно гарантировать, что все функции, которые необходимо использовать в модели, имеют требуемый тип данных, и избежать ошибок.  
 
  
-   `rxSummary`. С помощью этой функции можно получить более подробную статистику по отдельным переменным. Вы также можете преобразовывать значения, вычислять сводки с помощью уровней факторов и сохранять сводки для повторного использования.  
  
  
### <a name="inspect-variables-in-the-data-source"></a>Просмотр переменных в источнике данных  
    
+ Вызовите функцию `rxGetVarInfo`, используя источник данных  `inDataSource` в качестве аргумента, чтобы получить список переменных в источнике данных и их типы данных.  
  
    ```R  
    rxGetVarInfo(data = inDataSource)  
    ```  
  
    *Результаты:*  
    *Var 1: tipped, тип: integer*  
    *Var 2: fare_amount, тип: numeric*  
    *Var 3: passenger_count, тип: integer*  
    *Var 4: trip_time_in_secs, тип: numeric, Storage: int64*  
    *Var 5: trip_distance, тип: numeric*  
    *Var 6: pickup_datetime, тип: character*  
    *Var 7: dropoff_datetime, тип: character*  
    *Var 8: pickup_longitude, тип: numeric*  
    *Var 9: pickup_latitude, тип: numeric*  
    *Var 10: dropoff_longitude, тип: numeric*  
  
### <a name="create-a-summary-using-r"></a>Создание отчета с помощью R

+ Вызовите функцию RevoScaleR `rxSummary`, чтобы создать сводку по размеру оплаты на основе количества пассажиров. 
    ```R  
    start.time <- proc.time()  
    rxSummary(~fare_amount:F(passenger_count), data = inDataSource)  
    used.time <- proc.time() - start.time  
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2), 
      " seconds to summarize the inDataSource.", sep=""))
    ```  
 
    + Первый аргумент `rxSummary` определяет формулу или термин, по которому создается сводка. Здесь функция `F()` используется для преобразования значений в passenger_count в факторы перед созданием сводки.  
    + Если не указать выводимые статистические данные, по умолчанию функция `rxSummary` выводит Mean, StDev, Min, Max, а также число допустимых и отсутствующих наблюдений.  
    + В этом примере также есть код для отслеживания времени начала и завершения выполнения функции, что позволяет сравнить производительность.  
  
    *Результаты*  
    *rxSummary(formula = ~fare_amount:F(passenger_count), data = inDataSource)*  
    *Сводные статистические результаты для: ~fare_amount:F(passenger_count)*  
    *Данные: inDataSource (RxSqlServerData Data Source)*  
    *Число допустимых наблюдений: 1000*   
    *Name                          Mean    StdDev   Min Max ValidObs MissingObs*  
    *fare_amount:F_passenger_count 12.4875 9.682605 2.5 64  1000     0*   
    *Статистика по категориям (6 категорий):   *Category                             F_passenger_count Means    StdDev    Min*   
    *fare_amount for F(passenger_count)=1 1                 12.00901  9.219458  2.5*  
    *fare_amount for F(passenger_count)=2 2                 11.61893  8.858739  3.0*  
    *fare_amount for F(passenger_count)=3 3                 14.40196 10.673340  3.5*  
    *fare_amount for F(passenger_count)=4 4                 13.69048  8.647942  4.5*  
    *fare_amount for F(passenger_count)=5 5                 19.30909 14.122969  3.5*  
    *fare_amount for F(passenger_count)=6 6                 12.00000        NA 12.0*  
    *Max ValidObs*  
    *55  666*   
    *52  206*   
    *52   51*   
    *39   21*   
    *64   55*   
    *12    1*   
    *"Затрачено времени ЦП=0,5 с, Прошло времени=4,59 с для создания сводки по inDataSource."*  
  

  
## <a name="next-step"></a>Следующий шаг  
[Создание диаграмм и графиков с помощью R (пошаговое руководство по обработке и анализу данных)](../../advanced-analytics/r-services/create-graphs-and-plots-using-r-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Предыдущее занятие  
[Занятие 1. Подготовка данных (пошаговое руководство по обработке и анализу данных)](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
