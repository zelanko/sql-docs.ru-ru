---
title: "Оценка новых данных (глубокое погружение в обработку и анализ данных) | Microsoft Docs"
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
ms.assetid: 87056467-f67f-4d72-a83c-ac052736d85d
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Оценка новых данных (глубокое погружение в обработку и анализ данных)
Теперь, когда у вас есть модель, которую можно использовать для прогнозирования, вы внесете в нее данные из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для получения ряда прогнозов.  
  
## Оценка новых данных  
Вы будете использовать модель логистической регрессии *logitObj* для формирования оценок для еще одного набора данных с теми же независимыми переменными в качестве входных данных.  
  
> [!NOTE]  
> Для выполнения некоторых действий потребуются права администратора DDL.  
  
1.  Обновите ранее настроенный источник данных *sqlScoreDS*, добавив сведения о необходимых столбцах.  
  
    ```R  
    sqlScoreDS <- RxSqlServerData(  
        connectionString = sqlConnString,   
        table = sqlScoreTable,   
        colInfo = ccColInfo,   
        rowsPerRead = sqlRowsPerRead)    
    ```  
  
2.  Чтобы не потерять результаты, вы создадите новый объект источника данных и с его помощью заполните новую таблицу в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```R    
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",   
        connectionString = sqlConnString,   
        rowsPerRead = sqlRowsPerRead )    
    ```  
     К этому моменту таблица не была создана. Эта инструкция просто определяет контейнер для данных.
     
3.  Проверьте текущий контекст вычисления и при необходимости задайте серверный контекст.  
  
    ```R  
    rxSetComputeContext(sqlCompute)  
    ```  
  
4.  Перед выполнением функции прогнозирования, создающей результаты, необходимо проверить наличие таблицы выходных данных. В противном случае при попытке записи в новую таблицу произойдет ошибка  
  
    Для этого вызовите функции *rxSqlServerTableExists* и *rxSqlServerDropTable*, передав имя таблицы в качестве входных данных.  
  
    ```R  
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")   
    ```  
  
    -   Функция *rxSqlServerTableExists* запрашивает драйвер ODBC и возвращает значение TRUE, если таблица существует, или значение FALSE в противном случае.    
    -   Функция *rxSqlServerDropTable* выполняет DDL и возвращает значение TRUE, если таблица успешно удалена, или значение FALSE в противном случае.   
  
5.  Теперь вы готовы использовать функцию *rxPredict* для создания оценок и их сохранения в новой таблице, определенной в источнике данных *sqlScoreDS*.  
  
    ```R  
    rxPredict(modelObject = logitObj,   
        data = sqlScoreDS,        
        outData = sqlServerOutDS,     
        predVarNames = "ccFraudLogitScore",   
          type = "link",      
        writeModelVars = TRUE,        
        overwrite = TRUE)    
    ```  
  
    Функция *RxPredict* является еще одной функцией, поддерживающей выполнение в удаленных контекстах вычисления. Функцию *rxPredict* можно использовать для создания оценок из моделей, сформированных с помощью *rxLinMod*, *rxLogit* или *rxGlm*.  
  
    -   В этом случае параметру *writeModelVars* присвоено значение **TRUE**. Это означает, что переменные, которые использовались для оценки, будут включены в новую таблицу.  
  
    -   Параметр *predVarNames* определяет переменную, в которой будут храниться результаты. В этом случае передается новая переменная *ccFraudLogitScore*.  
  
    -   Параметр *type* функции *rxPredict* определяет способ вычисления прогнозов. Укажите ключевое слов **response**, чтобы оценки формировались на основе шкалы зависимой переменной, или используйте ключевое слово **link**, чтобы оценки формировались с помощью базовой функции связи, в которой ситуационные прогнозы основываются на логистической шкале.  

6. Через некоторое время вы можете обновить список таблиц в среде Management Studio, чтобы увидеть новую таблицу и ее данные.

7. Чтобы добавить дополнительные переменные в результирующие прогнозы, можно использовать аргумент *extraVarsToWrite*.  Например, в следующем коде переменная *custID* добавляется из таблицы данных для оценки в выходную таблицу прогнозов.  
  
    ```R   
    rxPredict(modelObject = logitObj,    
            data = sqlScoreDS,        
            outData = sqlServerOutDS,     
            predVarNames = "ccFraudLogitScore",   
              type = "link",      
            writeModelVars = TRUE,        
            extraVarsToWrite = "custID",      
            overwrite = TRUE)    
    ```  
  
## Отображение оценок на гистограмме  
После создания новой таблицы производится вычисление и отображение гистограммы с 10 000 прогнозируемых оценок. Вычисления будут производиться быстрее, если указать нижнее и верхнее значения, поэтому они будут получены из базы данных и добавлены в рабочие данные.  
  
1.  Создайте источник данных *sqlMinMax*, который выполняет запрос к базе данных для получения нижнего и верхнего значений.  
  
    ```R  
    sqlMinMax <- RxSqlServerData(  
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",   
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),   
        connectionString = sqlConnString)    
    ```  
     В этом примере можно увидеть, насколько просто использовать объекты источника данных *RxSqlServerData* для определения произвольных наборов данных на основе запросов SQL, функций или хранимых процедур, а затем использовать их в коде R. Переменная не хранит фактические значения, а только определение источника данных. Запрос выполняется для создания значений только при его использовании в функции наподобие *rxImport*.  
      
2.  Вызовите функцию *rxImport*, чтобы поместить значения в кадр данных, который можно использовать совместно в разных контекстах вычисления.  
  
    ```R  
    minMaxVals <- rxImport(sqlMinMax)   
    minMaxVals <- as.vector(unlist(minMaxVals))  
  
    ```  
     **Результаты**
 
     *> minMaxVals*
     
     *[1] –23,970256   9,786345*
  
3.  Теперь, когда максимальное и минимальное значения доступны, используйте их для создания источника данных для оценки.  
  
    ```R  
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",    
        connectionString = sqlConnString,   
        rowsPerRead = sqlRowsPerRead,   
            colInfo = list(ccFraudLogitScore = list(   
                low = floor(minMaxVals[1]),    
                        high = ceiling(minMaxVals[2]) ) ) )  
  
    ```  

  
4.  И наконец, используйте объект источника данных для получения данных оценки и вычисления и отображения гистограммы. При необходимости добавьте код для задания контекста вычисления.  
  
    ```R  
    # rxSetComputeContext(sqlCompute)   
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)  
  
    ```  
  
    **Результаты**  
  
    ![complex histogram created by R](../../advanced-analytics/r-services/media/rsql-sue-complex-histogram.png "complex histogram created by R")  
  
## Следующий шаг  
[Занятие 3. Преобразование данных с помощью языка R (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/lesson-3-transform-data-using-r-data-science-deep-dive.md)  
  
## Предыдущий шаг  
[Создание моделей (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/create-models-data-science-deep-dive.md)  
  
## См. также:  
[Глубокое погружение в обработку и анализ данных: общие сведения (службы SQL Server R Services)](http://msdn.microsoft.com/library/mt637368(SQL.130).aspx)  
  
  
  
