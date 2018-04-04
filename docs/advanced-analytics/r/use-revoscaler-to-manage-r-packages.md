---
title: Как использовать функции RevoScaleR для поиска или установить R пакетов на SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 02/20/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.openlocfilehash: 65bfbe18ddc6a39bb1d27bf4babab1d4dd3cf0de
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Как использовать функции RevoScaleR для поиска или установка пакетов R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Выпуск Microsoft R Server 9.0.1 появились новые функции RevoScaleR, поддерживают работу с установленных пакетов в контексте вычислений SQL Server. Эти новые функции упрощают процесс специалист по анализу данных для выполнения кода R и установки пакетов на SQL Server, не имеющие прямого доступа к серверу.

## <a name="how-does-it-work"></a>Как это работает

Если у вас есть R Server 9.0.1 или более поздней версии, можно использовать [rxInstallPackages](https://docs.microsoft.com/en-us/machine-learning-server/r-reference/revoscaler/rxinstallpackages) функция с удаленного клиента R для установки пакетов в контексте вычислений SQL Server. Чтобы использовать этот параметр, необходимо включить управление пакетами для сервера и базы данных. Этот компонент также требует наличия эквивалентной версией служб R или Machine Learning Services на сервере.

Новая версия RevoScaleR также включает следующие функции: 

+ [RxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) функция возвращает путь для одного или нескольких пакетов в контексте указанной вычислений.

    Для поиска пакетов или для добавления пакетов в определенной базе данных можно использовать комбинацию пользователей и область действия:

+ [RxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) функция возвращает список пакетов, установленных в контексте указанной вычислений.

+ [RxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) функция устанавливает пакеты в контекст вычислений, либо из указанного хранилища, либо путем чтения локально сохраненные пакеты ZIP-архиве.

    Эта функция проверяет зависимости и гарантирует, что все связанные пакеты могут быть установлены для SQL Server, так же, как установка пакетов R в локальном контексте.

+ [RxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) функция удаляет пакеты из контекста указанной вычислений.

    Также вычисляет зависимости и гарантирует, что пакеты, которые больше не используются другие пакеты в экземпляре SQL Server удаляются для высвобождения ресурсов.

+ Используйте [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) функции для копирования сведений о библиотеке пакета между файловой системы и базы данных для контекста заданного вычислений.

+ Используйте [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) контекста вычислений функцию, чтобы определить путь к библиотеке экземпляра на SQL Server.

**Применяется к:** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]. Также поддерживается в [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] при обновлении R Server 9.0 или более поздней версии. Другие ограничения.

## <a name="requirements"></a>Требования

+ Чтобы выполнить эти функции, необходимо иметь разрешения для подключения к серверу и базе данных, а также запуска команды R.

+ При использовании этих функций с удаленного клиента R, необходимо создать объект контекста вычислений во-первых, с помощью [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) функции. После этого для каждой функции управления пакета, которая используется, передайте контекст вычислений в качестве аргумента.

+ Если не указать имя пользователя и пароль при создании контекста вычислений, используется идентификатор пользователя, выполняющего этот код R.

+ Можно также для выполнения функций пакета управления внутри `sp_execute_external_script`. При этом выполняется функция, используя контекст безопасности вызывающего объекта хранимой процедуры.

+ Пакеты в **общая область** можно установить с пользователей, принадлежащих `rpkgs-shared` роли в указанной базе данных. Все пользователи в этой роли можно удалить общие пакеты.

+ Пакеты в **закрытая область** можно установить любой пользователь, принадлежащий `rpkgs-private` роли в базе данных. Тем не менее пользователи могли просматривать и удалять только свои собственные пакеты.

+ Владельцы базы данных можно работать с пакетами совместно используемой или закрытой.

## <a name="package-installation-from-machine-learning-server-or-remote-r-client"></a>Установка пакета с машины обучения сервера или удаленного клиента R

Прежде чем начать, убедитесь, что выполняются следующие условия:

+ У вашего клиента есть RevoScale 9.0.1 или более поздней версии.
+ Эквивалентной версией RevoScaleR установлен на экземпляре SQL Server.
+ [Функции пакета управления](..\r\r-package-how-to-enable-or-disable.md) включена на экземпляре.
+ Вы являетесь членом роли базы данных, которая позволяет установить пакеты на указанном экземпляре и базе данных. В будущем роли будут поддерживать пакеты установки, либо расположение совместно используемой или закрытой. Теперь можно установить пакеты, если вы являетесь владельцем базы данных.

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

## <a name="examples"></a>Примеры

В этом разделе приведены примеры использования этих функций с удаленного клиента при подключении к экземпляру SQL Server или базы данных в контексте.

Все примеры необходимо указать строку подключения или контекст вычислений, в которой требуется строка подключения. Этот пример показывает один из способов создания контекста вычислений для SQL Server:

```R
instance_name <- "Machine name/Instance name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

В зависимости от того, где расположен сервер и модель безопасности может потребоваться предоставить спецификацию домена и подсети в строке подключения или используйте имя входа SQL. Например:

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"


### Get package path on a remote SQL Server compute context

This example gets the path for the **RevoScaleR** package on the compute context, `sqlcc`.

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
