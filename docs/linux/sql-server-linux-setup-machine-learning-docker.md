---
title: Установка в Docker
titleSuffix: SQL Server Machine Learning Services
description: Сведения об установке Служб машинного обучения SQL Server (Python, R) в Docker.
author: cawrites
ms.author: chadam
ms.reviewer: davidph
manager: cgronlun
ms.date: 03/23/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e5a53419aba5515a9a60817ec0cc2a9de5a648d2
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80228345"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-docker"></a>Установка Служб машинного обучения SQL Server (Python, R) в Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье объясняется, как установить Службы машинного обучения SQL Server в Docker. Службы машинного обучения можно использовать для запуска сценариев R или Python в базе данных. Мы не предоставляем готовые контейнеры со Службами машинного обучения. Вы можете создать их из контейнеров SQL Server, используя [пример шаблона, доступный на сайте GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

## <a name="prerequisites"></a>Предварительные требования

- Интерфейс командной строки Git.

- Docker Engine 1.8 или более поздней версии на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в статье [Получение Docker](https://docs.docker.com/get-docker/).

- См. также [требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

## <a name="clone-the-mssql-docker-repository"></a>Клонирование репозитория mssql-docker

Следующая команда позволяет клонировать репозиторий `mssql-docker` Git в локальный каталог.

1. Откройте терминал bash в ОС Linux или Mac либо откройте терминал подсистемы Windows для Linux (WSL) в ОС Windows.

2. Создайте каталог для хранения локальной копии репозитория mssql-docker.

3. Выполните команду git clone, чтобы клонировать репозиторий mssql-docker:

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-a-sql-server-linux-container-image"></a>Создание образа контейнера SQL Server Linux

Чтобы создать образ Docker, выполните следующие шаги:

1. Измените каталог на mssql-mlservices:

2. В том же каталоге выполните следующую команду:

    ```bash
    docker builds -t mssql-server-mlservices
    ```

3. Выполните приведенную ниже команду.

    ```bash
    docker runs -d -e MSSQL_PID=Developer -e ACCEPT_EULA=Y -e ACCEPT_EULA_ML=Y -e SA_PASSWORD=<your_sa_password> -v OS>:/var/opt/mssql -p 1433:1433 mssql-server-mlservices
    ```

    Измените `<your_sa_password>` в `SA_PASSWORD=<your_sa_password>` и измените путь `-v`. 

4. Подтвердите, выполнив следующую команду:

    ```bash
    docker ps -a
    ```

   > [!NOTE]
   > Для создания образа Docker вам нужно установить пакеты размером в несколько ГБ. Выполнение скрипта может занять некоторое время в зависимости от пропускной способности сети.

## <a name="run-the-sql-server-linux-container-image"></a>Запуск образа контейнера SQL Server Linux

1. Перед запуском контейнера задайте переменные среды. В качестве значения переменной среды PATH_TO_MSSQL укажите каталог узла:

   ```bash
   export MSSQL_PID='Developer'
   export ACCEPT_EULA='Y'
   export ACCEPT_EULA_ML='Y'
   export PATH_TO_MSSQL='/home/mssql/'
   ```

2. Выполните скрипт run.sh:

   ```bash
   ./run.sh
   ```

   Эта команда позволяет создать контейнер SQL Server со Службами машинного обучения, используя выпуск Developer Edition (по умолчанию). Порт SQL Server **1433** доступен на узле как порт **1401**.

   > [!NOTE]
   > Процесс запуска контейнера с рабочими выпусками SQL Server немного отличается. Дополнительные сведения см. в статье [Настройка образов контейнеров SQL Server в Docker](sql-server-linux-configure-docker.md). Если вы используете те же имена и порты контейнеров, действия в оставшейся части этого руководства будут актуальны и для рабочих контейнеров.

3. Чтобы просмотреть контейнеры Docker, выполните команду `docker ps`:

   ```bash
   sudo docker ps -a
   ```

4. Если в столбце **STATUS** (Состояние) отображается значение **Up** (Работает), SQL Server выполняется в контейнере и прослушивает порт, указанный в столбце **PORTS** (Порты). Если в столбце **STATUS** контейнера с SQL Server отображается **Exited** (завершен), см.руководство [Устранение неполадок конфигурации](sql-server-linux-configure-docker.md#troubleshooting).

   ```bash
   $ sudo docker ps -a
   ```

    Выходные данные:

    ```
    CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
    941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour     0.0.0.0:1401->1433/tcp   sql1
    ```

## <a name="enable-machine-learning-services"></a>Включение служб машинного обучения

Чтобы включить Службы машинного обучения, подключитесь к экземпляру SQL Server и выполните следующую инструкцию T-SQL:

```sql
EXEC sp_configure  'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE
```

## <a name="next-steps"></a>Дальнейшие действия

Разработчики на языке Python могут узнать, как использовать Python с SQL Server, изучив следующие руководства.

+ [Учебник по Python. Прогнозирование проката лыж с помощью линейной регрессии в Службах машинного обучения SQL Server](../advanced-analytics/tutorials/python-ski-rental-linear-regression.md)
+ [Руководство. Классификация клиентов на основе кластеризации методом k-средних с помощью служб машинного обучения SQL Server](../advanced-analytics/tutorials/python-clustering-model.md)

Разработчики на языке R могут ознакомиться с простыми примерами, а также узнать, как код R работает с SQL Server. Дополнительные сведения см. в следующих статьях.

+ [Руководство. Запуск R в T-SQL](../advanced-analytics/tutorials/quickstart-r-create-script.md)
+ [Руководство. Аналитические функции в базе данных для разработчиков R](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)
