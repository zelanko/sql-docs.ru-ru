---
title: Создание таблицы SQL Server с помощью rxDataStep RevoScaleR - машинного обучения SQL Server
description: Руководство по созданию таблицы SQL Server с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4d0eea1921a089141819c49ac78c59e57e01291a
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53644733"
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Создание таблицы SQL Server с помощью rxDataStep (руководство по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом занятии вы узнаете, как перемещать данные между кадрами данных в памяти, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] контекст и локальные файлы.

> [!NOTE]
> Это занятие используются различные наборы данных. Набор данных задержки авиарейсов является общедоступного набора данных, который широко используется в экспериментах машинного обучения. Файлы данных, используемые в этом примере доступны в том же каталоге, что и другие образцы продуктов.

## <a name="load-data-from-a-local-xdf-file"></a>Загрузка данных из локального файла XDF

В первой половине работы с этим руководством, вы использовали **RxTextData** для импорта данных в среду R из текстового файла, а затем использовать **RxDataStep** function для перемещения данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Это занятие используется другой подход, а использует данные из файла в [формате XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). После ряда простых преобразований данных с помощью xdf-файл, сохраните преобразованные данные в новую [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.

**Что такое XDF?**

Формат XDF — это стандарт XML, разработанный для многомерных данных и собственным форматом файлов используется [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). Это двоичный формат файла с интерфейсом R, который оптимизирует процессы обработки и анализа строк и столбцов.  Его можно использовать для хранения подмножеств данных в целях анализа.

1. Задайте в качестве контекста вычисления локальную рабочую станцию. **Для выполнения этого шага, необходимы разрешения DDL.**

    ```R
    rxSetComputeContext("local")
    ```
  
2. Определите новый объект источника данных с помощью функции **RxXdfData** . Для определения источника данных XDF, укажите путь к файлу данных.  

    Можно указать путь к файлу, с помощью текстовой переменной. Однако в этом случае есть удобный ярлык, который заключается в использовании **rxGetOption** функции и загрузите его (AirlineDemoSmall.xdf) из каталога образцов данных.
  
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
> Вы заметили, что вам не пришлось вызывать другие функции для загрузки данных в файл XDF и вы смогли сразу же вызвать функцию **rxGetVarInfo** ? Это потому, что XDF является методом промежуточное хранилище по умолчанию для **RevoScaleR**. Помимо файлов XDF **rxGetVarInfo** функция теперь поддерживает несколько типов источников.

## <a name="move-contents-to-sql-server"></a>Переместить содержимое в SQL Server

С помощью источника данных XDF, созданные в локальном сеансе R, теперь можно переместить эти данные в таблицу базы данных хранения *DayOfWeek* к целому числу со значениями от 1 до 7.

1. Определите объект источника данных SQL Server, указав таблицу для хранения данных и подключения к удаленному серверу.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
2. В качестве меры предосторожности включают шаги, проверяет ли таблицы с таким именем уже существует и удалить таблицу, если он существует. Существующую таблицу с теми же именами предотвращает его создание.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
3. Загрузка данных в таблицу с помощью **rxDataStep**. Эта функция перемещает данные между двумя уже определенных источников данных и при необходимости можно преобразовать данные в процессе перемещения.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
        transforms = list( DayOfWeek = as.integer(DayOfWeek),
        rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
        overwrite = TRUE )
    ```
  
    Это довольно большая таблица, поэтому Подождите, пока не увидите итоговое сообщение о состоянии такого рода: *Строк считано: 200000, всего строк обработано: 600000*.
     
## <a name="load-data-from-a-sql-table"></a>Загрузка данных из таблицы SQL

Когда данные находятся в таблице, его можно загрузить с помощью простого SQL-запроса. 

1. Создайте новый источник данных SQL Server. Входные данные — это запрос на новую таблицу, вы только что создан и загружен данными. Это определение добавляет уровни признаков для *DayOfWeek* столбца, с помощью *colInfo* аргумент **RxSqlServerData**.
  
    ```R
    sqlServerAirDemo2 <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
2. Вызовите **rxSummary** еще раз для просмотра сводки по данным в запросе.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo2)
    ```

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Выполнение фрагментирующего анализа с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)