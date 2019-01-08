---
title: Определение и использование контекстов вычислений RevoScaleR - машинного обучения SQL Server
description: Руководство о том, как для определения контекста вычисления, используя язык R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c0ae593264abad52873cfc152da721b6c0867109
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645091"
---
# <a name="define-and-use-compute-contexts-sql-server-and-revoscaler-tutorial"></a>Определение и использование контекстов вычислений (руководство по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

В предыдущем уроке вы использовали **RevoScaleR** функции для проверки объектов данных. В этом уроке рассматривается [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) функцию, которая позволяет определить контекст вычисления для удаленный экземпляр SQL Server. Контекст удаленных вычислений вы можете сместить выполнения R из локального сеанса в удаленный сеанс на сервере. 

> [!div class="checklist"]
> * Узнайте, что контекст вычислений элементы удаленный экземпляр SQL Server
> * Включение трассировки на объект контекста вычислений

**RevoScaleR** поддерживает несколько контекстов вычислений: Hadoop, Spark в HDFS и SQL Server в базе данных. Для SQL Server **RxInSqlServer** функция используется для подключения к серверу и передача объектов между локальным компьютером и удаленным контекстом выполнения.

## <a name="create-and-set-a-compute-context"></a>Создание и задание контекста вычисления

**RxInSqlServer** функцию, которая создает контекст вычислений SQL Server использует следующие сведения:

+ Строка подключения для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра
+ Спецификация способа обработки выходных данных
+ Необязательная спецификация каталога общих данных
+ Необязательные аргументы, включить трассировку или указать уровень трассировки

В этом разделе рассматривается каждая часть.

1. Укажите строку подключения для экземпляра, где вычисления выполняются. Кроме того, можно повторно использовать строку подключения, созданную ранее.

    **Использование имени для входа SQL**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user nme>;Pwd=<password>"
      ```

    **Использование проверки подлинности Windows**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=RevoDeepDive;Trusted_Connection=True"
    ```
    
2. Укажите способ обработки выходных данных. Следующий скрипт направляет в локальный сеанс R, чтобы дожидаться результатов задания R на сервере перед обработкой следующей операции. Он также отключает выходные данные от удаленных вычислений появлялось в локальном сеансе.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    Аргумент *wait* функции **RxInSqlServer** может иметь перечисленные ниже значения.
  
    -   **TRUE**. Задание работает в режиме блокировки и не возвращается до его завершения, или произошел сбой.  Дополнительные сведения см. в разделе [распределенные и параллельные вычисления в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Задания настраиваются как без блокировки и возвращать результат немедленно, позволяя продолжить выполнение других кода R. Однако даже в режиме без блокировки подключение клиента к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должно сохраняться, пока задание выполняется.

3. При необходимости укажите расположение локального каталога для совместного использования в локальном сеансе R и удаленным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера и его учетными записями.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
   Если вы хотите создать вручную в определенный каталог для совместного использования, можно добавить строку следующего вида:

    ```R
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. Передача аргументов в **RxInSqlServer** конструктор для создания *объект контекста вычислений*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    Синтаксис **RxInSqlServer** выглядит почти так же, **RxSqlServerData** функцию, которая ранее использовалась для определения источника данных. Однако есть несколько важных различий.
      
    - Объект источника данных, определенный с помощью функции [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)указывает, где хранятся данные.
    
    - Напротив, контекст вычислений, определенных с помощью функции [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) указывает, где агрегаты и другие вычисления вступили в силу.
    
    Определение контекста вычислений не влияет на другие обычные вычисления R, которые могут выполняться на рабочей станции, и не изменяет источник данных. Например, можно определить в качестве источника данных локальный текстовый файл, но изменить контекст вычислений на SQL Server и выполнять все операции чтения и обобщения данных на компьютере SQL Server.

5. Активируйте контекст удаленных вычислений.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

6. Возвращают сведения о контексте вычислений, включая его свойства.

    ```R
    rxGetComputeContext()
    ```

7. Сбросьте контекст вычисления обратно на локальный компьютер, указав ключевое слово «local» (следующем уроке демонстрируется использование контекст удаленных вычислений).

    ```R
    rxSetComputeContext("local")
    ```

> [!Tip]
> Чтобы просмотреть список других ключевых слов, поддерживаемых этой функцией, в командной строке R введите `help("rxSetComputeContext")` .

## <a name="enable-tracing"></a>Включение трассировки

Иногда в операциях, которые работают в локальном контексте, могут возникать проблемы при работе в контексте удаленных вычислений. Если вы хотите анализировать проблемы или наблюдать за производительностью, можно включить трассировку в контексте вычислений для помощи при устранении неполадок во время выполнения.

1. Создайте новый контекст вычисления, который использует ту же строку подключения, но добавьте аргументы *traceEnabled* и *traceLevel* для **RxInSqlServer** конструктор.

    ```R
    sqlComputeTrace <- RxInSqlServer(
        connectionString = sqlConnString,
        #shareDir = sqlShareDir,
        wait = sqlWait,
        consoleOutput = sqlConsoleOutput,
        traceEnabled = TRUE,
        traceLevel = 7)
    ```
  
   В этом примере свойству *traceLevel* присваивается значение 7, что означает "показывать все данные трассировки".

2. Используйте [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) функцию, чтобы указать контекст вычисления с включенной функцией трассировки по имени.

    ```R
    rxSetComputeContext(sqlComputeTrace)
    ```

## <a name="next-steps"></a>Следующие шаги

Сведения о переключении контекстов вычислений для запуска кода R на сервере или локально.

> [!div class="nextstepaction"]
> [Сводные статистические данные вычислений в локальных и удаленных контекстов вычислений](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)