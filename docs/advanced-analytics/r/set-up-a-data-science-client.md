---
title: "Настройка клиента обработки и анализа данных для использования с SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d15ee956-918f-40e0-b986-2bf929ef303a
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 80b4898397cd0cb6460b379d91be81eb28cd9b87
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="set-up-a-data-science-client-for-use-with-sql-server"></a>Настройка клиента обработки и анализа данных для использования с SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

После настройки экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для поддержки машинного обучения, следует настроить среду разработки, можно подключаться к серверу для удаленного выполнения и развертывания.

В этой статье описываются некоторых типичных клиентских сценариях, включая конфигурацию бесплатный выпуск Visual Studio Community для запуска кода R в SQL Server.

## <a name="install-r-libraries-on-the-client"></a>Установка библиотек R на клиентском компьютере

Клиентская среда должна содержать Microsoft R Open, а также дополнительные пакеты RevoScaleR, поддерживающие распределенное выполнение R в SQL Server. Стандартные каналы R имеют пакеты, которые поддерживают контекстах удаленных вычислений или параллельному выполнению задач R.

Чтобы получить эти библиотеки, установите одно из следующих:
  
+ [Microsoft R Client](http://aka.ms/rclient/download)

+ Microsoft R Server (для SQL Server 2016)

    - Чтобы установить из программы установки SQL Server, в разделе [создать изолированный сервер R](../../advanced-analytics/r/create-a-standalone-r-server.md)

    - Чтобы использовать отдельный установщик под управлением Windows, см. [Установка машины обучения сервера для Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)

+ Машинное обучение сервера (для SQL Server 2017 г.)

    - Чтобы установить из программы установки SQL Server, в разделе [создать изолированный сервер R](../../advanced-analytics/r/create-a-standalone-r-server.md)

    - Чтобы использовать отдельный установщик под управлением Windows, см. [установить 9.1 R Server для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

## <a name="install-a-development-environment"></a>Установка среды разработки

Если у вас еще нет предпочтительной среду разработки R, мы рекомендуем одно из следующих:

+ cредства R для Visual Studio

    Работает с Visual Studio 2015.

    Сведения о настройке в разделе [установке средств R для Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation).
 
    Настройка RTVS для использования клиентских библиотек Microsoft R в разделе [о клиент Microsoft R](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

+ Visual Studio 2017 г.

    Даже бесплатный выпуск Community Edition включает в себя нагрузки обработки и анализа данных, что установка шаблонов проектирования для R, Python и F #.

    Загрузите Visual Studio из [этот сайт](https://www.visualstudio.com/vs/). 

+ RStudio

    Если вы предпочитаете RStudio, для использования библиотек RevoScaleR вам потребуется выполнить некоторые дополнительные действия.

    - Установка клиента Microsoft R для получения необходимых пакетов и библиотек.
    - Обновите путь к R для использования среды выполнения Microsoft R.

    Дополнительные сведения см. в разделе [клиента R - настроить интерфейс IDE](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client#step-2-configure-your-ide).

## <a name="configure-your-ide"></a>Настроить интерфейс IDE

+ cредства R для Visual Studio

    В разделе [этот сайт](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r) некоторые примеры того, как создать и отладить R проектов, с помощью средства R для Visual Studio. 

+ Visual Studio 2017 г.

    Если установить клиент Microsoft R или R Server **перед** установки Visual Studio, библиотеки R Server автоматически обнаруживаются и используется для пути к библиотеке. Если вы не установили библиотеки RevoScaleR из **средств R** последовательно выберите пункты **установить клиент R**.

## <a name="run-r-in-sql-server"></a>Выполнение R в SQL Server

В этом примере использует Visual Studio 2017 г Community Edition с установлен рабочей нагрузки обработки и анализа данных.

1. Из **файл** последовательно выберите пункты **New** , а затем выберите **проекта**.

2. -Рука область содержит список предустановленных шаблонов. Нажмите кнопку **R**и выберите **проект R**. В **имя** введите `dbtest` и нажмите кнопку **ОК**.

3. Visual Studio создает новую папку проекта и файл скрипта по умолчанию `Script.R`. 

4. Тип `.libPaths()` в первой строке скрипта файл и нажмите сочетание клавиш CTRL + ВВОД.

5. Текущий путь к библиотеке R, которые должны отображаться в **R интерактивный** окна. 

6. Нажмите кнопку **средств R** и выбрать пункт **Windows** для просмотра списка других окон конкретного R, которая отображается в рабочей области.
 
    + Просмотр справки в пакетах в текущей библиотеке, нажав клавиши CTRL + 3.
    + Переменные R в разделе **переменной Explorer**, нажав клавиши CTRL + 8.

7. Создать строку подключения к экземпляру SQL Server и использовать строку подключения в RxInSqlServer конструктор для создания объекта источника данных SQL Server. 

    ```r
    connStr <- "Driver=SQL Server;Server=MyServer;Database=MyTestDB;Uid=;Pwd="
    sqlShareDir <- paste("C:\\AllShare\\", Sys.getenv("USERNAME"), sep = "")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    cc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    sampleDataQuery <- "SELECT TOP 100 * from [dbo].[MyTestTable]"
    inDataSource <- RxSqlServerData(sqlQuery = sampleDataQuery, connectionString = connStr, rowsPerRead = 500)
    ```

    > [!TIP]
    > Чтобы запустить пакет, выберите строки, которые требуется запустить и нажмите клавиши CTRL + ВВОД.

8. Задать контекст вычислений на сервер, а затем запустите простого кода R на основе данных.

    ```r
    rxSetComputeContext(cc)
    rxGetVarInfo(data = inDataSource)
    ```

    Результаты возвращаются в **R интерактивный** окна.
    
    Если вы хотите убедиться, что код выполняется на экземпляре SQL Server, можно использовать профилировщик для создания трассировки.