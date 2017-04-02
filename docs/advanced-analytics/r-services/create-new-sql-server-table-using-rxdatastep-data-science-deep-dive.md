---
title: "Создание таблицы SQL Server с помощью rxDataStep (глубокое погружение в обработку и анализ данных) | Microsoft Docs"
ms.custom: ""
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
ms.assetid: 98cead96-6de7-4edf-98b9-a1efb09297b9
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Создание таблицы SQL Server с помощью rxDataStep (глубокое погружение в обработку и анализ данных)
На этом занятии вы узнаете, как перемещать данные между кадрами данных в памяти, контекстом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и локальными файлами.  
  
> [!NOTE]  
> В этом занятии будет использоваться другой набор данных. Набор данных о задержках авиарейсов является общедоступным набором данных, который широко используется в экспериментах машинного обучения. Если вы только начинаете работу с R, этот набор данных удобен для тестирования, так как он используется в различных образцах продуктов для [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], которые были опубликованы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Необходимые для этого примера файлы данных доступны в том же каталоге, что и другие образцы продуктов.  
  
## Создание таблицы SQL Server на основе локальных данных  
На первом занятии этого учебника вы использовали функцию *RxTextData* для импорта данных в среду R из текстового файла, а затем с помощью функции *RxDataStep* передавали данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
На этом занятии вы будете использовать другой подход и получите данные из файла в [формате XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). Формат XDF — это стандарт XML, разработанный для многомерных данных. Это двоичный формат файла с интерфейсом R, который оптимизирует процессы обработки и анализа строк и столбцов.  Его можно использовать для хранения подмножеств данных в целях анализа.
  
После ряда простых преобразований данных с помощью файла XDF вы сохраните их в новой таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
> Для этого шага потребуются разрешения DDL.  
  
1.  Задайте в качестве контекста вычисления локальную рабочую станцию.  
  
    ```R  
    rxSetComputeContext("local")   
    ```  
  
2.  Определите новый объект источника данных с помощью функции *RxXdfData*. Для источника данных XDF просто укажите путь к файлу данных.  Путь к файлу можно было бы указать с помощью текстовой переменной, но в этом случае есть более удобный способ, так как файл с образцом данных (AirlineDemoSmall.xdf) находится в каталоге, возвращаемом функцией *rxGetOption*.
  
    ```R  
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))   
    ```  
  
  
3.  Вызовите функцию *rxGetVarInfo* для данных в памяти, чтобы просмотреть сводку по набору данных.  
  
    ```R  
    rxGetVarInfo(xdfAirDemo)    
    ```  
  
**Результаты**  
  
*Var 1: ArrDelay, Тип: integer, Нижнее и верхнее значения: (-86, 1490)*   
*Var 2: CRSDepTime, Тип: numeric, Хранение: float32, Нижнее и верхнее значения: (0,0167, 23,9833)*   
*Var 3: DayOfWeek 7 уровней факторов: Monday Tuesday Wednesday Thursday Friday Saturday Sunday*  

> [!NOTE]
> 
> Вы заметили, что вам не пришлось вызывать другие функции для загрузки данных в файл XDF и вы смогли сразу же вызвать функцию *rxGetVarInfo*? Это связано с тем, что XDF является промежуточным методом хранения по умолчанию для RevoScaleR. Дополнительные сведения о файлах XDF см. в разделе [Руководство по началу работы со ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-transform#using-the-data-step-to-create-an-xdf-file-from-a-data-frame). 
  
4.  Далее вы поместите эти данные в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сохранив переменную _DayOfWeek_ как целочисленную со значениями от 1 до 7.  
  
    Для этого сначала определите источник данных SQL Server.  
  
    ```R  
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)   
    ```  
  
5.  Проверьте наличие таблицы с таким именем и удалите ее, если она уже имеется.  
  
    ```R  
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)    
    ```  
  
6.  Создайте таблицу и загрузите данные с помощью функции `rxDataStep`.  
  
    ```R  
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,    
            transforms = list( DayOfWeek = as.integer(DayOfWeek),   
            rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),   
            overwrite = TRUE )    
    ```  
  
7.  Снова задайте сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве контекста вычисления.  
  
    ```R  
    rxSetComputeContext(sqlCompute)  
    ```  
  
8.  Определите подмножество данных с помощью простой инструкции SQL.  
  
    ```R    
    SqlServerAirDemo <- RxSqlServerData(  
        sqlQuery = "SELECT * FROM AirDemoSmallTest",      
        connectionString = sqlConnString,   
        rowsPerRead = 50000,      
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))    
    ```  
  
9. Вызовите функцию *rxSummary* для просмотра сводки по данным в запросе.  
  
    ```R  
    rxSummary(~., data = sqlServerAirDemo)   
    ```  
  
## Следующий шаг  
[Выполнение фрагментирующего анализа с помощью rxDataStep (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/perform-chunking-analysis-using-rxdatastep-data-science-deep-dive.md)  
  
## Предыдущий шаг  
[Загрузка данных в память с помощью функции rxImport (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/load-data-into-memory-using-rximport-data-science-deep-dive.md)  
  
## См. также:  
[Глубокое погружение в обработку и анализ данных: использование пакетов RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
