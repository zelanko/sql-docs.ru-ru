---
title: Определение и использование контекстов вычислений (SQL и R глубокое погружение в обработку) | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6a76e07cb2ecd03a59112f6c39e3fa2f7895e0a2
ms.sourcegitcommit: aa9d2826e3c451f4699c0e69c9fcc8a2781c6213
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45975643"
---
# <a name="define-and-use-compute-contexts-sql-and-r-deep-dive"></a>Определение и использование контекстов вычислений (SQL и R глубокое погружение в обработку)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья входит углубленное рассмотрение обработки и анализа данных руководства по использованию [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

В этом уроке рассматривается [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) функцию, которая позволяет определить контекст вычисления для SQL Server и выполнять сложные вычисления на сервере, а не на локальном компьютере. 

RevoScaleR поддерживает несколько контекстов вычислений, чтобы обеспечить возможность выполнения кода R в Hadoop, Spark или в базе данных. Для SQL Server определите сервер, и она отвечает за задачи создания базы данных, подключения и передачи объектов между локальным компьютером и удаленным контекстом выполнения.

Функцию, которая создает SQL Server вычислительный контекст использует следующие сведения:

- Строка подключения для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра
- Спецификация способа обработки выходных данных
- Необязательные аргументы, включить трассировку или указать уровень трассировки
- Необязательная спецификация каталога общих данных

## <a name="create-and-set-a-compute-context"></a>Создание и задание контекста вычисления

1. Укажите строку подключения для экземпляра, где вычисления выполняются.  Кроме того, можно повторно использовать строку подключения, созданную ранее. Если вы хотите переместить вычисления на другой сервер или использовать другой имя входа для выполнения некоторых задач, можно создать другую строку подключения.

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
  
    -   **TRUE**. Задание работает в режиме блокировки и не возвращается до его завершения, или произошел сбой.  Дополнительные сведения см. в разделе [распределенные и параллельные вычисления в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Задания настраиваются как без блокировки и возвращать результат немедленно, позволяя продолжить выполнение других кода R. Однако даже в режиме без блокировки подключение клиента к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должно сохраняться, пока задание выполняется.

3. Кроме того, можно указать расположение локального каталога для совместного использования в локальном сеансе R и удаленным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера и его учетными записями.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
4. Если вы хотите создать вручную в определенный каталог для совместного использования, можно добавить строку следующего вида:

    ```
    dir.create(sqlShareDir, recursive = TRUE)
    ```

    Чтобы определить, какая папка используется для совместного использования, выполните `rxGetComputeContext()`, который возвращает сведения о текущем контексте вычислений. Дополнительные сведения см. в [справочнике по ScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/).

4. Подготовив все переменные, укажите их в качестве аргументов для **RxInSqlServer** конструктор для создания *объект контекста вычислений*.

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

## <a name="enable-tracing-on-the-compute-context"></a>Включить трассировку в контексте вычислений

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

2. Чтобы сменить контекст вычислений, используйте функцию [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) и указывайте контекст по имени.

    ```R
    rxSetComputeContext( sqlComputeTrace)
    ```

    > [!NOTE]
    > 
    > В этом учебнике используется контекст вычисления, который не поддерживает трассировка включена. 
    > 
    > Тем не менее если вы решите использовать трассировку, имейте в виду, что влияет на взаимодействие может быть с подключения к сети. Кроме того, так как не была протестирована производительности для параметра включить трассировку для всех операций.

На следующем шаге вы узнаете, как использовать вычислительных контекстов, для запуска кода R на сервере или локально.

## <a name="next-step"></a>Следующий шаг

[Создание и выполнение скриптов R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)

## <a name="previous-step"></a>Предыдущий шаг

[Запрос и изменение данных SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
