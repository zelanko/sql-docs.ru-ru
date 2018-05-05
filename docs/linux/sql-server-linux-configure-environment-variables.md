---
title: Настройка параметров SQL Server с переменными среды | Документы Microsoft
description: В этой статье описывается использование переменных среды для настройки определенных параметров 2017 г. SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.openlocfilehash: 19da900b114131bc3c1549a59e8ed14d2d13afef
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Настройка параметров SQL Server с помощью переменных среды в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Настройка 2017 г. SQL Server в Linux, можно использовать несколько переменных в другой среде. Эти переменные используются в двух сценариях:

- Настройка начальной настройки с `mssql-conf setup` команды.
- Для настройки нового [контейнера SQL Server в Docker](quickstart-install-connect-docker.md).

> [!TIP]
> Если необходимо настроить SQL Server после этих сценариев установки, см. раздел [Настройка SQL Server в Linux с помощью средства mssql conf](sql-server-linux-configure-mssql-conf.md).

## <a name="environment-variables"></a>Переменные среды

| Переменная среды | Описание |
|-----|-----|
| **ACCEPT_EULA** | Примите лицензионное соглашение SQL Server, если задано любое значение (например, «Y»). |
| **MSSQL_SA_PASSWORD** | Настройте пароль пользователя SA. |
| **MSSQL_PID** | Установите ключ edition или продукта SQL Server. Возможные значения. </br></br>**Ознакомительная версия**</br>**Разработчик**</br>**Экспресс-выпуск**</br>**Web**</br>**Standard Edition Edition**</br>**Enterprise**</br>**Ключ продукта**</br></br>При указании ключа продукта, он должен иметь вид ###-###-###-###-###, где «#» — это число или буквы.|
| **MSSQL_LCID** | Задает идентификатор языка для SQL Server. Например 1036 — французский. |
| **MSSQL_COLLATION** | Задает параметры сортировки по умолчанию для SQL Server. Он переопределяет сопоставление по умолчанию идентификатор языка (LCID) для параметров сортировки. |
| **MSSQL_MEMORY_LIMIT_MB** | Задает максимальный объем памяти (в МБ), который можно использовать SQL Server. По умолчанию он составляет 80% от общего объема физической памяти. |
| **MSSQL_TCP_PORT** | Настройка порта TCP, который SQL Server прослушивает (по умолчанию 1433). |
| **MSSQL_IP_ADDRESS** | Задайте IP-адрес. В настоящий момент IP-адрес должен быть стиль IPv4 (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Задайте расположение каталога резервного копирования по умолчанию. |
| **MSSQL_DATA_DIR** | Перейдите в каталог, в котором создаются новые базы данных файлы данных SQL Server (.mdf). |
| **MSSQL_LOG_DIR** | Перейдите в каталог, в котором создаются новые файлы журналов (LDF) базы данных SQL Server. |
| **MSSQL_DUMP_DIR** | Перейдите в каталог, где SQL Server будет помещать дампы памяти и другие файлы устранения неполадок по умолчанию. |
| **MSSQL_ENABLE_HADR** | Включить группы доступности. Например "1" включен и отключен "0" |
| **MSSQL_AGENT_ENABLED** | Включите агент SQL Server. Например включить 'true' и 'false' отключена. По умолчанию агент отключен.  |
| **MSSQL_MASTER_DATA_FILE** | Задает расположение файла данных базы данных master. |
| **MSSQL_MASTER_LOG_FILE** | Задает расположение файла журнала базы данных master. |
| **MSSQL_ERROR_LOG_FILE** | Задает расположение файлов журнала ошибок. |


## <a name="example-initial-setup"></a>Пример: начальная настройка

В этом примере выполняется `mssql-conf setup` настроен переменные среды. Определены следующие переменные среды:

- **ACCEPT_EULA** принимает лицензионное соглашение.
- **MSSSQL_PID** указывает свободно лицензированных разработчика версию SQL Server для использования в нерабочей.
- **MSSQL_SA_PASSWORD** задает надежный пароль.
- **MSSQL_TCP_PORT** задает TCP-порта SQL Server прослушивает 1234.

```bash
sudo ACCEPT_EULA='Y' MSSQL_PID='Developer' MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' MSSQL_TCP_PORT=1234 /opt/mssql/bin/mssql-conf setup
```

## <a name="example-docker"></a>Пример: Docker

В этом примере команда docker использует следующие переменные среды для создания нового контейнера 2017 г. SQL Server:

- **ACCEPT_EULA** принимает лицензионное соглашение.
- **MSSSQL_PID** указывает свободно лицензированных разработчика версию SQL Server для использования в нерабочей.
- **MSSQL_SA_PASSWORD** задает надежный пароль.
- **MSSQL_TCP_PORT** задает TCP-порта SQL Server прослушивает 1234. Это означает, что вместо сопоставления порт 1433 (по умолчанию) для порта узла, пользовательские TCP-порт должен быть сопоставлен со `-p 1234:1234` команды в этом примере.

При выполнении Docker на Linux или macOS, используйте следующий синтаксис в одинарные кавычки:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d microsoft/mssql-server-linux:2017-latest
```

Если вы используете Docker в Windows, используйте следующий синтаксис в двойные кавычки:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d microsoft/mssql-server-linux:2017-latest
```

> [!NOTE]
> Процесс запуска контейнера с производственными выпусками немного отличается. Дополнительные сведения см. в разделе [Запуск образов контейнеров с производственными выпусками](sql-server-linux-configure-docker.md#production).

## <a name="next-steps"></a>Следующие шаги

Другие параметры SQL Server, не перечисленных здесь, в разделе [Настройка SQL Server в Linux с помощью средства mssql conf](sql-server-linux-configure-mssql-conf.md).

Дополнительные сведения о том, как установить и запустить SQL Server в Linux см. в разделе [Установка SQL Server в Linux](sql-server-linux-setup.md).
