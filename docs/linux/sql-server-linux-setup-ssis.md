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
ms.openlocfilehash: 0f400667e73effb73ff41c3c7270e3f89a2ca0da
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76162655"
---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Установка служб SQL Server Integration Services (SSIS) в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Выполните действия, описанные в этой статье, чтобы установить SQL Server Integration Services (**mssql-server-is**) в Linux. Сведения о функциях, поддерживаемых в этом выпуске Integration Services для Linux, см. в [заметках о выпуске](sql-server-linux-release-notes.md).

Установка служб SQL Server Integration Services в Linux доступна на следующих платформах.

- [Ubuntu 16.04](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="install-ssis-on-ubuntu"></a><a name="ubuntu"></a> Установка SSIS в Ubuntu

Чтобы установить пакет **mssql-server-is** в Ubuntu, сделайте следующее.

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Импортируйте открытые ключи GPG из репозитория.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Зарегистрируйте репозиторий Ubuntu для SQL Server.

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

1. Выполните следующие команды для установки SQL Server Integration Services.

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

1. После установки Integration Services запустите **ssis-conf**. Дополнительные сведения см. в статье [Настройка служб SSIS в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. Завершив настройку, задайте переменную среды PATH.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Импортируйте открытые ключи GPG из репозитория.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Зарегистрируйте репозиторий Ubuntu для SQL Server.

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)"
   ```

1. Выполните следующие команды для установки SQL Server Integration Services.

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

1. После установки Integration Services запустите **ssis-conf**. Дополнительные сведения см. в статье [Настройка служб SSIS в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. Завершив настройку, задайте переменную среды PATH.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

::: moniker-end

### <a name="update-ssis"></a>Обновление служб SSIS

Если у вас уже есть **mssql-server-is**, обновите пакет до последней версии, выполнив следующие команды.

```bash
sudo apt-get install mssql-server-is
```

### <a name="remove-ssis"></a>Удаление служб SSIS

Чтобы удалить **mssql-server-is**, выполните приведенную ниже команду.

```bash
sudo apt-get remove mssql-server-is
```

## <a name="install-ssis-on-rhel"></a><a name="RHEL"></a> Установка SSIS в RHEL
Чтобы установить пакет **mssql-server-is** в RHEL, сделайте следующее.

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Скачайте файл конфигурации репозитория SQL Server Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

1. Выполните следующие команды для установки SQL Server Integration Services.

   ```bash
   sudo yum install -y mssql-server-is
   ```

1. После установки запустите **ssis-conf**. Дополнительные сведения см. в статье [Настройка служб SSIS в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. Завершив настройку, задайте переменную среды PATH.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Скачайте файл конфигурации репозитория SQL Server Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2019.repo
   ```

1. Выполните следующие команды для установки SQL Server Integration Services.

   ```bash
   sudo yum install -y mssql-server-is
   ```

1. После установки запустите **ssis-conf**. Дополнительные сведения см. в статье [Настройка служб SSIS в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. Завершив настройку, задайте переменную среды PATH.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

::: moniker-end

### <a name="update-ssis"></a>Обновление служб SSIS

Если у вас уже есть **mssql-server-is**, обновите пакет до последней версии, выполнив следующие команды.

```bash
sudo yum update mssql-server-is
```

### <a name="remove-ssis"></a>Удаление служб SSIS
Чтобы удалить **mssql-server-is**, выполните приведенную ниже команду.

```bash
sudo yum remove mssql-server-is
```

## <a name="unattended-installation"></a>Автоматическая установка

Для запуска программы **ssis-conf** в режиме автоматической установки выполните следующие действия.

1. Укажите параметр **-n** (без запроса).
1. Укажите необходимые значения, задав переменные среды.

Приведенный ниже пример выполняет эти действия.

- Устанавливает службы SSIS.
- Указывает выпуск Developer, задавая значение для переменной среды SSIS_PID.
- Принимает условия лицензионного соглашения на использование программного обеспечения корпорации Майкрософт, задавая значение для переменной среды ACCEPT_EULA.
- Запускает автоматическую установку, указывая параметр **-n** (без запроса).

```
sudo SSIS_PID=Developer ACCEPT_EULA=Y /opt/ssis/bin/ssis-conf -n setup 
```

### <a name="environment-variables-for-unattended-installation"></a>Переменные среды для автоматической установки

| Переменная среды | Description |
|---|---|
| ACCEPT_EULA | Принимает условия лицензионного соглашения SQL Server при задании любого значения (например, "Y").|
| SSIS_PID | Указывает выпуск SQL Server или ключ продукта. Возможные значения<ul><li>Ознакомительная версия</li><li>Разработчик</li><li>Express</li><li>Интернет</li><li>Standard</li><li>Enterprise</li><li>Ключ продукта</li></ul>Если указывается ключ продукта, он должен иметь форму *#####* - *#####* - *#####* - *#####* - *#####* , где *#*  — буква или цифра.  |
| | |

## <a name="next-steps"></a>Дальнейшие действия

Чтобы запустить пакеты SSIS в Linux, см. статью [Извлечение, преобразование и загрузка данных для SQL Server в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md).

Чтобы настроить дополнительные параметры SSIS в Linux, см. статью [Настройка SQL Server Integration Services в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md).

## <a name="related-content-about-ssis-on-linux"></a>Связанные материалы о службах SSIS в Linux

- [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)
- [Настройка SQL Server Integration Services в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md)
- [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
- [Планирование выполнения пакетов SQL Server Integration Services в Linux с помощью cron](sql-server-linux-schedule-ssis-packages.md)
