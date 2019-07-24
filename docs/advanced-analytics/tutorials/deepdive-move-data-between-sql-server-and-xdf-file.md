---
title: Перемещение данных между файлами SQL Server и Xdf-с помощью RevoScaleR
description: Пошаговое руководство по перемещению данных с помощью Xdf-и языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0e4c0fbdd9f625886a7d38fc80895e9f4407ce88
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344749"
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-server-and-revoscaler-tutorial"></a>Перемещение данных между SQL Server и файлом Xdf-(учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [учебника RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом шаге вы узнаете, как использовать файл Xdf-для перемещения данных между удаленными и локальными контекстами вычислений. Хранение данных в файле Xdf-позволяет выполнять преобразования данных.

Когда все будет готово, используйте данные в файле для создания новой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы. Функция [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) может применять преобразования к данным и выполняет преобразование между кадрами данных и файлами Xdf-.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Создание SQL Server таблицы из файла Xdf-

В этом упражнении вы снова используете данные мошенничества с кредитными картами. В этом сценарии вас попросили провести дополнительный анализ данных по пользователям в штатах Калифорния, Орегон и Вашингтон. Для повышения эффективности вы решили хранить данные только для этих штатов на локальном компьютере и работать только с переменными, пол, владелец, штат и баланс.

1. Повторно используйте `stateAbb` созданную ранее переменную, чтобы указать уровни для включения, и запишите их в новую `statesToKeep`переменную.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Результаты**
    
    CA|OR|WA
    ----|----|----
    5|38|48
    
2. Укажите данные, которые необходимо перенести из SQL Server с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса.  Позже эта переменная будет использоваться в качестве аргумента *данных* для **rxImport**.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Убедитесь в том, что в запросе нет скрытых символов, например переводов строки или символов табуляции.
  
3. Далее определите столбцы, используемые при работе с данными в R. Например, в наборе данных меньшего размера необходимы только три уровня множителя, поскольку запрос возвращает данные только для трех состояний.  Примените `statesToKeep` переменную, чтобы указать нужные уровни для включения.
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. Задайте для контекста вычислений значение **локальный**, поскольку все данные должны быть доступны на локальном компьютере.
  
    ```R
    rxSetComputeContext("local")
    ```
    
    Функция [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) может импортировать данные из любого поддерживаемого источника данных в локальный файл Xdf-. Использование локальной копии данных удобно, когда требуется выполнить много различных анализов данных, но нужно избегать выполнения одного и того же запроса.

5. Создайте объект источника данных, передав переменные, ранее определенные в качестве аргументов в **RxSqlServerData**.
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. Вызовите **rxImport** , чтобы записать данные в файл с `ccFraudSub.xdf`именем в текущем рабочем каталоге.
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    Объект, возвращаемый функцией **rxImport** , представляет собой облегченный объект источника `ccFraud.xdf` данных RxXdfData, представляющий файл данных, хранящийся локально на диске.  `localDs`
  
7. Вызовите функцию [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) , указав в качестве цели XDF-файл, чтобы убедиться, что схема данных такая же.
  
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

8. Теперь можно вызывать различные функции R для анализа объекта **локалдс** так же, как и исходные данные на SQL Server. Например, вы можете суммировать данные по полу:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

## <a name="next-steps"></a>Следующие шаги

На этом занятии серия многокомпонентных руководств посвящена **RevoScaleR** и SQL Server. В нем представлено множество связанных с данными и вычислительных концепций, предоставляющая основу для перехода к собственным требованиям к данным и проекту.

Чтобы углубить знания о **RevoScaleR**, можно вернуться к списку учебников R, чтобы проанализировать все упражнения, которые могли быть пропущены. Кроме того, дополнительные сведения о общих задачах см. в статьях с инструкциями в содержании.

> [!div class="nextstepaction"]
> [Учебные материалы по R в SQL Server](sql-server-r-tutorials.md)