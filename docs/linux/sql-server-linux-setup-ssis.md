---
title: Установка служб SQL Server Integration Services в Linux
description: Эта статья описывает установку служб SQL Server Integration Services (SSIS) в Linux.
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 68f3497e9f3f47d7e43c2bda0083bc25632d8221
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032437"
---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Установка служб SQL Server Integration Services (SSIS) в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Выполните действия, описанные в этой статье, чтобы установить SQL Server Integration Services (`mssql-server-is`) в Linux. Сведения о функциях, поддерживаемых в этом выпуске Integration Services для Linux, см. в [заметках о выпуске](sql-server-linux-release-notes.md).

Установите SQL Server Integration Services для своей платформы.

- [Ubuntu 16.04](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="ubuntu"></a> Установка SSIS в Ubuntu
Чтобы установить пакет `mssql-server-is` в Ubuntu, сделайте следующее.

1. Импортируйте открытые ключи GPG из репозитория.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Зарегистрируйте репозиторий Ubuntu для Microsoft SQL Server.

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

3. Выполните следующие команды для установки SQL Server Integration Services.

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

4. После установки Integration Services запустите `ssis-conf`. Дополнительные сведения см. в статье [Настройка служб SSIS в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

5. Завершив настройку, задайте путь.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Обновление служб SSIS
Если у вас уже установлен `mssql-server-is`, можно обновить его до последней версии, выполнив следующие команды.

```bash
sudo apt-get install mssql-server-is
```

### <a name="remove-ssis"></a>Удаление служб SSIS
Для удаления `mssql-server-is` можно выполнить следующую команду.
```bash
sudo apt-get remove mssql-server-is
```

## <a name="RHEL"></a> Установка SSIS в RHEL
Чтобы установить пакет `mssql-server-is` в RHEL, сделайте следующее.

1. Скачайте файл конфигурации репозитория Microsoft SQL Server Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

1. Выполните следующие команды для установки SQL Server Integration Services.

   ```bash
   sudo yum install -y mssql-server-is
   ```


1. После установки запустите `ssis-conf`. Дополнительные сведения см. в статье [Настройка служб SSIS в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. Завершив настройку, задайте путь.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Обновление служб SSIS
Если у вас уже установлен `mssql-server-is`, можно обновить его до последней версии, выполнив следующие команды.

```bash
sudo yum update mssql-server-is
```

### <a name="remove-ssis"></a>Удаление служб SSIS
Для удаления `mssql-server-is` можно выполнить следующую команду.
```bash
sudo yum remove mssql-server-is
```

## <a name="unattended-installation"></a>Автоматическая установка
Чтобы выполнить автоматическую установку при запуске `ssis-conf setup`, сделайте следующее.
1.  Укажите параметр `-n` (без запроса).
2.  Укажите необходимые значения, задав переменные среды.

Приведенный ниже пример выполняет следующие действия.
-   Устанавливает службы SSIS.
-   Указывает выпуск Developer, задавая значение для переменной среды `SSIS_PID`.
-   Принимает условия лицензионного соглашения, задавая значение для переменной среды `ACCEPT_EULA`.
-   Запускает автоматическую установку, указывая параметр `-n` (без запроса).

```
sudo SSIS_PID=Developer ACCEPT_EULA=Y /opt/ssis/bin/ssis-conf -n setup 
```

### <a name="environment-variables-for-unattended-installation"></a>Переменные среды для автоматической установки

| Переменная среды | Описание |
|---|---|
| **ACCEPT_EULA** | Принимает условия лицензионного соглашения SQL Server при задании любого значения (например, `Y`).|
| **SSIS_PID** | Указывает выпуск SQL Server или ключ продукта. Возможные значения<br/>Ознакомительная версия<br/>Разработчик<br/>Express <br/>Web Edition <br/>Standard<br/>Enterprise <br/>Ключ продукта<br/><br/>Если указывается ключ продукта, он должен иметь форму `#####-#####-#####-#####-#####`, где `#` — буква или цифра.  |
| | |

## <a name="next-steps"></a>Следующие шаги

Чтобы запустить пакеты SSIS в Linux, см. статью [Извлечение, преобразование и загрузка данных для SQL Server в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md).

Чтобы настроить дополнительные параметры SSIS в Linux, см. статью [Настройка SQL Server Integration Services в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md).

## <a name="related-content-about-ssis-on-linux"></a>Связанные материалы о службах SSIS в Linux
-   [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)
-   [Настройка SQL Server Integration Services в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md)
-   [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
-   [Планирование выполнения пакетов SQL Server Integration Services в Linux с помощью cron](sql-server-linux-schedule-ssis-packages.md)
