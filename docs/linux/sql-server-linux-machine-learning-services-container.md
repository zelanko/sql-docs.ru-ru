---
title: Запуск контейнера со Службами машинного обучения SQL Server | Документация Майкрософт
description: В этом руководстве приводятся инструкции по работе с контейнером Linux со Службами машинного обучения SQL Server, запущенном в Docker.
author: uc-msft
ms.author: umajay
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.collection: linux-container
moniker: '>= sql-server-linux-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: f3d3774adf4bee07269b25c3359b031ca24eb99e
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68300424"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>Запуск контейнера со Службами машинного обучения SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом руководстве показано, как создать контейнер Docker со Службами машинного обучения SQL Server и выполнить сценарии машинного обучения из Transact-SQL.

> [!div class="checklist"]
> * Клонирование репозитория mssql-docker.
> * Создание образа контейнера SQL Server Linux со Службами машинного обучения.
> * Запуск образа контейнера SQL Server Linux со Службами машинного обучения.
> * Выполнение сценариев R или Python с помощью инструкций Transact-SQL.
> * Остановка и удаление контейнера SQL Server Linux. 

## <a name="prerequisites"></a>предварительные требования

* Интерфейс командной строки Git.
* Docker Engine 1.8+ на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).
* Не менее 2 ГБ места на диске.
* Не менее 2 ГБ ОЗУ.
* [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

## <a name="clone-the-mssql-docker-repository"></a>Клонирование репозитория mssql-docker

1. Откройте терминал bash в ОС Linux или Mac либо терминал WSL в ОС Windows.

1. Создайте локальный каталог для локального хранения копии репозитория mssql-docker.
1. Выполните команду git clone, чтобы клонировать репозиторий mssql-docker.

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-sql-server-linux-container-image-with-machine-learning-services"></a>Создание образа контейнера SQL Server Linux со Службами машинного обучения

1. Измените каталог на mssql-mlservices.

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Выполните сценарий build.sh.

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Для создания образа docker требуется установить пакеты размером несколько ГБ. В зависимости от пропускной способности сети выполнение сценария может занять до 20 минут.

## <a name="run-sql-server-linux-container-image-with-machine-learning-services"></a>Запуск образа контейнера SQL Server Linux со Службами машинного обучения

1. Перед запуском контейнера задайте переменные среды. В качестве значения переменной среды PATH_TO_MSSQL задайте каталог узла.

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

1. Выполните сценарий run.sh.

   ```bash
   ./run.sh
   ```

   Эта команда создаст контейнер SQL Server со Службами машинного обучения в выпуске Developer Edition (по умолчанию). Порт SQL Server **1433** доступен на узле как порт **1401**.

   > [!NOTE]
   > Процесс запуска контейнера с рабочими выпусками SQL Server немного отличается. Дополнительные сведения см. в статье [Настройка образов контейнеров SQL Server в Docker](sql-server-linux-configure-docker.md). Если вы используете те же имена и порты контейнеров, действия в оставшейся части этого руководства будут актуальны и для рабочих контейнеров.

1. Для просмотра ваших контейнеров Docker используйте команду `docker ps`.

   ```bash
   sudo docker ps -a
   ```

1. Если в столбце **STATUS** (состояние) отображается состояние **Up** (запущен), то SQL Server выполняется в контейнере и прослушивает порт, указанный в столбце **PORTS** (порты). Если в столбце **STATUS** контейнера с SQL Server отображается **Exited** (завершен), см.руководство [Устранение неполадок конфигурации](sql-server-linux-configure-docker.md#troubleshooting).

   ```bash
   $ sudo docker ps -a
   ```

    Выходные данные: 
    
    ```
    CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
    941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour     0.0.0.0:1401->1433/tcp   sql1
    ```

## <a name="change-the-sa-password"></a>Смена пароля администратора

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="execute-r--python-scripts-from-transact-sql"></a>Выполнение сценариев R или Python из Transact-SQL

1. Подключитесь к SQL Server в контейнере и включите параметр конфигурации внешнего сценария, выполнив следующую инструкцию T-SQL.

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. Убедитесь, что Службы машинного обучения работают, выполнив следующий простой сценарий sp_execute_external_script на R или Python.

    ```sql
    execute sp_execute_external_script 
    @language = N'R',
    @script = N'
    print("Hello World!")
    print(R.version)
    print(Revo.version)
    OutputDataSet <- InputDataSet', 
    @input_data_1 = N'select 1'
    with result sets((i int));
    go
    ```

    ```sql
    execute sp_execute_external_script 
    @language = N'Python',
    @script = N'
    import sys
    print(sys.version)
    print("Hello World!")
    OutputDataSet = InputDataSet',
    @input_data_1 = N'select 1'
    with result sets((i int));
    go 
    ```

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как выполнять следующие задачи.

> [!div class="checklist"]
> * Клонирование репозитория mssql-docker.
> * Создание образа контейнера SQL Server Linux со Службами машинного обучения.
> * Запуск образа контейнера SQL Server Linux со Службами машинного обучения.
> * Выполнение сценариев R или Python с помощью инструкций Transact-SQL.
> * Остановка и удаление контейнера SQL Server Linux.

Затем ознакомьтесь с другими сценариями настройки и устранения неполадок Docker:

> [!div class="nextstepaction"]
>[Настройка SQL Server в Docker](sql-server-linux-configure-docker.md)
