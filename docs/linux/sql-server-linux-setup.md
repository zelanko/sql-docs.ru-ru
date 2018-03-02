---
title: "Установка SQL Server 2017 г. для Linux | Документы Microsoft"
description: "Установка, обновление и удаление SQL Server в Linux. Online, вне сети и автоматической сценарии рассматриваются в данной статье."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/21/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.workload: Active
ms.openlocfilehash: c686e97bd3d06b99fcbb847c23ac7e174e85dd6b
ms.sourcegitcommit: f0c5e37c138be5fb2cbb93e9f2ded307665b54ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/24/2018
---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Руководство по установке для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается установка, обновление и удаление 2017 г. SQL Server в Linux. В Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) и Ubuntu поддерживается 2017 г. SQL Server. Она также доступна как образ Docker, который можно запустить на подсистема Docker в Linux или Docker для Windows или Mac.

> [!TIP]
> Чтобы быстро приступить к работе, перейти к одному из примеры использования для [RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), [Ubuntu](quickstart-install-connect-ubuntu.md), или [Docker](quickstart-install-connect-docker.md).

Ответы на часто задаваемые вопросы см. в разделе [SQL Server в Linux часто задаваемые вопросы о](../linux/sql-server-linux-faq.md).

## <a id="supportedplatforms"></a> Поддерживаемые платформы

2017 г. SQL Server поддерживается на следующих платформах Linux:

| Платформа | Поддерживаемые версии | Получить
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 или 7.4 | [Получить RHEL 7.4](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | v12 SP2 | [Получить SP2 SLES версии 12](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Получить Ubuntu 16.04](http://www.ubuntu.com/download/server)
| **Подсистема docker** | 1.8+ | [Получить Docker](http://www.docker.com/products/overview)

> [!NOTE]
> Иногда имеется возможность установить и запустить SQL Server на других платформах Linux тесно связаны, но SQL Server только протестированы и поддерживаются на платформах, перечисленные в предыдущей таблице.

Корпорация Майкрософт поддерживает развертывание и Управление контейнерами SQL Server с помощью OpenShift и Kubernetes.

Последние политика поддержки для SQL Server 2017 г. в разделе [политика технической поддержки для Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a id="system"></a> Требования к системе

2017 г. SQL Server имеет следующие требования к системе для Linux:

|||
|-----|-----|
| **Память** | 2 GB |
| **Файловая система** | **XFS** или **EXT4** (других файловых систем, таких как **BTRFS**, не поддерживаются) |
| **Место на диске** | 6 ГБ |
| **Быстродействие процессора** | 2 ГГц |
| **Процессорных ядер** | 2 ядра |
| **Тип процессора** | x64 совместим только |

Если вы используете **сетевой файловой системы (NFS)** удаленные общие ресурсы в рабочей среде, ознакомьтесь со следующими требованиями поддержки:

- Использование NFS версии **4.2 или более поздней версии**. NFS более ранних версий не поддерживают необходимые компоненты, такие как fallocate и создания разреженный файл, общие для современных файловых систем.
- Найдите только **/var/opt/mssql** каталогов на подключения NFS. Другие файлы, такие как системные файлы SQL Server и не поддерживаются.
- Убедитесь, что клиенты NFS использовать параметр «nolock» при подключении к удаленной общей папке.

## <a id="platforms"></a> Установка SQL Server

SQL Server в Linux можно установить из командной строки. Соответствующие инструкции см. следующие примеры использования:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-docker.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

## <a id="repositories"></a> Настройка исходных репозиториев

При установке или обновлении SQL Server, можно получить последнюю версию 2017 г. SQL Server из репозитория настроенных Microsoft. Используйте примеры использования **накопительное обновление (CU)** репозитория. Но вместо этого можно настроить **GDR** репозитория. Дополнительные сведения о репозитории и их настройке см. в разделе [настроить репозитории для SQL Server в Linux](sql-server-linux-change-repo.md).

> [!IMPORTANT]
> Если ранее была установлена CTP-версии или версию-КАНДИДАТ 2017 г. SQL Server, необходимо удалить предварительный просмотр репозитория и зарегистрировать Общая доступность (GA) один. Дополнительные сведения см. в разделе [настроить репозитории для SQL Server в Linux](sql-server-linux-change-repo.md).

## <a id="upgrade"></a> Обновление SQL Server

Чтобы обновить **mssql server** пакета до последней версии, используйте один из приведенных ниже команд, в зависимости от используемой платформы:

| Платформа | Выполнение команд пакета обновления |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

Эти команды загрузить последние пакет и замените двоичные файлы, расположенные в группе `/opt/mssql/`. Созданное пользователем базы данных и системных баз данных не зависит от этой операции.

## <a id="rollback"></a> Откат SQL Server

Для отката или возврат к предыдущей версии SQL Server в предыдущем выпуске выполните следующие действия:

1. Укажите номер версии для пакета SQL Server, который вы хотите перейти на. Список номеров пакета см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

1. Перейти к предыдущей версии SQL Server. В приведенных ниже команд, замените `<version_number>` с номером версии SQL Server, определенный на шаге 1.

   | Платформа | Выполнение команд пакета обновления |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> Она поддерживается только может понижаться до выпуска в пределах той же основной версии, например 2017 г. SQL Server.

## <a id="versioncheck"></a> Проверьте установленную версию SQL Server

Чтобы проверить текущую версию и выпуск SQL Server в Linux, используйте следующую процедуру:

1. Если еще не установлен, установите [средства командной строки SQL Server](sql-server-linux-setup-tools.md).

1. Используйте **sqlcmd** для выполнения команды Transact-SQL, отображающий SQL Server версии и выпуска.

   ```bash
   sqlcmd -S localhost -U SA -Q 'select @@VERSION'
   ```

## <a id="uninstall"></a> Удаление SQL Server

Чтобы удалить **mssql server** пакета в Linux, используйте один из приведенных ниже команд, в зависимости от используемой платформы:

| Платформа | Команды удаления пакета |
|-----|-----|
| RHEL | `sudo yum remove mssql-server` |
| SLES | `sudo zypper remove mssql-server` |
| Ubuntu | `sudo apt-get remove mssql-server` |

После удаления пакета не приводит к удалению файлов созданной базе данных. Если вы хотите удалить файлы базы данных, используйте следующую команду:

```bash
sudo rm -rf /var/opt/mssql/
```

## <a id="unattended"></a> Автоматическая установка

Можно выполнить автоматическую установку следующим образом:

- Необходимо выполнить начального действия в [краткие руководства](#platforms) репозиториями регистрация и установка SQL Server.
- При запуске `mssql-conf setup`, задайте [переменных среды](sql-server-linux-configure-environment-variables.md) и использовать `-n` (без запроса) параметра.

В следующем примере настраивается Developer edition, SQL Server с **MSSQL_PID** переменной среды. Он также принимает условия лицензионного соглашения (**ACCEPT_EULA**) и задает пароль пользователя SA (**MSSQL_SA_PASSWORD**). `-n` Параметр выполняет unprompted установку, где значения конфигурации извлекаются из переменных среды.

```bash
sudo MSSQL_PID=Developer ACCEPT_EULA=Y MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' /opt/mssql/bin/mssql-conf -n setup
```

Можно также создать скрипт, который выполняет другие действия. Например можно установить другие пакеты SQL Server.

Более подробный пример сценария см. следующие примеры:

- [Red Hat сценарий автоматической установки](sample-unattended-install-redhat.md)
- [SUSE сценарий автоматической установки](sample-unattended-install-suse.md)
- [Ubuntu сценарий автоматической установки](sample-unattended-install-ubuntu.md)

## <a id="offline"></a> Автономную установку

Если компьютер Linux не имеет доступа к сети хранилища, используемых в [краткие](#platforms), можно непосредственно загрузить файлы пакета. Эти пакеты находятся в хранилище Майкрософт по адресу [https://packages.microsoft.com](https://packages.microsoft.com).

> [!TIP]
> После успешной установки шаги, указанные в краткие руководства необязательно для загрузки или вручную установить пакеты SQL Server. Этот раздел предназначен только для сценария автономной работы.

1. **Загрузите пакет ядра базы данных для вашей платформы**. Найти ссылки для загрузки пакета в разделе сведений пакета [заметки о выпуске](sql-server-linux-release-notes.md).

1. **Переместить загруженного пакета на компьютер Linux**. Если используется другой компьютер для загрузки пакетов, один из способов перемещения пакетов на компьютер Linux связана с **scp** команды.

1. **Установить пакет ядра базы данных**. Используйте одну из следующих команд в зависимости от используемой платформы. Замените точное имя, загруженный в этом примере имя файла пакета.

   | Платформа | Команда удаления пакета |
   |-----|-----|
   | RHEL | `sudo yum localinstall mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `sudo zypper install mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `sudo dpkg -i mssql-server_versionnumber_amd64.deb` |

    > [!NOTE]
    > Можно также установить пакеты RPM (RHEL и SLES) с `rpm -ivh` команда, но команды в предыдущей таблице зависимости автоматически устанавливать доступные утвержденный репозиториев.

1. **Разрешить отсутствующие зависимости**: возможно, на этом этапе отсутствующих зависимостей. В противном случае этот шаг можно пропустить. В Ubuntu — команду, если у вас есть доступ для утвержденных репозиториев, содержащий эти зависимости простейшим решением является использование `apt-get -f install` команды. Эта команда также завершается установка SQL Server. Чтобы вручную проверить зависимости, используйте следующие команды:

   | Платформа | Команда list зависимости |
   |-----|-----|
   | RHEL | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `dpkg -I mssql-server_versionnumber_amd64.deb` |

   После устранения отсутствующие зависимости, попытайтесь установить mssql сервера пакета еще раз.

1. **Завершите установку SQL Server**. Используйте **mssql conf** для завершения работы программы установки SQL Server:

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

## <a name="next-steps"></a>Следующие шаги

После установки можно также установить другие дополнительные пакеты SQL Server.

- [Средства командной строки SQL Server](sql-server-linux-setup-tools.md)
- [Агент SQL Server](sql-server-linux-setup-sql-agent.md)
- [Полнотекстовый поиск SQL Server](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services (Ubuntu)](sql-server-linux-setup-ssis.md)

Подключитесь к экземпляру SQL Server, чтобы начать создание и управление базами данных. Чтобы приступить к работе, см. Примеры использования:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)
