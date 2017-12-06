---
title: "Перемещение данных между SQL Server и файлом XDF. | Документы Microsoft"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 40887cb3-ffbb-4769-9f54-c006d7f4798c
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a140cc358afab1f1ff324e0a47ed67501ee75e23
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="move-data-between-sql-server-and-xdf-file"></a>Перенос данных между SQL Server и файлом XDF

При работе в локальный контекст вычислений имеется доступ к обоих локальными файлами данных и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных (определяется как источник данных RxSqlServerData).

В этом разделе вы узнаете, как получить данные и сохранить их в файле на локальном компьютере, чтобы получить возможность преобразовывать данные. Когда закончите, будет использовать данные в файле для создания нового [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы, с помощью rxDataStep.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Создание таблицы SQL Server на основе файла XDF

Функция rxImport позволяет импортировать данные из любого поддерживаемого источника данных в локальный файл XDF. Использование локального файла может быть удобным, если требуется проанализировать данные, хранящиеся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , множеством различных способов и вы хотите избежать выполнения одного и того же запроса много раз.

В этом упражнении вы снова будете использовать данные по мошенничеству с кредитными картами. В этом сценарии вас попросили провести дополнительный анализ данных по пользователям в штатах Калифорния, Орегон и Вашингтон. Чтобы повысить эффективность, вы решили сохранить на локальном компьютере данные только по этим штатам и работать с переменными gender, cardholder, state и balance.

1. Используйте ранее созданный вектор *stateAbb* , чтобы определить уровни, которые необходимо включить, а затем отобразите на консоли новую переменную *statesToKeep*.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Результаты**
    
    CA|или|WA
    ----|----|----
    5|38|48
    
2. Теперь будут определены данные, переносимые с сервера SQL Server, при помощи запроса [!INCLUDE[tsql](../../includes/tsql-md.md)] .  В дальнейшем эта переменная будет использоваться в качестве аргумента *inData* функции *rxImport*.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Убедитесь в том, что в запросе нет скрытых символов, например переводов строки или символов табуляции.
  
3. Далее следует определить столбцы, используемые при работе с данными в R. Например в наборе данных меньше необходимо только три уровня коэффициент, так как запрос будет возвращать данные только три состояния.  Переменную *statesToKeep* можно использовать многократно, чтобы обозначать включаемые уровни.
  
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
  
5. Создайте объект источника данных путем передачи все переменные, определенные как аргументы для RxSqlServerData.
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. Затем вызовите метод **rxImport** для записи данных в файл с именем `ccFraudSub.xdf`, в текущем рабочем каталоге.
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    *LocalDs* объект, возвращаемый функцией rxImport является упрощенная RxXdfData объект источника данных, представляющий ccFraud.xdf файла данных, расположенных на локальном диске.
  
7. Вызовите rxGetVarInfo XDF-файл, убедитесь, что схема данных.
  
    ```R
    rxGetVarInfo(data = localDS)
    ```

    **Результаты**
    
    *rxGetVarInfo(data = localDS)*

    *Var 1: gender, Type: factor, no factor levels available (Переменная 1: пол, тип: признак, уровни признаков недоступны)*

    *Var 2: cardholder, Type: factor, no factor levels available (Переменная 2: держатель карты, тип: признак, уровни признаков недоступны)*

    *Var 3: balance, Type: integer, Low/High: (0, 22463) (Переменная 3: баланс, тип: целое число, нижнее/верхнее: (0, 22463))*

    *Var 4: state, Type: factor, no factor levels available (Переменная 4: состояние, тип: признак, уровни признаков недоступны)*
  
8. Теперь можно вызывать различные функции R, чтобы анализировать объект *localDs* (аналогично анализу источника данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Например:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

Теперь, когда вы научились использовать контексты вычисления и работать с различными источниками данных, пора попробовать что-нибудь более интересное. На последнем занятии вы создадите простую симуляцию с помощью пользовательской функции R и запустите ее на удаленном сервере.

## <a name="next-step"></a>Следующий шаг

[Создание простого моделирования](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

## <a name="previous-step"></a>Предыдущий шаг

[Анализ данных в локальном контексте](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)



