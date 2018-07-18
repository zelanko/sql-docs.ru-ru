---
title: Перемещение данных между SQL Server и XDF-файла (SQL и R глубокое погружение) | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6eb2ed7bdda7fab662048d7e8da692253cf9c164
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31204596"
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-and-r-deep-dive"></a>Перемещение данных между SQL Server и XDF-файла (SQL и R глубокое погружение)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом шаге вы узнаете, как использовать файл XDF для передачи данных между удаленных и локальных вычислительных контекстов. Хранение данных в файле XDF дает возможность выполнять преобразования данных.

После завершения, можно использовать данные в файле для создания нового [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы. Функция [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) может применить преобразования к данным и выполняет преобразование между блоками данных и xdf-файлов.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Создать таблицу SQL Server из XDF-файла

Для этого упражнения данные кредитной карты мошенничества использовать снова. В этом сценарии вас попросили провести дополнительный анализ данных по пользователям в штатах Калифорния, Орегон и Вашингтон. Чтобы быть более эффективным, вы решили хранения данных только эти состояния на локальном компьютере и работы с только переменные пол, владельца, состояние и баланс.

1. Повторное использование `stateAbb` переменной, созданные ранее для обозначения уровней для включения и записывать их в переменную, `statesToKeep`.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Результаты**
    
    CA|или|WA
    ----|----|----
    5|38|48
    
2. Определите данные, которые необходимо перенести из SQL Server, с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса.  Далее Используйте эту переменную как *inData* аргумент для **rxImport**.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Убедитесь в том, что в запросе нет скрытых символов, например переводов строки или символов табуляции.
  
3. Затем определите столбцы, используемые при работе с данными в R. Например в наборе данных меньше необходимо только три уровня коэффициент, поскольку запрос возвращает данные только три состояния.  Применить `statesToKeep` переменную для идентификации правильного уровней для включения.
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. Задайте для контекста вычислений **локального**, так как вы хотите все доступные данные на локальном компьютере.
  
    ```R
    rxSetComputeContext("local")
    ```
    
    [RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) функции можно импортировать данные из любого поддерживаемого источника данных в локальный файл XDF. Использование локальной копии данных удобно в том случае, если необходимо сделать много различные виды анализа данных, но чтобы избежать повторного запуска тот же запрос.

5. Создайте объект источника данных, передав переменных, определенных ранее в качестве аргументов **RxSqlServerData**.
  
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
  
    `localDs` Объект, возвращаемый **rxImport** функции будет недоступно: **RxXdfData** объект источника данных, представляющий `ccFraud.xdf` файла данных, расположенных на локальном диске.
  
7. Вызовите функцию [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) , указав в качестве цели XDF-файл, чтобы убедиться, что схема данных такая же.
  
    ```R
    rxGetVarInfo(data = localDS)
    ```

    **Результаты**
    
    *rxGetVarInfo(data = localDS)*

    *Var 1: gender, Type: factor, no factor levels available (Переменная 1: пол, тип: признак, уровни признаков недоступны)*

    *Var 2: cardholder, Type: factor, no factor levels available (Переменная 2: держатель карты, тип: признак, уровни признаков недоступны)*

    *Var 3: balance, Type: integer, Low/High: (0, 22463) (Переменная 3: баланс, тип: целое число, нижнее/верхнее: (0, 22463))*

    *Var 4: state, Type: factor, no factor levels available (Переменная 4: состояние, тип: признак, уровни признаков недоступны)*
  
8. Теперь можно вызывать различные функции R для анализа объекта `localDs` так же, как и в случае с источником данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Например может Суммировать по пол:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

Теперь, когда вы научились использовать контексты вычисления и работать с различными источниками данных, пора попробовать что-нибудь более интересное. В разделе Далее и последней создать простой моделирование, которое выполняет пользовательскую функцию R на удаленном сервере.

## <a name="next-step"></a>Следующий шаг

[Создание простого моделирования](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

## <a name="previous-step"></a>Предыдущий шаг

[Анализ данных в локальном контексте вычисления](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)



