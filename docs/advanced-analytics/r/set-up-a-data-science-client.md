---
title: Настройка клиента обработки и анализа данных для разработки на R
description: Установите локальные библиотеки R и средства на рабочей станции разработки для удаленных подключений к SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7c81a69181d1bc723e622bac9ffeb5ff67fd0280
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69633635"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Настройка клиента обработки и анализа данных для разработки R на SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Интеграция r доступна в SQL Server 2016 или более поздней версии, если включить параметр языка R в [SQL Server 2016 служб R](../install/sql-r-services-windows-install.md) или [SQL Server службы машинного обучения (в базе данных)](../install/sql-machine-learning-services-windows-install.md) . 

Чтобы разрабатывать и развертывать решения R для SQL Server, установите [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) на рабочей станции разработки, чтобы получить [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) и другие библиотеки R. Библиотека RevoScaleR, которая также необходима на удаленном экземпляре SQL Server, координирует вычислительные запросы между обеими системами. 

Из этой статьи вы узнаете, как настроить рабочую станцию разработки R Client, чтобы вы могли взаимодействовать с удаленными SQL Server, включенными для машинного обучения и интеграции R. После выполнения действий, описанных в этой статье, вы получите те же библиотеки R, что и на SQL Server. Вы также узнаете, как отправлять вычисления из локального сеанса R в удаленный сеанс R на SQL Server.

![Клиент-серверные компоненты](media/sqlmls-r-client-revo.png "Локальные и удаленные сеансы и библиотеки R")

Чтобы проверить установку, можно использовать встроенное средство **RGUI** , как описано в этой статье, или [связать библиотеки](#install-ide) с RStudio или любой другой интегрированной средой разработки, которая используется в обычном режиме.

> [!Note]
> Альтернативой установке клиентской библиотеки является использование [изолированного сервера](../install/sql-machine-learning-standalone-windows-install.md) в качестве полнофункционального клиента, который некоторые клиенты предпочитают использовать более глубокий сценарий. Изолированный сервер полностью отделен от SQL Server, но, поскольку он имеет те же библиотеки R, его можно использовать в качестве клиента для SQL Server аналитики в базе данных. Его также можно использовать для работы, не связанной с SQL, включая возможность импорта и моделирования данных из других платформ данных. Если вы устанавливаете автономный сервер, исполняемый файл R можно найти в следующем расположении: `C:\Program Files\Microsoft SQL Server\140\R_SERVER`. Чтобы проверить установку, [Откройте консольное приложение r](#R-tools) для выполнения команд с помощью r. exe в этом расположении.

## <a name="commonly-used-tools"></a>Часто используемые средства

Если вы являетесь разработчиком R, новым для SQL, или разработчиком SQL, новым для R и аналитики в базе данных, вам потребуется как средство разработки R, так и редактор запросов T-SQL, например [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) для выполнения всех возможностей в базе данных. средства.

Для простых сценариев разработки R можно использовать исполняемый файл RGUI, Объединенный в базовое распределение R в MRO и SQL Server. В этой статье объясняется, как использовать RGUI как для локальных, так и для удаленных сеансов R. Для повышения производительности следует использовать полнофункциональную интегрированную среду разработки, например [RStudio или Visual Studio](#install-ide).

SSMS — это отдельная загрузка, которая полезна для создания и выполнения хранимых процедур на SQL Server, включая те, которые содержат код R. Практически любой код R, написанный в среде разработки, может быть внедрен в хранимую процедуру. Вы можете пошагово пройти другие учебники, чтобы узнать о [SSMS и Embedded R](../tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="1---install-r-packages"></a>1\. Установка пакетов R

Пакеты R Microsoft доступны в нескольких продуктах и службах. На локальной рабочей станции рекомендуется установить Microsoft R Client. Клиент r предоставляет [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package), [SQLRUtils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)и другие пакеты R.

1. [Скачайте Microsoft R Client](https://aka.ms/rclient/download).

2. В мастере установки примите или измените путь установки по умолчанию, примите или измените список компонентов и примите условия лицензии Microsoft R Client.

  После завершения установки появится экран приветствия с описанием продукта и документации.

3. Создайте переменную системной среды MKL_CBWR, чтобы обеспечить последовательный вывод данных в вычислениях для библиотеки Intel Math Kernel (MKL).

  + На панели управления щелкните **система и система безопасности** >  > **Дополнительные** > **переменные среды**системы.
  + Создайте новую системную переменную с именем **MKL_CBWR**и значением, равным **Auto**.

## <a name="2---locate-executables"></a>2\. Обнаружение исполняемых файлов

Выберите и перечислите содержимое папки установки, чтобы убедиться, что установлены R. exe, RGUI и другие пакеты. 

1. В проводнике откройте папку C:\Program Филес\микрософт\р Client\R_SERVER\bin, чтобы подтвердить расположение R. exe.

2. Откройте вложенную папку x64, чтобы подтвердить **RGUI**. Это средство будет использоваться на следующем шаге.

3. Откройте папку C:\Program Филес\микрософт\р Client\R_SERVER\library, чтобы просмотреть список пакетов, установленных с помощью клиента R, включая RevoScaleR, MicrosoftML и другие.


<a name="R-tools"></a>
 
## <a name="3---start-rgui"></a>3\. Запуск RGUI

При установке R с SQL Server вы получаете те же средства R, которые являются стандартными для любой базовой установки R, например RGui, Rterm и т. д. Эти средства являются упрощенными и полезны для проверки сведений о пакетах и библиотеках, выполнения нерегламентированных команд или сценариев, а также пошаговых руководств. Эти средства можно использовать для получения сведений о версии R и подтверждения подключения.

1. Откройте папку C:\Program Филес\микрософт\р Client\R_SERVER\bin\x64 и дважды щелкните **RGui** , чтобы запустить сеанс r с помощью командной строки r.

  При запуске сеанса R из папки программы Майкрософт несколько пакетов, включая RevoScaleR, загружаются автоматически. 

2. Введите `print(Revo.version)` в командной строке, чтобы вернуть сведения о версии пакета RevoScaleR. Для RevoScaleR должна быть установлена версия 9.2.1 или 9.3.0.

3. Введите **Search ()** в командной строке R, чтобы получить список установленных пакетов.

   ![Сведения о версии при загрузке R](../install/media/rclient-rgui-r-prompt.png "Открытие запроса R")


## <a name="4---get-sql-permissions"></a>4\. получение разрешений SQL

В клиенте R обработка R ограничена двумя потоками и данными в памяти. Для масштабируемой обработки с использованием нескольких ядер и больших наборов данных можно сдвинуть выполнение (называемое контекстом *вычислений*) на наборы данных и вычислительную мощность удаленного экземпляра SQL Server. Это рекомендуемый подход к интеграции клиента с экземпляром рабочего SQL Server, и для его работы потребуются разрешения и сведения о подключении.

Чтобы подключиться к экземпляру SQL Server для выполнения скриптов и передачи данных, необходимо иметь допустимое имя входа на сервере базы данных. Можно использовать либо имя входа SQL, либо встроенную проверку подлинности Windows. Обычно рекомендуется использовать встроенную проверку подлинности Windows, но использовать имя входа SQL проще в некоторых сценариях, особенно если скрипт содержит строки подключения к внешним данным.

Как минимум, учетная запись, используемая для выполнения кода, должна иметь разрешение на чтение из баз данных, с которыми вы работаете, а специальное разрешение ВЫПОЛНЯЕТ любой внешний сценарий. Большинству разработчиков также требуются разрешения на создание хранимых процедур и запись данных в таблицы, содержащие обучающие данные или данные с оценками. 

Попросите администратора базы данных [настроить следующие разрешения для вашей учетной записи](../security/user-permission.md)в базе данных, где используется R:

+ **Выполните любой внешний скрипт** для выполнения скрипта R на сервере.
+ **db_datareader** привилегии для выполнения запросов, используемых для обучения модели.
+ **db_datawriter** для записи обучающих данных или оценочных данных.
+ **db_owner** для создания таких объектов, как хранимые процедуры, таблицы, функции. 
  Кроме того, для создания образцов и тестовых баз данных требуется **db_owner** . 

Если для кода требуются пакеты, которые не устанавливаются по умолчанию с SQL Server, следует попытаться установить пакеты с экземпляром с помощью администратора базы данных. SQL Server является защищенной средой, а также существуют ограничения на установку пакетов. Дополнительные сведения см. [в статье Установка новых пакетов R на SQL Server](install-additional-r-packages-on-sql-server.md).

## <a name="5---test-connections"></a>5\. Тестирование подключений

 В качестве шага проверки используйте **RGUI** и RevoScaleR для подтверждения подключения к удаленному серверу. SQL Server должны быть включены для [удаленных подключений](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server) , и необходимо иметь разрешения, включая имя входа пользователя и базу данных для подключения. 

Для выполнения следующих действий предполагается демонстрационная база данных, [NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md)и проверка подлинности Windows.

1. Откройте **RGUI** на клиентской рабочей станции. Например, откройте `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` и дважды щелкните **RGui. exe** , чтобы запустить его.

2. RevoScaleR загружается автоматически. Убедитесь, что RevoScaleR работает, выполнив следующую команду:`print(Revo.version)`

3. Введите демонстрационный сценарий, выполняемый на удаленном сервере. Необходимо изменить следующий пример скрипта, включив в него допустимое имя для удаленного экземпляра SQL Server. Этот сеанс начинается как локальный сеанс, но функция **rxSummary** выполняется на удаленном экземпляре SQL Server.

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

  Этот сценарий подключается к базе данных на удаленном сервере, предоставляет запрос, создает инструкцию `cc` контекста вычислений для удаленного выполнения кода, а затем предоставляет функцию RevoScaleR **rxSummary** для возврата статистической сводки по запросу. результаты.

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

4. Получение и задание контекста вычислений. После установки контекста вычислений он остается в силе на время сеанса. Если вы не уверены, являются ли вычисления локальными или удаленными, выполните следующую команду, чтобы узнать. Результаты, указывающие строку соединения, указывают на удаленный контекст вычислений.

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

5. Возвращает сведения о переменных в источнике данных, включая имя и тип.

  ```R
  rxGetVarInfo(data = inDataSource)
  ```
  Результаты включают 23 переменных.


6. Создайте точечную диаграмму, чтобы узнать, существуют ли зависимости между двумя переменными. 

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

  На следующем снимке экрана показаны входные и точечные выходные диаграммы.

   ![Точечная диаграмма в RGUI](media/rclient-setup-scatterplot.png "Точечная диаграмма на демонстрационных данных Нью такси")

<a name="install-ide"></a>

## <a name="6---link-tools-to-rexe"></a>6\. Связывание инструментов с R. exe

Для устойчивых и серьезных проектов разработки следует установить интегрированную среду разработки (IDE). Средства SQL Server и встроенные инструменты R не имеют большого объема разработки R. После работы с кодом можно развернуть его как хранимую процедуру для выполнения на SQL Server.

Наведите на IDE локальные библиотеки R: Base R, RevoScaleR и т. д. Выполнение рабочих нагрузок на удаленном SQL Server происходит во время выполнения скрипта, когда скрипт вызывает удаленный контекст вычислений на SQL Server, осуществляя доступ к данным и операциям на этом сервере.

### <a name="rstudio"></a>RStudio

При использовании [RStudio](https://www.rstudio.com/)можно настроить среду для использования библиотек R и исполняемых файлов, которые соответствуют удаленным SQL Server.

1. Проверьте версии пакетов R, установленные на SQL Server. Дополнительные сведения см. в разделе [Получение сведений о пакете R](../package-management/r-package-information.md).

1. Установите Microsoft R Client или один из отдельных параметров сервера, чтобы добавить RevoScaleR и другие пакеты R, включая базовое распределение R, используемое экземпляром SQL Server. Выберите версию на том же уровне или ниже (пакеты имеют обратную совместимость), которая предоставляет те же версии пакетов, что и на сервере. Сведения о версии см. в схеме версии в этой статье: [Обновление компонентов R и Python](../install/upgrade-r-and-python.md).

1. В RStudio [Обновите свой путь r](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) , чтобы он указывал на среду r, которая предоставляет RevoScaleR, Microsoft R Open и другие пакеты Майкрософт. 

  + Для установки клиента R найдите папку C:\Program Филес\микрософт\р Client\R_SERVER\bin\x64
  + Для изолированного сервера найдите папку C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library или C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library

2. Закройте, а затем откройте RStudio.

Когда вы повторно открываете RStudio, исполняемый файл R из R Client (или изолированный сервер) является подсистемой R по умолчанию.


### <a name="r-tools-for-visual-studio-rtvs"></a>Инструменты R для Visual Studio (RTVS)

Если у вас еще нет предпочтительной интегрированной среды разработки для R, рекомендуем **инструменты R для Visual Studio**.

+ [Инструменты R для Visual Studio загрузки (RTVS)](https://visualstudio.microsoft.com/vs/features/rtvs/)
+ [Инструкции по установке](https://docs.microsoft.com/visualstudio/rtvs/installing-r-tools-for-visual-studio) — RTVS доступны в нескольких версиях Visual Studio.
+ [Начало работы с Инструменты R для Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>Подключение к SQL Server из RTVS

В этом примере используется Visual Studio 2017 Community Edition с установленной рабочей нагрузкой обработки и анализа данных.

1. В меню **файл** выберите пункт **создать** , а затем выберите **проект**.

2. На левой панели содержится список предварительно установленных шаблонов. Щелкните **r**и выберите **проект r**. В поле **имя** введите `dbtest` и нажмите кнопку **ОК**. 

  Visual Studio создает новую папку проекта и файл скрипта по умолчанию `Script.R`,. 

3. Введите `.libPaths()` текст в первой строке файла сценария, а затем нажмите клавиши CTRL + ВВОД.

  Текущий путь к библиотеке R должен отображаться в окне **интерактивное окно R** . 

4. Щелкните меню **Сервис r** и выберите **Windows** , чтобы просмотреть список других окон, связанных с R, которые можно отобразить в рабочей области.
 
  + Просмотрите справку по пакетам в текущей библиотеке, нажав клавиши CTRL + 3.
  + Чтобы просмотреть переменные R в **Обозреватель переменных**, нажмите клавиши CTRL + 8.

## <a name="next-steps"></a>Следующие шаги

В двух разных учебниках есть упражнения, позволяющие переходить от локальной среды к удаленному экземпляру SQL Server.

+ [Учебник. Использование функций R RevoScaleR с данными SQL Server](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Пошаговое руководство по обработке и анализу данных](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)