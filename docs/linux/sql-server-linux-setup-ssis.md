---
title: Установка SQL Server Integration Services в Linux
description: В этой статье описывается установка SQL Server Integration Services (SSIS) в Linux.
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 68f3497e9f3f47d7e43c2bda0083bc25632d8221
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032437"
---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Установка SQL Server Integration Services (SSIS) в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Выполните действия, описанные в этой статье, чтобы установить SQL Server Integration Services (`mssql-server-is`) на платформе Linux. Сведения о функциях, поддерживаемых в этом выпуске служб Integration Services для Linux, см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

Установка интеграции серверов SQL Server для вашей платформы:

- [Ubuntu 16.04](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="ubuntu"></a> Установка служб SSIS в Ubuntu
Чтобы установить `mssql-server-is` пакет в Ubuntu, выполните следующие действия:

1. Импорт общедоступного репозитория ключей GPG.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Зарегистрируйте репозиторий Microsoft SQL Server Ubuntu.

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

3. Выполните следующие команды для установки SQL Server Integration Services.

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

4. После установки служб Integration Services, запустите `ssis-conf`. Дополнительные сведения см. в разделе [Настройка служб SSIS в Linux с помощью служб ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

5. После завершения конфигурации, задайте путь.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Обновления служб SSIS
Если у вас уже есть `mssql-server-is` установлен, можно обновить до последней версии, выполнив следующую команду:

```bash
sudo apt-get install mssql-server-is
```

### <a name="remove-ssis"></a>Удаление служб SSIS
Чтобы удалить `mssql-server-is`, можно запустить следующую команду:
```bash
sudo apt-get remove mssql-server-is
```

## <a name="RHEL"></a> Установка служб SSIS на RHEL
Чтобы установить `mssql-server-is` пакет на RHEL, выполните следующие действия:

1. Скачайте файл конфигурации репозитория Microsoft SQL Server Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

1. Выполните следующие команды для установки SQL Server Integration Services.

   ```bash
   sudo yum install -y mssql-server-is
   ```


1. После установки, запустите `ssis-conf`. Дополнительные сведения см. в разделе [Настройка служб SSIS в Linux с помощью служб ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. После завершения конфигурации, задайте путь.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Обновления служб SSIS
Если у вас уже есть `mssql-server-is` установлен, можно обновить до последней версии, выполнив следующую команду:

```bash
sudo yum update mssql-server-is
```

### <a name="remove-ssis"></a>Удаление служб SSIS
Чтобы удалить `mssql-server-is`, можно запустить следующую команду:
```bash
sudo yum remove mssql-server-is
```

## <a name="unattended-installation"></a>Автоматическая установка
Для выполнения автоматической установки при запуске `ssis-conf setup`, выполните указанные ниже действия:
1.  Укажите `-n` (без запроса) параметр.
2.  Укажите необходимые значения, задав переменные среды.

Следующий пример выполняет следующие действия:
-   Установка служб SSIS.
-   Указывает выпуск Developer edition, указав значение для `SSIS_PID` переменной среды.
-   Принимает условия лицензионного соглашения, указав значение для `ACCEPT_EULA` переменной среды.
-   Запускает автоматическую установку, указав `-n` (без запроса) параметр.

```
sudo SSIS_PID=Developer ACCEPT_EULA=Y /opt/ssis/bin/ssis-conf -n setup 
```

### <a name="environment-variables-for-unattended-installation"></a>Переменные среды для автоматической установки

| Переменная среды | Описание |
|---|---|
| **ACCEPT_EULA** | Принимает лицензионное соглашение SQL Server, если задано любое значение (например, `Y`).|
| **SSIS_PID** | Задает ключ SQL Server edition или продукта. Ниже приведены возможные значения:<br/>Ознакомительная версия<br/>Разработчик<br/>Express <br/>Интернет <br/>Standard<br/>Enterprise <br/>Ключ продукта<br/><br/>Если указать ключ продукта, ключ продукта должен быть в форме `#####-#####-#####-#####-#####`, где `#` является буквой или цифрой.  |
| | |

## <a name="next-steps"></a>Следующие шаги

Для запуска пакетов служб SSIS в Linux, см. в разделе [извлечения, преобразования и загрузки данных для SQL Server в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md).

Чтобы настроить дополнительные параметры служб SSIS в Linux, см. в разделе [настроить SQL Server Integration Services в Linux с помощью служб ssis-conf](sql-server-linux-configure-ssis.md).

## <a name="related-content-about-ssis-on-linux"></a>См. также сведения о службах SSIS на платформе Linux
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)
-   [Настройка SQL Server Integration Services в Linux с помощью служб ssis-conf](sql-server-linux-configure-ssis.md)
-   [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
-   [Расписание SQL Server Integration Services выполнения пакета в Linux с помощью cron](sql-server-linux-schedule-ssis-packages.md)
