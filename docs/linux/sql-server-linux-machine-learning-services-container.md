---
title: Запустите SQL Server службы машинного обучения в контейнере | Документация Майкрософт
description: Этом руководстве показано, как использовать службы машинного обучения SQL Server в контейнере Linux, запуск в Docker.
author: uc-msft
ms.author: umajay
manager: craigg
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.collection: linux-container
moniker: '>= sql-server-linux-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 3e654e29d6c49d3bf68cdfe7c4e3b479b47a973c
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67840473"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>Запустите SQL Server службы машинного обучения в контейнере

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Этот учебник посвящен построения контейнера Docker с помощью службы машинного обучения SQL Server и запуска сценариев Transact-SQL.

> [!div class="checklist"]
> * Клонируйте репозиторий mssql-docker.
> * Создание образа контейнера SQL Server Linux со службами машинного обучения.
> * Запустите образ контейнера SQL Server Linux со службами машинного обучения.
> * Выполните сценарии R или Python, с помощью инструкций Transact-SQL.
> * Остановить и удалить контейнер SQL Server Linux. 

## <a name="prerequisites"></a>предварительные требования

* Интерфейс командной строки Git.
* Docker Engine 1.8+ на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).
* Минимум 2 ГБ места на диске.
* Не менее 2 ГБ ОЗУ.
* [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

## <a name="clone-the-mssql-docker-repository"></a>Клонируйте репозиторий mssql-docker

1. Откройте окно терминала bash в Linux, Mac или WSL терминал на Windows.

1. Создайте локальный каталог для хранения копии репозитория mssql-docker локально.
1. Выполните команду клона git, чтобы клонировать репозиторий с mssql-docker.

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-sql-server-linux-container-image-with-machine-learning-services"></a>Создание образа контейнера SQL Server Linux со службами машинного обучения

1. Перейдите в каталог в каталог mssql mlservices.

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Выполните этот сценарий.

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Построение образа docker необходимо установить пакеты, которые несколько гигабайт в размере. Скрипт может занять до 20 минут для завершения в зависимости от пропускной способности сети.

## <a name="run-sql-server-linux-container-image-with-machine-learning-services"></a>Запустите образ контейнера SQL Server Linux со службами машинного обучения

1. Задать переменные среды перед запуском контейнера. Необходимо задать переменную среды PATH_TO_MSSQL каталог узла.

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

   Эта команда создает контейнер SQL Server со службами машинного обучения с Developer edition (по умолчанию). Порт SQL Server **1433** предоставляется на узле, что порт **1401**.

   > [!NOTE]
   > Процесс запуска производственными выпусками SQL Server в контейнерах, немного отличается. Дополнительные сведения см. в разделе [Запуск образов контейнеров с производственными выпусками](sql-server-linux-configure-docker.md#production). Если вы используете те же имена контейнеров и порты, остальной части этого пошагового руководства по-прежнему работает с контейнерами в рабочей среде.

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

## <a name="execute-r--python-scripts-from-transact-sql"></a>Выполнение R / Python скрипты Transact-SQL

1. Подключитесь к SQL Server в контейнере и включите параметр конфигурации внешнего скрипта, выполнив следующую инструкцию T-SQL.

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. Проверки работоспособности служб машинного обучения, выполнив следующий простой sp_execute_external_script R и Python.

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

В этом руководстве вы узнали, как сделать следующее:

> [!div class="checklist"]
> * Клонируйте репозиторий mssql-docker.
> * Создание образа контейнера SQL Server Linux со службами машинного обучения.
> * Запустите образ контейнера SQL Server Linux со службами машинного обучения.
> * Выполните сценарии R или Python, с помощью инструкций Transact-SQL.
> * Остановить и удалить контейнер SQL Server Linux.

Затем просмотрите другие конфигурации Docker и устранение неполадок в сценариях:

> [!div class="nextstepaction"]
>[Руководство по настройке для SQL Server в Docker](sql-server-linux-configure-docker.md)
