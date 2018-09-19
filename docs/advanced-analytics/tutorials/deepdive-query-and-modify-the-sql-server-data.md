---
title: Запрос и изменение данных SQL Server (SQL и R глубокое погружение в обработку) | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 57fff9b8ddfd6507876bd6eb174a127d70d0b916
ms.sourcegitcommit: aa9d2826e3c451f4699c0e69c9fcc8a2781c6213
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45975653"
---
# <a name="query-and-modify-the-sql-server-data-sql-and-r-deep-dive"></a>Запрос и изменение данных SQL Server (SQL и R глубокое погружение в обработку)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья входит углубленное рассмотрение обработки и анализа данных руководства по использованию [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Теперь, когда вы загрузили данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вы можете использовать источники данных, созданные в качестве аргументов функций R в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], для получения основных сведений о переменных и создания сводок и гистограмм.

На этом шаге вы повторно использовать источники данных для проведения быстрого анализа и расширения возможностей данных.

## <a name="query-the-data"></a>Запрос данных

Сначала получите список столбцов и их типов данных.

1.  Используйте функцию [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) и укажите источник данных, которые необходимо проанализировать.

    В зависимости от установленной версии RevoScaleR, можно также использовать [rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames). 
  
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

Все переменные хранятся как целочисленные, но некоторые из них представляют категориальные данные, называемые *переменными* в R. Например, столбец *состояние* содержит числа, которые используются в качестве идентификаторов для 50 штатов, а также округа Колумбия.  Чтобы упростить понимание данных, замените числа списком сокращений, обозначающих штаты.

На этом шаге Создайте строковый вектор, содержащий эти сокращения и затем сопоставить эти категориальные значения исходным целочисленным идентификаторам. Затем используйте новую переменную в *colInfo* аргумента, чтобы указать, что этот столбец будет обрабатываться как коэффициент. Каждый раз, когда анализ данных или переместить его, используются эти сокращения, и столбец будет обрабатываться как коэффициент.

Сопоставление столбца сокращениям перед использованием столбца в качестве коэффициента также способствует повышению производительности. Дополнительные сведения см. в разделе [R и данных оптимизации](..\r\r-and-data-optimization-r-services.md).

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
  
3. Для создания источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использующего обновленные данные, вызовите функцию **RxSqlServerData** как раньше, но добавьте в нее аргумент *colInfo* .
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - Для параметра *table* передайте переменную *sqlFraudTable*, которая содержит созданный ранее источник данных.
    - Для параметра *colInfo* передайте переменную *ccColInfo* , которая содержит типы данных столбцов и уровни коэффициентов.

4.  Теперь с помощью функции **rxGetVarInfo** можно просматривать переменные в новом источнике данных.
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **Результаты**
    
    *Var 1: custID, Тип: integer*
    
    *Var 2: gender 2 уровня факторов: Male Female*
    
    *Var 3: state 51 уровень факторов: AK AL AR AZ CA... VT WA WI WV WY*
    
    *Var 4: cardholder 2 уровня факторов: Principal Secondary*
    
    *Var 5: balance, Тип: integer*
    
    *Var 6: numTrans, Тип: integer*
    
    *Var 7: numIntlTrans, Тип: integer*
    
    *Var 8: creditLine, Тип: integer*
    
    *Var 9: fraudRisk, Тип: integer*

Теперь три указанные вами переменные (_gender_, _state_и _cardholder_) обрабатываются как факторы.

## <a name="next-step"></a>Следующий шаг

[Определение и использование контекстов вычисления](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание объектов данных SQL Server с помощью функции RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
