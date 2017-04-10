---
title: "Перенос данных между SQL Server и файлом XDF (глубокое погружение в обработку и анализ данных) | Microsoft Docs"
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
ms.assetid: 40887cb3-ffbb-4769-9f54-c006d7f4798c
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Перенос данных между SQL Server и файлом XDF (глубокое погружение в обработку и анализ данных)
При работе в локальном контексте вычислений у вас есть доступ как к локальным файлам данных, так и к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (определяемой как источник данных *RxSqlServerData*).  
  
В этом разделе вы узнаете, как получить данные и сохранить их в файле на локальном компьютере, чтобы получить возможность преобразовывать данные. По завершении этой процедуры данные в файле будут использованы для создания новой таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи функции *rxDataStep*.  
  
## Создание таблицы SQL Server на основе файла XDF  

Функция *rxImport* позволяет импортировать данные из любого поддерживаемого источника данных в локальный XDF-файл. Использование локального файла может быть удобным, если требуется проанализировать данные, хранящиеся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], множеством различных способов и вы хотите избежать выполнения одного и того же запроса много раз.  
  
В этом упражнении вы снова будете использовать данные по мошенничеству с кредитными картами. В этом сценарии вас попросили провести дополнительный анализ данных по пользователям в штатах Калифорния, Орегон и Вашингтон. Чтобы повысить эффективность, вы решили сохранить на локальном компьютере данные только по этим штатам и работать с переменными gender, cardholder, state и balance.  
  
1.  Используйте ранее созданный вектор *stateAbb*, чтобы определить уровни, которые необходимо включить, а затем отобразите на консоли новую переменную *statesToKeep*.  
  
    ```  
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)   
  
    statesToKeep  
  
    ```  
 **Результаты**
CA |  или  | WA 
-- | -- | --
 5 |  38  | 48 
  
2.  Теперь будут определены данные, переносимые с сервера SQL Server, при помощи запроса [!INCLUDE[tsql](../../includes/tsql-md.md)].  В дальнейшем эта переменная будет использоваться в качестве аргумента *inData* функции *rxImport*.  
  
    ```R  
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")  
  
    ```  
  
    Убедитесь в том, что в запросе нет скрытых символов, например переводов строки или символов табуляции.  
  
3.  Затем необходимо определить столбцы, которые будут использоваться при работе с данными в R.  
  Например, в наборе данных небольшого размера нужно только три уровня признаков, поскольку запрос вернет данные только для трех состояний.  Переменную *statesToKeep* можно использовать многократно, чтобы обозначать включаемые уровни.  
  
    ```R  
    importColInfo <- list(   
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),       
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),     
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))   
            )  
  
    ```  
  
4.  Задайте **локальный** контекст вычисления, так как все данные должны быть доступны на локальном компьютере.  
  
    ```R  
    rxSetComputeContext("local")   
    ```  
  
5.  Создайте объект — источник данных, передав все только что определенные переменные в качестве аргументов функции *RxSqlServerData*.  
  
    ```R  
    sqlServerImportDS <- RxSqlServerData(  
        connectionString = sqlConnString,   
        sqlQuery = importQuery,   
        colInfo = importColInfo)  
  
    ```  
  
6.  Затем вызовите функцию *rxImport*, чтобы сохранить данные в текущем рабочем каталоге, в файле с именем `ccFraudSub.xdf`.  
  
    ```R  
    localDS <- rxImport(inData = sqlServerImportDS,   
        outFile = "ccFraudSub.xdf",    
        overwrite = TRUE)  
  
    ```  
  
    Объект *localDs*, возвращенный функцией *rxImport*, является облегченным объектом — источником данных *RxXdfData*, который представляет локально сохраненный на диске файл ccFraud.xdf.  
  
7.  Вызовите функцию *rxGetVarInfo*, указав в качестве цели XDF-файл, чтобы убедиться, что схема данных такая же.  
  
    ```R  
    rxGetVarInfo(data = localDS)   
    ```  
    **Результаты**
    
    *rxGetVarInfo(data = localDS)*    
    *Var 1: gender, Type: factor, no factor levels available (Переменная 1: пол, тип: признак, уровни признаков недоступны)*    
    *Var 2: cardholder, Type: factor, no factor levels available (Переменная 2: держатель карты, тип: признак, уровни признаков недоступны)*    
    *Var 3: balance, Type: integer, Low/High: (0, 22463) (Переменная 3: баланс, тип: целое число, нижнее/верхнее: (0, 22463))*    
    *Var 4: state, Type: factor, no factor levels available (Переменная 4: состояние, тип: признак, уровни признаков недоступны)*
  
8.  Теперь можно вызывать различные функции R, чтобы анализировать объект *localDs* (аналогично анализу источника данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Например:  
  
    ```R  
    rxSummary(~gender + cardholder + balance + state, data = localDS)    
    ```  
  
Теперь, когда вы научились использовать контексты вычисления и работать с различными источниками данных, пора попробовать что-нибудь более интересное.  
  
На последнем занятии вы создадите простую симуляцию с помощью пользовательской функции R и запустите ее на удаленном сервере.  
  
## Следующий шаг  
[Занятие 5. Создание простого моделирования (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/lesson-5-create-a-simple-simulation-data-science-deep-dive.md)  
  
## Предыдущий шаг  
[Занятие 4. Анализ данных в локальном контексте вычисления (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md)  
  
## См. также:  
[Глубокое погружение в обработку и анализ данных: использование пакетов RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
