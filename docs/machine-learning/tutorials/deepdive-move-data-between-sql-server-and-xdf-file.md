---
title: Перенос данных с помощью файла XDF
description: Учебник по RevoScaleR, часть 13. Сведения о переносе данных с помощью XDF-файла и языка R в SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9c7e5ce4cbe995fd677acd406187dfaf264a7461
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85680002"
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-server-and-revoscaler-tutorial"></a>Перенос данных между SQL Server и файлом XDF (учебник по SQL Server и RevoScaleR)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Эта часть 13 входит в состав [серии учебников по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), посвященной использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

В этом учебнике вы узнаете, как использовать XDF-файл для передачи данных между удаленным и локальным контекстами вычисления. Хранение данных в файле XDF позволяет выполнять их преобразование.

По завершении этой процедуры вы используете данные в файле для создания таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Функция [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) может применять преобразования к данным и преобразовывать кадры данных в файлы XDF и наоборот.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Создание таблицы SQL Server на основе файла XDF

В этом упражнении вы снова будете использовать данные по мошенничеству с кредитными картами. В этом сценарии вас попросили провести дополнительный анализ данных по пользователям в штатах Калифорния, Орегон и Вашингтон. Чтобы повысить эффективность, вы решили сохранить на локальном компьютере данные только по этим штатам и работать с переменными gender, cardholder, state и balance.

1. Повторно используйте ранее созданную переменную `stateAbb` для определения уровней, которые необходимо включить, а затем запишите их в новую переменную `statesToKeep`.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Результаты**
    
    CA|OR|WA
    ----|----|----
    5|38|48
    
2. Определите данные, которые нужно перенести с сервера SQL Server, с помощью запроса [!INCLUDE[tsql](../../includes/tsql-md.md)].  В дальнейшем эта переменная будет использоваться в качестве аргумента *inData* функции **rxImport**.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Убедитесь в том, что в запросе нет скрытых символов, например переводов строки или символов табуляции.
  
3. Затем определите столбцы, которые будут использоваться при работе с данными в R. Например, в наборе данных небольшого размера нужно только три уровня признаков, так как запрос вернет данные только для трех состояний.  Примените переменную `statesToKeep` для определения включаемых уровней.
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. Задайте **локальный** контекст вычисления, так как все данные должны быть доступны на локальном компьютере.
  
    ```R
    rxSetComputeContext("local")
    ```
    
    Функция [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) позволяет импортировать данные из любого поддерживаемого источника данных в локальный XDF-файл. Использовать локальную копию данных удобно, если требуется проанализировать данные множеством различных способов и вы хотите избежать многократного выполнения одного и того же запроса.

5. Создайте объект-источник данных, передав ранее определенные переменные в качестве аргументов функции **RxSqlServerData**.
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. Вызовите функцию **rxImport**, чтобы записать данные в файл с именем `ccFraudSub.xdf` в текущем рабочем каталоге.
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    Объект `localDs`, возвращенный функцией **rxImport**, является облегченным объектом-источником данных **RxXdfData**, который представляет локально сохраненный на диске файл данных `ccFraud.xdf`.
  
7. Вызовите функцию [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf), указав в качестве цели XDF-файл, чтобы убедиться, что схема данных такая же.
  
    ```R
    rxGetVarInfo(data = localDS)
    ```

    **Результаты**
    
    ```R
    rxGetVarInfo(data = localDS)
    Var 1: gender, Type: factor, no factor levels available
    Var 2: cardholder, Type: factor, no factor levels available
    Var 3: balance, Type: integer, Low/High: (0, 22463)
    Var 4: state, Type: factor, no factor levels available
    ```

8. Теперь можно вызывать различные функции R, чтобы анализировать объект **localDs** (аналогично анализу источника данных в SQL Server). Например, можно свести данные по полу:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

## <a name="next-steps"></a>Дальнейшие действия

Этот учебник завершает серию, посвященную **RevoScaleR** и SQL Server. В них было представлено множество понятий, связанных с данными и вычислениями, и был заложен фундамент для дальнейшей работы с учетом ваших собственных проектных требований.

Чтобы углубить знания о **RevoScaleR**, можно вернуться к списку учебников по R и пройти упражнения, которые вы могли пропустить. Кроме того, можно обратиться к практическим руководствам в содержании, чтобы получить сведения об общих задачах.

> [!div class="nextstepaction"]
> [Учебные материалы по R в SQL Server](sql-server-r-tutorials.md)