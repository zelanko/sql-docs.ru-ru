---
title: Создание объектов RxSqlServerData
description: Учебник по RevoScaleR, часть 2. Сведения о том, как создавать объекты данных с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7869fc3fc67cb24542223c2300cd7b6ebcf1eb41
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76922573"
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-server-and-revoscaler-tutorial"></a>Создание объектов данных SQL Server с помощью функции RxSqlServerData (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта часть 2 входит в состав [серии учебников по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), посвященной использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

В этом учебнике мы продолжим создавать базу данных: добавим таблицы и загрузим данные. Если администратор базы данных создал базу данных и выполнил вход, как описано в [первом уроке](deepdive-work-with-sql-server-data-using-r.md), вы сможете добавить таблицы с помощью интегрированной среды разработки R, например RStudio, или встроенного средства, такого как **Rgui**.

Из R подключитесь к SQL Server и используйте функции **RevoScaleR** для выполнения следующих задач.

> [!div class="checklist"]
> * Создание таблиц для обучающих данных и прогнозов
> * Загрузка таблиц с данными из локального CSV-файла

Демонстрационные данные моделируют данные о мошенничестве с кредитными картами (набор данных ccFraud), которые разделены на обучающие и оценочные наборы данных. Файл данных включен в **RevoScaleR**.

Для выполнения этих задач используйте интегрированную среду разработки R или **Rgui**. Не забудьте использовать исполняемые файлы R в этом расположении: C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64 (Rgui.exe, если вы используете это средство, или R IDE, указывающий на C:\Program Files\Microsoft\R Client\R_SERVER). Наличие [клиентской рабочей станции R](../r/set-up-a-data-science-client.md) с этими исполняемыми файлами считается необходимым условием для этого учебника.

## <a name="create-the-training-data-table"></a>Создание таблицы с данными для обучения

1. Храните строку подключения к базе данных в переменной R. Ниже приведены два примера допустимых строк подключения ODBC для SQL Server: один с использованием имени для входа SQL и второй для встроенной проверки подлинности Windows. 

   Измените имя сервера, имя пользователя и пароль на нужные.

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
  
    Так как имена экземпляра сервера и базы данных уже указаны в строке подключения, при объединении этих двух переменных *полное* имя новой таблицы принимает вид *имя экземпляра.имя базы данных.схема.ccFraudSmall*.
  
3.  Можно также указать параметр *rowsPerRead*, который управляет тем, сколько строк данных считывается в каждом пакете.
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    Хотя этот параметр является необязательным, его установка может повысить эффективность вычислений. Большинство расширенных аналитических функций в **RevoScaleR** и **MicrosoftML** обрабатывают данные в виде блоков. Параметр *rowsPerRead* определяет количество строк в каждом блоке.
  
    Возможно, потребуется поэкспериментировать с этим параметром, чтобы найти правильный баланс. Если значение слишком велико, доступ к данным может оказаться слишком медленным, если недостаточно памяти для обработки данных в блоках такого размера. И наоборот: в некоторых системах, если значение параметра *rowsPerRead* слишком мало, возможно снижение производительности.
  
    В качестве начального значения используйте размер пакетной обработки по умолчанию, определенный экземпляром ядра СУБД, для управления количеством строк в каждом блоке (5 000 строк). Сохраните это значение в переменной *sqlRowsPerRead*.
  
4.  Определите переменную для нового объекта источника данных и передайте ранее определенные аргументы в конструктор **RxSqlServerData**. Обратите внимание, что при этом происходит только создание, но не заполнение объекта источника данных. Загрузка данных выполняется отдельно.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

## <a name="create-the-scoring-data-table"></a>Создание таблицы с данными для оценки

Аналогичным образом вы создадите таблицу, содержащую данные для оценки.

1. Создайте переменную R *sqlScoreTable*для хранения имени таблицы, используемой для оценки.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Передайте эту переменную в качестве аргумента в функцию **RxSqlServerData** , чтобы определить еще один объект источника данных *sqlScoreDS*.
  
    ```R
    sqlScoreDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Так как вы уже определили строку подключения и другие параметры в качестве переменных в рабочем пространстве R, их можно использовать повторно, чтобы создавать источники данных для других таблиц, представлений или запросов.

> [!NOTE]
> Функция использует разные аргументы для определения источника данных на основе всей таблицы и для источника данных на основе запроса. Это обусловлено тем, что ядро СУБД SQL Server должно по-разному подготавливать запросы. Далее в этом учебнике вы узнаете, как создать объект источника данных на основе запроса SQL.

## <a name="load-data-into-sql-tables-using-r"></a>Загрузка данных в таблицы SQL с помощью языка R

Теперь, когда вы создали таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , можете загрузить в них данные с помощью соответствующей функции **Rx** .

Пакет **RevoScaleR** содержит функции, относящиеся к типам источников данных. Для текстовых данных используйте [RxTextData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata) для создания объекта источника данных. Имеются также дополнительные функции для создания объектов источников данных на основе Hadoop, ODBC и других типов данных.

> [!NOTE]
> Для задач, описываемых в этом разделе, требуются разрешения на **выполнение DDL** в базе данных.

### <a name="load-data-into-the-training-table"></a>Загрузка данных в таблицу для обучения

1. Создайте переменную R *ccFraudCsv*и присвойте переменной путь к CSV-файлу, который содержит образцы данных. Этот набор данных предоставляется в **RevoScaleR**. "sampleDataDir" — это ключевое слово в функции **rxGetOption**.
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Обратите внимание на вызов **rxGetOption**, который является методом GET, связанным с [rxOptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions) в **RevoScaleR**. Используйте эту служебную программу, чтобы задать и вывести параметры, связанные с локальными и удаленными контекстами вычисления. К этим параметрам относятся общий каталог по умолчанию, число процессоров (ядер), используемых при вычислениях и т. д.
    
    Этот вызов получает образцы из правильной библиотеки независимо от среды выполнения кода. Например, запустите функцию на сервере SQL Server и на компьютере разработчика и посмотрите различия.
  
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
  
3. На этом этапе можно прерваться и просмотреть базу данных в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Обновите список таблиц в базе данных.
  
    Вы увидите, что хотя объекты данных R были созданы в локальном рабочем пространстве, таблицы в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не созданы. Никакие данные не были загружены из текстового файла в переменную R.
  
4. Вставьте данные, вызвав функцию [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep).
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
    
    При отсутствии проблем со строкой подключения после небольшой паузы должны появиться результаты наподобие следующих:
  
    *Всего строк записано: 10 000. Общее время: 0.466* *Прочитано строк: 10 000. Всего обработано строк: 10 000. Общее время обработки блока: 0,577 секунд*
  
5. Обновите список таблиц. Чтобы проверить, имеет ли каждая переменная правильный тип данных и успешно ли она импортирована, можно щелкнуть таблицу правой кнопкой мыши в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и выбрать пункт **Выделить 1000 верхних строк**.

### <a name="load-data-into-the-scoring-table"></a>Загрузка данных в таблицу для анализа

1. Повторите те же действия, чтобы загрузить в базу данных набор данных для оценки.
  
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
  
    - Если таблица уже существует и параметр *overwrite* не используется, результаты будут вставлены без усечения.
  
Если соединение установлено успешно, вы увидите сообщение, информирующее о завершении и указывающее время, необходимое для записи данных в таблицу:

*Всего строк записано: 10 000. Общее время: 0,384*
*Считано строк: 10 000. Всего обработано строк: 10 000. Общее время обработки блока: 0,456 секунд*

## <a name="more-about-rxdatastep"></a>Дополнительные сведения о функции rxDataStep

[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) — это эффективная функция, которая может выполнять несколько преобразований в кадре данных R. RxDataStep можно также использовать для преобразования данных в представление, необходимое в месте назначения. В данном случае — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

При необходимости можно указать преобразования данных с помощью функций R в аргументах для **rxDataStep**. Примеры этих операций приведены далее в этом учебнике.

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Запрос и изменение данных SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)