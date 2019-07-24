---
title: Запрос и изменение данных SQL Server с помощью RevoScaleR
description: Пошаговое руководство по запросу и изменению данных с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0784f10bfc4405ce17e365b6afcb596fa534202d
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344657"
---
# <a name="query-and-modify-the-sql-server-data-sql-server-and-revoscaler-tutorial"></a>Запрос и изменение данных SQL Server (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [учебника RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На предыдущем занятии вы загрузили данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. На этом шаге вы можете просматривать и изменять данные с помощью **RevoScaleR**:

> [!div class="checklist"]
> * Возвращает основные сведения о переменных
> * Создание данных о категориях на основе необработанных данных

Данные по категориям или значения коэффициентов полезны для визуализации произвольных данных. Их можно использовать в качестве входных данных для гистограмм, чтобы понять, как выглядят переменные данные.

## <a name="query-for-columns-and-types"></a>Запрос столбцов и типов

Используйте R IDE или RGui. exe для выполнения скрипта R. 

Сначала получите список столбцов и их типов данных. Можно использовать функцию [функцию rxgetvarinfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) и указать источник данных, который нужно проанализировать. В зависимости от версии **RevoScaleR**можно также использовать [рксжетварнамес](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames). 
  
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

## <a name="create-categorical-data"></a>Создание данных по категориям

Все переменные хранятся в виде целых чисел, но некоторые переменные представляют данные по категориям,  называемые переменными коэффициента в R. Например, *состояние* столбца содержит числа, используемые в качестве идентификаторов для состояний 50 плюс округ Колумбия. Чтобы упростить понимание данных, замените числа списком сокращений, обозначающих штаты.

На этом шаге вы создадите строковый вектор, содержащий аббревиатуры, а затем сопоставьте эти значения категорий с исходными целочисленными идентификаторами. Затем используйте новую переменную в аргументе *colInfo* , чтобы указать, что этот столбец должен обрабатываться как фактор. При анализе данных или их перемещении используются аббревиатуры, а столбец обрабатывается как фактор.

Сопоставление столбца сокращениям перед использованием столбца в качестве коэффициента также способствует повышению производительности. Дополнительные сведения см. в разделе [R and Data Optimization](../r/r-and-data-optimization-r-services.md).

1. Начните с создания переменной R *stateAbb*и определения вектора строк для добавления в нее, как показано ниже.
  
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
  
3. Чтобы создать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источник данных, использующий обновленные данные, вызовите функцию **RxSqlServerData** , как и раньше, но добавьте аргумент *colInfo* .
  
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