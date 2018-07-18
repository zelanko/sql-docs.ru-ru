---
title: Руководство по установке для SQL Server 2017 на платформе Linux | Документация Майкрософт
description: Установка, обновление и удаление SQL Server в Linux. В этой статье описаны online, вне сети и автоматического сценария.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/06/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.openlocfilehash: bbf781d365174042f9358fd1e78a26d916f81f99
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37982814"
---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Руководство по установке для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Эта статья содержит инструкции по установке и при удалении SQL Server 2017 в Linux.

> [!TIP]
> В этом руководстве coves несколько сценариев развертывания. Если только вы ищете пошаговые инструкции по установке, перейдите к одному из кратких руководств:
> - [Краткое руководство RHEL](quickstart-install-connect-red-hat.md)
> - [Краткое руководство SLES](quickstart-install-connect-suse.md)
> - [Краткое руководство Ubuntu](quickstart-install-connect-ubuntu.md)
> - [Краткое руководство docker](quickstart-install-connect-docker.md)

Ответы на часто задаваемые вопросы см. в разделе [SQL Server на Linux часто задаваемые вопросы о](../linux/sql-server-linux-faq.md).

## <a id="supportedplatforms"></a> Поддерживаемые платформы

SQL Server 2017 поддерживается в Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) и Ubuntu. Также поддерживается как образ Docker, которая может выполняться на подсистема Docker в Linux или Docker для Windows или Mac.

| Платформа | Поддерживаемые версии | Получить
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 или 7.4 | [Получить RHEL 7.4](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | до версии 12 с пакетом обновления 2 | [Получить SLES версии 12 с пакетом обновления 2](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Получить Ubuntu 16.04](http://www.ubuntu.com/download/server)
| **Подсистема docker** | 1.8+ | [Получить Docker](http://www.docker.com/products/overview)

Корпорация Майкрософт также поддерживает развертывание и управление ими контейнеры SQL Server с помощью OpenShift и Kubernetes.

> [!NOTE]
> SQL Server протестированы и поддерживаются в Linux, перечисленные выше дистрибутивов. Если вы решили установить SQL Server в неподдерживаемой операционной системе, просмотрите **политика поддержки** раздел [политики технической поддержки для Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server) о поддержке последствия.

## <a id="system"></a> Требования к системе

SQL Server 2017 имеет следующие требования к системе для Linux:

|||
|-----|-----|
| **Память** | 2 GB |
| **Файловая система** | **XFS** или **EXT4** (других файловых систем, таких как **BTRFS**, не поддерживаются) |
| **Место на диске** | 6 ГБ |
| **Тактовая частота процессора** | С частотой 2 ГГц |
| **Процессорные ядра** | 2 ядра |
| **Тип процессора** | x64-совместимых только |

Если вы используете **сетевой файловой системы (NFS)** удаленные общие ресурсы в рабочей среде, ознакомьтесь со следующими требованиями поддержки:

- Использование NFS версии **4.2 или более поздней версии**. Более старые версии NFS не поддерживают необходимые функции, такие как fallocate и создания разреженный файл, общие для современных файловых систем.
- Найдите только **/var/opt/mssql** каталоги на подключения NFS. Другие файлы, например системные файлы SQL Server и не поддерживаются.
- Убедитесь, что NFS-клиенты использовать параметр «nolock», при подключении к удаленной общей папке.

## <a id="repositories"></a> Настройка репозиториев источника

При установке или обновлении SQL Server, вы получите последнюю версию SQL Server 2017 из настроенного репозитория Microsoft. Краткие руководства используйте **накопительное обновление (CU)** репозиторий. Но вместо этого можно настроить **GDR** репозитория. Дополнительные сведения о репозитории и их настройке см. в разделе [Настройка репозиториев для SQL Server в Linux](sql-server-linux-change-repo.md).

> [!IMPORTANT]
> Если вы ранее установили CTP-ВЕРСИЮ или версию-КАНДИДАТ SQL Server 2017, необходимо удалить репозиторий предварительной версии и зарегистрировать Общая доступность (GA) один. Дополнительные сведения см. в разделе [Настройка репозиториев для SQL Server в Linux](sql-server-linux-change-repo.md).

## <a id="platforms"></a> Установка SQL Server

Можно установить SQL Server в Linux из командной строки. Инструкции см. один из следующих кратких руководств:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустить в Docker](quickstart-install-connect-docker.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

## <a id="upgrade"></a> Обновите SQL Server

Чтобы обновить **mssql-server** пакет до последней версии, используйте один из следующих команд в зависимости от платформы:

| Платформа | Выполнение команд пакета обновления |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

Эти команды загрузить новейшие пакет и замените двоичные файлы, расположенный в `/opt/mssql/`. Созданное пользователем баз данных и системных баз данных, не подвержены этой операции.

## <a id="rollback"></a> Откат SQL Server

Для отката или на более раннюю версию SQL Server предыдущего выпуска сделайте следующее:

1. Определите номер версии для пакета SQL Server, который вы хотите понизить до. Список номеров пакета, см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

1. Возврат к предыдущей версии SQL Server. В следующих командах замените `<version_number>` с номером версии SQL Server, определенного на шаге 1.

   | Платформа | Выполнение команд пакета обновления |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> Он поддерживается только можно понизить до выпуска в той же основной версией, например SQL Server 2017.

## <a id="versioncheck"></a> Проверьте установленные версии SQL Server

Проверьте текущую версию и выпуск SQL Server в Linux, используйте следующую процедуру:

1. Если еще не установлен, установите [средств командной строки SQL Server](sql-server-linux-setup-tools.md).

1. Используйте **sqlcmd** для выполнения команды Transact-SQL, отображающий используемых SQL Server версии и выпуска.

   ```bash
   sqlcmd -S localhost -U SA -Q 'select @@VERSION'
   ```

## <a id="uninstall"></a> Удаление SQL Server

Чтобы удалить **mssql-server** пакета в Linux, используйте один из следующих команд в зависимости от платформы:

| Платформа | Выполнение команд удаления пакета |
|-----|-----|
| RHEL | `sudo yum remove mssql-server` |
| SLES | `sudo zypper remove mssql-server` |
| Ubuntu | `sudo apt-get remove mssql-server` |

После удаления пакета не приводит к удалению файлов создаваемой базы данных. Если вы хотите удалить файлы базы данных, используйте следующую команду:

```bash
sudo rm -rf /var/opt/mssql/
```

## <a id="unattended"></a> Автоматическая установка

Можно выполнить автоматическую установку следующим образом:

- Сделайте первоначального в [краткие руководства](#platforms) Чтобы зарегистрировать репозиториев и установить SQL Server.
- При запуске `mssql-conf setup`, задайте [переменные среды](sql-server-linux-configure-environment-variables.md) и использовать `-n` (без запроса) параметр.

В следующем примере настраивается Developer edition, SQL Server с **MSSQL_PID** переменной среды. Он также принимает условия лицензионного соглашения (**ACCEPT_EULA**) и задает пароль пользователя SA (**MSSQL_SA_PASSWORD**). `-n` Параметр выполняет установку, незапрошенное, где извлеченные значения конфигурации из переменных среды.

```bash
sudo MSSQL_PID=Developer ACCEPT_EULA=Y MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' /opt/mssql/bin/mssql-conf -n setup
```

Можно также создать скрипт, который выполняет другие действия. Например можно установить другие пакеты SQL Server.

Более подробный пример сценария см. следующие примеры:

- [Red Hat сценарий автоматической установки](sample-unattended-install-redhat.md)
- [SUSE сценарий автоматической установки](sample-unattended-install-suse.md)
- [Ubuntu сценарий автоматической установки](sample-unattended-install-ubuntu.md)

## <a id="offline"></a> Автономная установка

Если компьютер Linux не имеет доступа к онлайн-хранилищам используется в [краткие](#platforms), можно загрузить файлы пакетов напрямую. Эти пакеты находятся в хранилище Microsoft [ https://packages.microsoft.com ](https://packages.microsoft.com).

> [!TIP]
> Если вы успешно установили при выполнении действий в краткие руководства, вы не обязательно должны загружать или вручную устанавливать пакеты SQL Server. Этот раздел предназначен только для автономного сценария.

1. **Скачайте пакет ядра СУБД для вашей платформы**. Найдите ссылки для загрузки пакета в разделе сведений о пакете [заметки о выпуске](sql-server-linux-release-notes.md).

1. **Перемещение скачанного пакета на компьютер Linux**. Если вы использовали другую машину, чтобы скачать пакеты, один из способов перемещения пакетов на компьютер Linux, — с **scp** команды.

1. **Установите пакет ядра СУБД**. Используйте один из следующих команд в зависимости от платформы. Замените точное имя, загруженный в этом примере имя файла пакета.

   | Платформа | Команда установки пакета |
   |-----|-----|
   | RHEL | `sudo yum localinstall mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `sudo zypper install mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `sudo dpkg -i mssql-server_versionnumber_amd64.deb` |

    > [!NOTE]
    > Вы также можете установить пакеты RPM (RHEL и SLES) с `rpm -ivh` команда, но команды в предыдущей таблице автоматически установить зависимости благодарственное из доступных репозиториев.

1. **Разрешить отсутствующие зависимости**: возможно, отсутствуют зависимости на этом этапе. В противном случае этот шаг можно пропустить. В Ubuntu, если у вас есть доступ для утвержденных репозиториев, содержащий эти зависимости, самым простым решением является использование `apt-get -f install` команды. Эта команда также завершается установка SQL Server. Чтобы вручную проверить зависимости, используйте следующие команды:

   | Платформа | Команда list зависимостей |
   |-----|-----|
   | RHEL | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `dpkg -I mssql-server_versionnumber_amd64.deb` |

   После устранения отсутствующие зависимости, попытайтесь установить пакет mssql-server, еще раз.

1. **Завершения работы программы установки SQL Server**. Используйте **mssql-conf** для завершения работы программы установки SQL Server:

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

## <a name="optional-sql-server-features"></a>Дополнительные возможности SQL Server

После установки можно также установить и включить дополнительные возможности SQL Server.

- [Программы командной строки SQL Server](sql-server-linux-setup-tools.md)
- [Агент SQL Server](sql-server-linux-setup-sql-agent.md)
- [Полнотекстовый поиск SQL Server](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services (Ubuntu)](sql-server-linux-setup-ssis.md)

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

> [!TIP]
> Ответы на часто задаваемые вопросы см. в разделе [SQL Server на Linux часто задаваемые вопросы о](sql-server-linux-faq.md).
