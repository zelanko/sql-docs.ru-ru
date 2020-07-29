---
title: Изменение данных SQL с помощью RevoScaleR
description: Учебник по RevoScaleR, часть 3. Сведения о запросах к данным и изменении данных с помощью языка R в SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7fda48d4d59ab66ae285e4aeda1899a214a5b901
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85679898"
---
# <a name="query-and-modify-the-sql-server-data-sql-server-and-revoscaler-tutorial"></a>Запрос и изменение данных SQL Server (учебник по SQL Server и RevoScaleR)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Эта часть 3 входит в состав [серии учебников по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), посвященной использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

В предыдущем учебнике вы загрузили данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Теперь вы сможете изучить и изменить данные с помощью **RevoScaleR**:

> [!div class="checklist"]
> * Получение основных сведений о переменных
> * Создание категориальных данных из необработанных данных

Категориальные данные или *факторные переменные* помогают визуализировать произвольные данные. Их можно использовать как входных данных для гистограмм, чтобы получить представление о переменных данных.

## <a name="query-for-columns-and-types"></a>Запрос столбцов и типов

Для выполнения скрипта R используйте IDE R или RGui.exe. 

Сначала получите список столбцов и их типов данных. Можно использовать функцию [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) и указать источник данных, которые нужно проанализировать. В зависимости от версии **RevoScaleR** можно также использовать [rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames). 
  
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

Все переменные хранятся как целочисленные, но некоторые из них представляют категориальные данные — в языке R они называются *факторными переменными*. Например, столбец *state* содержит числа, представляющие идентификаторы 50 штатов, а также округа Колумбия. Чтобы упростить понимание данных, замените числа списком сокращений, обозначающих штаты.

На этом этапе вы создадите вектор строк, содержащий эти сокращения, а затем сопоставите эти категориальные значения с исходными целочисленными идентификаторами. Затем вы добавите новую переменную в аргумент *colInfo*, чтобы указать, что этот столбец будет обрабатываться как коэффициент. При анализе данных или перемещении данных используются аббревиатуры, а столбец обрабатывается как коэффициент.

Сопоставление столбца сокращениям перед использованием столбца в качестве коэффициента также способствует повышению производительности. Дополнительные сведения см. в разделе [Язык R и оптимизация данных](../r/r-and-data-optimization-r-services.md).

1. Сначала создайте переменную R с именем *stateAbb* и определите вектор строк, который следует в нее добавить, следующим образом:
  
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
  
3. Для создания источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], использующего обновленные данные, вызовите функцию **RxSqlServerData** как раньше, но добавьте в нее аргумент *colInfo*.
  
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

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Определение и использование контекстов вычисления](../../machine-learning/tutorials/deepdive-define-and-use-compute-contexts.md)