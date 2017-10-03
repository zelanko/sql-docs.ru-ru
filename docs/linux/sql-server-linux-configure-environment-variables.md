---
title: "Настройка параметров SQL Server с переменными среды | Документы Microsoft"
description: "В этом разделе описывается использование переменных среды для настройки определенных параметров 2017 г. SQL Server в Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/21/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 2bbb64b775ab59665ac2c8eefdd21e514b4906cd
ms.contentlocale: ru-ru
ms.lasthandoff: 10/02/2017

---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Настройка параметров SQL Server с помощью переменных среды в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Настройка 2017 г. SQL Server в Linux, можно использовать несколько переменных в другой среде. Эти переменные используются в двух сценариях:

- Настройка начальной настройки с `mssql-conf setup` команды.
- Для настройки нового [контейнера SQL Server в Docker](quickstart-install-connect-docker.md).

> [!TIP]
> Если необходимо настроить SQL Server после этих сценариев установки, см. раздел [Настройка SQL Server в Linux с помощью средства mssql conf](sql-server-linux-configure-mssql-conf.md).

## <a name="environment-variables"></a>Переменные среды

| Переменная среды | Description |
|-----|-----|
| **ACCEPT_EULA** | Примите лицензионное соглашение SQL Server, если задано любое значение (например, «Y»). |
| **MSSQL_SA_PASSWORD** | Настройте пароль пользователя SA. |
| **MSSQL_PID** | Установите ключ edition или продукта SQL Server. Возможные значения: оценки, Developer, экспресс-выпуск, Web, Standard, Enterprise или ключ продукта в формате ###-###-###-###-###, где «#» — это число или буквы. |
| **MSSQL_LCID** | Задает идентификатор языка для SQL Server. Например 1036 — французский. |
| **MSSQL_COLLATION** | Задает параметры сортировки по умолчанию для SQL Server. Он переопределяет сопоставление по умолчанию идентификатор языка (LCID) для параметров сортировки. |
| **MSSQL_MEMORY_LIMIT_MB** | Задает максимальный объем памяти (в МБ), который можно использовать SQL Server. По умолчанию он составляет 80% от общего объема физической памяти. |
| **MSSQL_TCP_PORT** | Настройка порта TCP, который SQL Server прослушивает (по умолчанию 1433). |
| **MSSQL_IP_ADDRESS** | Задайте IP-адрес. В настоящий момент IP-адрес должен быть стиль IPv4 (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Задайте расположение каталога резервного копирования по умолчанию. |
| **MSSQL_DATA_DIR** | Перейдите в каталог, в котором создаются новые базы данных файлы данных SQL Server (.mdf). |
| **MSSQL_LOG_DIR** | Перейдите в каталог, в котором создаются новые файлы журналов (LDF) базы данных SQL Server. |
| **MSSQL_DUMP_DIR** | Перейдите в каталог, где SQL Server будет помещать дампы памяти и другие файлы устранения неполадок по умолчанию. |
| **MSSQL_ENABLE_HADR** | Включите группы доступности. |

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

## <a name="next-steps"></a>Следующие шаги

Другие параметры SQL Server, не перечисленных здесь, в разделе [Настройка SQL Server в Linux с помощью средства mssql conf](sql-server-linux-configure-mssql-conf.md).

Дополнительные сведения о том, как установить и запустить SQL Server в Linux см. в разделе [Установка SQL Server в Linux](sql-server-linux-setup.md).

