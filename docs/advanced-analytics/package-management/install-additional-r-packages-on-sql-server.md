---
title: Установка новых пакетов R
description: Сведения об использовании пакета sqlmlutils для установки новых пакетов R в экземпляре служб машинного обучения SQL Server или служб SQL Server R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/20/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ff2d40dab5fa2d8f03bf3d1fa32b08e66a0ccdbc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "79027939"
---
# <a name="install-new-r-packages-with-sqlmlutils"></a>Установка новых пакетов R с помощью sqlmlutils

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описывается использование функций в пакете [**sqlmlutils**](https://github.com/Microsoft/sqlmlutils) для установки новых пакетов R в экземпляре служб машинного обучения SQL Server или служб SQL Server R Services. Устанавливаемые пакеты можно использовать в сценариях R, выполняющихся в базе данных, с помощью инструкции T-SQL [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

> [!NOTE]
> Для добавления пакетов R в SQL Server не рекомендуется выполнять стандартную команду R `install.packages`. Вместо нее используйте **sqlmlutils**, как описано в этой статье.

## <a name="prerequisites"></a>предварительные требования

- Установите [R](https://www.r-project.org) и [RStudio Desktop](https://www.rstudio.com/products/rstudio/download/) на клиентском компьютере, который используется для подключения к SQL Server. Для выполнения сценариев можно использовать любую интегрированную среду разработки R, но в этой статье применяется RStudio.

- Установите [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) или [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) на клиентском компьютере, который используется для подключения к SQL Server. Можно использовать другие средства управления базами данных или инструменты работы с запросами, но в этой статье применяются Azure Data Studio или SSMS.

### <a name="other-considerations"></a>Другие замечания

- Сценарий R, выполняющийся в SQL Server, может использовать только пакеты, установленные в библиотеке экземпляра по умолчанию. SQL Server не может загружать пакеты из внешних библиотек, даже если эти библиотеки находятся на том же компьютере. В их число входят библиотеки R, установленные с другими продуктами Майкрософт.

- В защищенной среде SQL Server может потребоваться отказаться от следующих пакетов:
  - пакеты, которым требуется доступ к сети;
  - пакеты, которым требуется доступ к файловой системе с повышенными правами;
  - пакеты, используемые для веб-разработки или других задач, малоэффективных в SQL Server.

## <a name="install-sqlmlutils-on-the-client-computer"></a>Установка пакета sqlmlutils на клиентском компьютере

Сначала пакет **sqlmlutils** необходимо установить на клиентском компьютере, который используется для подключения к SQL Server.

Пакет **sqlmlutils** зависит от пакета **RODBCext**, а **RODBCext** — от ряда других пакетов. Следующие процедуры позволяют установить все эти пакеты в правильном порядке.

### <a name="install-sqlmlutils-online"></a>Установка пакета sqlmlutils в сетевом режиме

Если у клиентского компьютера есть доступ к Интернету, вы можете скачать и установить пакет **sqlmlutils** и его зависимые пакеты по сети.

1. Скачайте последнюю версию ZIP-файла **sqlmlutils** со страницы https://github.com/Microsoft/sqlmlutils/tree/master/R/dist на клиентский компьютер. Не распаковывайте файл.

1. Откройте **командную строку** и выполните следующие команды для установки пакетов **sqlmlutils** и **RODBCext**. Замените полный путь к скачанному ZIP-файлу **sqlmlutils** (в этом примере предполагается, что файл находится в папке Documents). Пакет **RODBCext** находится в сети и установлен.

   ```console
   R -e "install.packages('RODBCext', repos='https://cran.microsoft.com')"
   R CMD INSTALL %UserProfile%\Documents\sqlmlutils_0.7.1.zip
   ```

### <a name="install-sqlmlutils-offline"></a>Установка пакета sqlmlutils в автономном режиме

Если у клиентского компьютера нет подключения к Интернету, необходимо заранее скачать пакеты **sqlmlutils** и **RODBCext** на компьютере с доступом к Интернету. Затем файлы можно скопировать в папку на клиентском компьютере и установить пакеты в автономном режиме.

У пакета **RODBCext** есть несколько зависимых пакетов, но при определении всех зависимостей для пакета возникают сложности. Рекомендуется воспользоваться [**miniCRAN**](https://andrie.github.io/miniCRAN/) и создать папку локального репозитория для пакета, включающего все зависимые пакеты.
Дополнительные сведения см. в статье [Create a local R package repository using miniCRAN](create-a-local-package-repository-using-minicran.md) (Создание локального репозитория пакетов R с помощью miniCRAN).

Пакет **sqlmlutils** состоит из одного ZIP-файла, который можно скопировать на клиентский компьютер и установить.

На компьютере с доступом к Интернету

1. Установите **miniCRAN**. Дополнительные сведения см. в разделе об [установке miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran).

1. В RStudio выполните следующий сценарий R, чтобы создать локальный репозиторий пакета **RODBCext**. В этом примере репозиторий создается в папке `c:\downloads\rodbcext`.

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

   В качестве значения `Rversion` укажите версию R, установленную в SQL Server. Чтобы проверить установленную версию, используйте следующую команду T-SQL.

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. Скачайте последнюю версию ZIP-файла **sqlmlutils** со страницы [https://github.com/Microsoft/sqlmlutils/tree/master/R/dist](https://github.com/Microsoft/sqlmlutils/tree/master/R/dist) (не распаковывайте файл архива). Например, скачайте файл в папку `c:\downloads\sqlmlutils_0.7.1.zip`.

1. Скопируйте всю папку репозитория **RODBCext** (`c:\downloads\rodbcext`) и ZIP-файл **sqlmlutils** (`c:\downloads\sqlmlutils_0.7.1.zip`) на клиентский компьютер. Например, скопируйте их в папку `c:\temp\packages` на клиентском компьютере.

На клиентском компьютере, используемом для подключения к SQL Server, откройте командную строку и выполните следующие команды для установки **RODBCext** и **RODBCext**.

```console
R -e "install.packages('RODBCext', repos='c:\temp\packages\rodbcext')"
R CMD INSTALL c:\temp\packages\sqlmlutils_0.7.1.zip
```

## <a name="add-an-r-package-on-sql-server"></a>Добавление пакета R в SQL Server

В следующем примере вы добавите пакет [**glue**](https://cran.r-project.org/web/packages/glue/) в SQL Server.

### <a name="add-the-package-online"></a>Добавление пакета в сетевом режиме

Если клиентский компьютер, используемый для подключения к SQL Server, имеет доступ к Интернету, с помощью пакета **sqlmlutils** можно найти пакет **glue** и все зависимости через Интернет, а затем удаленно установить пакет в экземпляре SQL Server.

1. На клиентском компьютере откройте RStudio и создайте файл **сценария R**.

1. Выполните следующий сценарий R для установки пакета **glue** с помощью пакета **sqlmlutils**. Подставьте собственные значения для подключения к базе данных SQL Server.

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server   = "server",
     database = "database",
     uid      = "username",
     pwd      = "password")

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC")
   ```

   > [!TIP]
   > Параметр **scope** может иметь значение **PUBLIC** или **PRIVATE**. Общая область полезна администратору базы данных для установки пакетов, которые могут использовать все пользователи. В личной области пакет доступен только устанавливающему его пользователю. Если область не указана, по умолчанию используется область **PRIVATE**.

### <a name="add-the-package-offline"></a>Добавление пакета в автономном режиме

Если у клиентского компьютера нет подключения к Интернету, воспользуйтесь **miniCRAN**, чтобы скачать пакет **glue** на компьютере, имеющем доступ к Интернету. Затем пакет копируется на клиентский компьютер для установки в автономном режиме.
Сведения об установке [miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran) см. в разделе **Установка miniCRAN**.

На компьютере с доступом к Интернету

1. Выполните следующий сценарий R для создания локального репозитория для пакета **glue**. В этом примере папка репозитория создается в папке `c:\downloads\glue`.

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


   В качестве значения `Rversion` укажите версию R, установленную в SQL Server. Чтобы проверить установленную версию, используйте следующую команду T-SQL.

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. Скопируйте всю папку репозитория **glue** (`c:\downloads\glue`) на клиентский компьютер. Например, скопируйте ее в папку `c:\temp\packages\glue`.

На клиентском компьютере

1. Откройте RStudio и создайте файл **сценария R**.

1. Выполните следующий сценарий R для установки пакета **glue** с помощью пакета **sqlmlutils**. Замените сведения о подключении к базе данных SQL Server (если не используется проверка подлинности Windows, добавьте параметры `uid` и `pwd`).

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server= "yourserver",
     database = "yourdatabase")
   localRepo = "c:/temp/packages/glue"

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC", repos=paste0("file:///",localRepo))
   ```

   > [!TIP]
   > Параметр **scope** может иметь значение **PUBLIC** или **PRIVATE**. Общая область полезна администратору базы данных для установки пакетов, которые могут использовать все пользователи. В личной области пакет доступен только устанавливающему его пользователю. Если область не указана, по умолчанию используется область **PRIVATE**.

## <a name="use-the-package"></a>Использование пакета

После установки пакет **glue** можно использовать в сценарии R в SQL Server с командой T-SQL **sp_execute_external_script**.

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

Чтобы удалить пакет **glue**, выполните следующий сценарий R. Используйте ту же переменную **connection**, которая была определена ранее.

```R
sql_remove.packages(connectionString = connection, pkgs = "glue", scope = "PUBLIC")
```

## <a name="next-steps"></a>Дальнейшие действия

- Сведения об установленных пакетах R см. в статье [Get R package information](r-package-information.md) (Получение сведений о пакете R).
- Сведения о работе с пакетами R см. в статье [Tips for using R packages](tips-for-using-r-packages.md) (Советы по использованию пакетов R).
- Сведения об установке пакетов Python см. в статье [Install Python packages with pip](install-additional-python-packages-on-sql-server.md) (Установка пакетов Python с помощью pip).
- Дополнительные сведения о службах машинного обучения SQL Server см. в статье [What is SQL Server Machine Learning Services (Python и R)?](../what-is-sql-server-machine-learning.md) (Что такое службы машинного обучения SQL Server (Python и R)?)
