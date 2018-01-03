---
title: "Создание объектов данных SQL Server с помощью RxSqlServerData (SQL и R глубокое погружение) | Документы Microsoft"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: bcf5f7ff-795b-4815-b163-bcddd496efce
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 82522664c8e5ba3d8c8046413abe68133a738828
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-and-r-deep-dive"></a>Создание объектов данных SQL Server с помощью RxSqlServerData (SQL и R глубокое погружение)

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

К этому моменту вы создали [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных и иметь соответствующие разрешения для работы с данными. На этом шаге можно создать некоторые объекты в R, которые позволяют работать с данными.

## <a name="create-the-sql-server-data-objects"></a>Создание объектов данных SQL Server

На этом шаге можно использовать функции в **RevoScaleR** пакетов для создания и заполнения двух таблиц. Одна таблица используется для обучения моделей, а другая — для анализа. Обе таблицы содержат вымышленные данные по мошенническим операциям с кредитными картами.

Для создания таблиц на удаленном [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера, вызовите **RxSqlServerData** функции.

> [!TIP]
> Если вы используете средства R для Visual Studio, выберите **Средства R** на панели инструментов и щелкните **Windows** , чтобы открыть параметры для отладки и просмотра переменных R.

### <a name="create-the-training-data-table"></a>Создание таблицы данных для обучения

1. Сохраните строку подключения базы данных в переменной R. Ниже приведены два примера допустимые строки подключения ODBC для SQL Server: один, с помощью имени входа SQL и один для встроенной проверки подлинности Windows.

    **Имя входа SQL**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name; Database=DeepDive;Uid=user_name;Pwd=password"
    ```

    **Проверка подлинности Windows**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"
    ```

    Измените имя экземпляра, имя базы данных, имя пользователя и пароль на нужные.
  
2. Укажите имя таблицы, которую нужно создать, и сохраните его в переменной R.
  
    ```R
    sqlFraudTable <- "ccFraudSmall"
    ```
  
    Так как имена экземпляра и базы данных уже указаны в строке подключения, при объединении этих двух переменных *полное* имя новой таблицы принимает вид _имя экземпляра.имя базы данных.схема.ccFraudSmall_.
  
3.  Перед созданием экземпляра объекта источника данных добавьте строку, в которой указывается дополнительный параметр *rowsPerRead*.  Параметр *rowsPerRead* управляет тем, сколько строк данных считывается в каждый пакет.
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    Хотя этот параметр необязателен, он важен для управления использованием памяти и обеспечения эффективных вычислений.  Большинство расширенных аналитических функциях в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] данные фрагментами обработки и хранения промежуточных результатов, возврат окончательного вычисления после того как все данные уже считаны.
  
    Если значение этого параметра слишком велико, доступ к данным может замедлиться из-за нехватки памяти для эффективной обработки такого большого блока данных.  Если значение параметра *rowsPerRead* в некоторых системах слишком мало, возможно снижение производительности. Таким образом рекомендуется поэкспериментировать с этим параметром в системе при работе с большим набором данных.
  
    В этом пошаговом руководстве используется процесс размер пакета по умолчанию, определяемый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра для управления числом строк в каждом блоке. Сохранить его в переменной `sqlRowsPerRead`.
  
4.  Наконец Определите переменную для нового объекта источника данных и передачи аргументов, определенных ранее в конструктор RxSqlServerData. Обратите внимание, что при этом происходит только создание, но не заполнение объекта источника данных.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

#### <a name="to-create-the-scoring-data-table"></a>Создание таблицы с данными для анализа

Используя те же шаги, создайте таблицу, содержащую оценки данных, используя тот же процесс.

1. Создайте переменную R *sqlScoreTable*для хранения имени таблицы, используемой для оценки.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Предоставить эту переменную в качестве аргумента функции RxSqlServerData для определения второй объект источника данных, *sqlScoreDS*.
  
    ```R
    sqlScoreDS \<- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Так как уже определен как переменные в рабочую область R строки подключения и других параметров, легко создавать новые источники данных для разных таблиц, представлений и запросов.

> [!NOTE]
> Эта функция использует разные аргументы для определения источника данных на основе всей таблицы, чем для источника данных на основе запроса. Это так, как ядро СУБД SQL Server необходимо подготовить запросы по-разному. Далее в этом учебнике вы узнаете, как для создания объекта источника данных на основе запроса SQL.

## <a name="load-data-into-sql-tables-using-r"></a>Загрузка данных в таблицы SQL, с помощью R

Теперь, когда вы создали таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , можете загрузить в них данные с помощью соответствующей функции **Rx** .

**RevoScaleR** пакет содержит функции, поддерживающие множества различных источников данных: текстовые данные, используйте [RxTextData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata) для создания объекта источника данных. Имеются также дополнительные функции для создания объектов источников данных на основе Hadoop, ODBC и других типов данных.

> [!NOTE]
> Для этого раздела необходимо иметь **выполнение инструкции DDL** разрешения в базе данных.

### <a name="load-data-into-the-training-table"></a>Загрузка данных в таблицу обучения

1. Создайте переменную R *ccFraudCsv*и присвоить переменной путь к файлу для CSV-файл, содержащий данные образца.
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Обратите внимание, вызов **rxGetOption**, которой метод GET связан с [rxOptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions) в **RevoScaleR**. Используйте эту программу для установки и список параметров, связанных с локальных и удаленных вычислений контекстов, например общий каталог по умолчанию, или число процессоров (ядра), используемых в вычислениях.
    
    Этот конкретный вызов возвращает образцы из правильная библиотека, независимо от того, на котором выполняется код. Например, запустите функцию на сервере SQL Server и на компьютере разработчика и посмотрите различия.
  
2. Определите переменную для хранения новых данных и используйте функцию **RxTextData** , чтобы указать источник текстовых данных.
  
    ```R
    inTextData <- RxTextData(file = ccFraudCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer",
        "fraudRisk" = "integer"))
    ```
  
    Аргумент *colClasses* важен. С его помощью указывается тип данных, который назначается каждому столбцу данных, загружаемому из текстового файла. В этом примере все столбцы обрабатываются как текстовые, кроме именованных столбцов, которые обрабатываются как целочисленные.
  
3. На этом этапе может потребоваться приостановить немного и просмотреть базу данных в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  Обновите список таблиц в базе данных.
  
    Вы увидите, что, несмотря на то, что были созданы объекты данных R в локальной рабочей области, таблицы не были созданы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных. Кроме того данные не была загружена из текстового файла в переменную R.
  
4. Теперь вызовите функцию [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) , чтобы вставить данные в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
  
    При отсутствии проблем со строкой подключения после небольшой паузы должны появиться результаты наподобие следующих:
  
      *Всего строк записано: 10000, Общее время: 0,466*

      *Строк считано: 10000, Всего строк обработано: 10000, Общее время фрагмента: 0,577 секунды*
  
5. С помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]обновите список таблиц. Чтобы убедиться в каждой переменной имеет типов данных и успешно импортирован, щелкните правой кнопкой мыши таблицу в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и выберите **выделить 1000 верхних строк**.

### <a name="load-data-into-the-scoring-table"></a>Загрузка данных в таблицу оценки

1. Повторите шаги, чтобы загрузить набор данных, используемых для оценки в базу данных.
  
    Сначала укажите путь к исходному файлу.
  
    ```R
    ccScoreCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudScoreSmall.csv")
    ```
  
2. Используйте функцию **RxTextData** , чтобы получить данные и сохранить их в переменной *inTextData*.
  
    ```R
    inTextData <- RxTextData(file = ccScoreCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer"))
    ```
  
3.  Вызовите функцию **rxDataStep** , чтобы перезаписать текущую таблицу, используя новую схему и данные.
  
    ```R
    rxDataStep(inData = inTextData, sqlScoreDS, overwrite = TRUE)
    ```
  
    - Аргумент *inData* определяет используемый источник данных.
  
    - Аргумент *outFile* определяет таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в которой нужно сохранить данные.
  
    - Если таблица уже существует, и вы не используете *перезаписать* параметр, результаты вставляются без усечения.
  
Если соединение установлено успешно, вы увидите сообщение, информирующее о завершении и указывающее время, необходимое для записи данных в таблицу:

*Всего строк записано: 10000, Общее время: 0,384*

*Строк считано: 10000, Всего строк обработано: 10000, Общее время фрагмента: 0,456 секунды*

## <a name="more-about-rxdatastep"></a>Дополнительные сведения о функции rxDataStep

[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) — это мощная функция, можно выполнять несколько преобразований на кадр данных R. Можно также использовать rxDataStep для преобразования данных в представление, необходимые для назначения: в этом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

При необходимости можно указать преобразования данных, с помощью функций R в аргументах **rxDataStep**. Далее в этом учебнике приведены примеры этих операций.

## <a name="next-step"></a>Следующий шаг

[Запрос и изменение данных SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)

## <a name="previous-step"></a>Предыдущий шаг

[Работа с данными SQL Server с помощью R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)
