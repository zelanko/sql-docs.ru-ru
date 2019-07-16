---
title: Создание объектов данных SQL Server, с помощью функции RevoScaleR RxSqlServerData - машинного обучения SQL Server
description: Руководство по созданию объектов данных с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: b29f8136e3394c5424233ac3f966d2b6c0ad7bc0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962255"
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-server-and-revoscaler-tutorial"></a>Создание объектов данных SQL Server, с помощью функции RxSqlServerData (руководство по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Занятие 2 является продолжением создания базы данных: Добавление таблиц и загрузке данных. Если администратор базы данных создана база данных и входа в [урок один](deepdive-work-with-sql-server-data-using-r.md), можно добавить таблицы, с помощью R IDE, такую как RStudio или встроенные средства, как **Rgui**.

Из R, подключитесь к SQL Server и используйте **RevoScaleR** функции для выполнения следующей задачи:

> [!div class="checklist"]
> * Создание таблиц для обучающих данных и прогнозов
> * Загрузка таблицы данными из локальных CSV-файл

Образец данных данные имитации кредитной карты мошенничества (ccFraud набор данных), разделена обучения и оценки наборов данных. Файл данных включается в **RevoScaleR**.

Использование среды IDE R или **Rgui** для завершения этих taks. Обязательно используйте исполняемые файлы R, найден в этом расположении: C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64 (либо Rgui.exe при использовании этого средства или указывает на C:\Program Files\Microsoft\R Client\R_SERVER R IDE). Наличие [клиентской рабочей станции R](../r/set-up-a-data-science-client.md) с этими исполняемые файлы считается необходимым условием работы с этим руководством.

## <a name="create-the-training-data-table"></a>Создайте таблицу данных для обучения

1. Store строку подключения базы данных в переменной R. Ниже приведены два примера допустимых строк подключения ODBC для SQL Server: одна, с помощью имени входа SQL, а другая для встроенной проверки подлинности Windows. 

   Не забудьте изменить имя сервера, имя пользователя и пароль, соответствующим образом.

    **Имя входа SQL**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=<server-name>; Database=RevoDeepDive;Uid=<user_name>;Pwd=<password>"
    ```

    **Проверка подлинности Windows**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=<server-name>;Database=RevoDeepDive;Trusted_Connection=True"
    ```

2. Укажите имя таблицы, которую нужно создать, и сохраните его в переменной R.
  
    ```R
    sqlFraudTable <- "ccFraudSmall"
    ```
  
    Так как экземпляр сервера и имя базы данных уже указаны как часть строки подключения, при объединении этих двух переменных *полное* имя новой таблицы становится  *базы данных.схема.ccfraudsmall*.
  
3.  При необходимости укажите *rowsPerRead* для управления, сколько строк данных считывается в каждом пакете.
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    Несмотря на то, что этот параметр является необязательным, его установка может привести более обеспечения эффективных вычислений. Большинство расширенных аналитических функций в **RevoScaleR** и **MicrosoftML** обрабатывают данные блоками. *RowsPerRead* параметр определяет количество строк в каждом блоке.
  
    Может потребоваться поэкспериментировать с этим параметром, чтобы найти правильный баланс. Если значение слишком велико, доступ к данным может быть медленным, если не хватает памяти для обработки данных в виде фрагментов указанного размера. И наоборот, в некоторых системах Если значение *rowsPerRead* слишком мал, производительность может также замедлить.
  
    Как начальное значение используйте процесс размер пакета по умолчанию, задаваемый экземпляром компонента database engine для управления количеством строк в каждом блоке (5000 строк). Это значение сохраняется в переменной *sqlRowsPerRead*.
  
4.  Определите переменную для нового объекта источника данных и передайте ранее определенные аргументы **RxSqlServerData** конструктор. Обратите внимание, что при этом происходит только создание, но не заполнение объекта источника данных. Загрузка данных представляет собой отдельный шаг.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

## <a name="create-the-scoring-data-table"></a>Создание таблицы данных для оценки

Используя те же действия, создайте таблицу, содержащую данные для оценки, используя тот же процесс.

1. Создайте переменную R *sqlScoreTable*для хранения имени таблицы, используемой для оценки.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Передайте эту переменную в качестве аргумента в функцию **RxSqlServerData** , чтобы определить еще один объект источника данных *sqlScoreDS*.
  
    ```R
    sqlScoreDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Так как в качестве переменных в рабочем пространстве R уже определен строку подключения и другие параметры, его можно повторно использовать для новых источников данных, представляющий разных таблиц, представлений или запросов.

> [!NOTE]
> Эта функция использует разные аргументы для определения источника данных на основе всей таблицы, чем для источника данных, на основе запроса. Это так, как ядро СУБД SQL Server необходимо подготовить запросы по-разному. Далее в этом руководстве вы узнаете, как создать объект источника данных, на основе запроса SQL.

## <a name="load-data-into-sql-tables-using-r"></a>Загрузка данных в таблицы SQL, с помощью языка R

Теперь, когда вы создали таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , можете загрузить в них данные с помощью соответствующей функции **Rx** .

**RevoScaleR** пакет содержит функции, относящиеся к типам источников данных. Текстовые данные, использовать [RxTextData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata) для создания объекта источника данных. Имеются также дополнительные функции для создания объектов источников данных на основе Hadoop, ODBC и других типов данных.

> [!NOTE]
> Для этого раздела необходимо иметь **выполнение инструкции DDL** разрешения в базе данных.

### <a name="load-data-into-the-training-table"></a>Загрузка данных в таблицу для обучения

1. Создайте переменную R *ccFraudCsv*и присвойте переменной путь к CSV-файл, содержащий образец данных. Этот набор данных предоставляется в **RevoScaleR**. «sampleDataDir» включена ключевое слово **rxGetOption** функции.
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Обратите внимание, что вызов **rxGetOption**, метод GET связанный с [rxOptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions) в **RevoScaleR**. Используйте эту программу для установки и список параметров, связанных с контекстами локальных и удаленных вычислений, например общий каталог по умолчанию, или число процессоров (ядер), используемых в вычислениях.
    
    Этот конкретный вызов получает образцы из правильной библиотеки независимо от того, на котором выполняется ваш код. Например, запустите функцию на сервере SQL Server и на компьютере разработчика и посмотрите различия.
  
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
  
3. На этом этапе может потребоваться приостановить в данный момент и просмотреть базу данных в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Обновите список таблиц в базе данных.
  
    Вы увидите, что, несмотря на то, что объекты данных R были созданы в локальной рабочей области, таблицы не были созданы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных. Кроме того без загрузки данных из текстового файла в переменной R.
  
4. Вставьте данные путем вызова функции [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) функции.
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
    
    При отсутствии проблем со строкой подключения после небольшой паузы должны появиться результаты наподобие следующих:
  
    *Всего строк записано: 10000, общее время: 0,466* *считано строк: 10000, всего строк обработано: Время 10000, общее фрагмента: 0,577 секунды*
  
5. Обновите список таблиц. Чтобы убедиться, что каждая переменная имеет правильный тип данных и успешно импортирован, щелкните правой кнопкой мыши таблицу в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и выберите **выделить 1000 верхних строк**.

### <a name="load-data-into-the-scoring-table"></a>Загрузка данных в таблицу для анализа

1. Повторите шаги, чтобы загрузить набор данных, используемые для оценки в базу данных.
  
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
  
    - Если таблица уже существует, и вы не используете *перезаписать* параметр, результаты будут вставлены без усечения.
  
Если соединение установлено успешно, вы увидите сообщение, информирующее о завершении и указывающее время, необходимое для записи данных в таблицу:

*Всего строк записано: 10000, общее время: 0,384*
*считано строк: 10000, всего строк обработано: Время 10000, общее фрагмента: 0,456 секунды*

## <a name="more-about-rxdatastep"></a>Дополнительные сведения о функции rxDataStep

[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) — это мощная функция, которая позволяет производить различные преобразования кадра данных R. Можно также использовать rxDataStep для преобразования данных в представление, необходимого для целевой: в этом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

При необходимости можно указать преобразования данных, с помощью функций R в аргументах **rxDataStep**. Далее в этом руководстве приведены примеры этих операций.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Запрос и изменение данных SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)