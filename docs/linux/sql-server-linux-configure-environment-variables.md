---
title: Настройка параметров SQL Server с помощью переменных среды | Документация Майкрософт
description: В этой статье описывается, как использовать переменные среды, чтобы настраивать конкретные параметры SQL Server 2017 в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: ea8eaf28f33a07d446768c8d4d770bf4727ce48b
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085376"
---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Настройка параметров SQL Server с помощью переменных среды в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Несколько переменных другую среду можно использовать для настройки SQL Server 2017 в Linux. Эти переменные используются в двух сценариях:

- Настройка начальной настройки с `mssql-conf setup` команды.
- Чтобы настроить новый [контейнер SQL Server в Docker](quickstart-install-connect-docker.md).

> [!TIP]
> Если необходимо настроить SQL Server после этих сценариев установки, см. в разделе [Настройка SQL Server в Linux с использованием средство mssql-conf](sql-server-linux-configure-mssql-conf.md).

## <a name="environment-variables"></a>Переменные среды

| Переменная среды | Описание |
|-----|-----|
| **ACCEPT_EULA** | Примите лицензионное соглашение SQL Server, если задано любое значение (например, «Y»). |
| **MSSQL_SA_PASSWORD** | Настройте пароль пользователя SA. |
| **MSSQL_PID** | Задайте ключ SQL Server edition или продукта. Возможные значения. </br></br>**Ознакомительная версия**</br>**Разработчик**</br>**Express**</br>**Web**</br>**Standard Edition**</br>**Enterprise**</br>**Ключ продукта**</br></br>Если указывать код продукта, его необходимо в виде ###-###-###-###-###, где «#» — число или буква.|
| **MSSQL_LCID** | Задает идентификатор языка, используемого для SQL Server. Например, 1036 — французский. |
| **MSSQL_COLLATION** | Задает параметры сортировки по умолчанию для SQL Server. Это значение переопределяет сопоставление по умолчанию идентификатор языка (LCID) для параметров сортировки. |
| **MSSQL_MEMORY_LIMIT_MB** | Задает максимальный объем памяти (в МБ), который можно использовать SQL Server. По умолчанию он составляет 80% от общего объема физической памяти. |
| **MSSQL_TCP_PORT** | Настройте TCP-порт, который ожидает передачу данных SQL Server (по умолчанию 1433). |
| **MSSQL_IP_ADDRESS** | Настройка IP-адреса. В настоящее время IP-адрес должен быть стиля IPv4 (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Задайте расположение каталога резервного копирования по умолчанию. |
| **MSSQL_DATA_DIR** | Перейдите в каталог, где создаются новые базы данных файлы данных SQL Server (.mdf). |
| **MSSQL_LOG_DIR** | Перейдите в каталог, где создаются новые файлы журналов (LDF) базы данных SQL Server. |
| **MSSQL_DUMP_DIR** | Перейдите в каталог, где SQL Server будет Депонировать дампы памяти и другие файлы для устранения неполадок по умолчанию. |
| **MSSQL_ENABLE_HADR** | Включение группы доступности. Например "1" включена и отключена "0" |
| **MSSQL_AGENT_ENABLED** | Включите агент SQL Server. Например «true» включен, и «false» отключена. По умолчанию агент отключен.  |
| **MSSQL_MASTER_DATA_FILE** | Задает расположение файла данных базы данных master. |
| **MSSQL_MASTER_LOG_FILE** | Задает расположение файла журнала базы данных master. |
| **MSSQL_ERROR_LOG_FILE** | Задает расположение файлов журнала ошибок. |


## <a name="example-initial-setup"></a>Пример: начальная настройка

В этом примере выполняется `mssql-conf setup` настроить переменные среды. Указываются следующие переменные среды:

- **ACCEPT_EULA** принимает лицензионное соглашение конечного пользователя.
- **MSSSQL_PID** указывает в свободно лицензируемым Developer Edition SQL Server для непроизводственных задач.
- **MSSQL_SA_PASSWORD** задает надежный пароль.
- **MSSQL_TCP_PORT** задает TCP-порта SQL Server прослушивает 1234.

```bash
sudo ACCEPT_EULA='Y' MSSQL_PID='Developer' MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' MSSQL_TCP_PORT=1234 /opt/mssql/bin/mssql-conf setup
```

## <a name="example-docker"></a>Пример: Docker

В этом примере команда docker использует следующие переменные среды, чтобы создать новый контейнер SQL Server 2017:

- **ACCEPT_EULA** принимает лицензионное соглашение конечного пользователя.
- **MSSSQL_PID** указывает в свободно лицензируемым Developer Edition SQL Server для непроизводственных задач.
- **MSSQL_SA_PASSWORD** задает надежный пароль.
- **MSSQL_TCP_PORT** задает TCP-порта SQL Server прослушивает 1234. Это означает, что вместо сопоставления порта 1433 (по умолчанию) с портом узла, настраиваемый TCP-порт должен быть сопоставлен со `-p 1234:1234` команды в этом примере.

Если вы используете Docker в Linux и Mac OS, используйте следующий синтаксис в одинарные кавычки:

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

Другие параметры SQL Server, не перечисленные здесь, см. в разделе [Настройка SQL Server в Linux с использованием средство mssql-conf](sql-server-linux-configure-mssql-conf.md).

Дополнительные сведения о том, как установить и запустить SQL Server в Linux см. в разделе [Установка SQL Server в Linux](sql-server-linux-setup.md).
