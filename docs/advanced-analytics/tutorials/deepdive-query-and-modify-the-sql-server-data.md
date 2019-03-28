---
title: Запрос и изменение данных SQL Server, с помощью RevoScaleR - машинного обучения SQL Server
description: Руководство о том, как запрашивать и изменять данные с помощью языка R в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 6d2768399ecd3d504e5bc51d4c7cbd151488782a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513141"
---
# <a name="query-and-modify-the-sql-server-data-sql-server-and-revoscaler-tutorial"></a>Запрос и изменение данных SQL Server (руководство по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

В предыдущем уроке вы загрузили данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. На этом этапе могут просматривать и изменять данные при помощи **RevoScaleR**:

> [!div class="checklist"]
> * Возвращает основные сведения о переменных
> * Создание категориальные данные из необработанных данных

Категориальные данные или *переменными*, полезны для визуализации данных произвольного тестирования. Их можно использовать как входные данные гистограммы, чтобы получить представление о том, как выглядят данные переменной.

## <a name="query-for-columns-and-types"></a>Запрос для столбцов и типов

Используйте для запуска скрипта R R IDE или RGui.exe. 

Сначала получите список столбцов и их типов данных. Можно использовать функцию [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) и укажите источник данных, которые необходимо проанализировать. В зависимости от используемой версии **RevoScaleR**, можно также использовать [rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames). 
  
```R
rxGetVarInfo(data = sqlFraudDS)
```

**Результаты**

```R
Var 1: custID, Type: integer
Var 2: gender, Type: integer
Var 3: state, Type: integer
Var 4: cardholder, Type: integer
Var 5: balance, Type: integer
Var 6: numTrans, Type: integer
Var 7: numIntlTrans, Type: integer
Var 8: creditLine, Type: integer
Var 9: fraudRisk, Type: integer
```

## <a name="create-categorical-data"></a>Создание категориальных данных

Все переменные хранятся как целочисленные, но некоторые из них представляют категориальные данные, называемые *переменными* в R. Например, столбец *состояние* содержит числа, которые используются в качестве идентификаторов для 50 штатов, а также округа Колумбия. Чтобы упростить понимание данных, замените числа списком сокращений, обозначающих штаты.

На этом шаге Создайте строковый вектор, содержащий эти сокращения и затем сопоставить эти категориальные значения исходным целочисленным идентификаторам. Затем используйте новую переменную в *colInfo* аргумента, чтобы указать, что этот столбец будет обрабатываться как коэффициент. Каждый раз, когда анализ данных или переместить его, используются эти сокращения, и столбец будет обрабатываться как коэффициент.

Сопоставление столбца сокращениям перед использованием столбца в качестве коэффициента также способствует повышению производительности. Дополнительные сведения см. в разделе [R и данных оптимизации](../r/r-and-data-optimization-r-services.md).

1. Сначала создайте переменную R *stateAbb*и определите вектор строк, чтобы добавить к нему, как показано ниже.
  
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
  
3. Чтобы создать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных, использующего обновленные данные, вызовите **RxSqlServerData** работать по-прежнему, но добавить *colInfo* аргумент.
  
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
    
    ```R
    Var 1: custID, Type: integer
    Var 2: gender  2 factor levels: Male Female
    Var 3: state   51 factor levels: AK AL AR AZ CA ... VT WA WI WV WY
    Var 4: cardholder  2 factor levels: Principal Secondary
    Var 5: balance, Type: integer
    Var 6: numTrans, Type: integer
    Var 7: numIntlTrans, Type: integer
    Var 8: creditLine, Type: integer
    Var 9: fraudRisk, Type: integer
    ```

Теперь три указанные вами переменные (*gender*, *state*и *cardholder*) обрабатываются как факторы.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Определение и использование контекстов вычисления](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)