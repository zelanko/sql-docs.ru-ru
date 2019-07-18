---
title: Запуск SQL Server Службы машинного обучения в контейнере | Документация Майкрософт
description: В этом руководстве показано, как использовать SQL Server Службы машинного обучения в контейнере Linux, работающем в DOCKER.
author: uc-msft
ms.author: umajay
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.collection: linux-container
moniker: '>= sql-server-linux-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: f3d3774adf4bee07269b25c3359b031ca24eb99e
ms.sourcegitcommit: ef7834ed0f38c1712f45737018a0bfe892e894ee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300424"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>Запуск SQL Server Службы машинного обучения в контейнере

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом руководстве показано, как создать контейнер DOCKER с SQL Server Службы машинного обучения и выполнить скрипты Машинное обучение из Transact-SQL.

> [!div class="checklist"]
> * Клонировать репозиторий MSSQL-DOCKER.
> * Создание образа контейнера SQL Server Linux с Службы машинного обучения.
> * Запустите SQL Server образ контейнера Linux с Службы машинного обучения.
> * Выполнение скриптов R или Python с помощью инструкций Transact-SQL.
> * Закройте и удалите контейнер SQL Server Linux. 

## <a name="prerequisites"></a>предварительные требования

* Интерфейс командной строки Git.
* Docker Engine 1.8+ на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).
* Минимум 2 ГБ дискового пространства.
* Минимум 2 ГБ ОЗУ.
* [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

## <a name="clone-the-mssql-docker-repository"></a>Клонирование репозитория MSSQL-DOCKER

1. Откройте терминал Bash в Linux/Mac или WSL терминалов в Windows.

1. Создайте локальный каталог для локального хранения копии репозитория MSSQL-DOCKER.
1. Выполните команду git clone, чтобы клонировать репозиторий MSSQL-DOCKER.

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-sql-server-linux-container-image-with-machine-learning-services"></a>Создание образа контейнера SQL Server Linux с Службы машинного обучения

1. Перейдите в каталог MSSQL-млсервицес.

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Выполнение скрипта build.sh.

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Для создания образа DOCKER требуется установка пакетов, размер которых составляет несколько ГБ. Выполнение сценария может занять до 20 минут в зависимости от пропускной способности сети.

## <a name="run-sql-server-linux-container-image-with-machine-learning-services"></a>Запуск SQL Server образа контейнера Linux с Службы машинного обучения

1. Перед запуском контейнера задайте переменные среды. Задайте для переменной среды PATH_TO_MSSQL каталог узлов.

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

1. Выполнение скрипта run.sh.

   ```bash
   ./run.sh
   ```

   Эта команда создает контейнер SQL Server с Службы машинного обучения в выпуске Developer Edition (по умолчанию). SQL Server порт **1433** отображается на узле как порт **1401**.

   > [!NOTE]
   > Процесс выполнения рабочих SQL Server выпусков в контейнерах немного отличается. Дополнительные сведения см. [в статье Настройка образов контейнеров SQL Server в DOCKER](sql-server-linux-configure-docker.md). Если вы используете те же имена и порты контейнеров, оставшаяся часть этого руководства по-прежнему работает с рабочими контейнерами.

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

## <a name="execute-r--python-scripts-from-transact-sql"></a>Выполнение скриптов R/Python из Transact-SQL

1. Подключитесь к SQL Server в контейнере и включите параметр конфигурации External script, выполнив следующую инструкцию T-SQL.

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. Убедитесь, Службы машинного обучения работает, выполнив следующую простую sp_execute_external_script R/Python.

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

В этом руководстве вы узнали, как выполнить следующие действия.

> [!div class="checklist"]
> * Клонировать репозиторий MSSQL-DOCKER.
> * Создание образа контейнера SQL Server Linux с Службы машинного обучения.
> * Запустите SQL Server образ контейнера Linux с Службы машинного обучения.
> * Выполнение скриптов R или Python с помощью инструкций Transact-SQL.
> * Закройте и удалите контейнер SQL Server Linux.

Затем ознакомьтесь с другими сценариями настройки и устранения неполадок docker:

> [!div class="nextstepaction"]
>[Инструкции по настройке SQL Server в DOCKER](sql-server-linux-configure-docker.md)
