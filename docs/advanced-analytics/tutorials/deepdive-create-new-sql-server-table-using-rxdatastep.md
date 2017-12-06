---
title: "Создание новой таблицы SQL Server, с помощью rxDataStep | Документы Microsoft"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 98cead96-6de7-4edf-98b9-a1efb09297b9
caps.latest.revision: "19"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8f276a09ea785da6b31a54693a6f5d758bb77b43
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="create-new-sql-server-table-using-rxdatastep"></a>Создание таблицы SQL Server с помощью rxDataStep

На этом занятии вы узнаете, как перемещать данные между кадрами данных в памяти, контекстом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и локальными файлами.

> [!NOTE]
> В этом занятии будет использоваться другой набор данных. Набор данных задержки авиарейсов является открытый набор данных, широко используемый для эксперименты машинного обучения. Если вы только начинаете работу с R, этот набор данных удобен для тестирования, так как он используется в различных образцах продуктов для [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] , которые были опубликованы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Необходимые для этого примера файлы данных доступны в том же каталоге, что и другие образцы продуктов.

## <a name="create-sql-server-table-from-local-data"></a>Создание таблицы SQL Server на основе локальных данных

В первой части этого учебника вы использовали **RxTextData** для импорта данных в R из текстового файла и затем использовать **RxDataStep** function для перемещения данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

На этом занятии вы будете использовать другой подход и получите данные из файла в [формате XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). Формат XDF — это стандарт XML, разработанный для многомерных данных. Это двоичный формат файла с интерфейсом R, который оптимизирует процессы обработки и анализа строк и столбцов.  Его можно использовать для хранения подмножеств данных в целях анализа.

После ряда простых преобразований данных с помощью файла XDF вы сохраните их в новой таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

> [!NOTE]
> Для этого шага потребуются разрешения DDL.

1. Задайте в качестве контекста вычисления локальную рабочую станцию.
  
    ```R
    rxSetComputeContext("local")
    ```
  
2. Определите новый объект источника данных с помощью функции **RxXdfData** . Для источника данных XDF просто укажите путь к файлу данных.  Можно указать путь к файлу, используя переменную текст, но в этом случае есть удобный ярлык, так как образец файла данных (AirlineDemoSmall.xdf) находится в каталоге, возвращенный функцией rxGetOption.
  
    ```R
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))
    ```

3. Вызовите rxGetVarInfo данных в памяти, чтобы просмотреть сводку набора данных.
  
    ```R
    rxGetVarInfo(xdfAirDemo)
    ```

**Результаты**

*Var 1: ArrDelay, Тип: integer, Нижнее и верхнее значения: (-86, 1490)*

*Var 2: CRSDepTime, Тип: numeric, Хранение: float32, Нижнее и верхнее значения: (0,0167, 23,9833)*

*Var 3: DayOfWeek 7 уровней факторов: Monday Tuesday Wednesday Thursday Friday Saturday Sunday*

> [!NOTE]
> 
> Вы заметили, не нужно вызывать другие функции для загрузки данных в XDF-файл и может вызвать rxGetVarInfo данных немедленно? Это связано с тем, что XDF является промежуточным методом хранения по умолчанию для RevoScaleR. Дополнительные сведения о XDF-файлов см. в разделе [создания XDF](https://msdn.microsoft.com/microsoft-r/scaler-data-xdf).
  
4. Далее вы поместите эти данные в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , сохранив переменную _DayOfWeek_ как целочисленную со значениями от 1 до 7.
  
    Для этого сначала определите источник данных SQL Server.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
5. Проверьте наличие таблицы с таким именем и удалите ее, если она существует.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
6. Создайте таблицу и загрузите данные с помощью функции **rxDataStep**. Эта функция перемещает данные между двумя уже определения источников данных и преобразовывать данные в процессе перемещения.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
            transforms = list( DayOfWeek = as.integer(DayOfWeek),
            rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
            overwrite = TRUE )
    ```
  
    Это довольно большая таблица, поэтому нужно немного подождать, пока отобразится итоговое сообщение о состоянии: *Rows Read: 200000, Total Rows Processed: 600000* (Прочитано 200 000 строк, обработано 600 000 строк).
     
7. Снова задайте сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве контекста вычисления.

    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
8. Создайте новый источник данных SQL Server с помощью простого запроса SQL к новой таблице. Это определение добавляет уровни признаков для столбца *DayOfWeek*, используя аргумент *colInfo* для RxSqlServerData.
  
    ```R
    SqlServerAirDemo <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
9. Вызов rxSummary еще раз, чтобы просмотреть сводку данных в запросе.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo)
    ```

## <a name="next-step"></a>Следующий шаг

[Выполнять анализ фрагментации, с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)

## <a name="previous-step"></a>Предыдущий шаг

[Загрузка данных в памяти с помощью rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)


