---
title: Настройка параметров SQL Server с помощью переменных среды
description: В этой статье описывается использование переменных среды для настройки параметров SQL Server 2017 в Linux.
author: VanMSFT
ms.author: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 11f8926ede3c4bcd1f0350be79add16c5ae52249
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531322"
---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Настройка параметров SQL Server с помощью переменных среды в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Для настройки SQL Server 2017 на Linux можно использовать несколько различных переменных среды. Эти переменные используются в двух сценариях:

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Для настройки SQL Server 2019 на Linux можно использовать несколько различных переменных среды. Эти переменные используются в двух сценариях:

::: moniker-end

- Начальная настройка с помощью команды `mssql-conf setup`.
- Настройка нового [контейнера SQL Server в Docker](quickstart-install-connect-docker.md).

> [!TIP]
> Если требуется выполнить настройку SQL Server после начальной настройки, ознакомьтесь с разделом [Настройка SQL Server на Linux с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md).

## <a name="environment-variables"></a>Переменные среды

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

| Переменная среды | Описание |
|-----|-----|
| **ACCEPT_EULA** | Присвойте переменной **ACCEPT_EULA** любое значение, чтобы подтвердить свое согласие с [лицензионным соглашением](https://go.microsoft.com/fwlink/?LinkId=746388). Обязательный параметр для образа SQL Server. |
| **MSSQL_SA_PASSWORD** | Настройте пароль пользователя SA. |
| **MSSQL_PID** | Укажите выпуск SQL Server или ключ продукта. Возможные значения. </br></br>**Ознакомительная версия**</br>**Разработчик**</br>**Express**</br>**Web**</br>**Standard Edition**</br>**Enterprise**</br>**Ключ продукта**</br></br>Если указывается ключ продукта, он должен соответствовать формату #####-#####-#####-#####-#####, где каждый знак "#" представляет собой букву или цифру.|
| **MSSQL_LCID** | Задайте идентификатор языка для SQL Server. Например, значение 1036 соответствует французскому языку. |
| **MSSQL_COLLATION** | Задает параметры сортировки по умолчанию для SQL Server. Переопределяет заданное по умолчанию сопоставление идентификатора языка (LCID) и параметров сортировки. |
| **MSSQL_MEMORY_LIMIT_MB** | Задает максимальный объем памяти (в МБ), который может использовать SQL Server. По умолчанию используется 80 % от общего объема физической памяти. |
| **MSSQL_TCP_PORT** | Настройте порт TCP, который будет прослушивать SQL Server (по умолчанию 1433). |
| **MSSQL_IP_ADDRESS** | Укажите IP-адрес. На данный момент необходимо задавать IP-адрес в стиле IPv4 (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Задайте каталог резервного копирования по умолчанию. |
| **MSSQL_DATA_DIR** | Измените каталог, в котором создаются новые файлы данных (MDF) базы данных SQL Server. |
| **MSSQL_LOG_DIR** | Измените каталог, в котором создаются новые файлы журнала (LDF) базы данных SQL Server. |
| **MSSQL_DUMP_DIR** | Измените каталог, в котором по умолчанию будут размещаться дампы памяти SQL Server, а также другие файлы для устранения неполадок. |
| **MSSQL_ENABLE_HADR** | Включение группы доступности. Например, значение "1" включает группу, а "0" отключает ее. |
| **MSSQL_AGENT_ENABLED** | Включение агента SQL Server. Например, значение "true" включает агент, а "false" отключает его. По умолчанию агент отключен.  |
| **MSSQL_MASTER_DATA_FILE** | Задает местонахождение файла базы данных master. До первого запуска SQL Server этот файл должен иметь имя **master.mdf**. |
| **MSSQL_MASTER_LOG_FILE** | Задает местонахождение файла журнала базы данных master. До первого запуска SQL Server этот файл должен иметь имя **mastlog.ldf**. |
| **MSSQL_ERROR_LOG_FILE** | Задает местонахождение файлов журнала ошибок. |

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

| Переменная среды | Описание |
|-----|-----|
| **ACCEPT_EULA** | Присвойте переменной **ACCEPT_EULA** любое значение, чтобы подтвердить свое согласие с [лицензионным соглашением](https://go.microsoft.com/fwlink/?LinkId=746388). Обязательный параметр для образа SQL Server. |
| **MSSQL_SA_PASSWORD** | Настройте пароль пользователя SA. |
| **MSSQL_PID** | Укажите выпуск SQL Server или ключ продукта. Возможные значения. </br></br>**Ознакомительная версия**</br>**Разработчик**</br>**Express**</br>**Web**</br>**Standard Edition**</br>**Enterprise**</br>**Ключ продукта**</br></br>Если указывается ключ продукта, он должен соответствовать формату #####-#####-#####-#####-#####, где каждый знак "#" представляет собой букву или цифру.|
| **MSSQL_LCID** | Задайте идентификатор языка для SQL Server. Например, значение 1036 соответствует французскому языку. |
| **MSSQL_COLLATION** | Задает параметры сортировки по умолчанию для SQL Server. Переопределяет заданное по умолчанию сопоставление идентификатора языка (LCID) и параметров сортировки. |
| **MSSQL_MEMORY_LIMIT_MB** | Задает максимальный объем памяти (в МБ), который может использовать SQL Server. По умолчанию используется 80 % от общего объема физической памяти. |
| **MSSQL_TCP_PORT** | Настройте порт TCP, который будет прослушивать SQL Server (по умолчанию 1433). |
| **MSSQL_IP_ADDRESS** | Укажите IP-адрес. На данный момент необходимо задавать IP-адрес в стиле IPv4 (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Задайте каталог резервного копирования по умолчанию. |
| **MSSQL_DATA_DIR** | Измените каталог, в котором создаются новые файлы данных (MDF) базы данных SQL Server. |
| **MSSQL_LOG_DIR** | Измените каталог, в котором создаются новые файлы журнала (LDF) базы данных SQL Server. |
| **MSSQL_DUMP_DIR** | Измените каталог, в котором по умолчанию будут размещаться дампы памяти SQL Server, а также другие файлы для устранения неполадок. |
| **MSSQL_ENABLE_HADR** | Включение группы доступности. Например, значение "1" включает группу, а "0" отключает ее. |
| **MSSQL_AGENT_ENABLED** | Включение агента SQL Server. Например, значение "true" включает агент, а "false" отключает его. По умолчанию агент отключен.  |
| **MSSQL_MASTER_DATA_FILE** | Задает местонахождение файла базы данных master. До первого запуска SQL Server этот файл должен иметь имя **master.mdf**. |
| **MSSQL_MASTER_LOG_FILE** | Задает местонахождение файла журнала базы данных master. До первого запуска SQL Server этот файл должен иметь имя **mastlog.ldf**. |
| **MSSQL_ERROR_LOG_FILE** | Задает местонахождение файлов журнала ошибок. |

::: moniker-end

## <a name="use-with-initial-setup"></a>Использование с начальной настройкой

В этом примере `mssql-conf setup` запускается с настроенными переменными среды. Заданы следующие переменные среды:

- **ACCEPT_EULA** — принимает условия лицензионного соглашения.
- **MSSQL_PID** — задает выпуск SQL Server Developer Edition с бесплатной лицензией для нерабочего использования.
- **MSSQL_SA_PASSWORD** — задает надежный пароль.
- **MSSQL_TCP_PORT** — задает порт TCP 1234, который будет прослушивать SQL Server.

```bash
sudo ACCEPT_EULA='Y' MSSQL_PID='Developer' MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' MSSQL_TCP_PORT=1234 /opt/mssql/bin/mssql-conf setup
```

## <a name="use-with-docker"></a>Использование с Docker

В этом примере в команде docker используются следующие переменные среды для создания нового контейнера SQL Server:

- **ACCEPT_EULA** — принимает условия лицензионного соглашения.
- **MSSQL_PID** — задает выпуск SQL Server Developer Edition с бесплатной лицензией для нерабочего использования.
- **MSSQL_SA_PASSWORD** — задает надежный пароль.
- **MSSQL_TCP_PORT** — задает порт TCP 1234, который будет прослушивать SQL Server. Это означает, что вместо сопоставления порта 1433 (по умолчанию) с портом узла в этом примере необходимо выполнить сопоставление пользовательского порта TCP с помощью команды `-p 1234:1234`.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Если вы работаете с Docker в Linux/macOS, используйте следующий синтаксис с одинарными кавычками:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

Если вы работаете с Docker в Windows, используйте следующий синтаксис с двойными кавычками:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

> [!NOTE]
> Процесс запуска контейнера с производственными выпусками немного отличается. Дополнительные сведения см. в разделе [Запуск образов контейнеров с производственными выпусками](sql-server-linux-configure-docker.md#production).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Если вы работаете с Docker в Linux/macOS, используйте следующий синтаксис с одинарными кавычками:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```

Если вы работаете с Docker в Windows, используйте следующий синтаксис с двойными кавычками:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

Другие параметры SQL Server, не представленные здесь, описываются в статье [Настройка SQL Server на Linux с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md).

Дополнительные сведения об установке и запуске SQL Server на Linux см. в статье [Установка SQL Server на Linux](sql-server-linux-setup.md).
