---
title: Определить и использовать контексты вычислений (SQL и R глубокое погружение) | Документы Microsoft
ms.custom: ''
ms.date: 12/14/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: e8d5a04733ec11aff3b304d183d99c5c89b3feae
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="define-and-use-compute-contexts-sql-and-r-deep-dive"></a>Определить и использовать контексты вычислений (SQL и R глубокое погружение)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

В этом уроке рассматривается [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) функции, которая позволяет определить контекст вычислений для SQL Server и выполнять сложные вычисления на сервере, а не локального компьютера. 

RevoScaleR поддерживает несколько контекстов вычислений, позволяющие выполнять код R в Hadoop, Spark или в базе данных. Для SQL Server определите сервер и функция обрабатывает создание базы данных соединения и передача объектов между локальным компьютером и контекст выполнения удаленной задачи.

Функция, которая создает SQL Server вычислений контекста использует следующие сведения:

- Строка подключения для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра
- Задавать способ обработки выходных данных
- Необязательные аргументы, трассировка, или указать уровень трассировки
- Необязательная спецификация каталог общих данных

## <a name="create-and-set-a-compute-context"></a>Создайте и задайте контекст вычислений.

1. Укажите строку подключения для экземпляра, когда выполняются вычисления.  Можно повторно использовать строку подключения, которое было создано ранее. Если вы хотите переместить результаты вычислений на другой сервер или использовать другое имя пользователя для выполнения некоторых задач, можно создать другую строку соединения.

    **Использование имени для входа SQL**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user name>;Pwd=<password>"
      ```

    **Использование проверки подлинности Windows**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"
      ```
2. Укажите способ обработки выходных данных. В следующем коде вы указываете, что сеанс R на рабочей станции всегда должен дожидаться результатов задания R, но не возвращать вывод с консоли от удаленных вычислений.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    Аргумент *wait* функции **RxInSqlServer** может иметь перечисленные ниже значения.
  
    -   **TRUE**. Задание настраивается как блокировки и не возвращается до его завершения, или произошел сбой.  Дополнительные сведения см. в разделе [распределенных и параллельных вычислений в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Задания настраиваются в качестве без блокировки и возврат немедленно, что позволяет продолжить выполнение других код R. Однако даже в режиме без блокировки подключение клиента к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должно сохраняться, пока задание выполняется.

3. Кроме того, можно указать расположение локальный каталог для совместного использования с локального сеанса R, удаленный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера и его учетные записи.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
4. Если вы хотите создать вручную в определенный каталог для общего доступа, можно добавить строку следующим образом:

    ```
    dir.create(sqlShareDir, recursive = TRUE)
    ```

    Чтобы определить, какие папки используются в настоящее время для совместного использования, выполните `rxGetComputeContext()`, которая возвращает сведения о текущего контекста вычислений. Дополнительные сведения см. в [справочнике по ScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/).

4. Подготовлены все переменные, предоставить их в качестве аргументов для **RxInSqlServer** конструктор для создания *объект контекста вычислений*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    Синтаксис **RxInSqlServer** выглядит так же, **RxSqlServerData** функции, которые ранее использовались для определения источника данных. Однако есть несколько важных различий.
      
    - Объект источника данных, определенный с помощью функции [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)указывает, где хранятся данные.
    
    - Напротив, контекст вычислений, определенных с помощью функции [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) указывает, где агрегаты и других вычислений, вступили в силу.
    
    Определение контекста вычислений не влияет на другие обычные вычисления R, которые могут выполняться на рабочей станции, и не изменяет источник данных. Например, можно определить в качестве источника данных локальный текстовый файл, но изменить контекст вычислений на SQL Server и выполнять все операции чтения и обобщения данных на компьютере SQL Server.

## <a name="enable-tracing-on-the-compute-context"></a>Включить трассировку в контексте вычислений.

Иногда в операциях, которые работают в локальном контексте, могут возникать проблемы при работе в контексте удаленных вычислений. Если вы хотите анализировать проблемы или наблюдать за производительностью, можно включить трассировку в контексте вычислений для помощи при устранении неполадок во время выполнения.

1. Создает контекст вычислений, использует ту же строку подключения, но добавить аргументы *traceEnabled* и *traceLevel* для **RxInSqlServer** конструктор.

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

2. Чтобы сменить контекст вычислений, используйте функцию [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) и указывайте контекст по имени.

    ```R
    rxSetComputeContext( sqlComputeTrace)
    ```

    > [!NOTE]
    > 
    > В этом учебнике будет использоваться контекст вычислений, у которого нет трассировка включена. 
    > 
    > Тем не менее если вы решили использовать трассировку, следует помнить, что работы могут быть затронуты сетевое подключение. Кроме того, помните, так как производительность для параметра включена трассировка не были проверены для всех операций.

В следующем шаге вы узнаете, как использовать вычислений контекстов, чтобы выполнить код R на сервере или локально.

## <a name="next-step"></a>Следующий шаг

[Создание и выполнение скриптов R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)

## <a name="previous-step"></a>Предыдущий шаг

[Запрос и изменение данных SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
