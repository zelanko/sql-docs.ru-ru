---
title: Как использовать функции RevoScaleR для поиска или установить R пакетов на SQL Server | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d92b3e993968ce48d7489b0c17d6bdba005809a3
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707532"
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Как использовать функции RevoScaleR для поиска или установка пакетов R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR 9.0.1 и более поздние версии включают функции для управления пакетами R контекста вычислений SQL Server. Эти функции могут использоваться с удаленным, не являющимся администраторами для установки пакетов на SQL Server, не имеющие прямого доступа к серверу.

Службы SQL Server 2017 г машины обучения уже есть более новая версия RevoScaleR. Клиенты служб SQL Server 2016 R необходимо выполнить [обновления компонента](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md) для получения функций управления пакета RevoScaleR. Инструкции о способах получения пакета версии и содержимое, см. в разделе [получить сведения о пакете](determine-which-packages-are-installed-on-sql-server.md).

## <a name="revoscaler-functions-for-package-management"></a>Функции RevoScaleR для пакета управления

Ниже перечислены функции, которые используются для установки пакетов R и управления.

| Компонент | Описание |
|----------|-------------|
| [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | Определите путь к библиотеке экземпляра на удаленном сервере SQL. |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage); | Получает путь для одного или нескольких пакетов на удаленный экземпляр SQL Server. |
| [rxInstallPackages](https://docs.microsoft.com/en-us/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | Эта функция вызывается с удаленного клиента R для установки пакетов в контексте вычислений SQL Server, либо из указанного хранилища, либо путем чтения локально сохраненные ZIP-пакеты. Эта функция проверяет зависимости и гарантирует, что все связанные пакеты могут быть установлены для SQL Server, так же, как установка пакетов R в локальном контексте. Чтобы использовать этот параметр, необходимо включить управление пакетами для сервера и базы данных. Клиентские и серверные среды должны иметь одну и ту же версию RevoScaleR. |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages). | Возвращает список пакетов, установленных в контексте указанной вычислений. |
| [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | Скопируйте сведения о библиотеке пакета между файловой системы и базы данных для контекста заданного вычислений. |
| [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | Удаление пакетов из контекста указанной вычислений. Также вычисляет зависимости и гарантирует, что пакеты, которые больше не используются другие пакеты в экземпляре SQL Server удаляются для высвобождения ресурсов. |

## <a name="prerequisites"></a>предварительные требования

+ [Включение удаленного управления пакета R в SQL Server](r-package-how-to-enable-or-disable.md)

+ RevoScaleR версии должен совпадать в клиентских и серверных средах. Дополнительные сведения см. в разделе [получить сведения о пакете](determine-which-packages-are-installed-on-sql-server.md).

+ Разрешения для подключения к серверу и базе данных, а также запуска команды R. Необходимо быть членом роли базы данных, которая позволяет установить пакеты на указанном экземпляре и базе данных.

+ Пакеты в **общая область** можно установить с пользователей, принадлежащих `rpkgs-shared` роли в указанной базе данных. Все пользователи в этой роли можно удалить общие пакеты.

+ Пакеты в **закрытая область** можно установить любой пользователь, принадлежащий `rpkgs-private` роли в базе данных. Тем не менее пользователи могли просматривать и удалять только свои собственные пакеты.

+ Владельцы базы данных можно работать с пакетами совместно используемой или закрытой.

## <a name="client-connections"></a>Клиентские соединения

На клиентской рабочей станции может быть [клиент Microsoft R](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows) или [Microsoft Server обучения машины](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (специалисты по анализу данных часто используют свободного developer edition) в той же сети.

При вызове функций пакета управления с удаленного клиента R, необходимо создать объект контекста вычислений во-первых, с помощью [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) функции. После этого для каждой функции управления пакета, которая используется, передайте контекст вычислений в качестве аргумента.

Удостоверение пользователя обычно указывается при настройке контекст вычислений. Если не указать имя пользователя и пароль при создании контекста вычислений, используется идентификатор пользователя, выполняющего этот код R.

1. Из командной строки R необходимо определите строку соединения для экземпляра и базы данных.
2. Используйте [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) конструктор, чтобы определить контекст вычислений SQL Server с помощью строки подключения.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Создайте список пакетов, который вы хотите установить и сохраните список в строковой переменной.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Вызовите [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) и передать в контексте вычислений и строковая переменная, содержащая имена пакетов.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Если зависимые пакеты не требуются, они также будут установлены, при условии, что подключение к Интернету на клиенте.
    
    Пакеты устанавливаются с использованием учетных данных пользователя, выполняющего соединение, в области по умолчанию для этого пользователя.

## <a name="call-package-management-functions-in-stored-procedures"></a>Вызов функций пакета управления в хранимых процедурах

Камера запуск функций пакета управления внутри `sp_execute_external_script`. При этом выполняется функция, используя контекст безопасности вызывающего объекта хранимой процедуры.

## <a name="examples"></a>Примеры

В этом разделе приведены примеры использования этих функций с удаленного клиента при подключении к экземпляру SQL Server или базы данных в контексте.

Все примеры необходимо указать строку подключения или контекст вычислений, в которой требуется строка подключения. Этот пример показывает один из способов создания контекста вычислений для SQL Server:

```R
instance_name <- "computer-name/instance-name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

В зависимости от того, где расположен сервер и модель безопасности может потребоваться предоставить спецификацию домена и подсети в строке подключения или используйте имя входа SQL. Например:

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Получить путь к пакету в удаленном контексте вычислений SQL Server

В этом примере возвращает путь для **RevoScaleR** пакет в контексте вычислений `sqlcc`.

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**Результаты**

«C:/Program файлы или Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/библиотека/RevoScaleR»

> [!TIP]
> Если включен параметр для просмотра выходных данных консоли SQL может появиться сообщения об изменении состояния из функции, которая предшествует `print` инструкции. После завершения тестирования кода, установите `consoleOutput` значение FALSE в конструкторе контекст вычислений для устранения сообщения.

### <a name="get-locations-for-multiple-packages"></a>Получение расположений для нескольких пакетов

Следующий пример получает пути для **RevoScaleR** и **решетки** пакетов в контексте вычислений, `sqlcc`. Чтобы получить сведения о нескольких пакетов, передайте строку вектор, содержащий имена пакетов.

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>Получение версии пакетов в контексте удаленного вычислений.

Выполните следующую команду из консоли R: получить номер сборки и номера версий для пакетов, установленных в контексте вычислений, *sqlServer*.

```R
sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

**Результаты**

```text
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/RevoScaleR"

[2] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/lattice"
```

### <a name="install-a-package-on-sql-server"></a>Установка пакета в SQL Server

В этом примере устанавливается **прогноз** пакет и его зависимости в контексте вычислений.

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>Удаление пакета из SQL Server

В этом примере удаляется **прогноз** пакет и его зависимости от контекста вычислений.

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>Синхронизация пакетов между системой базы данных и файла

В следующем примере проверяется в базе данных **TestDB**и определяет, установлены ли все пакеты в файловой системе. Если отсутствуют некоторые пакеты, они устанавливаются в файловой системе.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

Синхронизация пакета работает на отдельных баз данных и на пользователя. Дополнительные сведения см. в разделе [синхронизацию пакета R для SQL Server](../r/package-install-uninstall-and-sync.md).

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>Использование хранимой процедуры, чтобы вывести список пакетов в SQL Server

Выполните следующую команду из среды Management Studio или другое средство, которое поддерживает T-SQL, чтобы получить список установленных пакетов в текущем экземпляре, с помощью `rxInstalledPackages` в хранимой процедуре.

```SQL
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

`rxSqlLibPaths` Функцию можно использовать для определения активных библиотека, используемая службами SQL Server машины обучения. Этот скрипт может возвращать только путь к библиотеке для текущего сервера. 

```SQL
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
+ [Советы по установке пакетов r.](packages-installed-in-user-libraries.md)
+ [Пакеты по умолчанию](installing-and-managing-r-packages.md)