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
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 28bdf20b51769e15a887b4f9ec227f7aaf6afc95
ms.sourcegitcommit: 071065bc5433163ebfda4fdf6576349f9d195663
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2019
ms.locfileid: "71923824"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>Запуск контейнера со Службами машинного обучения SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом руководстве показано, как создать контейнер Docker с помощью Служб машинного обучения SQL Server и выполнить скрипты машинного обучения в Transact-SQL. Оно включает следующее задачи:

> [!div class="checklist"]
> * Клонирование репозитория mssql-docker.
> * создание образа контейнера SQL Server в Linux со Службами машинного обучения;
> * запуск образа контейнера SQL Server в Linux со Службами машинного обучения;
> * выполнение скриптов R или Python с помощью инструкций Transact-SQL;
> * Остановка и удаление контейнера SQL Server Linux.

## <a name="prerequisites"></a>предварительные требования

* Интерфейс командной строки Git.
* Docker Engine 1.8 или более поздней версии на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).
* Не менее 2 гигабайт (ГБ) места на диске.
* Не менее 2 ГБ ОЗУ.
* [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

## <a name="clone-the-mssql-docker-repository"></a>Клонирование репозитория mssql-docker

1. Откройте терминал bash в ОС Linux или Mac либо терминал WSL в ОС Windows.

1. Создайте локальный каталог для хранения локальной копии репозитория mssql-docker.
1. Выполните команду git clone, чтобы клонировать репозиторий mssql-docker:

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-a-sql-server-linux-container-image-with-machine-learning-services"></a>Создание образа контейнера SQL Server в Linux со Службами машинного обучения

1. Измените каталог на mssql-mlservices:

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Выполните скрипт build.sh:

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Для создания образа Docker вам нужно установить пакеты размером в несколько ГБ. Выполнение скрипта может занять до 20 минут. Этот период зависит от пропускной способности сети.

## <a name="run-the-sql-server-linux-container-image-with-machine-learning-services"></a>Запуск образа контейнера SQL Server в Linux со Службами машинного обучения

1. Перед запуском контейнера задайте переменные среды. В качестве значения переменной среды PATH_TO_MSSQL укажите каталог узла:

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

1. Выполните скрипт run.sh:

   ```bash
   ./run.sh
   ```

   Эта команда позволяет создать контейнер SQL Server со Службами машинного обучения, используя выпуск Developer Edition (по умолчанию). Порт SQL Server **1433** доступен на узле как порт **1401**.

   > [!NOTE]
   > Процесс запуска контейнера с рабочими выпусками SQL Server немного отличается. Дополнительные сведения см. в статье [Настройка образов контейнеров SQL Server в Docker](sql-server-linux-configure-docker.md). Если вы используете те же имена и порты контейнеров, действия в оставшейся части этого руководства будут актуальны и для рабочих контейнеров.

1. Чтобы просмотреть контейнеры Docker, выполните команду `docker ps`:

   ```bash
   sudo docker ps -a
   ```

1. Если в столбце **STATUS** (Состояние) отображается значение **Up** (Работает), SQL Server выполняется в контейнере и прослушивает порт, указанный в столбце **PORTS** (Порты). Если в столбце **STATUS** контейнера с SQL Server отображается **Exited** (завершен), см.руководство [Устранение неполадок конфигурации](sql-server-linux-configure-docker.md#troubleshooting).

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

1. Подключитесь к SQL Server в контейнере и включите параметр конфигурации внешнего скрипта, выполнив следующую инструкцию T-SQL:

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. Убедитесь, что Службы машинного обучения работают, выполнив следующий простой скрипт sp_execute_external_script на R или Python:

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
> * Клонирование репозитория mssql-docker
> * Создание образа контейнера SQL Server Linux со Службами машинного обучения
> * Запуск образа контейнера SQL Server Linux со Службами машинного обучения
> * Выполнение скриптов R или Python с помощью инструкций Transact-SQL
> * Остановка работы и удаление контейнера SQL Server в Linux

Затем ознакомьтесь с другими сценариями настройки и устранения неполадок Docker:

> [!div class="nextstepaction"]
>[Настройка SQL Server в Docker](sql-server-linux-configure-docker.md)
