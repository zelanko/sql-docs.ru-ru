---
title: Создание таблицы с использованием rxDataStep
description: Учебник по RevoScaleR, часть 11. Сведения о создании таблицы SQL Server с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 99f693210b567523b74f851d1db68470cae2891d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "74947264"
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Создание новой таблицы SQL Server с помощью rxDataStep (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта часть 11 входит в состав [серии учебников по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), посвященной использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

Из этого учебника вы узнаете, как перемещать данные между кадрами данных в памяти, контекстом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и локальными файлами.

> [!NOTE]
> В этом учебнике используется другой набор данных. Набор данных о задержках авиарейсов является общедоступным набором данных, который широко используется в экспериментах машинного обучения. Используемые в этом примере файлы данных доступны в том же каталоге, что и другие образцы продуктов.

## <a name="load-data-from-a-local-xdf-file"></a>Загрузка данных из локального XDF-файла

В первой половине этой серии учебников вы использовали функцию **RxTextData** для импорта данных в среду R из текстового файла, а затем с помощью функции **RxDataStep** передавали данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Теперь мы применим другой подход, а именно используем данные из сохраненного файла в [формате XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). После ряда простых преобразований данных с помощью файла XDF вы сохраните их в новой таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

**Что такое XDF?**

Формат XDF — это стандарт XML, разработанный для многомерных данных, а также собственный формат файлов, используемый в [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). Это двоичный формат файла с интерфейсом R, который оптимизирует процессы обработки и анализа строк и столбцов.  Его можно использовать для хранения подмножеств данных в целях анализа.

1. Задайте в качестве контекста вычисления локальную рабочую станцию. **Для этого шага необходимы разрешения DDL.**

    ```R
    rxSetComputeContext("local")
    ```
  
2. Определите новый объект источника данных с помощью функции **RxXdfData** . Чтобы задать источник данных XDF, укажите путь к файлу данных.  

    Путь к файлу можно указать с помощью текстовой переменной. Однако в этом случае есть маленькая хитрость, которая заключается в использовании функции **rxGetOption** и получении файла (AirlineDemoSmall.xdf) из каталога образцов данных.
  
    ```R
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))
    ```

3. Вызовите функцию [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) для данных в памяти, чтобы просмотреть сводку по набору данных.
  
    ```R
    rxGetVarInfo(xdfAirDemo)
    ```

**Результаты**

```R
Var 1: ArrDelay, Type: integer, Low/High: (-86, 1490)
Var 2: CRSDepTime, Type: numeric, Storage: float32, Low/High: (0.0167, 23.9833)
Var 3: DayOfWeek 7 factor levels: Monday Tuesday Wednesday Thursday Friday Saturday Sunday
```

> [!NOTE]
> 
> Вы заметили, что вам не пришлось вызывать другие функции для загрузки данных в файл XDF и вы смогли сразу же вызвать функцию **rxGetVarInfo** ? Это связано с тем, что XDF является промежуточным методом хранения по умолчанию для **RevoScaleR**. Помимо файлов XDF, функция **rxGetVarInfo** теперь поддерживает несколько типов источников.

## <a name="move-contents-to-sql-server"></a>Перенос содержимого в SQL Server

С помощью источника данных XDF, созданного в локальном сеансе R, теперь можно переместить эти данные в таблицу базы данных, сохранив *DayOfWeek* в виде целого числа со значениями от 1 до 7.

1. Определите объект источника данных SQL Server, указав таблицу, содержащую данные, и соединение с удаленным сервером.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
2. В качестве меры предосторожности проверьте наличие таблицы с таким именем и удалите ее, если она существует. Существующая таблица с таким же именем не позволит создать новую таблицу.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
3. Загрузите данные в таблицу с помощью **rxDataStep**. Эта функция перемещает данные между двумя уже определенными источниками данных и при необходимости может преобразовать данные в пути.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
        transforms = list( DayOfWeek = as.integer(DayOfWeek),
        rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
        overwrite = TRUE )
    ```
  
    Это достаточно большая таблица, поэтому дождитесь, пока не увидите окончательное сообщение о состоянии, подобное следующему: *Прочитано строк: 200000, Всего обработано строк: 600000*.
     
## <a name="load-data-from-a-sql-table"></a>Загрузка данных из таблицы SQL

После того как данные записаны в таблицу, их можно загрузить с помощью простого SQL-запроса. 

1. Создайте новый источник данных SQL Server. Входные данные — запрос к новой таблице, которую вы только что создали и заполнили данными. Это определение добавляет уровни признаков для столбца *DayOfWeek*, используя аргумент *colInfo* для **RxSqlServerData**.
  
    ```R
    sqlServerAirDemo2 <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
2. Вызовите функцию **rxSummary** еще раз для просмотра сводки по данным в запросе.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo2)
    ```

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Выполнение фрагментирующего анализа с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)