---
title: "Запрос и изменение данных SQL Server (глубокое погружение в обработку и анализ данных) | Microsoft Docs"
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
ms.assetid: 8c7007a9-9a8f-4dcd-8068-40060d4f6444
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Запрос и изменение данных SQL Server (глубокое погружение в обработку и анализ данных)
Теперь, когда вы загрузили данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вы можете использовать источники данных, созданные в качестве аргументов функций R в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], для получения основных сведений о переменных и создания сводок и гистограмм.  
  
В этом шаге вы повторно используете источники данных для проведения быстрого анализа и расширения возможностей данных.  
  
## Запрос данных  
Сначала получите список столбцов и их типов данных.  
  
1.  Используйте функцию *rxGetVarInfo* и укажите источник данных, который нужно проанализировать:  
  
    ```R  
    rxGetVarInfo(data = sqlFraudDS)   
    ```  
  
  
**Результаты**  
*Var 1: custID, Тип: integer*  
*Var 2: gender, Тип: integer*  
*Var 3: state, Тип: integer*  
*Var 4: cardholder, Тип: integer*  
*Var 5: balance, Тип: integer*  
*Var 6: numTrans, Тип: integer*  
*Var 7: numIntlTrans, Тип: integer*  
*Var 8: creditLine, Тип: integer*  
*Var 9: fraudRisk, Тип: integer*  
  
## Изменение метаданных  
Все переменные хранятся как целочисленные, но некоторые из них представляют категориальные данные — в языке R они называются *факторными переменными*. Например, столбец *state* содержит числа, представляющие идентификаторы 50 штатов, а также округа Колумбия.  Чтобы упростить понимание данных, замените числа списком сокращений, обозначающих штаты.  
  
На этом этапе необходимо указать вектор строк, содержащий эти сокращения, а затем сопоставить эти категориальные значения исходным целочисленным идентификаторам. Когда эта переменная будет готова, она отобразится в аргументе *colInfo*, указывая на то, что этот столбец будет обрабатываться как коэффициент. Следовательно, при анализе или импорте данных будут использоваться эти сокращения, а столбец будет обрабатываться как коэффициент.  
  
1.  Сначала создайте переменную R с именем *stateAbb* и определите вектор строк, который следует в нее добавить, следующим образом:  
  
    ```R  
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",     
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",   
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",   
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",   
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")  
  
    ```  
  
2.  Затем создайте объект сведений о столбце с именем *ccColInfo*, в котором задается сопоставление существующих целочисленных значений категориальным уровням (сокращенным названиям штатов).  
  
    Эта инструкция также создает факторные переменные для gender и cardholder.  
  
    ```R  
    ccColInfo <- list(
    gender = list(
              type = "factor",
              levels = c("1", "2"), 
              newLevels = c("Male", "Female")
              ),
    cardholder = list(
                  type = "factor",
                  levels = c("1", "2"),
                  newLevels = c("Principal", "Secondary")
                   ),
    state = list(
             type = "factor",
             levels = as.character(1:51), 
             newLevels = stateAbb
             ),
    balance = list(type = "numeric")
    )  

    ```  
  
3.  Для создания источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], использующего обновленные данные, вызовите функцию *RxSqlServerData* как раньше, но добавьте в нее аргумент *colInfo*.  
  
    ```R  
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,  
    table = sqlFraudTable, colInfo = ccColInfo,  
    rowsPerRead = sqlRowsPerRead)   
    ```  
  
    -   Для параметра *table* передайте переменную *sqlFraudTable*, которая содержит созданный ранее источник данных.    
    -   Для параметра *colInfo* передайте переменную *ccColInfo*, которая содержит типы данных столбцов и уровни коэффициентов.
    -   Сопоставление столбца сокращениям перед использованием столбца в качестве коэффициента также способствует повышению производительности. Дополнительные сведения см. в разделе [Язык R и оптимизация данных](https://msdn.microsoft.com/library/mt723575.aspx).  
  
4.  Теперь с помощью функции *rxGetVarInfo* можно просматривать переменные в новом источнике данных.  
  
    ```R  
    rxGetVarInfo(data = sqlFraudDS)   
    ```  
  
**Результаты**  
  
*Var 1: custID, Тип: integer*  
*Var 2: gender       2 уровня факторов: Male Female*  
*Var 3: state       51 уровень факторов: AK AL AR AZ CA ... VT WA WI WV WY*  
*Var 4: cardholder       2 уровня факторов: Principal Secondary*  
*Var 5: balance, Тип: integer*  
*Var 6: numTrans, Тип: integer*  
*Var 7: numIntlTrans, Тип: integer*  
*Var 8: creditLine, Тип: integer*  
*Var 9: fraudRisk, Тип: integer*  
  
Теперь три указанные вами переменные (_gender_, _state_ и _cardholder_) обрабатываются как факторы.  
  
## Следующий шаг  
[Определение и использование контекстов вычисления (глубокое погружение в обработку и анализ данных)](../../advanced-analytics/r-services/define-and-use-compute-contexts-data-science-deep-dive.md)  
  
## Предыдущий шаг  
[Создание объектов данных SQL Server с помощью функции RxSqlServerData](../../advanced-analytics/r-services/create-sql-server-data-objects-using-rxsqlserverdata.md)  
  
## См. также:  
[Глубокое погружение в обработку и анализ данных: использование пакетов RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
