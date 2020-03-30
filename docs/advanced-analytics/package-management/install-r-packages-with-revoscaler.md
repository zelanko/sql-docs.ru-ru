---
title: Установка пакетов R с помощью RevoScaleR
description: Узнайте, как использовать функции RevoScaleR для установки пакетов R в SQL Server со Службами машинного обучения или R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/20/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: =sql-server-2016||=sql-server-2017||=sqlallproducts-allversions
ms.openlocfilehash: 1d5d832d41f6bd087c6e9b334ebeac03728f97b1
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "74485289"
---
# <a name="use-revoscaler-to-install-r-packages"></a>Установка пакетов R с помощью RevoScaleR

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описывается, как использовать функции [RevoScaleR](../r/ref-r-revoscaler.md) (версии 9.0.1 и выше) для установки пакетов R в SQL Server со Службами машинного обучения или R Services. Удаленные пользователи без прав администратора могут использовать функции RevoScaleR, чтобы установить пакеты в SQL Server без прямого доступа к серверу.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
> [!NOTE]
> Клиенты SQL Server R Services должны выполнить [обновление компонентов](../install/upgrade-r-and-python.md) для получения функций управления пакетами RevoScaleR. Инструкции по получению версии и содержимого пакета см. в [этой статье](../package-management/r-package-information.md).
::: moniker-end

## <a name="revoscaler-functions-for-package-management"></a>Функции RevoScaleR для управления пакетами

В следующей таблице приведены функции, используемые для установки пакетов R и управления ими.

| Компонент | Description |
|----------|-------------|
| [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | Определяет путь к библиотеке экземпляров на удаленном SQL Server. |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage); | Получает путь для одного или нескольких пакетов на удаленном SQL Server. |
| [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | Вызывайте эту функцию из удаленного клиента R для установки пакетов в контексте вычислений SQL Server из указанного репозитория или посредством считывания сжатых пакетов, сохраненных локально. Эта функция проверяет зависимости, чтобы убедиться, что в SQL Server можно установить все связанные пакеты, как и при установке пакета R в локальном контексте. Чтобы использовать этот параметр, необходимо включить управление пакетами на сервере и в базе данных. Клиентская и серверная среды должны иметь одинаковую версию RevoScaleR. |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages). | Получает список пакетов, установленных в указанном контексте вычислений. |
| [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | Копирует сведения о библиотеке пакетов между файловой системой и базой данных для указанного контекста вычислений. |
| [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | Удаляет пакеты из указанного контекста вычислений. Функция также вычисляет зависимости и гарантирует удаление пакетов, которые больше не используются другими пакетами в SQL Server, для освобождения ресурсов. |

## <a name="prerequisites"></a>предварительные требования

+ Удаленное управление на SQL Server включено. Дополнительные сведения см. в статье [Enable or disable remote package management for SQL Server](r-package-how-to-enable-or-disable.md) (Включение и выключение удаленного управления пакетами на SQL Server).

+ Клиентская и серверная среды должны иметь одинаковую версию RevoScaleR. Дополнительные сведения см. в статье [Получение сведений о пакете R](../package-management/r-package-information.md).

+ У вас есть разрешение на подключение к серверу и базе данных, а также на выполнение команд R. Необходимо быть членом роли базы данных, которая позволяет устанавливать пакеты на заданном экземпляре и базе данных.

  + Пакеты в **общей области** могут быть установлены пользователями с ролью `rpkgs-shared` в указанной базе данных. Все пользователи этой роли могут удалять общие пакеты.

  + Пакеты в **закрытой области** могут быть установлены любым пользователем с ролью `rpkgs-private` в базе данных. Тем не менее пользователи могут просматривать и удалять только свои собственные пакеты.

  + Владельцы базы данных могут работать с общими или закрытыми пакетами.

## <a name="client-connections"></a>Клиентские подключения

Поддерживается клиентская рабочая станция [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows) или [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (специалисты по обработке и анализу данных часто используют бесплатный выпуск Developer) в той же сети.

При вызове функций управления пакетами из удаленного клиента R необходимо сначала создать объект контекста вычислений, используя функцию [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver). Затем для каждой используемой функции управления пакетами передайте контекст вычислений в качестве аргумента.

При установке контекста вычислений обычно указывается удостоверение пользователя. Если при создании контекста вычислений не указать имя пользователя и пароль, будет использоваться удостоверение пользователя, запускающего код R.

1. В командной строке R определите строку подключения к экземпляру и базе данных.
2. Используйте конструктор [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver), чтобы определить контекст вычислений SQL Server с помощью строки подключения.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Создайте список пакетов, которые необходимо установить, и сохраните его в строковой переменной.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Вызовите [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) и передайте контекст вычислений и строковую переменную, содержащую имена пакетов.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Если требуются зависимые пакеты, они также устанавливаются при условии, что на клиенте доступно подключение к Интернету.
    
    Пакеты устанавливаются с использованием учетных данных пользователя, инициирующего подключение, в его области по умолчанию.

## <a name="call-package-management-functions-in-stored-procedures"></a>Вызов функций управления пакетами в хранимых процедурах

Функции управления пакетами можно выполнять в `sp_execute_external_script`. При выборе этого варианта функция выполняется в контексте безопасности вызывающего хранимую процедуру.

## <a name="examples"></a>Примеры

В этом разделе приводятся примеры использования этих функций из удаленного клиента при подключении к экземпляру SQL Server или базе данных в качестве контекста вычислений.

Для всех примеров необходимо указать строку подключения или контекст вычислений, для которого требуется строка подключения. В этом примере представлен один из способов создания контекста вычислений для SQL Server:

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

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Получение пути пакета в удаленном контексте вычислений SQL Server

Этот пример возвращает путь для пакета **RevoScaleR** в контексте вычислений `sqlcc`.

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**Результаты**

C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/RevoScaleR.

> [!TIP]
> Если вы включили параметр для просмотра выходных данных консоли SQL, вы можете получить сообщения о состоянии от функции, предшествующей оператору `print`. После завершения тестирования кода задайте для параметра `consoleOutput` значение FALSE в конструкторе контекста вычислений, чтобы очистить сообщения.

### <a name="get-locations-for-multiple-packages"></a>Получение расположений для нескольких пакетов

Этот пример возвращает пути для пакетов **RevoScaleR** и **lattice** в контексте вычислений `sqlcc`. Для получения сведений о нескольких пакетах передайте строковый вектор, содержащий имена пакетов.

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>Получение версий пакетов в удаленном контексте вычислений

Запустите эту команду в консоли R, чтобы получить номер сборки и номера версий для пакетов, установленных в контексте вычислений *sqlServer*.

```R
sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

### <a name="install-a-package-on-sql-server"></a>Установка пакета в SQL Server

В этом примере устанавливается пакет **forecast** и его зависимости в контексте вычислений.

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>Удаление пакета из SQL Server

В этом примере удаляется пакет **forecast** и его зависимости из контекста вычислений.

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>Синхронизация пакетов между базой данных и файловой системой

В следующем примере проверяется база данных **TestDB** и определяется, все ли пакеты установлены в файловой системе. Если некоторые пакеты отсутствуют, они устанавливаются в файловой системе.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

Синхронизация пакетов выполняется для каждой базы данных и для каждого пользователя. Дополнительные сведения о синхронизации пакетов R для SQL Server см. в [этой статье](package-install-uninstall-and-sync.md).

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>Использование хранимой процедуры для перечисления пакетов в SQL Server

Используя `rxInstalledPackages` в хранимой процедуре, выполните эту команду из Management Studio или другого средства, поддерживающего T-SQL, чтобы получить список установленных пакетов на текущем экземпляре.

```sql
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

Функцию `rxSqlLibPaths` можно использовать для определения активной библиотеки, которая работает со Службами машинного обучения SQL Server. Этот скрипт может возвращать путь к библиотеке только для текущего сервера. 

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

## <a name="see-also"></a>См. также раздел

+ [Включение удаленного управления пакетами R](r-package-how-to-enable-or-disable.md)
+ [Синхронизация пакетов R](package-install-uninstall-and-sync.md)
+ [Советы по использованию пакетов R](tips-for-using-r-packages.md)
+ [Получение сведений о пакете R](../package-management/r-package-information.md)