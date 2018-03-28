---
title: Настройка клиента обработки и анализа данных для разработки R на сервере SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 10/31/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ''
caps.latest.revision: ''
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 414410cdac959fb23989dda6569e0711b8a6fc23
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Настройка клиента обработки и анализа данных для разработки R на сервере SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

После настройки экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для поддержки машинного обучения, следует настроить среду разработки, можно подключаться к серверу для удаленного выполнения и развертывания.

В этой статье описываются некоторых типичных клиентских сценариях, включая конфигурацию бесплатный выпуск Visual Studio Community для запуска кода R в SQL Server.

## <a name="install-r-libraries-on-the-client"></a>Установка библиотек R на клиентском компьютере

Клиентская среда должна содержать Microsoft R Open, а также дополнительные пакеты RevoScaleR, поддерживающие распределенное выполнение R в SQL Server. Стандартные каналы R имеют пакеты, которые поддерживают контекстах удаленных вычислений или параллельному выполнению задач R.

Чтобы получить эти библиотеки, установите одно из следующих:
  
+ [Microsoft R Client](http://aka.ms/rclient/download)

+ Microsoft R Server (для SQL Server 2016)

    - Чтобы установить из программы установки SQL Server, в разделе [Установка SQL Server 2016 R Server (автономный)](../install/sql-r-standalone-windows-install.md)

    - Чтобы использовать отдельный установщик под управлением Windows, см. [Установка машины обучения сервера для Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)

+ Машинное обучение сервера (для SQL Server 2017 г.)

    - Чтобы установить из программы установки SQL Server, в разделе [установки сервера SQL Server 2017 г машины обучения (автономный)](../install/sql-machine-learning-standalone-windows-install.md)

    - Чтобы использовать отдельный установщик под управлением Windows, см. [установить 9.1 R Server для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

## <a name="r-tools"></a>Средства R

Если вы устанавливаете R с SQL Server, вы получаете те же средства R, которые устанавливаются вместе с любой **базового** установки r, например RGui, Rterm и т. д. Поэтому с технической точки зрения, у вас все средства, необходимые для разработки и тестирования кода R.

Следующие стандартные средства R включены в *базовые установки* r и поэтому устанавливаются по умолчанию.

+ **RTerm**: терминал командной строки для выполнения скриптов R

+ **RGui.exe** — простой интерактивный редактор для R. Аргументы командной строки для RGui.exe и RTerm одни и те же.

+ **RScript** — средство командной строки для выполнения скриптов R в пакетном режиме.

Чтобы найти эти средства, определите R библиотеки, в которой была установлена при установке SQL Server или автономный машинного обучения функции. Например по умолчанию при установке средств R находятся в этих папках:

+ Службы SQL Server 2016 R: `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`
+ Изолированный сервер Microsoft R: `~\Program Files\Microsoft R\R_SERVER\bin\x64`
+ Машины SQL Server 2017 г. изучение служб: `~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`
+ Машинное обучение Server (изолированный): `~\Program Files\Microsoft\ML Server\R_SERVER\bin\x64`

Если вам нужна помощь с помощью средств R, просто откройте **RGui**, нажмите кнопку **справки**, а затем выберите один из параметров

## <a name="microsoft-r-client"></a>Microsoft R Client

Клиент Microsoft R можно бесплатно загрузить, предоставляющая доступ к пакетам RevoScaleR для целей разработки. Установка клиента R, можно создать решения R, которые могут выполняться во всех контекстах поддерживаемых вычислений, включая анализа в базе данных SQL Server и распределенных вычислений в Hadoop, Spark или Linux с помощью сервера обучения Machine R.

Если вы уже установили другой среды разработки R, например RStudio, не забудьте изменить параметры среды для использования библиотек и исполняемых файлов, предоставляемые Microsoft R клиента. В результате можно использовать все возможности пакета RevoScaleR, несмотря на то, что производительности будет ограничен.

Дополнительные сведения см. в разделе [что такое клиент Microsoft R?](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

## <a name="install-a-development-environment"></a>Установка среды разработки

Если у вас еще нет предпочтительной среду разработки R, мы рекомендуем одно из следующих:

+ cредства R для Visual Studio

    Работает с Visual Studio 2015.

    Сведения о настройке в разделе [установке средств R для Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation).
 
    Настройка RTVS для использования клиентских библиотек Microsoft R в разделе [о клиент Microsoft R](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

+ Visual Studio 2017

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

+ Visual Studio 2017

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