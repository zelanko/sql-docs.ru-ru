---
title: Настройка клиента обработки и анализа данных для средств разработки R - служб машинного обучения SQL Server
description: Установка локального библиотеки и средства R на рабочей станции разработки для удаленных подключений к SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 12fefddcc01caeb9705c823a4e7283169dda1cc3
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510441"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Настройка клиента обработки и анализа данных для средств разработки R на сервере SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Интеграция R в SQL Server 2016 или более поздней версии, при включении параметра language R в [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) или [служб SQL Server 2017 машинного обучения (в базе данных)](../install/sql-machine-learning-services-windows-install.md) установки. 

Для разработки и развертывания решений R для SQL Server следует установить [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) на рабочей станции разработки, чтобы получить [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) и другие библиотеки R. Библиотеки RevoScaleR, который также является обязательным на удаленном экземпляре SQL Server, координирует вычислительной запросы между обеих систем. 

В этой статье сведения о настройке рабочей станции разработки R клиента, так что вы можете взаимодействовать с удаленный экземпляр SQL Server для машинного обучения и интеграция R. После выполнения действий, описанных в этой статье, вы получите те же библиотеки R, как на SQL Server. Также будет знать, как принудительно отправлять вычисления в локальном сеансе r. в удаленный сеанс R на SQL Server.

![Клиент серверные компоненты](media/sqlmls-r-client-revo.png "локальных и удаленных сеансов R и библиотеки")

Чтобы проверить установку, можно воспользоваться встроенным **RGUI** средство, как описано в этой статье или [привязывать библиотеки](#install-ide) RStudio или любой другой интегрированной среде разработки, которое вы обычно используете.

> [!Tip]
> Видеозапись с демонстрацией упражнений, см. в разделе [выполнения R и Python удаленно в SQL Server из записных книжек Jupyter](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/).

> [!Note]
> Вместо установки библиотеки клиента использует [изолированный сервер](../install/sql-machine-learning-standalone-windows-install.md) качестве полнофункционального клиента, что некоторые клиенты предпочитают для более глубокого работы сценария. Автономный сервер полностью отделен от SQL Server, но так как он имеет те же библиотеки R, можно использовать его как клиент для анализа в базе данных SQL Server. Вы также можно использовать для работы, не относящиеся к SQL, включая возможность импортировать и моделирование данных с других платформ данных. При установке изолированного сервера, можно найти исполняемый файл R в этом месте: `C:\Program Files\Microsoft SQL Server\140\R_SERVER`. Проверить установку, [открытие приложения консоли R](#R-tools) для выполнения команд, с помощью R.exe в этом расположении.

## <a name="commonly-used-tools"></a>Широко используемых средств

Вы — разработчик R в SQL или разработчик опыта работы с R и аналитики в базе данных SQL, необходимо будет средство разработки R и редактор T-SQL-запросов например [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) соблюдать все возможности аналитики в базе данных.

Для простых сценариев разработки R можно использовать RGUI исполняемого файла, объединенными в базовое распределение R в MRO и SQL Server. В этой статье описываются способы использования RGUI для локальных и удаленных сеансов R. Для повышения производительности следует использовать полнофункциональная интегрированная среда разработки например [Visual Studio или RStudio](#install-ide).

SSMS является отдельной загрузкой, используются для создания и выполнения хранимых процедур на сервере SQL Server, в том числе кодом R. Практически любой код R, созданный в среде разработки можно внедрить в хранимой процедуре. В пошаговом режиме других руководств, чтобы узнать о [SSMS и внедренных R](../tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="1---install-r-packages"></a>1 - Установка пакетов R

Пакеты R корпорации Майкрософт будут доступны в нескольких продуктах и службах. На локальной рабочей станции мы рекомендуем установить Microsoft R Client. R Client предоставляет [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package), [SQLRUtils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)и другие пакеты R.

1. [Скачайте Microsoft R Client](https://aka.ms/rclient/download).

2. В мастере установки принять или изменить путь установки по умолчанию, принять или изменить список компонентов и примите условия лицензии Microsoft R Client.

  По завершении установки экран приветствия рассказывается о продукте и документации.

3. Создание переменной среды MKL_CBWR системы, чтобы обеспечить согласованный результат на вычислениях Intel Math Kernel Library (MKL).

  + На панели управления выберите **система и безопасность** > **системы** > **Дополнительные параметры системы**  >   **Переменные среды**.
  + Создать новую переменную с именем **MKL_CBWR**, со значением, равным **АВТОМАТИЧЕСКИ**.

## <a name="2---locate-executables"></a>2 - поиск исполняемых файлов

Найдите и список содержимого папки установки, чтобы убедиться, что R.exe RGUI и другие пакеты установлены. 

1. В проводнике откройте папку C:\Program Files\Microsoft\R Client\R_SERVER\bin, чтобы проверить расположение соответствующих R.exe.

2. Открыть x64 во вложенную папку для подтверждения **RGUI**. Это средство будет использовать на следующем шаге.

3. Откройте C:\Program Files\Microsoft\R Client\R_SERVER\library, чтобы просмотреть список пакетов, установленных с R Client, включая RevoScaleR, MicrosoftML и пр.


<a name="R-tools"></a>
 
## <a name="3---start-rgui"></a>3 - start RGUI

При установке R с SQL Server, вы получите те же средства R, которые являются стандартными для любой базовой установке R, например RGui и Rterm, т. д. Эти средства являются упрощенная, что удобно для проверка сведений о пакете и библиотеки, выполнение нерегламентированных команд или сценария или пошагового руководства. Эти средства можно использовать для получения сведений о версии R и проверке подключения.

1. Откройте C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64 и дважды щелкните **RGui** запускается сеанс R с командной строкой R.

  При запуске сеанса R из папки программы Майкрософт, несколько пакетов, включая RevoScaleR, загружаются автоматически. 

2. Введите `print(Revo.version)` в командной строке, чтобы вернуть RevoScaleR упаковать сведения о версии. Должна быть версия 9.2.1 или 9.3.0 для RevoScaleR.

3. Введите **search()** в командной строке R список установленных пакетов.

   ![Сведения о версии при загрузке R](../install/media/rclient-rgui-r-prompt.png "откройте командную строку R")


## <a name="4---get-sql-permissions"></a>4 - получение разрешений SQL

В R Client обработки R составляет два потока и данных в памяти. Для масштабируемой обработки, использование нескольких ядер и больших наборов данных, вы можете сместить выполнения (называется *контекста вычислений*) для наборов данных и вычислительную мощь удаленного экземпляра SQL Server. Это рекомендуемый подход для клиента интеграцию с рабочим экземпляром SQL Server, и вам потребуется разрешения и сведения о соединении для его работы.

Чтобы подключиться к экземпляру SQL Server для выполнения скриптов и отправки данных, необходимо иметь допустимое имя входа на сервере базы данных. Можно использовать либо имя входа SQL, либо встроенную проверку подлинности Windows. Обычно рекомендуется использовать встроенную проверку подлинности Windows, что с помощью имени входа SQL проще для некоторых сценариев, особенно в том случае, если скрипт содержит строки подключения к внешним данным.

Как минимум учетная запись, используемая для запуска кода необходимо иметь разрешение на чтение из базы данных, вы работаете, а также специальное разрешение Выполнение ЛЮБОГО ВНЕШНЕГО СКРИПТА. Большинство разработчиков также требуются разрешения для создания хранимых процедур и для записи данных в таблицы, содержащие данные для обучения или оценки данных. 

Попросите администратора базы данных [настроить следующие разрешения для учетной записи](../security/user-permission.md), в базе данных, где используется R:

+ **EXECUTE ANY EXTERNAL SCRIPT** для выполнения скрипта R на сервере.
+ **db_datareader** привилегий для выполнения запросов, используемых для обучения модели.
+ **db_datawriter** для записи данных для обучения или оценки данных.
+ **db_owner** для создания объектов, таких как хранимые процедуры, таблицы, функции. 
  Необходимо также **db_owner** создавать пример и тестирования базы данных. 

Если код требует пакеты, которые не устанавливаются по умолчанию вместе с SQL Server, упорядочить администратору базы данных, чтобы получить пакеты, установленные с экземпляром. SQL Server является безопасной среде и существуют ограничения на установки пакетов. Дополнительные сведения см. в разделе [Установка новых пакетов R в SQL Server](install-additional-r-packages-on-sql-server.md).

## <a name="5---test-connections"></a>5 - Тестирование подключений

 В качестве шага проверки, используйте **RGUI** и RevoScaleR для подтверждения подключения к удаленному серверу. SQL Server должна быть включена для [удаленные подключения](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server) и необходимо иметь разрешения, включая имя входа пользователя и для подключения к базе данных. 

В следующих шагах предполагается демонстрационной базы данных, [NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md)и проверка подлинности Windows.

1. Откройте **RGUI** на клиентской рабочей станции. Например, перейдите к `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` и дважды щелкните **RGui.exe** для его запуска.

2. Автоматически загружает RevoScaleR. Убедитесь, что RevoScaleR работает, выполнив следующую команду: `print(Revo.version)`

3. Введите демонстрационный сценарий, который выполняется на удаленном сервере. В следующем образце сценария, чтобы включить допустимое имя для удаленного экземпляра SQL Server, необходимо изменить. Этот сеанс начинается как локальный сеанс, но **rxSummary** функция выполняется на удаленном экземпляре SQL Server.

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

  Этот сценарий подключается к базе данных на удаленном сервере, предоставляет запрос, создает контекст вычислений `cc` инструкция удаленный запуск программного кода, затем обеспечивает функцию RevoScaleR **rxSummary** для возврата статистический Сводка результатов запроса.

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

4. Получение и задание контекста вычислений. После настройки контекста вычислений, он действует в течение сеанса. Если вы не уверены ли вычислений является локальным или удаленным, выполните следующую команду, чтобы узнать. Результаты, укажите строку соединения указывают контекст удаленных вычислений.

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

5. Возвращают сведения о переменных в источнике данных, включая имя и тип.

  ```R
  rxGetVarInfo(data = inDataSource)
  ```
  Результаты включают 23 переменные.


6. Создайте точечную диаграмму, чтобы изучить, существуют зависимости между двумя переменными. 

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

  На следующем рисунке показаны входные данные и точечных выходные данные построения.

   ![Точечная диаграмма в RGUI](media/rclient-setup-scatterplot.png "точечную диаграмму на такси Нью-ЙОРКА демонстрационных данных")

<a name="install-ide"></a>

## <a name="6---link-tools-to-rexe"></a>6 - link, позволяющих R.exe

Для постоянной и серьезных проектов необходимо установить интегрированную среду разработки (IDE). Средства SQL Server и встроенные средства R для усиленно R не способны. Получив рабочий код, его можно развернуть как хранимую процедуру для выполнения на сервере SQL Server.

Пункты локальных библиотек R IDE: базовый R, RevoScaleR и т. д. Происходит во время выполнения скрипта, рабочих нагрузок выполняются на удаленном экземпляре SQL Server, когда сценарий вызывает контекст удаленных вычислений на сервере SQL Server, доступ к данным и операциям на этом сервере.

### <a name="rstudio"></a>RStudio

При использовании [RStudio](https://www.rstudio.com/), можно настроить среду для использования библиотеки R и исполняемые файлы, которые соответствуют элементам на удаленный экземпляр SQL Server.

1. Проверка версии пакета R, установленные на сервере SQL Server. Дополнительные сведения см. в разделе [R, получить сведения о пакете](determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).

1. Установите Microsoft R Client, или один из параметров автономного сервера для добавления RevoScaleR и другие пакеты R, включая базового дистрибутива R, используемые экземпляром SQL Server. Выберите версию в то же уровня или ниже (пакеты обратно совместимы), предоставляет те же версии пакета как на сервере. Сведения о версии см. в разделе версии сопоставления в этой статье: [Обновление компонентов R и Python](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

1. В RStudio [обновить путь R](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) указывал в среду R, обеспечивая RevoScaleR, Microsoft R Open и другие пакеты Microsoft. 

  + Для установки R Client искать C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64
  + Для автономного сервера ищите C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library или C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library

2. Закройте и откройте RStudio.

При повторном открытии RStudio, R, исполняемый из клиента R (или отдельного сервера) — это ядро R по умолчанию.


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

## <a name="next-steps"></a>Следующие шаги

Два разных руководства содержат упражнения, таким образом, вы сможете совершенствовать переключение контекста вычислений на локальный с удаленным экземпляром SQL Server.

+ [Учебник. Использовать функции RevoScaleR R с данными SQL Server](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Пошаговое руководство по обработке и анализу данных](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)