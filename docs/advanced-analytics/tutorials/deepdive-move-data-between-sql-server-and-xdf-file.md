---
title: Перемещение данных между SQL Server и файлом XDF, с помощью RevoScaleR - машинного обучения SQL Server
description: Руководство по переносу данных с использованием XDF и языка R в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 40852f62cc985f300d04eac4dbef5810f823e124
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512311"
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-server-and-revoscaler-tutorial"></a>Перемещение данных между SQL Server и файлом XDF (руководство по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом шаге Узнайте, как использовать файл XDF для передачи данных между удаленных и локальных вычислительных контекстов. Сохранение данных в файл XDF позволяет выполнять преобразования данных.

Когда все будет готово, можно использовать данные в файле для создания нового [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы. Функция [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) может применить преобразования к данным и выполняет преобразование между кадрами данных и xdf-файлов.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Создание таблицы SQL Server на основе файла XDF

В этом упражнении вы кредитной карты мошенничества снова использовать данные. В этом сценарии вас попросили провести дополнительный анализ данных по пользователям в штатах Калифорния, Орегон и Вашингтон. Чтобы быть более эффективным, вы решили хранить данные для только эти состояния на локальном компьютере и работать с только переменными gender, cardholder, state и баланс.

1. Повторное использование `stateAbb` переменной, которую вы создали ранее для определения уровней, которые необходимо включить и их записи в переменную, `statesToKeep`.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Результаты**
    
    CA|OR|WA
    ----|----|----
    5|38|48
    
2. Определение данных, которые вы хотите перенести из SQL Server, с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса.  Далее Используйте эту переменную в качестве *inData* аргумент для **rxImport**.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Убедитесь в том, что в запросе нет скрытых символов, например переводов строки или символов табуляции.
  
3. Затем определите столбцы для использования при работе с данными в R. Например в наборе данных меньшего размера, необходимо только три уровня признаков, так как запрос возвращает данные только для трех состояний.  Применить `statesToKeep` переменную для определения соответствующих уровней для включения.
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. Задайте контекст вычислений для **локального**, так как вы хотите все данные, доступные на локальном компьютере.
  
    ```R
    rxSetComputeContext("local")
    ```
    
    [RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) функции можно импортировать данные из любого поддерживаемого источника данных в локальный файл XDF. Использование локальной копии данных удобно в том случае, если вы хотите сделать многие различные операции анализа данных, но не выполняя тот же запрос снова и снова.

5. Создайте объект источника данных, передав переменные, определенные ранее в качестве аргументов **RxSqlServerData**.
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. Вызовите **rxImport** для записи данных в файл с именем `ccFraudSub.xdf`, в текущем рабочем каталоге.
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    `localDs` Объект, возвращаемый **rxImport** функция является упрощенная **RxXdfData** объект источника данных, представляющий `ccFraud.xdf` файла данных, расположенных на локальном диске.
  
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

8. Теперь можно вызвать различные функции R для анализа **localDs** объекта, так же, как с исходными данными на сервере SQL Server. Например может получить сводку по полу:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

## <a name="next-steps"></a>Следующие шаги

Это занятие завершает нескольких частях серии руководств на **RevoScaleR** и SQL Server. Он был представлен множество связанных с данными и вычислительные основные понятия, они предоставляют основу для дальнейшее развитие вместе с вашими требованиями данных и проектов.

Улучшить свои знания о **RevoScaleR**, вы можете вернуться к списку учебники R для пошагового выполнения любой упражнения, вы не решены. Кроме того просмотрите инструкции в таблице, содержащих сведения о типовых задач.

> [!div class="nextstepaction"]
> [Учебные материалы по R в SQL Server](sql-server-r-tutorials.md)