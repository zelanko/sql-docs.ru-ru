---
title: Защита контейнеров Docker в SQL Server
description: Узнайте о различных способах защиты контейнеров Docker на SQL Server и о том, как запускать контейнеры на узле от имени другого непривилегированного пользователя.
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.custom: contperfq1
ms.date: 09/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: 10d2eb061a4ee6d9ff9c8d0594561667dd882dc9
ms.sourcegitcommit: 678f513b0c4846797ba82a3f921ac95f7a5ac863
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2020
ms.locfileid: "89511616"
---
# <a name="secure-sql-server-docker-containers"></a>Защита контейнеров Docker в SQL Server

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Контейнеры SQL Server 2017 по умолчанию запускаются как привилегированные пользователи. Это может привести к некоторым проблемам безопасности. В этой статье рассказывается о доступных вариантах безопасности при запуске контейнеров Docker SQL Server, а также о том, как создать контейнер SQL Server в качестве непривилегированного пользователя.

## <a name="build-and-run-non-root-sql-server-2017-containers"></a><a id="buildnonrootcontainer"></a> Создание и запуск контейнеров SQL Server 2017, не являющихся корневыми

Чтобы создать контейнер SQL Server 2017, который запускается от имени пользователя `mssql` (не являющегося привилегированным), выполните указанные ниже действия.

> [!NOTE]
> Контейнеры SQL Server 2019 автоматически запускаются как не корневые, поэтому следующие шаги применяются только к контейнерам SQL Server 2017, которые по умолчанию запускаются как корневые.

1. Скачайте [образец файла dockerfile для непривилегированного контейнера SQL Server](https://raw.githubusercontent.com/microsoft/mssql-docker/master/linux/preview/examples/mssql-server-linux-non-root/Dockerfile) и сохраните его как `dockerfile`.

2. Выполните следующую команду в контексте каталога dockerfile, чтобы выполнить сборку непривилегированного контейнера SQL Server:

    ```bash
    cd <path to dockerfile>
    docker build -t 2017-latest-non-root .
    ```

3. Запустите контейнер.

    ```bash
    docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword@" --cap-add SYS_PTRACE --name sql1 -p 1433:1433 -d 2017-latest-non-root
    ```

    > [!NOTE]
    > Флаг `--cap-add SYS_PTRACE` необходим для создания дампов в целях устранения неполадок непривилегированных контейнеров SQL Server.

4. Убедитесь в том, что контейнер запущен от имени пользователя, не являющегося привилегированным:

    ```bash
    docker exec -it sql1 bash
    ```

    Выполните команду `whoami`, которая вернет пользователя, от имени которого выполняется контейнер.
    
    ```bash
    whoami
    ```

## <a name="run-container-as-a-different-non-root-user-on-the-host"></a><a id="nonrootuser"></a> Запуск контейнера от имени другого непривилегированного пользователя в узле

Чтобы запустить контейнер SQL Server от имени другого непривилегированного пользователя, добавьте флаг -u в команду docker run. Непривилегированный контейнер должен выполняться в составе привилегированной группы, если только том не подключен к каталогу `/var/opt/mssql`, к которому есть доступ у непривилегированного пользователя. Привилегированная группа не предоставляет дополнительных привилегированных разрешений пользователю, не являющемуся привилегированным.

#### <a name="run-as-a-user-with-a-uid-4000"></a>Выполнение от имени пользователя с ИД пользователя 4000

SQL Server можно запускать с настраиваемым идентификатором пользователя. Например, следующая команда запускает SQL Server с идентификатором пользователя 4000:

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u 4000:0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

> [!Warning]
> Убедитесь в том, что в контейнере SQL Server есть именованный пользователь, например mssql или root. В противном случае SQLCMD невозможно будет запустить в контейнере. Вы можете проверить, выполняется ли контейнер SQL Server от имени именованного пользователя, запустив `whoami` в контейнере.

#### <a name="run-the-non-root-container-as-the-root-user"></a>Запуск непривилегированного контейнера от имени привилегированного пользователя

При необходимости непривилегированный контейнер можно запустить от имени привилегированного пользователя. При этом контейнер также автоматически получает все разрешения на доступ к файлам.

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" -u 0:0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

#### <a name="run-as-a-user-on-your-host-machine"></a>Запуск от имени пользователя на хост-компьютере

SQL Server можно запустить от имени существующего пользователя на хост-компьютере с помощью следующей команды:
```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u $(id -u myusername):0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

#### <a name="run-as-a-different-user-and-group"></a>Запуск от имени другого пользователя и группы

SQL Server можно запускать от имени произвольного пользователя и группы. В этом примере подключенный том имеет разрешения, настроенные для пользователя или группы на хост-компьютере.

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u (id -u myusername):(id -g myusername) -v /path/to/mssql:/var/opt/mssql -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

## <a name="configure-persistent-storage-permissions-for-non-root-containers"></a><a id="storagepermissions"></a> Настройка разрешений на постоянное сохранение для непривилегированных контейнеров

Чтобы разрешить непривилегированному пользователю доступ к файлам базы данных в подключенных томах, пользователь или группа, от имени которых выполняется контейнер, должны иметь доступ на чтение и запись к постоянному хранилищу файлов.  

Узнать текущего владельца файлов базы данных можно с помощью приведенной ниже команды.

```bash
ls -ll <database file dir>
```

Если у SQL Server нет доступа к сохраненным файлам базы данных, выполните одну из приведенных ниже команд.

#### <a name="grant-the-root-group-rw-access-to-the-db-files"></a>Предоставление привилегированной группе доступа к файлам базы данных для чтения и записи

Предоставьте привилегированной группе разрешения на доступ к указанным ниже каталогам, чтобы у непривилегированного контейнера SQL Server был доступ к файлам базы данных.

```bash
chgrp -R 0 <database file dir>
chmod -R g=u <database file dir>
```

#### <a name="set-the-non-root-user-as-the-owner-of-the-files"></a>Назначение непривилегированного пользователя владельцем файлов

Это может быть непривилегированный пользователь по умолчанию или любой другой непривилегированный пользователь на ваш выбор. В этом примере в качестве непривилегированного пользователя задан пользователь с идентификатором 10001.

```bash
chown -R 10001:0 <database file dir>
```

## <a name="next-steps"></a>Дальнейшие действия

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

- Сведения о начале работы с образами контейнеров с SQL Server 2017 в Docker можно найти в [кратком руководстве](quickstart-install-connect-docker.md?view=sql-server-2017)

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

- Сведения о начале работы с образами контейнеров с SQL Server 2019 в Docker можно найти в [кратком руководстве](quickstart-install-connect-docker.md?view=sql-server-ver15)

::: moniker-end

- [Развертывание контейнеров Docker в SQL Server и подключение к ним](sql-server-linux-docker-container-deployment.md)

- [Ссылка на дополнительную конфигурацию и настройку контейнеров Docker](sql-server-linux-docker-container-configure.md)

- [Устранение неполадок контейнеров Docker на SQL Server](sql-server-linux-docker-container-troubleshooting.md)