---
title: "Запрашивать и изменять данные SQL Server (SQL и R глубокое погружение) | Документы Microsoft"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: 8c7007a9-9a8f-4dcd-8068-40060d4f6444
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 38273ac15673344ff00714d38ec87386ca5dae64
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="query-and-modify-the-sql-server-data-sql-and-r-deep-dive"></a>Запрашивать и изменять данные SQL Server (SQL и R глубокое погружение)

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Теперь, когда вы загрузили данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вы можете использовать источники данных, созданные в качестве аргументов функций R в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], для получения основных сведений о переменных и создания сводок и гистограмм.

На этом этапе, повторно использовать источники данных для анализа и затем улучшен данные.

## <a name="query-the-data"></a>Запрос данных

Сначала получите список столбцов и их типов данных.

1.  Используйте функцию [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) и укажите источник данных, который требуется проанализировать.

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


## <a name="modify-metadata"></a>Изменения метаданных

Все переменные хранятся как целочисленные, но некоторые из них представляют категориальные данные — в языке R они называются *факторными переменными* . Например, столбец *state* содержит числа, представляющие идентификаторы 50 штатов, а также округа Колумбия.  Чтобы упростить понимание данных, замените числа списком сокращений, обозначающих штаты.

На этом шаге создания строки вектор, содержащий сокращения и затем сопоставить эти категориальных значений исходного целочисленных идентификаторов. Затем с помощью новой переменной в *colInfo* аргумент, чтобы указать, что этот столбец будет обрабатываться как коэффициент. Каждый раз, когда нужно анализировать данные, или переместить его, сокращения используются, и столбец будет обрабатываться как фактор.

Сопоставление столбца сокращениям перед использованием столбца в качестве коэффициента также способствует повышению производительности. Дополнительные сведения см. в разделе [R и данные оптимизации](..\r\r-and-data-optimization-r-services.md).

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

[Определение и использование контекстов вычисления](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание объектов данных SQL Server с помощью функции RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
