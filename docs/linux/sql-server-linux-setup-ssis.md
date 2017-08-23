---
title: "Установка служб интеграции SQL Server в Linux | Документы Microsoft"
description: "В этом разделе описывается установка служб интеграции SQL Server в Linux."
author: leolimsft
ms.author: lle
manager: craigg
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: integration-services
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c3943870ec10b8430ac4819398908c5459a8b03c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Установка SQL Server Integration Services (SSIS) для Linux


Выполните действия в этой статье, чтобы установить SQL Server Integration Services (`mssql-server-is`) в Linux. Сведения о функции, поддерживаемые в этом выпуске служб Integration Services для Linux см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

Установка серверов интеграции SQL Server для вашей платформы:

- [Ubuntu](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)



## <a name="ubuntu"></a>Установка служб SSIS для Ubuntu
Чтобы установить `mssql-server-is` пакет в Ubuntu, выполните следующие действия:


1.  Импорт ключей GPG общедоступный репозиторий.

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add –
    ```


2.  Регистрация в Microsoft SQL Server Ubuntu репозиторий.

    ```bash
    curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server.list | sudo tee /etc/apt/sources.list.d/mssql-server.list
    ```


3.  Выполните следующие команды для установки SQL Server Integration Services.

    ```bash
    sudo apt-get update
    sudo apt-get install -y mssql-server-is
    ```


4.  После установки служб Integration Services, запустите `ssis-conf`.

    ```bash
    sudo /opt/ssis/bin/ssis-conf setup
    ```


5.  После завершения конфигурации задайте путь.

    ```bash
    export PATH=/opt/ssis/bin:$PATH
    ```


Если у вас уже есть `mssql-server-is` установлены, можно обновить до последней версии с помощью следующей команды:

```bash
sudo apt-get install mssql-server-is
```


Чтобы удалить `mssql-server-is`, можно запустить следующую команду:
```bash
sudo apt-get remove msssql-server-is
```



## <a name="RHEL"></a>Установка служб SSIS на RHEL
Чтобы установить `mssql-server-is` пакет в RHEL, выполните следующие действия:


1.  Перейдите в режим суперпользователя.

    ```bash
    sudo su
    ```


2.  Загрузите файл конфигурации Microsoft SQL Server Red Hat репозитория.

    ```bash
    curl https://packages.microsoft.com/config/rhel/7/mssql-server.repo > /etc/yum.repos.d/mssql-server.repo
    ```


3.  Выход из режима суперпользователя.

    ```bash
    exit
    ```


4.  Выполните следующие команды для установки SQL Server Integration Services.

    ```bash
    sudo yum install -y mssql-server-is
    ```


5.  После установки, выполните команду `ssis-conf`.

    ```bash
    sudo /opt/ssis/bin/ssis-conf setup
    ```


6.  После завершения конфигурации задайте путь.

    ```bash
    export PATH=/opt/ssis/bin:$PATH
    ```


Если у вас уже есть `mssql-server-is` установлены, можно обновить до последней версии с помощью следующей команды:

```bash
sudo yum update mssql-server-is
```


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
