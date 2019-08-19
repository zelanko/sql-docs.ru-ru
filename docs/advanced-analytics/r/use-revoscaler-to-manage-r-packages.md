---
title: Как использовать функции RevoScaleR для поиска и установки пакетов R
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8db20295c2e21b6499d4d935f9c99161983b588f
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715584"
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Как использовать функции RevoScaleR для поиска или установки пакетов R на SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

RevoScaleR 9.0.1 и более поздние версии включают функции для управления пакетами R SQL Server контексте вычислений. Эти функции могут использоваться удаленными пользователями, не являющимися администраторами, для установки пакетов на SQL Server без прямого доступа к серверу.

SQL Server Службы машинного обучения уже содержит более новую версию RevoScaleR. SQL Server 2016 служб R клиенты должны выполнить [Обновление компонентов](../install/upgrade-r-and-python.md) для получения функций управления пакетами RevoScaleR. Инструкции по получению версии и содержимого пакета см. в разделе [Получение сведений о пакете](../package-management/installed-package-information.md).

## <a name="revoscaler-functions-for-package-management"></a>Функции RevoScaleR для управления пакетами

В следующей таблице описаны функции, используемые для установки и управления пакетами R.

| Компонент | Описание |
|----------|-------------|
| [рксскллибпасс](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | Определите путь к библиотеке экземпляров на удаленном SQL Server. |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage); | Возвращает путь для одного или нескольких пакетов на удаленном SQL Server. |
| [рксинсталлпаккажес](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | Вызывайте эту функцию из удаленного клиента R для установки пакетов в SQL Server контексте вычислений либо из указанного репозитория, либо путем считывания локально сохраненных zip-пакетов. Эта функция проверяет зависимости и гарантирует, что все связанные пакеты можно установить в SQL Server, точно так же, как установка пакета R в локальном контексте вычислений. Чтобы использовать этот параметр, необходимо включить управление пакетами на сервере и в базе данных. Как клиентские, так и серверные среды должны иметь одинаковую версию RevoScaleR. |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages). | Возвращает список пакетов, установленных в указанном контексте вычислений. |
| [ркссинкпаккажес](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | Копирование сведений о библиотеке пакетов между файловой системой и базой данных для указанного контекста вычислений. |
| [рксремовепаккажес](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | Удаляет пакеты из указанного контекста вычислений. Он также рассчитывает зависимости и гарантирует, что пакеты, которые больше не используются другими пакетами на SQL Server, будут удалены, чтобы освободить ресурсы. |

## <a name="prerequisites"></a>предварительные требования

+ [Включить удаленное управление пакетами R на SQL Server](r-package-how-to-enable-or-disable.md)

+ Версии RevoScaleR должны быть одинаковыми в клиентской и серверной средах. Дополнительные сведения см. в разделе [Получение сведений о пакете](../package-management/installed-package-information.md).

+ Разрешение на подключение к серверу и базе данных, а также выполнение команд R. Необходимо быть членом роли базы данных, которая позволяет устанавливать пакеты на заданном экземпляре и базе данных.

+ Пакеты в **общей области** могут быть установлены пользователями, принадлежащими `rpkgs-shared` роли в указанной базе данных. Все пользователи этой роли могут удалять общие пакеты.

+ Пакеты в **частной области** могут устанавливаться любым пользователем, принадлежащим к `rpkgs-private` роли в базе данных. Тем не менее пользователи могут просматривать и удалять только свои собственные пакеты.

+ Владельцы баз данных могут работать с общими или частными пакетами.

## <a name="client-connections"></a>Клиентские подключения

Клиентская рабочая станция может быть [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows) или [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (специалисты по обработке и анализу данных часто используют бесплатный выпуск Developer) в той же сети.

При вызове функций управления пакетами из удаленного клиента R необходимо сначала создать объект контекста вычислений с помощью функции [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) . Затем для каждой используемой функции управления пакетами передайте контекст вычислений в качестве аргумента.

Удостоверение пользователя обычно указывается при задании контекста вычислений. Если при создании контекста вычислений не указать имя пользователя и пароль, будет использоваться удостоверение пользователя, запускающего код R.

1. Из командной строки R определите строку подключения к экземпляру и базе данных.
2. Используйте конструктор [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) для определения контекста вычислений SQL Server, используя строку подключения.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Создайте список пакетов, которые необходимо установить, и сохраните список в строковой переменной.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Вызовите [рксинсталлпаккажес](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) и передайте контекст вычислений и строковую переменную, содержащую имена пакетов.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Если требуются зависимые пакеты, они также устанавливаются при условии, что на клиенте доступно подключение к Интернету.
    
    Пакеты устанавливаются с использованием учетных данных пользователя, выполняющего подключение, в области по умолчанию для этого пользователя.

## <a name="call-package-management-functions-in-stored-procedures"></a>Вызов функций управления пакетами в хранимых процедурах

Камера выполняет функции управления пакетами внутри `sp_execute_external_script`. После этого функция выполняется с использованием контекста безопасности вызывающего объекта хранимой процедуры.

## <a name="examples"></a>Примеры

В этом разделе приводятся примеры использования этих функций из удаленного клиента при подключении к SQL Server экземпляру или базе данных в качестве контекста вычислений.

Для всех примеров необходимо указать строку подключения или контекст вычислений, для которого требуется строка подключения. В этом примере представлен один из способов создания контекста вычислений для SQL Server.

```R
instance_name <- "computer-name/instance-name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

В зависимости от расположения сервера и модели безопасности может потребоваться указать в строке подключения спецификацию домена и подсети или использовать имя входа SQL. Пример:

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Получение пути к пакету на удаленном SQL Server контексте вычислений

В этом примере получается путь к пакету **RevoScaleR** в контексте `sqlcc`вычислений.

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**Результаты**

"C:/Program Files/Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/Library/RevoScaleR "

> [!TIP]
> Если вы включили параметр для просмотра выходных данных консоли SQL, вы можете получить сообщения о состоянии от функции, предшествующей `print` инструкции. После завершения тестирования кода задайте `consoleOutput` значение false в конструкторе контекста вычислений, чтобы исключить сообщения.

### <a name="get-locations-for-multiple-packages"></a>Получение расположений для нескольких пакетов

В следующем примере показано получение путей для пакетов **RevoScaleR** и **Lattice** в контексте `sqlcc`вычислений. Чтобы получить сведения о нескольких пакетах, передайте строковый вектор, содержащий имена пакетов.

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>Получение версий пакета в удаленном контексте вычислений

Выполните эту команду из консоли R, чтобы получить номер сборки и номера версий для пакетов, установленных в контексте вычислений *sqlServer*.

```R
sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

**Результаты**

```text
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/RevoScaleR"

[2] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/lattice"
```

### <a name="install-a-package-on-sql-server"></a>Установка пакета в SQL Server

В этом примере пакет **прогноза** и его зависимости устанавливаются в контекст вычислений.

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>Удаление пакета из SQL Server

В этом примере удаляется пакет **прогноза** и его зависимости из контекста вычислений.

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>Синхронизация пакетов между базой данных и файловой системой

Следующий пример проверяет базу данных **TestDB**и определяет, установлены ли все пакеты в файловой системе. Если некоторые пакеты отсутствуют, они устанавливаются в файловой системе.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

Синхронизация пакетов выполняется для каждой базы данных и для каждого пользователя. Дополнительные сведения см. в статье [Синхронизация пакетов R для SQL Server](../r/package-install-uninstall-and-sync.md).

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>Использование хранимой процедуры для перечисления пакетов в SQL Server

Выполните эту команду из Management Studio или другого средства, поддерживающего T-SQL, чтобы получить список установленных пакетов в текущем экземпляре, используя `rxInstalledPackages` хранимую процедуру.

```sql
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

`rxSqlLibPaths` Функцию можно использовать для определения активной библиотеки, используемой SQL Server службы машинного обучения. Этот скрипт может возвращать только путь к библиотеке для текущего сервера. 

```sql
declare @instance_name nvarchar(100) = @@SERVERNAME, @database_name nvarchar(128) = db_name();
exec sp_execute_external_script 
  @language = N'R',
  @script = N'
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    .libPaths(rxSqlLibPaths(connStr));
    print(.libPaths());
  ', 
  @input_data_1 = N'', 
  @params = N'@instance_name nvarchar(100), @database_name nvarchar(128)',
  @instance_name = @instance_name, 
  @database_name = @database_name;
```

## <a name="see-also"></a>См. также

+ [Включение удаленного управления пакетами R](r-package-how-to-enable-or-disable.md)
+ [Синхронизация пакетов R](package-install-uninstall-and-sync.md)
+ [Советы по установке пакетов R](packages-installed-in-user-libraries.md)
+ [Пакеты по умолчанию](../package-management/default-packages.md)