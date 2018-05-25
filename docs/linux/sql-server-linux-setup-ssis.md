---
title: Установка служб интеграции SQL Server в Linux | Документы Microsoft
description: В этой статье описывается установка служб SQL Server Integration Services (SSIS) для Linux.
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 01/09/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: d2e72c77ad5f200c07a6e71025a3461d6397032a
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Установка SQL Server Integration Services (SSIS) для Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Выполните действия в этой статье, чтобы установить SQL Server Integration Services (`mssql-server-is`) в Linux. Сведения о функции, поддерживаемые в этом выпуске служб Integration Services для Linux см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

Установка серверов интеграции SQL Server для вашей платформы:

- [Ubuntu](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="ubuntu"></a> Установка служб SSIS для Ubuntu
Чтобы установить `mssql-server-is` пакет в Ubuntu, выполните следующие действия:

1. Импорт ключей GPG общедоступный репозиторий.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Регистрация в Microsoft SQL Server Ubuntu репозиторий.

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

3. Выполните следующие команды для установки SQL Server Integration Services.

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

4. После установки служб Integration Services, запустите `ssis-conf`. Дополнительные сведения см. в разделе [настройки служб SSIS в Linux с помощью служб ssis conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

5. После завершения конфигурации задайте путь.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Обновление служб SSIS
Если у вас уже есть `mssql-server-is` установлены, можно обновить до последней версии с помощью следующей команды:

```bash
sudo apt-get install mssql-server-is
```

### <a name="remove-ssis"></a>Удаление служб SSIS
Чтобы удалить `mssql-server-is`, можно запустить следующую команду:
```bash
sudo apt-get remove mssql-server-is
```

## <a name="RHEL"></a> Установка служб SSIS на RHEL
Чтобы установить `mssql-server-is` пакет в RHEL, выполните следующие действия:

1. Загрузите файл конфигурации Microsoft SQL Server Red Hat репозитория.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

1. Выполните следующие команды для установки SQL Server Integration Services.

   ```bash
   sudo yum install -y mssql-server-is
   ```


1. После установки, выполните `ssis-conf`. Дополнительные сведения см. в разделе [настройки служб SSIS в Linux с помощью служб ssis conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. После завершения конфигурации задайте путь.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Обновление служб SSIS
Если у вас уже есть `mssql-server-is` установлены, можно обновить до последней версии с помощью следующей команды:

```bash
sudo yum update mssql-server-is
```

### <a name="remove-ssis"></a>Удаление служб SSIS
Чтобы удалить `mssql-server-is`, можно запустить следующую команду:
```bash
sudo yum remove mssql-server-is
```

## <a name="unattended-installation"></a>Автоматическая установка
Для выполнения автоматической установки при запуске `ssis-conf setup`, выполните следующие действия:
1.  Укажите `-n` (без запроса) параметра.
2.  Укажите необходимые значения, задав переменные среды.

Следующий пример выполняет следующие действия:
-   Установка служб SSIS.
-   Указывает выпуск Developer edition, указав значение для `SSIS_PID` переменной среды.
-   Принимает условия лицензионного соглашения, указав значение для `ACCEPT_EULA` переменной среды.
-   Запускает автоматическую установку, указав `-n` (без запроса) параметра.

```
sudo SSIS_PID=Developer ACCEPT_EULA=Y /opt/ssis/bin/ssis-conf -n setup 
```

### <a name="environment-variables-for-unattended-installation"></a>Переменные среды для автоматической установки

| Переменная среды | Описание |
|---|---|
| **ACCEPT_EULA** | Принимает лицензионного соглашения SQL Server, если задано любое значение (например, `Y`).|
| **SSIS_PID** | Задает ключ, выпуск или продукта SQL Server. Ниже приведены возможные значения:<br/>Ознакомительная версия<br/>Разработчик<br/>Express <br/>Web Edition <br/>Standard Edition<br/>Enterprise <br/>Ключ продукта<br/><br/>Если указать ключ продукта, ключ продукта должен быть в форме `#####-#####-#####-#####-#####`, где `#` является буквой или цифрой.  |
| | |

## <a name="next-steps"></a>Следующие шаги

Выполнение пакетов служб SSIS в Linux, см. [извлечения, преобразования и загрузки данных для SQL Server в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md).

Чтобы настроить дополнительные параметры служб SSIS в Linux, в разделе [настройки SQL Server Integration Services в Linux с помощью служб ssis conf](sql-server-linux-configure-ssis.md).

## <a name="related-content-about-ssis-on-linux"></a>См. также о служб SSIS в Linux
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)
-   [Настройка служб интеграции SQL Server в Linux с conf служб ssis](sql-server-linux-configure-ssis.md)
-   [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
-   [Выполнение в Linux с cron пакетов служб интеграции SQL Server расписание](sql-server-linux-schedule-ssis-packages.md)
