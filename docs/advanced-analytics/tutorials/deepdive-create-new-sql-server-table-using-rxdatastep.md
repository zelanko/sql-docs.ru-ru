---
title: Создание новой таблицы SQL Server с помощью rxDataStep (SQL и R глубокое погружение) | Документы Microsoft
ms.custom: ''
ms.date: 12/14/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 3afc3e58771377190e42d92bc9a125bfa82a4546
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-and-r-deep-dive"></a>Создание новой таблицы SQL Server с помощью rxDataStep (SQL и R глубокое погружение)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом занятии вы узнаете, как перемещение данных между кадрами данных в памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] контекст и локальные файлы.

> [!NOTE]
> На этом занятии рассматривается другой набор данных. Набор данных задержки авиарейсов является открытый набор данных, широко используемый для эксперименты машинного обучения. Файлы данных, используемые в этом примере доступны в том же каталоге, как другие образцы продуктов.

## <a name="create-sql-server-table-from-local-data"></a>Создать таблицу SQL Server на основе локальных данных

В первой половине этого учебника вы использовали **RxTextData** для импорта данных в R из текстового файла и затем использовать **RxDataStep** function для перемещения данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

На этом занятии использует другой подход, а использует данные из файла в [XDF формат](https://en.wikipedia.org/wiki/Extensible_Data_Format). После выполнения некоторых упрощенных преобразований XDF-файл с данными, сохраняющий преобразованные данные в новый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.

**Что такое XDF.**

Формат XDF — это стандарт XML, разработанных для многомерными данными и используется собственный формат [машины обучения Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). Это двоичный формат файла с интерфейсом R, который оптимизирует процессы обработки и анализа строк и столбцов.  Его можно использовать для хранения подмножеств данных в целях анализа.

1. Задайте в качестве контекста вычисления локальную рабочую станцию. **Для выполнения этого шага необходимы разрешения DDL.**

  
    ```R
    rxSetComputeContext("local")
    ```
  
2. Определите новый объект источника данных с помощью функции **RxXdfData** . Для определения источника данных XDF, укажите путь к файлу данных.  

    Можно указать путь к файлу, используя переменную текста. Однако в этом случае есть удобный ярлык, который заключается в использовании **rxGetOption** функцией и получить файл (AirlineDemoSmall.xdf) из папки образцов данных.
  
    ```R
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))
    ```

3. Вызовите функцию [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) для данных в памяти, чтобы просмотреть сводку по набору данных.
  
    ```R
    rxGetVarInfo(xdfAirDemo)
    ```

**Результаты**

*Var 1: ArrDelay, Тип: integer, Нижнее и верхнее значения: (-86, 1490)*

*Var 2: CRSDepTime, Тип: numeric, Хранение: float32, Нижнее и верхнее значения: (0,0167, 23,9833)*

*Var 3: DayOfWeek 7 уровней факторов: Monday Tuesday Wednesday Thursday Friday Saturday Sunday*

> [!NOTE]
> 
> Вы заметили, что вам не пришлось вызывать другие функции для загрузки данных в файл XDF и вы смогли сразу же вызвать функцию **rxGetVarInfo** ? Это связано с тем, что XDF является промежуточным методом хранения по умолчанию для RevoScaleR. Помимо файлов XDF **rxGetVarInfo** функции теперь поддерживает несколько типов источников.
  
4. Поместить эти данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы хранения _DayOfWeek_ является значением типа integer со значениями от 1 до 7.
  
    Для этого сначала определите источник данных SQL Server.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
5. Проверьте наличие таблицы с таким именем и удалите ее, если она существует.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
6. Создайте таблицу и загрузите данные с помощью функции **rxDataStep**. Эта функция перемещает данные между двумя уже определения источников данных и при необходимости можно преобразовывать данные прохождения.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
            transforms = list( DayOfWeek = as.integer(DayOfWeek),
            rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
            overwrite = TRUE )
    ```
  
    Это довольно большой таблицы, поэтому Подождите, пока не появится сообщение конечного состояния, похожее на следующее: *чтения строки: 200000, Всего обработано строк: 600000*.
     
7. Снова задайте сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве контекста вычисления.

    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
8. Создайте новый источник данных SQL Server с помощью простого запроса SQL к новой таблице. Это определение добавляет уровни коэффициент для *DayOfWeek* столбца, с помощью *colInfo* аргумент **RxSqlServerData**.
  
    ```R
    SqlServerAirDemo <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
9. Вызовите **rxSummary** еще раз, чтобы просмотреть сводку данных в запросе.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo)
    ```

## <a name="next-step"></a>Следующий шаг

[Выполнение фрагментирующего анализа с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)

## <a name="previous-step"></a>Предыдущий шаг

[Загрузка данных в память с помощью функции rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)
