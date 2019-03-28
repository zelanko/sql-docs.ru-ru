---
title: Как использовать функции RevoScaleR для поиска или установки пакетов R - служб машинного обучения SQL Server
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7eed38e54b0c4e77af8f7b3ede0af2d98b9c58b2
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510791"
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Как использовать функции RevoScaleR для поиска или установки пакетов R на сервере SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR 9.0.1 и более поздней версии включает функции для управления пакетами R контекста вычислений SQL Server. Эти функции могут использоваться с удаленными, пользователям без прав администратора для установки пакетов на SQL Server, не имеющие прямого доступа к серверу.

Службы машинного обучения SQL Server 2017 уже включает в себя более новая версия RevoScaleR. Клиенты SQL Server 2016 R Services необходимо выполнить [обновления компонента](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md) для получения функций управления пакета RevoScaleR. Инструкции о том, как для получения пакетов, версии и содержимым, см. в разделе [получить сведения о пакете](determine-which-packages-are-installed-on-sql-server.md).

## <a name="revoscaler-functions-for-package-management"></a>Функции RevoScaleR для управления пакетами

Следующая таблица описывает функции, используемые для установки пакетов R и управления.

| Компонент | Описание |
|----------|-------------|
| [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | Определите путь к библиотеке экземпляра на удаленном сервере SQL. |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage); | Получает путь для одного или нескольких пакетов на удаленный экземпляр SQL Server. |
| [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | Вызывайте эту функцию с удаленного клиента R для установки пакетов в контексте вычислений SQL Server, либо из указанного репозитория или посредством считывания сжатых пакетов, локально сохраненных. Эта функция проверяет зависимости и гарантирует, что все связанные пакеты могут быть установлены для SQL Server, как и для установки пакетов R в локальном контексте вычисления. Чтобы использовать этот параметр, необходимо включить управление пакетами на сервере и базе данных. Клиентские и серверные среды должен иметь ту же версию RevoScaleR. |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages). | Возвращает список пакетов, установленных в указанном контексте вычислений. |
| [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | Скопируйте сведения о библиотеке пакета между файловой системой и базы данных, для указанном контексте вычислений. |
| [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | Удаление пакетов в указанном контексте вычислений. Также вычисляет зависимости и гарантирует, что удаляются пакеты, которые больше не используются другими пакетами на сервере SQL Server, чтобы освободить ресурсы. |

## <a name="prerequisites"></a>предварительные требования

+ [Включение удаленного управления пакетами R на сервере SQL Server](r-package-how-to-enable-or-disable.md)

+ RevoScaleR версии должен быть одинаковым на клиентские и серверные среды. Дополнительные сведения см. в разделе [получить сведения о пакете](determine-which-packages-are-installed-on-sql-server.md).

+ Разрешение на подключение к серверу и базе данных и выполнять команды R. Необходимо быть членом роли базы данных, позволяющий установить пакеты на указанном экземпляре и базе данных.

+ Пакеты в **общая область** можно установить с пользователей, принадлежащих к `rpkgs-shared` роли в указанной базе данных. Все пользователи с этой ролью можно удалить общие пакеты.

+ Пакеты в **закрытой области** можно установить любой пользователь, принадлежащий `rpkgs-private` роли в базе данных. Тем не менее пользователи могли просматривать и удалять только свои собственные пакеты.

+ Владельцы базы данных можно работать с пакетами совместно используемой или закрытой.

## <a name="client-connections"></a>Клиентские подключения

На клиентской рабочей станции может быть [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows) или [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (специалисты по анализу данных часто используют бесплатную developer edition) в той же сети.

При вызове функции управления пакетами из удаленного клиента R, сначала необходимо создать объект контекста вычислений, с помощью [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) функции. После этого для каждой функции управления пакета, который можно использовать, передайте контекст вычислений в качестве аргумента.

При задании контекста вычислений обычно указаны учетные данные пользователя. Если вы не укажете имя пользователя и пароль при создании контекста вычислений, используется удостоверение пользователя, запустившего код R.

1. Из командной строки R необходимо определите строку подключения к экземпляру и базе данных.
2. Используйте [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) конструктор, чтобы определить контекст вычислений SQL Server, с помощью строки подключения.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Создайте список из пакетов, которые вы хотите установить и сохранить список в строковой переменной.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Вызовите [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) и передать контекст вычислений и строковая переменная, содержащая имена пакетов.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Если требуются зависимые пакеты, они установлены, при условии, что подключение к Интернету доступен на клиенте.
    
    Пакеты устанавливаются с использованием учетных данных пользователя, выполняющего соединение, в области по умолчанию для этого пользователя.

## <a name="call-package-management-functions-in-stored-procedures"></a>Вызов функции управления пакетами в хранимых процедурах

Камера на выполнение функций пакета управления внутри `sp_execute_external_script`. После этого, выполняется функция, используя контекст безопасности вызывающего объекта хранимой процедуры.

## <a name="examples"></a>Примеры

В этом разделе приведены примеры использования этих функций с удаленного клиента при подключении к экземпляру SQL Server или базу данных в качестве контекста вычисления.

Все примеры необходимо указать строку подключения или контекст вычислений, который требуется строка подключения. В этом примере описывается один из способов создания контекста вычислений для SQL Server:

```R
instance_name <- "computer-name/instance-name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

Зависимости от того, где расположен сервер и модель безопасности может потребоваться предоставить спецификацию домена и подсети, в строке подключения или используйте имя входа SQL. Пример:

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Получить путь к пакету в удаленном контексте вычислений SQL Server

В этом примере извлекаются пути для **RevoScaleR** пакет в контексте вычислений `sqlcc`.

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**Результаты**

«C:/Program файлы или Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/library/RevoScaleR»

> [!TIP]
> Если вы включили параметр, чтобы просмотреть выходные данные консоли SQL, вы можете получать сообщения о состоянии от функции, которая предшествует `print` инструкции. После завершения тестирования кода, задать `consoleOutput` значение FALSE в конструкторе контекста вычислений, чтобы исключить сообщения.

### <a name="get-locations-for-multiple-packages"></a>Получение расположений для нескольких пакетов

Следующий пример возвращает пути для **RevoScaleR** и **lattice** пакетов в контексте вычислений, `sqlcc`. Чтобы получить сведения о нескольких пакетах, передайте строковый вектор, содержащий имена пакетов.

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>Получение версий пакета в контексте удаленных вычислений

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

В этом примере устанавливается **прогноз** пакет и его зависимости в качестве контекста вычисления.

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>Удаление пакета из SQL Server

В этом примере удаляется **прогноз** пакет и его зависимости из контекста вычислений.

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>Синхронизация пакетов между системой базы данных и файла

В следующем примере проверяется базе **TestDB**и определяет, установлены ли все пакеты в файловой системе. Если некоторые пакеты отсутствуют, они устанавливаются в файловой системе.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

Пакет синхронизация работает на отдельных баз данных и на пользователя. Дополнительные сведения см. в разделе [синхронизацию пакета R для SQL Server](../r/package-install-uninstall-and-sync.md).

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>Используйте хранимую процедуру, чтобы вывести список пакетов в SQL Server

Выполните следующую команду из Management Studio или другое средство, которое поддерживает T-SQL, чтобы получить список установленных пакетов в текущем экземпляре, с помощью `rxInstalledPackages` в хранимой процедуре.

```sql
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

`rxSqlLibPaths` Функция может использоваться для определения активных библиотеки, используемой службы машинного обучения SQL Server. Этот сценарий может возвращать только путь к библиотеке для выбранного сервера. 

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
+ [Пакеты по умолчанию](installing-and-managing-r-packages.md)