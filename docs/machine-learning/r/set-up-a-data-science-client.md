---
title: Настройка клиента обработки и анализа данных для разработки на R
description: Установите локальные библиотеки и инструменты R на рабочей станции разработки для удаленных подключений к SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 160365ea9782f50376a34eb87a3bf6893ce404c9
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "81117377"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Настройка клиента обработки и анализа данных для разработки на R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Интеграция R доступна в SQL Server 2016 и более поздних версиях, если включить параметр для языка R во время установки [служб SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) и [служб машинного обучения SQL Server (в базе данных)](../install/sql-machine-learning-services-windows-install.md). 

Чтобы разрабатывать и развертывать решения R для SQL Server, установите [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) на рабочей станции разработки для получения библиотеки [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) и других библиотек R. Библиотека RevoScaleR, которая также требуется на удаленном экземпляре SQL Server, координирует вычислительные запросы между обеими системами. 

Из этой статьи вы узнаете, как настроить рабочую станцию разработки для клиента R, чтобы взаимодействовать с удаленным сервером SQL Server, на котором включены машинное обучение и интеграция R. После выполнения действий, описанных в этой статье, у вас будут те же библиотеки R, что и на сервере SQL Server. Вы также узнаете, как отправлять вычисления из локального сеанса R в удаленный сеанс R на сервере SQL Server.

![Клиент-серверные компоненты](media/sqlmls-r-client-revo.png "Локальные и удаленные сеансы и библиотеки R")

Чтобы проверить установку, можно использовать встроенное средство **RGUI**, как описано в этой статье, либо [связать библиотеки](#install-ide) с RStudio или любой другой интегрированной средой разработки, которой вы обычно пользуетесь.

> [!Note]
> Вместо установки клиентской библиотеки можно использовать [автономный сервер](../install/sql-machine-learning-standalone-windows-install.md) в качестве полнофункционального клиента. Некоторые заказчики предпочитают эту конфигурацию для более глубокой работы сценария. Изолированный сервер полностью отделен от SQL Server, но поскольку он содержит те же библиотеки R, которые установлены на SQL Server, его можно использовать в качестве клиента для анализа SQL Server в базе данных. Его также можно использовать для решения задач, не связанных с SQL, в том числе для импорта и моделирования данных из других платформ данных. Если вы устанавливаете изолированный сервер, исполняемый файл R можно найти в следующем расположении: `C:\Program Files\Microsoft SQL Server\140\R_SERVER`. Для проверки установки [откройте консольное приложение R](#R-tools), чтобы выполнять команды с помощью исполняемого файла R.exe в этом расположении.

## <a name="commonly-used-tools"></a>Часто используемые инструменты

Независимо от того, являетесь ли вы разработчиком на R, который мало знаком с SQL, или разработчиком на SQL, который мало знаком с R и анализом в базе данных, для использования всех возможностей анализа в базе данных вам потребуется как средство разработки R, так и редактор запросов T-SQL, например [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Для простых сценариев разработки R можно использовать исполняемый файл RGUI, входящий в базовый дистрибутив R в MRO и SQL Server. В этой статье приводятся инструкции по использованию RGUI как для локальных, так и для удаленных сеансов R. Для повышения производительности следует использовать полнофункциональную интегрированную среду разработки, например [RStudio или Visual Studio](#install-ide).

Набор средств SSMS необходимо скачать отдельно. Он подходит для создания и выполнения хранимых процедур в SQL Server, в том числе процедур, содержащих код R. Практически любой код R, написанный в среде разработки, можно внедрять в хранимые процедуры. Вы можете ознакомиться с другими руководствами, чтобы узнать о [SSMS и внедрении кода R](../tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="1---install-r-packages"></a>1\. Установка пакетов R

Пакеты R Microsoft доступны в нескольких продуктах и службах. На локальной рабочей станции рекомендуется установить Microsoft R Client. R Client предоставляет [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package), [SQLRUtils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) и другие пакеты R.

1. [Скачайте Microsoft R Client](https://aka.ms/rclient/download).

2. В мастере установки примите или измените путь установки по умолчанию, примите или измените список компонентов и примите условия лицензии Microsoft R Client.

  После завершения установки появится экран приветствия с описанием продукта и списком документации.

3. Создайте системную переменную среды MKL_CBWR для получения согласованных выходных данных из вычислений Intel Math Kernel Library (MKL).

  + На панели управления щелкните **Система и безопасность** > **Система** > **Расширенные параметры системы** > **Переменные среды**.
  + Создайте системную переменную с именем **MKL_CBWR** и значением **AUTO**.

## <a name="2---locate-executables"></a>2\. Обнаружение исполняемых файлов

Найдите и выведите список файлов в папке установки, чтобы убедиться, что установлены R.exe, RGUI и другие пакеты. 

1. В проводнике откройте папку C:\Program Files\Microsoft\R Client\R_SERVER\bin, чтобы проверить расположение файла R.exe.

2. Откройте вложенную папку x64, чтобы проверить расположение **RGUI**. Это средство будет использоваться в следующем шаге.

3. Откройте папку C:\Program Files\Microsoft\R Client\R_SERVER\library, чтобы просмотреть список пакетов, установленных с R Client, включая RevoScaleR, MicrosoftML и другие.


<a name="R-tools"></a>
 
## <a name="3---start-rgui"></a>3\. Запуск RGUI

При установке R с SQL Server вы получаете стандартные инструменты R для базовой установки R, например RGui, Rterm и т. д. Они просты в использовании и позволяют проверять сведения о пакетах и библиотеках, запускать специальные команды или скрипты, а также применяются для выполнения инструкций в руководствах. С помощью этих средств можно получать сведения о версии R и проверять подключения.

1. Откройте папку C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64 и дважды щелкните **RGui**, чтобы запустить сеанс R с помощью командной строки R.

  При запуске сеанса R из папки программ Майкрософт автоматически загрузятся несколько пакетов, включая RevoScaleR. 

2. В командной строке введите `print(Revo.version)`, чтобы получить сведения о версии пакета RevoScaleR. Пакет RevoScaleR должен иметь версию 9.2.1 или 9.3.0.

3. В командной строке R введите **search()** , чтобы получить список установленных пакетов.

   ![Сведения о версии при загрузке R](../install/media/rclient-rgui-r-prompt.png "Открытие командной строки R")


## <a name="4---get-sql-permissions"></a>4\. Получение разрешений SQL

В R Client обработка R ограничена двумя потоками и данными в памяти. При масштабируемой обработке, в которой задействовано несколько ядер и больших наборов данных, выполнение (называемое *контекстом вычисления*) можно перенести в наборы данных и использовать вычислительную мощность удаленного экземпляра SQL Server. Это рекомендуемый подход к интеграции клиента с рабочим экземпляром SQL Server, и для его реализации потребуются разрешения и сведения о подключении.

Чтобы подключиться к экземпляру SQL Server для выполнения сценариев и передачи данных, необходимо иметь допустимое имя входа на сервере базы данных. Можно использовать либо имя входа SQL, либо встроенную проверку подлинности Windows. Обычно рекомендуется использовать встроенную проверку подлинности Windows, но в некоторых случаях проще использовать имя входа SQL, особенно если сценарий содержит строки подключения к внешним данным.

У учетной записи, используемой для выполнения кода, должно быть разрешение на чтение для баз данных, с которыми вы работаете, а также специальное разрешение EXECUTE ANY EXTERNAL SCRIPT. Большинству разработчиков также требуются разрешения на создание хранимых процедур и на запись данных в таблицы, содержащие данные обучения или данные оценки. 

Попросите администратора базы данных [настроить следующие разрешения для учетной записи](../security/user-permission.md) в базе данных, в которой используется R:

+ **EXECUTE ANY EXTERNAL SCRIPT** для запуска скрипта R на сервере.
+ Привилегии **db_datareader** для выполнения запросов, используемых для обучения модели.
+ **db_datawriter** для записи данных обучения и данных оценки.
+ **db_owner** для создания таких объектов, как хранимые процедуры, таблицы и функции. 
  Разрешение **db_owner** также потребуется для создания примеров баз данных и тестовых баз данных. 

Если для кода требуются пакеты, которые по умолчанию не установлены в SQL Server, обратитесь к администратору базы данных, чтобы установить необходимые пакеты. SQL Server представляет собой защищенную среду, и существуют ограничения на места установки пакетов. Дополнительные сведения см. в статье [Installing New R Packages on SQL Server](../package-management/install-additional-r-packages-on-sql-server.md)(Установка новых пакетов R в SQL Server).

## <a name="5---test-connections"></a>5\. Проверка подключения

 Для проверки подключения к удаленному серверу используйте **RGUI** и RevoScaleR. SQL Server должен быть включен для [удаленных подключений](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server), а вам требуются разрешения, в том числе имя входа пользователя и база данных для подключения. 

При выполнений следующих действий используется демонстрационная база данных [NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md) и проверка подлинности Windows.

1. Откройте **RGUI** на клиентской рабочей станции. Например, перейдите к папке `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` и дважды щелкните файл **RGui.exe**, чтобы запустить его.

2. RevoScaleR загрузится автоматически. Проверьте работоспособность RevoScaleR, выполнив следующую команду: `print(Revo.version)`.

3. Введите демонстрационный скрипт, выполняемый на удаленном сервере. Необходимо изменить следующий пример скрипта, включив в него допустимое имя для удаленного экземпляра SQL Server. Этот сеанс начинается как локальный сеанс, но функция **rxSummary** выполняется на удаленном экземпляре SQL Server.

  ```R
  # Define a connection. Replace server with a valid server name.
  connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
  
  # Specify the input data in a SQL query.
  sampleQuery <-"SELECT DISTINCT TOP(100) tip_amount FROM [dbo].nyctaxi_sample ORDER BY tip_amount DESC;"
  
  # Define a remote compute context based on the remote server.
  cc <-RxInSqlServer(connectionString=connStr)

  # Execute the function using the remote compute context.
  rxSummary(formula = ~ ., data = RxSqlServerData(sqlQuery=sampleQuery, connectionString=connStr), computeContext=cc)
  ```

  **Результаты:**

  Этот скрипт подключается к базе данных на удаленном сервере, предоставляет запрос, создает инструкцию `cc` контекста вычисления для удаленного выполнения кода, а затем предоставляет функцию RevoScaleR **rxSummary** для возврата статистической сводки результатов запроса.

  ```R
    Call:
  rxSummary(formula = ~., data = RxSqlServerData(sqlQuery = sampleQuery, 
      connectionString = connStr), computeContext = cc)

  Summary Statistics Results for: ~.
  Data: RxSqlServerData(sqlQuery = sampleQuery, connectionString = connStr) (RxSqlServerData Data Source)
  Number of valid observations: 100 
  
  Name       Mean   StdDev   Min Max ValidObs MissingObs
  tip_amount 63.245 31.61087 36  180 100      0     
  ```

4. Получите и задайте контекст вычисления. Заданный контекст вычисления действует в течение сеанса. Если вы не уверены, что вычисления являются локальными или удаленными, выполните следующую команду, чтобы выяснить это. Результаты, указывающие строку соединения, означают удаленный контекст вычисления.

  ```R
  # Return the current compute context.
  rxGetComputeContext()

  # Revert to a local compute context.
  rxSetComputeContext("local")
  rxGetComputeContext()

  # Switch back to remote.
  connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
  cc <-RxInSqlServer(connectionString=connStr)
  rxSetComputeContext(cc)
  rxGetComputeContext()
  ```  

5. Получите сведения о переменных в источнике данных, включая имя и тип.

  ```R
  rxGetVarInfo(data = inDataSource)
  ```
  Результаты содержат 23 переменные.


6. Создайте точечную диаграмму, чтобы определить наличие зависимостей между двумя переменными. 

  ```R
  # Set the connection string. Substitute a valid server name for the placeholder.
  connStr <- "Driver=SQL Server;Server=<your database name>;Database=NYCTaxi_Sample;Trusted_Connection=true"

  # Specify a query on the nyctaxi_sample table.
  # For variables on each axis, remove nulls. Use a WHERE clause and <> to do this.
  sampleQuery <-"SELECT DISTINCT TOP 100 * from [dbo].[nyctaxi_sample] WHERE fare_amount <> '' AND  tip_amount <> ''"
  cc <-RxInSqlServer(connectionString=connStr)

  # Generate a scatter plot.
  rxLinePlot(fare_amount ~ tip_amount, data = RxSqlServerData(sqlQuery=sampleQuery, connectionString=connStr, computeContext=cc), type="p")
  ```

  На следующем снимке экрана показаны входные данные и выходные данные в виде точечной диаграммы.

   ![Точечная диаграмма в RGUI](media/rclient-setup-scatterplot.png "Точечная диаграмма на основе демонстрационных данных по работе такси в Нью-Йорке")

<a name="install-ide"></a>

## <a name="6---link-tools-to-rexe"></a>6\. Связывание инструментов с R.exe

Для поддержки долговременных и серьезных проектов разработки следует установить интегрированную среду разработки (IDE). Средства SQL Server и встроенные инструменты R не предназначены для интенсивной разработки на R. Существующий рабочий код можно развернуть как хранимую процедуру для выполнения на SQL Server.

Укажите в IDE локальные библиотеки R: базовую библиотеку R, RevoScaleR и т. д. Выполнение рабочих нагрузок на удаленном SQL Server происходит во время выполнения скрипта, когда скрипт запускает удаленный контекст вычисления на SQL Server, получая доступ к данным и операциям на этом сервере.

### <a name="rstudio"></a>RStudio

В [RStudio](https://www.rstudio.com/) можно настроить среду для использования библиотек и исполняемых файлов R, которые соответствуют своим эквивалентам на удаленном экземпляре SQL Server.

1. Проверьте версии пакетов R, установленные на SQL Server. Дополнительные сведения см. в статье [Получение сведений о пакете R](../package-management/r-package-information.md).

1. Установите Microsoft R Client или один из изолированных серверов, чтобы добавить RevoScaleR и другие пакеты R, включая базовый дистрибутив R, используемый экземпляром SQL Server. Выберите версию на том же уровне или ниже (пакеты поддерживают обратную совместимость), которая предоставляет те же версии пакетов, что и на сервере. Сведения о версии см. в таблице в этой статье: [Обновление компонентов R и Python](../install/upgrade-r-and-python.md).

1. В RStudio [обновите путь R](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) так, чтобы он указывал на среду R, предоставляющую RevoScaleR, Microsoft R Open и другие пакеты Майкрософт. 

  + Для установки клиента R найдите папку C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64.
  + Для установки изолированного сервера найдите папку C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library или C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library.

2. Закройте, а затем откройте RStudio.

При повторном открытии RStudio, исполняемый файл R из R Client (или изолированного сервера) будет подсистемой R по умолчанию.


### <a name="r-tools-for-visual-studio-rtvs"></a>Инструменты R для Visual Studio (RTVS)

Если у вас еще нет предпочтительной интегрированной среды разработки для R, рекомендуется воспользоваться **инструментами R для Visual Studio**.

+ [Скачивание инструментов R для Visual Studio (RTVS)](https://marketplace.visualstudio.com/items?itemName=MikhailArkhipov007.RTVS2019)
+ [Инструкции по установке](https://docs.microsoft.com/visualstudio/rtvs/installing-r-tools-for-visual-studio) — инструменты RTVS доступны в нескольких версиях Visual Studio.
+ [Начало работы с инструментами R для Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>Подключение к SQL Server из RTVS

В этом примере используется Visual Studio 2017 Community Edition с установленной рабочей нагрузкой обработки и анализа данных.

1. В меню **Файл** выберите пункт **Создать**, а затем — **Проект**.

2. На левой панели находится список предварительно установленных шаблонов. Щелкните **R**и выберите **Проект R**. В поле **Имя** введите `dbtest`, а затем нажмите кнопку **ОК**. 

  Visual Studio создает папку проекта и файл скрипта по умолчанию `Script.R`. 

3. В первой строке файла скрипта введите `.libPaths()`, а затем нажмите клавиши CTRL+ВВОД.

  В **интерактивном окне R** должен появиться текущий путь к библиотеке R. 

4. Щелкните меню **Инструменты R** и выберите **Windows**, чтобы просмотреть список других связанных с R окон, которые можно открыть в рабочей области.
 
  + Просмотрите справку по пакетам в текущей библиотеке, нажав клавиши CTRL+3.
  + Просмотрите переменные R в **обозревателе переменных**, нажав клавиши CTRL+8.

## <a name="next-steps"></a>Дальнейшие действия

Упражнения по переключению контекста вычисления с локального на удаленный экземпляр SQL Server можно найти в двух разных учебниках.

+ [Руководство. Использование функций R RevoScaleR с данными SQL Server](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Пошаговое руководство по обработке и анализу данных](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)