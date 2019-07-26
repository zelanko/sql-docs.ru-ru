---
title: Определение и использование контекстов вычислений RevoScaleR
description: Пошаговое руководство по определению контекста вычислений с использованием языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 053fc48c4117372eb3e3bebb715b4176ec1dd828
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469728"
---
# <a name="define-and-use-compute-contexts-sql-server-and-revoscaler-tutorial"></a>Определение и использование контекстов вычислений (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Это занятие является частью [учебника RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На предыдущем занятии использовались функции **RevoScaleR** для проверки объектов данных. В этом занятии рассматривается функция [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) , позволяющая определить контекст вычислений для удаленного SQL Server. С помощью удаленного контекста вычислений можно переместить выполнение R из локального сеанса в удаленный сеанс на сервере. 

> [!div class="checklist"]
> * Сведения об элементах удаленного контекста вычислений SQL Server
> * Включение трассировки для объекта контекста вычислений

**RevoScaleR** поддерживает несколько контекстов вычислений: Hadoop, Spark на HDFS и SQL Server в базе данных. Для SQL Server функция **RxInSqlServer** используется для подключений к серверу и передачи объектов между локальным компьютером и контекстом удаленного выполнения.

## <a name="create-and-set-a-compute-context"></a>Создание и Установка контекста вычислений

Функция **RxInSqlServer** , которая создает SQL Server контекст вычислений, использует следующие сведения:

+ Строка подключения для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра
+ Спецификация обработки выходных данных
+ Необязательная спецификация каталога общих данных
+ Необязательные аргументы, которые позволяют выполнять трассировку или указывать уровень трассировки.

В этом разделе описывается каждая из частей.

1. Укажите строку соединения для экземпляра, на котором выполняются вычисления. Вы можете повторно использовать созданную ранее строку подключения.

    **Использование имени для входа SQL**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user nme>;Pwd=<password>"
      ```

    **Использование проверки подлинности Windows**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=RevoDeepDive;Trusted_Connection=True"
    ```
    
2. Укажите способ обработки выходных данных. Следующий скрипт направляет локальный сеанс R для ожидания результатов задания R на сервере перед обработкой следующей операции. Он также подавляет вывод из удаленных вычислений в локальном сеансе.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    Аргумент *wait* функции **RxInSqlServer** может иметь перечисленные ниже значения.
  
    -   **TRUE**. Задание настроено как блокирование и не возвращает значение до завершения или сбоя.  Дополнительные сведения см. [в разделе распределенные и параллельные вычисления в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Задания настраиваются как неблокирующие и немедленно возвращаются, что позволяет продолжить выполнение другого кода R. Однако даже в режиме без блокировки подключение клиента к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должно сохраняться, пока задание выполняется.

3. При необходимости укажите расположение локального каталога для общего использования в локальном сеансе R, а также на удаленном [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютере и его учетных записях.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
   Если вы хотите вручную создать конкретный каталог для совместного использования, можно добавить строку, подобную следующей:

    ```R
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. Передайте аргументы в конструктор **RxInSqlServer** , чтобы создать *объект контекста вычислений*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    Синтаксис для **RxInSqlServer** выглядит почти так же, как функция **RxSqlServerData** , которая использовалась ранее для определения источника данных. Однако есть несколько важных различий.
      
    - Объект источника данных, определенный с помощью функции [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)указывает, где хранятся данные.
    
    - В отличие от этого, контекст вычисления, определенный с помощью функции [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) , указывает, где должны выполняться агрегаты и другие вычисления.
    
    Определение контекста вычислений не влияет на другие обычные вычисления R, которые могут выполняться на рабочей станции, и не изменяет источник данных. Например, можно определить в качестве источника данных локальный текстовый файл, но изменить контекст вычислений на SQL Server и выполнять все операции чтения и обобщения данных на компьютере SQL Server.

5. Активируйте удаленный контекст вычислений.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

6. Возвращает сведения о контексте вычислений, включая его свойства.

    ```R
    rxGetComputeContext()
    ```

7. Верните контекст вычислений обратно на локальный компьютер, указав ключевое слово "Local" (следующее занятие демонстрирует использование удаленного контекста вычислений).

    ```R
    rxSetComputeContext("local")
    ```

> [!Tip]
> Чтобы просмотреть список других ключевых слов, поддерживаемых этой функцией, в командной строке R введите `help("rxSetComputeContext")` .

## <a name="enable-tracing"></a>Включить трассировку

Иногда в операциях, которые работают в локальном контексте, могут возникать проблемы при работе в контексте удаленных вычислений. Если требуется проанализировать проблемы или мониторинг производительности, можно включить трассировку в контексте вычислений для поддержки устранения неполадок во время выполнения.

1. Создайте новый контекст вычислений, использующий ту же строку подключения, но добавьте аргументы *traceEnabled* и *TraceLevel* в конструктор **RxInSqlServer** .

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

2. Используйте функцию [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) , чтобы указать контекст вычислений, поддерживающий трассировку, по имени.

    ```R
    rxSetComputeContext(sqlComputeTrace)
    ```

## <a name="next-steps"></a>Следующие шаги

Узнайте, как переключить контексты вычислений для выполнения кода R на сервере или локально.

> [!div class="nextstepaction"]
> [Сводная статистика вычислений в локальных и удаленных контекстах вычислений](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)