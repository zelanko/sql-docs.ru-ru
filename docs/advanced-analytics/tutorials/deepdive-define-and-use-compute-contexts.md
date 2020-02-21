---
title: Использование контекстов вычислений RevoScaleR
description: Учебник по RevoScaleR, часть 4. Сведения об определении контекста вычисления с помощью языка R в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c90c935f85584f8886ae112d5cfc03759c0a129a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "74947227"
---
# <a name="define-and-use-compute-contexts-sql-server-and-revoscaler-tutorial"></a>Определение и использование контекстов вычислений (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта часть 4 входит в состав [серии учебников по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), посвященной использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

В предыдущем учебнике вы использовали функции **RevoScaleR** для проверки объектов данных. В этом учебнике представлена функция [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver), которая позволяет определить контекст вычислений для удаленного экземпляра SQL Server. С помощью удаленного контекста вычислений можно переместить выполнение R из локального сеанса в удаленный сеанс на сервере. 

> [!div class="checklist"]
> * Элементы удаленного контекста вычислений SQL Server
> * Включение трассировки в объекте контекста вычислений

**RevoScaleR** поддерживает несколько контекстов вычислений: Hadoop, Spark на HDFS и SQL Server в базе данных. Для SQL Server функция **RxInSqlServer** используется для подключения к серверу и передачи объектов между локальным компьютером и удаленным контекстом выполнения.

## <a name="create-and-set-a-compute-context"></a>Создание и задание контекста вычисления

Функция **RxInSqlServer**, которая создает контекст вычислений SQL Server, использует следующие сведения:

+ строка подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];
+ спецификация способа обработки выходных данных;
+ необязательная спецификация каталога общих данных;
+ необязательные аргументы, которые позволяют выполнять трассировку или указывать уровень трассировки.

В этом разделе описывается каждая из этих частей.

1. Укажите строку подключения к экземпляру, в котором будут производиться вычисления. Вы можете повторно использовать созданную ранее строку подключения.

    **Использование имени для входа SQL**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user nme>;Pwd=<password>"
      ```

    **Использование проверки подлинности Windows**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=RevoDeepDive;Trusted_Connection=True"
    ```
    
2. Укажите способ обработки выходных данных. Следующий скрипт задает в локальном сеансе R ожидание результатов задания R на сервере перед обработкой следующей операции. Он также подавляет вывод из удаленных вычислений в локальном сеансе.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    Аргумент *wait* функции **RxInSqlServer** может иметь перечисленные ниже значения.
  
    -   **TRUE**. Задание будет блокироваться и не вернет результат, пока его выполнение не завершится успешно или с ошибкой.  Дополнительные сведения см. в разделе [Распределенные и параллельные вычисления в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Задания не будут блокироваться и вернут результат немедленно, что позволит продолжать выполнять другой код на языке R. Однако даже в режиме без блокировки подключение клиента к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должно сохраняться, пока задание выполняется.

3. При необходимости можно указать расположение локального каталога для совместного использования локальным сеансом R и удаленным компьютером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и его учетными записями.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
   Если вы хотите вручную создать каталог для совместного использования, можно добавить строку, подобную следующей:

    ```R
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. Передайте аргументы для конструктора **RxInSqlServer**, чтобы создать *объект контекста вычислений*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    Синтаксис **RxInSqlServer** почти идентичен синтаксису функции **RxSqlServerData**, которая ранее использовалась для определения источника данных. Однако есть несколько важных различий.
      
    - Объект источника данных, определенный с помощью функции [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)указывает, где хранятся данные.
    
    - Напротив, контекст вычислений (определенный с помощью функции [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)) указывает, где должно производиться агрегирование и другие вычисления.
    
    Определение контекста вычислений не влияет на другие обычные вычисления R, которые могут выполняться на рабочей станции, и не изменяет источник данных. Например, можно определить в качестве источника данных локальный текстовый файл, но изменить контекст вычислений на SQL Server и выполнять все операции чтения и обобщения данных на компьютере SQL Server.

5. Активируйте удаленный контекст вычислений.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

6. Возврат сведений о контексте вычислений, включая его свойства.

    ```R
    rxGetComputeContext()
    ```

7. Верните контекст вычислений обратно на локальный компьютер, указав ключевое слово "Local" (использование удаленного контекста вычислений описано в следующем учебнике).

    ```R
    rxSetComputeContext("local")
    ```

> [!Tip]
> Чтобы просмотреть список других ключевых слов, поддерживаемых этой функцией, в командной строке R введите `help("rxSetComputeContext")` .

## <a name="enable-tracing"></a>Включение трассировки

Иногда в операциях, которые работают в локальном контексте, могут возникать проблемы при работе в контексте удаленных вычислений. Если вы хотите анализировать проблемы или наблюдать за производительностью, можно включить трассировку в контексте вычислений для помощи при устранении неполадок во время выполнения.

1. Создайте новый контекст вычислений, использующий ту же строку подключения, но добавьте аргументы *traceEnabled* и *traceLevel* в конструктор **RxInSqlServer**.

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

2. Используйте функцию [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) и указывайте контекст с включенной трассировкой по имени.

    ```R
    rxSetComputeContext(sqlComputeTrace)
    ```

## <a name="next-steps"></a>Дальнейшие действия

Узнайте, как переключать контексты вычислений для выполнения кода R на сервере или локально.

> [!div class="nextstepaction"]
> [Вычисление сводной статистики в локальных и удаленных контекстах вычислений](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)