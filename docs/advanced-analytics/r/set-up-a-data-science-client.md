---
title: Настройка клиента обработки и анализа данных для средств разработки R на SQL Server | Документация Майкрософт
description: Установка локального библиотеки и средства R на рабочей станции разработки для удаленных подключений к SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a88269ff6b55aa473c48cfa0937e926770bbaff1
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2018
ms.locfileid: "49462110"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Настройка клиента обработки и анализа данных для средств разработки R на сервере SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

После настройки экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для поддержки машинного обучения, необходимо настроить среду разработки R, которая может подключиться к серверу для удаленного выполнения и развертывания.

### <a name="evaluation-and-independent-development"></a>Оценка и независимая Разработка
 
Если у вас есть developer edition и план, чтобы локально поработать над сценарий R, планируется переместить в SQL Server, вы можете сразу перейти к [Установка IDE](#install-ide) и указать средству локальных библиотек R, используемый сервером SQL Server.

> [!Tip]
> Для демонстрации и видеоруководство, см. в разделе [выполнения R и Python удаленно, в SQL Server из записных книжек Jupyter или любой интегрированной среде разработки](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/) или это [видео YouTube](https://youtu.be/D5erljpJDjE).

## <a name="1---install-r-packages"></a>1 - Установка пакетов R

Функции R в продуктах Майкрософт носит многоуровневый характер. Он начинается с базового дистрибутива R корпорации Майкрософт открытым исходным кодом, но затем расширяется с помощью пакетов конкретных продуктов, таких как [RevoScaleR](revoscaler-overview.md), позволяющие контексты удаленных вычислений и параллельного выполнения задач R.

Скоординированными операциями между клиентом и удаленном сервере требуется обеих системах, где те же пакеты. Чтобы получить полный набор библиотек на клиентской рабочей станции, необходимо установите один из пакетов программного обеспечения в следующей таблице. 

| Библиотека поставщика | Использование  |
|------------------|--------------------------------|
| [Microsoft R Client](http://aka.ms/rclient/download) |  Бесплатно загрузите этот продукт предоставляет RevoScaleR, MicrosoftML и другие пакеты R, но ограничен двух потоков и данных в памяти. Тем не менее, вы можете по-прежнему создавать решения R, запустите локально,- and -shift выполнения (называется *контекста вычислений*) для доступа к данным и вычислительную мощь удаленного экземпляра SQL Server. Это рекомендуемый подход для клиента интеграцию с рабочим экземпляром SQL Server. Дополнительные сведения об использовании этого инструмента см. в разделе [что такое Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client).|
| Автономные серверы | В разделе **общие компоненты**, программа установки SQL Server включает в себя параметры установки автономного сервера для служб R SQL Server 2016 и SQL Server 2017 машинного обучения. Это полнофункциональная серверов, полностью отделены от SQL Server, с возможностью подключения к и использование данных из нескольких платформ данных. Однако можно потенциально использовать программное обеспечение в емкости клиента для доступа к экземпляру SQL Server database engine задачи R и Python. [SQL Server 2017 машины обучения Server (изолированный)](../install/sql-machine-learning-standalone-windows-install.md) имеет те же библиотеки, как экземпляр SQL Server 2017 машины обучения. [SQL Server 2016 R Server (изолированный)](../install/sql-r-standalone-windows-install.md) имеет те же библиотеки, как SQL Server 2016 R Services. |


<a name="r-tool"></a>
 
## <a name="2---open-an-r-prompt"></a>2 - откройте командную строку R

При установке R с SQL Server, вы получите те же средства R, которые являются стандартными для любой базовой установке R, например RGui и Rterm, т. д. Эти средства являются упрощенная, что удобно для проверка сведений о пакете и библиотеки, выполнение нерегламентированных команд или сценария или пошагового руководства. Эти средства можно использовать для получения сведений о версии R и проверке подключения.

Чтобы использовать версию R, установленной с SQL Server или R Client, откройте строку R из папки программы SQL Server или R Client. Следующие действия предназначены для R Client и RGui.exe.

1. R Client, см. в статье `~\Program Files\Microsoft\R Client\R_SERVER\bin\x64`.
2. Дважды щелкните **RGui.exe** запускается сеанс R с командной строкой R.

При запуске сеанса R из папки программы Майкрософт, несколько пакетов, включая RevoScaleR, загружаются автоматически. Введите **search()** в командной строке R для подтверждения.

   ![Сведения о версии при загрузке R](../install/media/rclient-rgui-r-prompt.png "откройте командную строку R")

### <a name="tool-list-and-location"></a>Список средств и расположение

| Инструмент | Описание | 
|------|-------------|
| **RTerm**: | Терминал командной строки для выполнения скриптов R | 
| **RGui.exe** | — Простой интерактивный редактор для R. Аргументы командной строки для RGui.exe и RTerm совпадают. |
| **RScript** | Средство командной строки для выполнения скриптов R в пакетном режиме. |

Средства находятся в **bin** папку для базового R, что установленный сервер SQL или R Client. Следующие пути приведены допустимые расположения для средств, в зависимости от версии продукта и компонентов установки.

| Продукт Microsoft | Расположение средства R |
|-------------------|-----------------|
| Microsoft R Client | `~\Program Files\Microsoft\R Client\R_SERVER\bin\x64` |
| Microsoft Machine Learning (R) сервера | `~\Program Files\Microsoft\R_SERVER\bin\x64`
| SQL Server 2016 R Services | `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`|
| SQL Server 2016 R изолированный сервер | `~\Program Files\Microsoft SQL Server\130\R_SERVER\bin\x64` 
| SQL Server 2017 службы машинного обучения (R) | `~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`|
| SQL Server 2017 машинного обучения (R) изолированный сервер | `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` |

## <a name="3---permissions"></a>3 - разрешения

Чтобы подключиться к экземпляру SQL Server для выполнения скриптов и отправки данных, необходимо иметь допустимое имя входа на сервере базы данных. Можно использовать либо имя входа SQL, либо встроенную проверку подлинности Windows. Обычно рекомендуется использовать встроенную проверку подлинности Windows, что с помощью имени входа SQL проще для некоторых сценариев.

Как минимум учетная запись, используемая для запуска кода необходимо иметь разрешение на чтение из базы данных, вы работаете, а также специальное разрешение Выполнение ЛЮБОГО ВНЕШНЕГО СКРИПТА. Большинство разработчиков также требуются разрешения на создание новых объектов в виде хранимых процедур, содержащий скрипт и записывать данные в таблицы, содержащий данные для обучения или оценки данных. 

Обратитесь к администратору базы данных, чтобы настроить следующие разрешения для учетной записи, в базе данных, где используется R:

+ **EXECUTE ANY EXTERNAL SCRIPT** с языком R на сервере.
+ **db_datareader** привилегий для выполнения запросов, используемых для обучения модели.
+ **db_datawriter** для записи данных для обучения или оценки данных.
+ **db_owner** для создания объектов, таких как хранимые процедуры, таблицы, функции. 
  Необходимо также **db_owner** создавать пример и тестирования базы данных. 

Если код требует пакеты, которые не устанавливаются по умолчанию вместе с SQL Server, упорядочить администратору базы данных, чтобы получить пакеты, установленные с экземпляром. SQL Server является безопасной среде и существуют ограничения на установки пакетов. Ad hoc установку пакетов как часть кода не рекомендуется, даже если вы обладаете правами. Кроме того всегда внимательно рассмотрите влияние на безопасность, прежде чем устанавливать новые пакеты в библиотеке server.

> [!Tip]
> Если вы не знакомы с SQL Server и работе в локальной среде разработки, при прохождении этого учебника, чтобы узнать об именах входа и задание разрешений: [подробный обзор RevoScaleR](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)

## <a name="4---test-connections"></a>4 - Тестирование подключений

SQL Server должна быть включена для [удаленные подключения](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md) и необходимо иметь разрешения, включая имя входа пользователя и для подключения к базе данных. В следующих шагах предполагается демонстрационной базы данных, [NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md) и проверку подлинности Windows.

 В качестве шага проверки используйте встроенное средство и RevoScaleR для подтверждения подключения к удаленному серверу.

1. Начните с [открыв средство R](#r-tool) на клиентской рабочей станции. Автоматически загружает RevoScaleR. Например, перейдите к `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` и дважды щелкните **RGui.exe** для его запуска.

2. Убедитесь, что RevoScaleR работает, выполнив следующую команду, которая возвращает статистическая Сводка на демонстрационный набор данных. Убедитесь, что вы укажите допустимое имя сервера для экземпляра ядра базы данных SQL Server.

```r
connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
testQuery <-"SELECT DISTINCT TOP(100) tip_amount FROM [dbo].nyctaxi_sample ORDER BY tip_amount DESC;"
cc <-RxInSqlServer(connectionString=connStr)
rxSummary(formula = ~ ., data = RxSqlServerData(sqlQuery=testQuery, connectionString=connStr), computeContext=cc)
```
Этот сценарий подключается к базе данных на удаленном сервере, предоставляет запрос, создает контекст вычислений `cc` инструкция удаленный запуск программного кода, затем обеспечивает функцию RevoScaleR **rxSummary** для возврата статистический Сводка результатов запроса.

<a name="install-ide"></a>

## <a name="5---install-an-ide"></a>5 — Установка IDE

Для постоянной и серьезных проектов необходимо установить интегрированную среду разработки (IDE). Средства SQL Server и встроенные средства R для усиленно R не способны. Получив рабочий код, его можно развернуть как хранимую процедуру для выполнения на сервере SQL Server.

Интегрированная СРЕДА должна указывать на локальном библиотеки R: базовый R, RevoScaleR и т. д. Происходит во время выполнения скрипта, рабочих нагрузок выполняются на удаленном экземпляре SQL Server, когда сценарий вызывает контекст удаленных вычислений на сервере SQL Server, доступ к данным и операциям на этом сервере.

### <a name="rstudio"></a>RStudio

При использовании [RStudio](https://www.rstudio.com/), можно настроить среду для использования библиотеки R и исполняемые файлы, которые соответствуют элементам на удаленный экземпляр SQL Server.

1. Проверка версии пакета R, установленные на сервере SQL Server. Дополнительные сведения см. в разделе [R, получить сведения о пакете](determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).

1. Установите Microsoft R Client, или один из параметров автономного сервера для добавления RevoScaleR и другие пакеты R, включая базового дистрибутива R, используемые экземпляром SQL Server. Выберите версию в то же уровня или ниже (пакеты обратно совместимы), предоставляет те же версии пакета, что и на сервере. Сведения о версии, см. в разделе сопоставления в этой статье версии: [обновления R и Python компонентов](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

1. В RStudio [обновить путь R](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) указывал в среду R, обеспечивая RevoScaleR, Microsoft R Open и другие пакеты Microsoft. В зависимости от способа ее получения RevoScaleR и другие библиотеки это наиболее вероятный вариант из следующих путей:

  + C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library
  + C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library
  + C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64

### <a name="r-tools-for-visual-studio-rtvs"></a>Инструменты R для Visual Studio (RTVS)

Если у вас нет предпочтительной интегрированной среды разработки для R, мы рекомендуем **инструменты R для Visual Studio**.

+ [Скачать инструменты R для Visual Studio (RTVS)](https://visualstudio.microsoft.com/vs/features/rtvs/)
+ [Инструкции по установке](https://docs.microsoft.com/visualstudio/rtvs/installing-r-tools-for-visual-studio) -RTVS доступен в нескольких версиях Visual Studio.
+ [Начало работы с инструментами R для Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>Подключение к SQL Server из RTVS

В этом примере используется Visual Studio 2017 Community Edition с установленной рабочей нагрузки обработки и анализа данных.

1. Из **файл** меню, выберите **New** , а затем выберите **проекта**.

2. Область слева содержит список предустановленных шаблонов. Нажмите кнопку **R**и выберите **проект R**. В **имя** введите `dbtest` и нажмите кнопку **ОК**. 

  Visual Studio создает папку проекта и файл сценария по умолчанию `Script.R`. 

3. Тип `.libPaths()` в первой строке сценария файл и нажмите клавиши CTRL + ВВОД.

  Текущий путь к библиотеке R, которые должны отображаться в **интерактивное окно R** окна. 

4. Нажмите кнопку **инструменты R** меню и выберите **Windows** для просмотра списка других окон конкретного R, которая отображается в рабочей области.
 
    + Просмотреть справку о пакетах в текущей библиотеке, нажав клавиши CTRL + 3.
    + См. в разделе переменных r. в **обозреватель переменных**, нажав клавиши CTRL + 8.

5. Создать строку подключения к экземпляру SQL Server и использовать строку подключения в конструкторе RxInSqlServer для создания объекта источника данных SQL Server. 

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
    > Чтобы запустить пакет, выберите строки, которые вы хотите запустить и нажмите клавиши CTRL + ВВОД.

6. Настройки контекста вычислений на сервер и затем выполнить простой код R к данным.

    ```r
    rxSetComputeContext(cc)
    rxGetVarInfo(data = inDataSource)
    ```

    Результаты возвращаются в **интерактивное окно R** окна.
    
    Если вы хотите убедиться, что код выполняется на экземпляре SQL Server, можно использовать для создания трассировки Profiler.

## <a name="next-steps"></a>Следующие шаги

Два разных руководства содержат упражнения, таким образом, вы сможете совершенствовать переключение контекста вычислений на локальный с удаленным экземпляром SQL Server.

+ [Руководство: Функции RevoScaleR использующих R с данными SQL Server](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Пошаговое руководство по обработке и анализу данных](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)