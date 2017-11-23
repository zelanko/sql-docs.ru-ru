---
title: "Как использовать функции RevoScaleR для поиска или установить R пакетов на SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: 59f13d7c65818b49025f8578068b348c650e98c2
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Как использовать функции RevoScaleR для поиска или установка пакетов R в SQL Server

Выпуск Microsoft R Server 9.0.1 появились новые функции RevoScaleR, поддерживают работу с установленных пакетов в контексте вычислений SQL Server. Эти новые функции упрощают процесс специалист по анализу данных для запуска кода R в SQL Server без прямой доступ к серверу.

Каждый специалист по анализу данных можно установить закрытые пакеты, которые не видны другим пользователям. Так как пакеты, которые можно задавать в базе данных, и каждый пользователь получит изолированной отдельного пакета в каждой базе данных, проще установить разные версии того же пакета R.

Если вы переносите рабочей базе данных на новый сервер, также можно использовать функции синхронизации пакета считывает список всех пакетов и устанавливать их в базе данных на новом сервере.

В этой статье приведено описание этих функций и примеры использования функции.

## <a name="requirements"></a>Требования

+ Для выполнения этих функций, необходимо иметь разрешение на выполнение команды R в экземпляре.

+ Если не указать имя пользователя и пароль при создании контекста вычислений, используется идентификатор пользователя, выполняющего этот код R.

+ При использовании этих функций с удаленного клиента R, необходимо создать объект контекста вычислений во-первых, с помощью функции RxInSQLServer. После этого для каждой функции управления пакета, которая используется, передайте контекст вычислений в качестве аргумента.

+ Можно запускать с помощью функции управления пакета `sp_execute_external_script`. При этом выполняется функция, используя контекст безопасности вызывающего объекта хранимой процедуры.

## <a name="list-of-package-management-functions"></a>Список функций пакета управления

Для установки и удаления пакетов в контексте указанной вычислений в RevoScaleR, предусмотрены следующие функции пакета управления:

+ [rxInstalledPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstalledpackages): найти сведения о пакеты, установленные в контексте указанной вычислений.

+ [rxInstallPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstallpackages): установки пакетов в контексте вычислений, из указанного хранилища или чтении локально сохраненные ZIP-пакеты.

+ [rxRemovePackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxremovepackages): Удаление установленных пакетов из контекста вычислений.

+ [rxFindPackage](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxfindpackage): получить путь для одного или нескольких пакетов в контексте указанной вычислений.

+ [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages): копирует библиотеку пакета между файловой системы и баз данных в контексте указанной вычислений.

+ [rxSqlLibPaths](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqllibpaths): получить путь поиска для деревьев библиотеки для пакетов во время выполнения в SQL Server.

Эти пакеты включены по умолчанию в 2017 г. SQL Server. Сведения об этих функциях см. в разделе страницы ссылка функции RevoScaleR: (https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)

> [!NOTE]
> Функции R для управления пакетами, доступны, начиная с Microsoft R Server 9.0.1. Если функции не удается найти в RevoScaleR, возможно, необходимо обновление до последней версии. 
## <a name="examples"></a>Примеры

Этот раздел содержит примеры использования функций пакета управления с экземпляром SQL Server или базы данных. 

+ Функции установки пакета проверяют зависимости, чтобы убедиться, что в SQL Server можно установить все связанные пакеты, как и при установке пакета R в локальном контексте.

+ Функция, _удаляет_ пакеты также вычисляет зависимости и гарантирует, что пакеты, которые больше не используются другие пакеты в экземпляре SQL Server удаляются для высвобождения ресурсов.

+ Для поиска пакетов или для добавления пакетов в определенной базе данных можно использовать комбинацию пользователей и область действия:

    + Пакеты в **общая область** можно установить с пользователей, принадлежащих `rpkgs-shared` роли в указанной базе данных. Все пользователи в этой роли можно удалить общие пакеты.
    + Пакеты в **закрытая область** можно установить любой пользователь, принадлежащий `rpkgs-private` роли в базе данных. Тем не менее пользователи могли просматривать и удалять только свои собственные пакеты.
    + Владельцы базы данных можно работать с пакетами совместно используемой или закрытой.

**Из кода R**

Если имеется разрешение на установку пакетов, выполните одну из пакета управления функции из клиента R и укажите контекст вычислений, где пакеты должны быть добавлены или удалены.  Контекст вычислений может быть локальным компьютером или базой данных в экземпляре SQL Server. Учетные данные определяют, можно ли выполнить операцию на сервере.

**От Transact-SQL**

Для выполнения функций пакета управления из хранимой процедуры, помещать их в вызове `sp_execute_external_script`.

### <a name="get-list-of-packages-in-a-sql-server-compute-context"></a>Получить список пакетов в контексте вычислений SQL Server

В этом примере проверяется для пакетов, которые были установлены на экземпляре `myServer`, в базе данных `TestDB`. Пакет управления, ограничиваются конкретной базы данных и пользователей. Если пользователь не указан, предполагается пользователь, выполняющий вызова контекста вычислений. Дополнительные сведения см. в разделе [Scoping пакетов по ролям](#bkmk_scope).

```R
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;");
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerCompute);
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Получить путь к пакету в удаленном контексте вычислений SQL Server

Этот пример возвращает путь для пакета **RevoScaleR** в контексте вычислений *sqlServer*.

  ```R
  sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerL)
  ```

### <a name="get-locations-for-multiple-packages"></a>Получение расположений для нескольких пакетов

Этот пример возвращает пути для пакетов **RevoScaleR** и **lattice** в контексте вычислений *sqlServer*. Чтобы получить сведения о нескольких пакетов, передайте строку вектор, содержащий имена пакетов.

  ```R
  packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlServer)
  ```


### <a name="get-package-versions-on-a-remote-compute-context"></a>Получение версии пакетов в контексте удаленного вычислений.

Выполните следующую команду из консоли R: получить номер сборки и номера версий для пакетов, установленных в контексте вычислений, *sqlServer*.

  ```R
  sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

### <a name="install-a-package-on-sql-server"></a>Установка пакета в SQL Server

В этом примере устанавливается **прогноз** пакет и его зависимости в контексте вычислений *sqlServer*.

  ```R
  pkgs <- c("ggplot2")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlServer)
  ```

### <a name="remove-a-package-from-sql-server"></a>Удаление пакета из SQL Server

Этот пример удаляет пакет **ggplot2** и его зависимости из контекста вычислений *sqlServer*.

  ```R
  pkgs <- c("ggplot2")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlServer)
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
