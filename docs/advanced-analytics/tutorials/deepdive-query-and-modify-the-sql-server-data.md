---
title: "Запрашивать и изменять данные SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 8c7007a9-9a8f-4dcd-8068-40060d4f6444
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: db6a2ee4c642ca6e868170629460c4722020d935
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="query-and-modify-the-sql-server-data"></a>Запрос и изменение данных SQL Server

Теперь, когда вы загрузили данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вы можете использовать источники данных, созданные в качестве аргументов функций R в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], для получения основных сведений о переменных и создания сводок и гистограмм.

На этом шаге будет повторно использовать источники данных для анализа и затем улучшен данные.

## <a name="query-the-data"></a>Запрос данных

Сначала получите список столбцов и их типов данных.

1.  Используйте функцию **rxGetVarInfo** и укажите источник данных, который требуется проанализировать.
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **Результаты**
    
    *Var 1: custID, Тип: integer*
    
    *Var 2: gender, Тип: integer*
    
    *Var 3: state, Тип: integer*
    
    *Var 4: cardholder, Тип: integer*
    
    *Var 5: balance, Тип: integer*
    
    *Var 6: numTrans, Тип: integer*
    
    *Var 7: numIntlTrans, Тип: integer*
    
    *Var 8: creditLine, Тип: integer*
    
    *Var 9: fraudRisk, Тип: integer*


## <a name="modify-metadata"></a>Изменение метаданных

Все переменные хранятся как целочисленные, но некоторые из них представляют категориальные данные — в языке R они называются *факторными переменными* . Например, столбец *state* содержит числа, представляющие идентификаторы 50 штатов, а также округа Колумбия.  Чтобы упростить понимание данных, замените числа списком сокращений, обозначающих штаты.

На этом этапе необходимо указать вектор строк, содержащий эти сокращения, а затем сопоставить эти категориальные значения исходным целочисленным идентификаторам. Когда эта переменная будет готова, она отобразится в аргументе *colInfo* , указывая на то, что этот столбец будет обрабатываться как коэффициент. Следовательно, при анализе или импорте данных будут использоваться эти сокращения, а столбец будет обрабатываться как коэффициент.

1. Сначала создайте переменную R с именем *stateAbb*и определите вектор строк, который следует в нее добавить, следующим образом:
  
    ```R
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")
    ```

2. Затем создайте объект сведений о столбце с именем *ccColInfo*, в котором задается сопоставление существующих целочисленных значений категориальным уровням (сокращенным названиям штатов).
  
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
  
3. Для создания источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использующего обновленные данные, вызовите функцию *RxSqlServerData* как раньше, но добавьте в нее аргумент *colInfo* .
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - Для параметра *table* передайте переменную *sqlFraudTable*, которая содержит созданный ранее источник данных.
    - Для параметра *colInfo* передайте переменную *ccColInfo* , которая содержит типы данных столбцов и уровни коэффициентов.
    - Сопоставление столбца сокращениям перед использованием столбца в качестве коэффициента также способствует повышению производительности. Дополнительные сведения см. в разделе [Язык R и оптимизация данных](https://msdn.microsoft.com/library/mt723575.aspx).
  
4.  Теперь можно использовать функцию rxGetVarInfo для просмотра переменных в новом источнике данных.
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **Результаты**
    
    *Var 1: custID, Тип: integer*
    
    *Var 2: коэффициент уровней пола: Male Женский*
    
    *Var 3: состояние 51 коэффициент уровни: AK AL AR AZ ЦС... VT WA WI WV WY*
    
    *Var 4: 2 владельца карты коэффициент уровни: получатель участника*
    
    *Var 5: balance, Тип: integer*
    
    *Var 6: numTrans, Тип: integer*
    
    *Var 7: numIntlTrans, Тип: integer*
    
    *Var 8: creditLine, Тип: integer*
    
    *Var 9: fraudRisk, Тип: integer*

Теперь три указанные вами переменные (_gender_, _state_и _cardholder_) обрабатываются как факторы.

## <a name="next-step"></a>Следующий шаг

[Определение и использование контекстов вычислений](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание объектов данных SQL Server с помощью функции RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)



