---
title: "Выполнение фрагментирующего анализа с помощью rxDataStep (глубокое погружение в обработку и анализ данных) | Microsoft Docs"
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
ms.assetid: 4290ee5f-be90-446a-91e8-3095d694bd82
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Выполнение фрагментирующего анализа с помощью rxDataStep (глубокое погружение в обработку и анализ данных)
Функцию *rxDataStep* можно использовать для обработки данных фрагментами, вместо того чтобы загружать в память и сразу обрабатывать весь набор данных, как в традиционных системах R. В данном случае данные считываются фрагментами, а функции R используются для последовательной обработки каждого фрагмента данных. Затем сводные результаты для каждого фрагмента записываются в единый источник данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
В этом уроке вы освоите эту технику на практике: функция *table* в R используется для вычисления таблицы сопряженности.  
  
> [!TIP]  
> Этот пример предназначен только для обучения. Если требуется внести в таблицу наборы реальных неструктурированных данных, рекомендуется использовать функции *rxCrossTabs* или *rxCube*, интегрированные в **RevoScaleR** — они оптимизированы для решения подобных задач.  
  
## Секционирование данных по значениям  
  
1.  Сначала создайте пользовательскую функцию R с именем *ProcessChunk*, которая вызывает функцию *table* для каждого фрагмента данных.  
  
    ```R  
    ProcessChunk <- function( dataList) {      
    # Convert the input list to a data frame and compute contingency table      
    chunkTable <- table(as.data.frame(dataList))   
  
    # Convert table output to a data frame with a single row      
    varNames <- names(chunkTable)     
    varValues <- as.vector(chunkTable)        
    dim(varValues) <- c(1, length(varNames))      
    chunkDF <- as.data.frame(varValues)       
    names(chunkDF) <- varNames   
  
    # Return the data frame, which has a single row   
    return( chunkDF )   
    }    
    ```  
 
  
2.  В качестве контекста вычисления задайте сервер.  
  
    ```R  
    rxSetComputeContext( sqlCompute )   
    ```  
  
3.  Будет определен источник данных SQL Server для хранения обрабатываемых данных. Для начала назначьте переменной SQL-запрос.   
  
    ```R  
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"   
    ```  

4.  Включите эту переменную в аргумент *sqlQuery* нового источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```R  
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,  
        connectionString = sqlConnString,    
        rowsPerRead = 50000,      
        colInfo = list(DayOfWeek = list(type = "factor",   
            levels = as.character(1:7))))    
    ```  
     При обработке функцией *rxGetVarInfo* этого источника данных вы увидите, что имеется всего один столбец: *Var 1: DayOfWeek, Type: factor, no factor levels available* (Переменная 1: DayOfWeek, тип: признак, уровни признаков недоступны).
     
5.  Прежде чем применять эту переменную-признак к исходным данным, создайте отдельную таблицу для хранения промежуточных результатов. Используйте функцию *RxSqlServerData* для определения данных и удалите все имеющиеся таблицы с тем же именем.   
  
    ```R  
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)   
    # Check whether the table already exists.  
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }   
    ```  
  
7.  Теперь необходимо вызвать пользовательскую функцию *ProcessChunk*, чтобы преобразовывать данные во время чтения. Эта функция будет использоваться в качестве аргумента *transformFunc* для функции *rxDataStep*.  
  
    ```R  
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)   
    ```  
  
8.  Чтобы просмотреть промежуточные результаты функции *ProcessChunk*, назначьте результаты *rxImport* переменной, а затем выведите результаты на консоль.  
  
    ```R  
    iroResults <- rxImport(iroDataSource)   
  
    iroResults   
    ```  

**Частичные результаты**

|      |    1  |   2   |  3   |  4   |  5  |   6   |  7 |
| --- | ---  | --- | ---  |  ---  | ---  | ---  | --- |
| 1 | 8228 | 8924 | 6916 | 6932 | 6944 | 5602 | 6454 |
| 2  | 8321  | 5351 | 7329 | 7411 | 7409 | 6487 | 7692 |
  
9. Чтобы вычислить окончательные результаты по всем фрагментам, просуммируйте столбцы и отобразите результаты на консоли.  
  
    ```R  
    finalResults <- colSums(iroResults)   
  
    finalResults   
    ```  
 **Результаты**
  1  |   2  |   3  |   4  |   5  |   6  |   7
---  |   ---  |   ---  |   ---  |   ---  |   ---  |   ---
97975 | 77725 | 78875 | 81304 | 82987 | 86159 | 94975 
  
10. Чтобы удалить таблицу с промежуточными результатами, вызовите функцию *rxSqlServerDropTable* еще раз.  
  
    ```R  
    rxSqlServerDropTable( table = "iroResults",     connectionString = sqlConnString)    
    ```  
  
## Следующий шаг  
[Занятие 4. Анализ данных в локальном контексте вычисления (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md)  
  
## Предыдущий шаг  
[Создание таблицы SQL Server с помощью rxDataStep (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/create-new-sql-server-table-using-rxdatastep-data-science-deep-dive.md)  
  
## См. также:  
[Глубокое погружение в обработку и анализ данных: использование пакетов RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
