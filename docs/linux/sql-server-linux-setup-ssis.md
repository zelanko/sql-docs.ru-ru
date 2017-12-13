---
title: "Установка служб интеграции SQL Server в Linux | Документы Microsoft"
description: "В этой статье описывается установка служб SQL Server Integration Services (SSIS) для Linux."
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: 13bd5bde7e4e4ec63bb7e3bd7d8959440f499672
ms.sourcegitcommit: 05e2814fac4d308196b84f1f0fbac6755e8ef876
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Установка SQL Server Integration Services (SSIS) для Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Выполните действия в этой статье, чтобы установить SQL Server Integration Services (`mssql-server-is`) в Linux. Сведения о функции, поддерживаемые в этом выпуске служб Integration Services для Linux см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

Установка серверов интеграции SQL Server для вашей платформы:

- [Ubuntu](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="ubuntu"></a>Установка служб SSIS для Ubuntu
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
sudo apt-get remove msssql-server-is
```

## <a name="RHEL"></a>Установка служб SSIS на RHEL
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

## <a name="next-steps"></a>Следующие шаги

Выполнение пакетов служб SSIS в Linux, см. [извлечения, преобразования и загрузки данных для SQL Server в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md).

Чтобы настроить дополнительные параметры служб SSIS в Linux, в разделе [настройки SQL Server Integration Services в Linux с помощью служб ssis conf](sql-server-linux-configure-ssis.md).
