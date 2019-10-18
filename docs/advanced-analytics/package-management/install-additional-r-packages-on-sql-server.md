---
title: Установка новых пакетов R с помощью склмлутилс
description: Узнайте, как использовать склмлутилс для установки новых пакетов R на экземпляр SQL Server Службы машинного обучения или SQL Server R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f8ce5c7bcf12a2431c2de779912d2e309c628cb1
ms.sourcegitcommit: 8cb26b7dd40280a7403d46ee59a4e57be55ab462
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542140"
---
# <a name="install-new-r-packages-with-sqlmlutils"></a>Установка новых пакетов R с помощью склмлутилс

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описывается, как использовать функции в пакете [**склмлутилс**](https://github.com/Microsoft/sqlmlutils) для установки новых пакетов R в экземпляр SQL Server Службы машинного обучения или SQL Server R Services. Устанавливаемые пакеты можно использовать в скриптах R, выполняющихся в базе данных, с помощью инструкции T-SQL [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) .

> [!NOTE]
> Стандартная команда R `install.packages` не рекомендуется для добавления пакетов R в SQL Server. Вместо этого используйте **склмлутилс** , как описано в этой статье.

## <a name="prerequisites"></a>предварительные требования

- Установите [R](https://www.r-project.org) и [RStudio Desktop](https://www.rstudio.com/products/rstudio/download/) на клиентском компьютере, который используется для подключения к SQL Server. Для выполнения скриптов можно использовать любую интегрированную среду разработки R, но в этой статье предполагается RStudio.

- Установите [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) или [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) на клиентском компьютере, который используется для подключения к SQL Server. Можно использовать другие средства управления базами данных или запросов, но в этой статье предполагается Azure Data Studio или SSMS.

### <a name="other-considerations"></a>Другие рекомендации

- Скрипт R, выполняющийся в SQL Server, может использовать только пакеты, установленные в библиотеке экземпляров по умолчанию. SQL Server не может загружать пакеты из внешних библиотек, даже если эта библиотека находится на одном компьютере. Сюда входят библиотеки R, установленные с другими продуктами Майкрософт.

- В защищенной SQL Server среде может возникнуть необходимость избежать следующих проблем:
  - Пакеты, которым требуется доступ к сети
  - Пакеты, для которых требуется повышенный доступ к файловой системе
  - Пакеты, используемые для разработки веб-приложений или других задач, не выигрывающие от использования в SQL Server

## <a name="install-sqlmlutils-on-the-client-computer"></a>Установка склмлутилс на клиентском компьютере

Чтобы использовать **склмлутилс**, необходимо сначала установить его на клиентском компьютере, который используется для подключения к SQL Server.

Пакет **склмлутилс** зависит от пакета **Родбцекст** , а **родбцекст** зависит от ряда других пакетов. Следующие процедуры устанавливают все эти пакеты в правильном порядке.

### <a name="install-sqlmlutils-online"></a>Установка склмлутилс Online

Если клиентский компьютер имеет доступ к Интернету, вы можете скачать и установить **склмлутилс** и зависимые пакеты в сети.

1. Скачайте последний ZIP-файл **склмлутилс** с https://github.com/Microsoft/sqlmlutils/tree/master/R/dist на клиентский компьютер. Не Распакуйте файл.

1. Откройте **командную строку** и выполните следующие команды, чтобы установить пакеты **склмлутилс** и **родбцекст**. Замените полный путь к скачанному ZIP-файлу **склмлутилс** (в этом примере предполагается, что файл находится в папке "документы"). Пакет **родбцекст** находится в сети и установлен.

   ```console
   R -e "install.packages('RODBCext', repos='https://cran.microsoft.com')"
   R CMD INSTALL %UserProfile%\Documents\sqlmlutils_0.7.1.zip
   ```

### <a name="install-sqlmlutils-offline"></a>Установка склмлутилс в автономном режиме

Если у клиентского компьютера нет подключения к Интернету, необходимо загрузить пакеты **склмлутилс** и **родбцекст** заранее с помощью компьютера, имеющего доступ к Интернету. Затем можно скопировать файлы в папку на клиентском компьютере и установить пакеты в автономном режиме.

Пакет **родбцекст** содержит ряд зависимых пакетов, и определение всех зависимостей для пакета становится сложным. Рекомендуется использовать [**miniCRAN**](https://andrie.github.io/miniCRAN/) для создания локальной папки репозитория для пакета, включающего все зависимые пакеты.
Дополнительные сведения см. [в статье Создание локального репозитория пакетов R с помощью miniCRAN](create-a-local-package-repository-using-minicran.md).

Пакет **склмлутилс** состоит из одного ZIP-файла, который можно скопировать на клиентский компьютер и установить.

На компьютере с доступом к Интернету:

1. Установите **miniCRAN**. Дополнительные сведения см. в разделе [Install miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran) .

1. В RStudio выполните следующий скрипт R, чтобы создать локальный репозиторий пакета **родбцекст**. В этом примере репозиторий создается в папке `c:\downloads\rodbcext`.

   ::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/rodbcext"
   pkgs_needed <- "RODBCext"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.5");
   ```

   ::: moniker-end

   ::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/rodbcext"
   pkgs_needed <- "RODBCext"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "source", Rversion = "3.5");
   ```

   ::: moniker-end

   Для `Rversion` значения используйте версию R, установленную на SQL Server. Чтобы проверить установленную версию, используйте следующую команду T-SQL.

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. Скачайте последнюю версию ZIP-файла **склмлутилс** из https://github.com/Microsoft/sqlmlutils/tree/master/R/dist (не извлеките файл). Например, скачайте файл в `c:\downloads\sqlmlutils_0.7.1.zip`.

1. Скопируйте на клиентский компьютер всю папку репозитория **родбцекст** (`c:\downloads\rodbcext`) и ZIP-файл **склмлутилс** (`c:\downloads\sqlmlutils_0.7.1.zip`). Например, скопируйте их в папку, `c:\temp\packages` на клиентском компьютере.

На клиентском компьютере, используемом для подключения к SQL Server, откройте командную строку и выполните следующие команды, чтобы установить **родбцекст** , а затем **склмлутилс**.

```console
R -e "install.packages('RODBCext', repos='c:\temp\packages\rodbcext')"
R CMD INSTALL c:\temp\packages\sqlmlutils_0.7.1.zip
```

## <a name="add-an-r-package-on-sql-server"></a>Добавление пакета R на SQL Server

В следующем примере вы добавите [**связующий**](https://cran.r-project.org/web/packages/glue/) пакет в SQL Server.

### <a name="add-the-package-online"></a>Добавление пакета в режим «в сети»

Если клиентский компьютер, используемый для подключения к SQL Server, имеет доступ к Интернету, можно использовать **склмлутилс** для поиска **связывающего** пакета и всех зависимостей через Интернет, а затем установить пакет на экземпляр SQL Server удаленно.

1. На клиентском компьютере откройте RStudio и создайте новый файл **скрипта R** .

1. Используйте следующий скрипт R для установки **связывающего** пакета с помощью **склмлутилс**. Замените сведения о подключении к базе данных SQL Server (если не используется проверка подлинности Windows, добавьте параметры `uid` и `pwd`).

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server= "yourserver",
     database = "yourdatabase")

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC")
   ```

   > [!TIP]
   > **Область** может быть либо **открытой** , либо **закрытой**. Общедоступная область полезна администратору базы данных для установки пакетов, которые могут использовать все пользователи. Частная область делает пакет доступным только для пользователя, который его устанавливает. Если область не указана, областью по умолчанию является **Private**.

### <a name="add-the-package-offline"></a>Добавление пакета в автономный режим

Если у клиентского компьютера нет подключения к Интернету, можно использовать **miniCRAN** для загрузки **связывающего** пакета с помощью компьютера, имеющего доступ к Интернету. Затем пакет копируется на клиентский компьютер, на котором можно установить пакет в автономном режиме.
Сведения об установке **miniCRAN**см. в разделе [Install miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran) .

На компьютере с доступом к Интернету:

1. Выполните следующий скрипт R, чтобы создать локальный репозиторий для **приклеить**. В этом примере создается папка репозитория в `c:\downloads\glue`.

   ::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/glue"
   pkgs_needed <- "glue"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.5");
   ```

   ::: moniker-end

   ::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/glue"
   pkgs_needed <- "glue"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "source", Rversion = "3.5");
   ```

   ::: moniker-end


   Для `Rversion` значения используйте версию R, установленную на SQL Server. Чтобы проверить установленную версию, используйте следующую команду T-SQL.

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. Скопируйте всю папку **связующего** репозитория (`c:\downloads\glue`) на клиентский компьютер. Например, скопируйте его в папку `c:\temp\packages\glue`.

На клиентском компьютере:

1. Откройте RStudio и создайте новый файл **скрипта R** .

1. Используйте следующий скрипт R для установки **связывающего** пакета с помощью **склмлутилс**. Замените сведения о подключении к базе данных SQL Server (если не используется проверка подлинности Windows, добавьте параметры `uid` и `pwd`).

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server= "yourserver",
     database = "yourdatabase")
   localRepo = "c:/temp/packages/glue"

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC", repos=paste0("file:///",localRepo))
   ```

   > [!TIP]
   > **Область** может быть либо **открытой** , либо **закрытой**. Общедоступная область полезна администратору базы данных для установки пакетов, которые могут использовать все пользователи. Частная область делает пакет доступным только для пользователя, который его устанавливает. Если область не указана, областью по умолчанию является **Private**.

## <a name="use-the-package"></a>Использование пакета

После установки **связывающего** пакета его можно использовать в скрипте R SQL Server с помощью команды T-SQL **sp_execute_external_script** .

1. Откройте Azure Data Studio или SSMS и подключитесь к базе данных SQL Server.

1. Выполните следующую команду:

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
       , @script = N'
   library(glue)

   name <- "Fred"
   birthday <- as.Date("2020-06-14")
   text <- glue(''My name is {name} '',
   ''and my birthday is {format(birthday, "%A, %B %d, %Y")}.'')

   print(text)
         ';
   ```

    **Результаты**

    ```text
    My name is Fred and my birthday is Sunday, June 14, 2020.
    ```

## <a name="remove-the-package"></a>Удаление пакета

Если вы хотите удалить **связывающий** пакет, выполните следующий скрипт R. Используйте ту же переменную **подключения** , которая была определена ранее.

```R
sql_remove.packages(connectionString = connection, pkgs = "glue", scope = "PUBLIC")
```

## <a name="next-steps"></a>Следующие шаги

- Сведения об установленных пакетах R см. в разделе [Получение сведений о пакете r](r-package-information.md) .
- Справку по работе с пакетами R см. в статье [Советы по использованию пакетов r](tips-for-using-r-packages.md) .
- Дополнительные сведения об установке пакетов Python см. [в разделе Установка пакетов Python с PIP](install-additional-python-packages-on-sql-server.md) .
- Дополнительные сведения о SQL Server Службы машинного обучения см. в статье [что такое SQL Server службы машинного обучения (Python и R)?](../what-is-sql-server-machine-learning.md)
