---
title: Настройка параметров SQL Server с помощью переменных среды
description: В этой статье описывается, как использовать переменные среды для настройки конкретных параметров SQL Server 2017 в Linux.
author: VanMSFT
ms.author: vanto
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 51589a2183043c5c8ea8d1f9bf5d4af6fcc1eea3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419249"
---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Настройка параметров SQL Server с помощью переменных среды в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Для настройки SQL Server 2017 в Linux можно использовать несколько различных переменных среды. Эти переменные используются в двух сценариях:

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Для настройки предварительной версии SQL Server 2019 в Linux можно использовать несколько различных переменных среды. Эти переменные используются в двух сценариях:

::: moniker-end

- Для настройки начальной настройки с помощью `mssql-conf setup` команды.
- Настройка нового [контейнера SQL Server в DOCKER](quickstart-install-connect-docker.md).

> [!TIP]
> Если необходимо настроить SQL Server после этих сценариев установки, см. раздел [настройка SQL Server на Linux с помощью средства MSSQL-CONF](sql-server-linux-configure-mssql-conf.md).

## <a name="environment-variables"></a>Переменные среды

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

| Переменная среды | Описание |
|-----|-----|
| **ACCEPT_EULA** | Присвойте переменной **ACCEPT_EULA** любое значение, чтобы подтвердить свое согласие с [лицензионным соглашением](https://go.microsoft.com/fwlink/?LinkId=746388). Обязательный параметр для образа SQL Server. |
| **MSSQL_SA_PASSWORD** | Настройте пароль пользователя SA. |
| **MSSQL_PID** | Задайте выпуск SQL Server или ключ продукта. Возможные значения. </br></br>**Ознакомительная версия**</br>**Разработчик**</br>**Ражающий**</br>**Интернет**</br>**Standard Edition**</br>**Компании**</br>**Ключ продукта**</br></br>При указании ключа продукта он должен иметь вид # # # # #-# # # # #-# # # # #-# # # # #-# # # # #, где ' # '-число или буква.|
| **MSSQL_LCID** | Задает идентификатор языка, используемый для SQL Server. Например, 1036 — французский. |
| **MSSQL_COLLATION** | Задает параметры сортировки по умолчанию для SQL Server. Это переопределяет сопоставление по умолчанию идентификатора языка (LCID) с параметрами сортировки. |
| **MSSQL_MEMORY_LIMIT_MB** | Задает максимальный объем памяти (в МБ), который SQL Server может использоваться. По умолчанию это 80% общего объема физической памяти. |
| **MSSQL_TCP_PORT** | Настройте TCP-порт, который SQL Server прослушивается (по умолчанию 1433). |
| **MSSQL_IP_ADDRESS** | Задайте IP-адрес. Сейчас IP-адрес должен быть в формате IPv4 (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Укажите расположение каталога резервных копий по умолчанию. |
| **MSSQL_DATA_DIR** | Измените каталог, в котором создаются новые файлы данных SQL Server базы данных (MDF). |
| **MSSQL_LOG_DIR** | Измените каталог, в котором создаются новые файлы журнала SQL Server базы данных (LDF). |
| **MSSQL_DUMP_DIR** | Измените каталог, где SQL Server будет замещать дампы памяти и другие файлы для устранения неполадок по умолчанию. |
| **MSSQL_ENABLE_HADR** | Включите группу доступности. Например, "1" включен, а "0" отключен |
| **MSSQL_AGENT_ENABLED** | Включите агент SQL Server. Например, "true" (включено) и "false" отключено. По умолчанию агент отключен.  |
| **MSSQL_MASTER_DATA_FILE** | Задает расположение файла данных базы данных master. Должен иметь имя **master. mdf** до первого запуска SQL Server. |
| **MSSQL_MASTER_LOG_FILE** | Задает расположение файла журнала базы данных master. Необходимо присвоить имя **mastlog. ldf** до первого запуска SQL Server. |
| **MSSQL_ERROR_LOG_FILE** | Задает расположение файлов журнала ошибок. |

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

| Переменная среды | Описание |
|-----|-----|
| **ACCEPT_EULA** | Присвойте переменной **ACCEPT_EULA** любое значение, чтобы подтвердить свое согласие с [лицензионным соглашением](https://go.microsoft.com/fwlink/?LinkId=746388). Обязательный параметр для образа SQL Server. |
| **MSSQL_SA_PASSWORD** | Настройте пароль пользователя SA. |
| **MSSQL_PID** | Задайте выпуск SQL Server или ключ продукта. Возможные значения. </br></br>**Ознакомительная версия**</br>**Разработчик**</br>**Ражающий**</br>**Интернет**</br>**Standard Edition**</br>**Компании**</br>**Ключ продукта**</br></br>При указании ключа продукта он должен иметь вид # # # # #-# # # # #-# # # # #-# # # # #-# # # # #, где ' # '-число или буква.|
| **MSSQL_LCID** | Задает идентификатор языка, используемый для SQL Server. Например, 1036 — французский. |
| **MSSQL_COLLATION** | Задает параметры сортировки по умолчанию для SQL Server. Это переопределяет сопоставление по умолчанию идентификатора языка (LCID) с параметрами сортировки. |
| **MSSQL_MEMORY_LIMIT_MB** | Задает максимальный объем памяти (в МБ), который SQL Server может использоваться. По умолчанию это 80% общего объема физической памяти. |
| **MSSQL_TCP_PORT** | Настройте TCP-порт, который SQL Server прослушивается (по умолчанию 1433). |
| **MSSQL_IP_ADDRESS** | Задайте IP-адрес. Сейчас IP-адрес должен быть в формате IPv4 (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Укажите расположение каталога резервных копий по умолчанию. |
| **MSSQL_DATA_DIR** | Измените каталог, в котором создаются новые файлы данных SQL Server базы данных (MDF). |
| **MSSQL_LOG_DIR** | Измените каталог, в котором создаются новые файлы журнала SQL Server базы данных (LDF). |
| **MSSQL_DUMP_DIR** | Измените каталог, где SQL Server будет замещать дампы памяти и другие файлы для устранения неполадок по умолчанию. |
| **MSSQL_ENABLE_HADR** | Включите группу доступности. Например, "1" включен, а "0" отключен |
| **MSSQL_AGENT_ENABLED** | Включите агент SQL Server. Например, "true" (включено) и "false" отключено. По умолчанию агент отключен.  |
| **MSSQL_MASTER_DATA_FILE** | Задает расположение файла данных базы данных master. Должен иметь имя **master. mdf** до первого запуска SQL Server. |
| **MSSQL_MASTER_LOG_FILE** | Задает расположение файла журнала базы данных master. Необходимо присвоить имя **mastlog. ldf** до первого запуска SQL Server. |
| **MSSQL_ERROR_LOG_FILE** | Задает расположение файлов журнала ошибок. |

::: moniker-end

## <a name="use-with-initial-setup"></a>Использование с начальной настройкой

Этот пример выполняется `mssql-conf setup` с настроенными переменными среды. Указаны следующие переменные среды:

- **ACCEPT_EULA** принимает лицензионное соглашение.
- **MSSSQL_PID** указывает бесплатно лицензированный выпуск Developer SQL Server для нерабочего использования.
- **MSSQL_SA_PASSWORD** задает надежный пароль.
- **MSSQL_TCP_PORT** задает TCP-порт, который SQL Server прослушивать до 1234.

```bash
sudo ACCEPT_EULA='Y' MSSQL_PID='Developer' MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' MSSQL_TCP_PORT=1234 /opt/mssql/bin/mssql-conf setup
```

## <a name="use-with-docker"></a>Использование с DOCKER

В этом примере команда DOCKER использует следующие переменные среды для создания нового SQL Server контейнера:

- **ACCEPT_EULA** принимает лицензионное соглашение.
- **MSSSQL_PID** указывает бесплатно лицензированный выпуск Developer SQL Server для нерабочего использования.
- **MSSQL_SA_PASSWORD** задает надежный пароль.
- **MSSQL_TCP_PORT** задает TCP-порт, который SQL Server прослушивать до 1234. Это означает, что вместо порта 1433 (по умолчанию) к порту узла пользовательский TCP-порт должен быть сопоставлен с `-p 1234:1234` командой в этом примере.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Если вы используете DOCKER в Linux или macOS, используйте следующий синтаксис с одинарными кавычками:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

Если вы используете DOCKER в Windows, используйте следующий синтаксис с двойными кавычками:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

> [!NOTE]
> Процесс запуска контейнера с производственными выпусками немного отличается. Дополнительные сведения см. в разделе [Запуск образов контейнеров с производственными выпусками](sql-server-linux-configure-docker.md#production).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Если вы используете DOCKER в Linux или macOS, используйте следующий синтаксис с одинарными кавычками:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

Если вы используете DOCKER в Windows, используйте следующий синтаксис с двойными кавычками:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

Другие параметры SQL Server, не указанные здесь, см. [в разделе настройка SQL Server на Linux с помощью средства MSSQL-CONF](sql-server-linux-configure-mssql-conf.md).

Дополнительные сведения об установке и запуске SQL Server на Linux см. в разделе [install SQL Server на Linux](sql-server-linux-setup.md).
