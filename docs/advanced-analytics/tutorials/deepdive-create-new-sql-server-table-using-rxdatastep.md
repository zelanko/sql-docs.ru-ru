---
title: Создание новой SQL Server таблицы с помощью RevoScaleR rxDataStep
description: Пошаговое руководство по созданию SQL Server таблицы с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b18f2bd42070746551d21ff7508e7fce58b49037
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714915"
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Создание новой SQL Server таблицы с помощью rxDataStep (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Это занятие является частью [учебника RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом занятии вы узнаете, как перемещать данные между кадрами данных в памяти, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] контекстом и локальными файлами.

> [!NOTE]
> В этом занятии используется другой набор данных. Набор данных о задержке авиакомпании — это общедоступный набор данных, широко используемый для экспериментов машинного обучения. Файлы данных, используемые в этом примере, доступны в том же каталоге, что и другие образцы продуктов.

## <a name="load-data-from-a-local-xdf-file"></a>Загрузка данных из локального файла Xdf-

В первой половине этого руководства вы использовали функцию **функцию rxtextdata** для импорта данных в R из текстового файла, а затем использовали функцию **RxDataStep** для перемещения данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Это занятие принимает другой подход и использует данные из файла, сохраненного в [формате Xdf-](https://en.wikipedia.org/wiki/Extensible_Data_Format). После выполнения некоторых простых преобразований данных с помощью файла Xdf-вы сохраняете преобразованные данные в новой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблице.

**Что такое Xdf-?**

Формат Xdf-— это стандарт XML, разработанный для больших объемов данных, а также собственный формат файлов, используемый [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). Это двоичный формат файла с интерфейсом R, который оптимизирует процессы обработки и анализа строк и столбцов.  Его можно использовать для хранения подмножеств данных в целях анализа.

1. Задайте в качестве контекста вычисления локальную рабочую станцию. **Для этого шага требуются разрешения DDL.**

    ```R
    rxSetComputeContext("local")
    ```
  
2. Определите новый объект источника данных с помощью функции **RxXdfData** . Чтобы определить источник данных Xdf-, укажите путь к файлу данных.  

    Путь к файлу можно указать с помощью текстовой переменной. Однако в этом случае есть удобное сочетание клавиш, которое заключается в использовании функции **rxGetOption** и получении файла (AirlineDemoSmall. Xdf-) из каталога образцов данных.
  
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
> Вы заметили, что вам не пришлось вызывать другие функции для загрузки данных в файл XDF и вы смогли сразу же вызвать функцию **rxGetVarInfo** ? Это обусловлено тем, что Xdf-является методом промежуточного хранения по умолчанию для **RevoScaleR**. В дополнение к файлам Xdf-, функция **функцию rxgetvarinfo** теперь поддерживает несколько типов источников.

## <a name="move-contents-to-sql-server"></a>Переместить содержимое в SQL Server

С помощью источника данных Xdf-, созданного в локальном сеансе R, теперь можно переместить эти данные в таблицу базы данных, сохранив *DayOfWeek* в виде целого числа со значениями от 1 до 7.

1. Определите SQL Server объект источника данных, указав таблицу, содержащую данные, и соединение с удаленным сервером.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
2. В качестве меры предосторожности включите шаг, который проверяет, существует ли уже таблица с тем же именем, и удаляет таблицу, если она существует. Существующая таблица с теми же именами не допустить создания новой таблицы.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
3. Загрузка данных в таблицу с помощью **rxDataStep**. Эта функция перемещает данные между двумя уже определенными источниками данных и при необходимости может преобразовать маршрут короткого анализа данных.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
        transforms = list( DayOfWeek = as.integer(DayOfWeek),
        rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
        overwrite = TRUE )
    ```
  
    Это достаточно большая таблица, поэтому дождитесь, пока не увидите окончательное сообщение о состоянии, подобное этому: *Считано строк: 200000, всего обработано строк: 600000*.
     
## <a name="load-data-from-a-sql-table"></a>Загрузка данных из таблицы SQL

После того как данные существуют в таблице, их можно загрузить с помощью простого SQL-запроса. 

1. Создайте новый источник данных SQL Server. Входные данные — это запрос к новой таблице, которую вы только что создали и загрузили с данными. Это определение добавляет уровни коэффициента для столбца *DayOfWeek* , используя аргумент *colInfo* для **RxSqlServerData**.
  
    ```R
    sqlServerAirDemo2 <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
2. Вызовите **rxSummary** еще раз, чтобы посмотреть сводку данных в запросе.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo2)
    ```

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Выполнение фрагментирующего анализа с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)