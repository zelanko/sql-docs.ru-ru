---
title: "Установка служб интеграции SQL Server в Linux | Документы Microsoft"
description: "В этом разделе описывается установка служб SQL Server Integration Services (SSIS) для Linux."
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: cd81ffd71eb78a553703fc31650a0e60a8c513aa
ms.contentlocale: ru-ru
ms.lasthandoff: 10/10/2017

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
sudo yum remove msssql-server-is
```




## <a name="run-a-package"></a>Запуск пакета
Скопируйте пакет служб SSIS на компьютере Linux. Затем можно используйте следующую команду для запуска пакета.

```bash
dtexec /F <package name> /DE <protection password>
```



## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об использовании служб SSIS в Linux для извлечения, преобразования и загрузки данных см. в разделе [извлечения, преобразования и загрузки данных для SQL Server в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md).
