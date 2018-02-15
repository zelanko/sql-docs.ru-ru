---
title: "Настройка хранилища для SQL Server для Linux | Документы Microsoft"
description: "Проверить и настроить исходных репозиториев для 2017 г. SQL Server в Linux. Исходный репозиторий влияет на версию SQL Server, который применяется во время установки и обновления."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/07/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Active
ms.openlocfilehash: bf9a129df2e76f0eafc6992fc0d81f1a397df963
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Настройка хранилища для установки и обновления SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описываются способы настройки на правильный репозиторий для установки SQL Server 2017 г. и обновления в Linux.

> [!IMPORTANT]
> Если ранее была установлена CTP-версии или версию-КАНДИДАТ 2017 г. SQL Server, необходимо использовать шаги в этой статье регистрация репозитория Общая доступность (GA) и обновлением или переустановкой адаптера. Предварительных выпусков 2017 г. SQL Server не поддерживаются и истекает.

## <a id="repositories"></a>Репозитории

При установке SQL Server в Linux, необходимо настроить репозиторий Майкрософт. Этот репозиторий используется для получения пакета ядра базы данных, **mssql сервера**и связанные с ним пакетов SQL Server. В настоящее время существует три основных репозиториев.

| Хранилище | Название | Описание |
|---|---|---|
| **Предварительный просмотр** | **mssql-server** | Просмотр репозитория для версий SQL Server CTP-версии и версии-Кандидата. Этот репозиторий не поддерживается для 2017 г. SQL Server. |
| **CU** | **mssql-server-2017** | База данных SQL Server 2017 г. накопительное обновление (CU). |
| **GDR** | **mssql-server-2017-gdr** | Репозиторий только важные обновления GDR 2017 г. SQL Server. |

## <a id="cuversusgdr"></a> Накопительный пакет обновления и GDR

Это важно отметить, что существует два основных типа хранилища для каждого распределения:

- **Накопительный пакет обновления (CU)**: репозиторий накопительное обновление (CU) содержит пакеты для базовой версии SQL Server и исправления или улучшения версии. Накопительные пакеты обновления относятся только к версии, например 2017 г. SQL Server. Их появления в обычных ритме.

- **GDR**: GDR репозитория пакетов для базовой версии SQL Server и только важные исправления и обновления для системы безопасности содержит версии. Эти обновления также добавляются в следующий выпуск CU.

Каждое CU и GDR содержит полный пакет SQL Server и все последующие обновления для этого репозитория. Обновление с версии GDR на текущую версию поддерживается изменение настроенного хранилища SQL Server. Вы также можете [понизить](sql-server-linux-setup.md#rollback) для любого из выпусков в ваш основной номер версии (например: 2017 г.).

> [!NOTE]
> Можно обновить с версии GDR на CU выпуска в любое время, изменив репозиториев. Обновление с накопительным пакетом обновления версии GDR не поддерживается. 

## <a id="configure"></a> Настройка репозитория

В следующих разделах описаны как проверить и настроить репозиторий для следующих поддерживаемых платформ:

- [Red Hat Enterprise Server](#rhel)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#sles)

## <a id="rhel"></a> Настройка RHEL репозитории
Настройка хранилища в Red Hat Enterprise Server (RHEL), выполните следующие действия.

### <a name="check-for-previously-configured-repositories-rhel"></a>Проверьте ранее настроенные репозиториев (RHEL)
Прежде всего проверьте, является ли вы уже зарегистрировали репозитория SQL Server.

1. Просматривать файлы в **/etc/yum.repos.d** каталога с помощью следующей команды:

   ```bash
   sudo ls /etc/yum.repos.d
   ```

2. Найдите файл, который настраивает каталог SQL Server, такие как **mssql server.repo**.

3. Выводит содержимое файла.

   ```bash
   sudo cat /etc/yum.repos.d/mssql-server.repo
   ```

4. **Имя** свойство является настроенного репозитория. Можно идентифицировать его с таблицей в [репозиториев](#repositories) этой статьи.

### <a name="remove-old-repository-rhel"></a>Удалите старое хранилище (RHEL)
При необходимости удалите старое хранилище, с помощью следующей команды.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Эта команда предполагает, что файл, указанный в предыдущем разделе была с именем **mssql server.repo**.

### <a name="configure-new-repository-rhel"></a>Настройте новый репозиторий (RHEL)
Настройте новый репозиторий для установки SQL Server и обновления. Используйте одну из следующих команд для настройки репозитория по своему усмотрению.

| Хранилище | Command |
|---|---|
| **CU** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

## <a id="sles"></a> Настройка SLES репозитории
Выполните следующие действия для настройки на SLES репозиториев.

### <a name="check-for-previously-configured-repositories-sles"></a>Проверьте ранее настроенные репозиториев (SLES)
Прежде всего проверьте, является ли вы уже зарегистрировали репозитория SQL Server.

1. Используйте **zypper сведения** для получения сведений о любой ранее настроенного репозитория.

   ```bash
   sudo zypper info mssql-server
   ```

2. **Репозитория** свойство является настроенного репозитория. Можно идентифицировать его с таблицей в [репозиториев](#repositories) этой статьи.

### <a name="remove-old-repository-sles"></a>Удалите старое хранилище (SLES)
При необходимости удалите старое хранилище. Используйте одну из следующих команд в зависимости от типа ранее настроенного репозитория.

| Хранилище | Команда для удаления |
|---|---|
| **Предварительный просмотр** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

### <a name="configure-new-repository-sles"></a>Настройте новый репозиторий (SLES)
Настройте новый репозиторий для установки SQL Server и обновления. Используйте одну из следующих команд для настройки репозитория по своему усмотрению.

| Хранилище | Command |
|---|---|
| **CU** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

## <a id="ubuntu"></a> Настройка репозиториев Ubuntu
Выполните следующие действия для настройки на Ubuntu репозиториев.

### <a name="check-for-previously-configured-repositories-ubuntu"></a>Проверьте ранее настроенные репозиториев (Ubuntu)
Прежде всего проверьте, является ли вы уже зарегистрировали репозитория SQL Server.

1. Просмотр содержимого **/etc/apt/sources.list** файла.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Проверьте URL-адреса для сервера mssql пакета. Можно идентифицировать его с таблицей в [репозиториев](#repositories) этой статьи.

### <a name="remove-old-repository-ubuntu"></a>Удалите старое хранилище (Ubuntu)
При необходимости удалите старое хранилище. Используйте одну из следующих команд в зависимости от типа ранее настроенного репозитория.

| Хранилище | Команда для удаления |
|---|---|
| **Предварительный просмотр** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` 
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

### <a name="configure-new-repository-ubuntu"></a>Настройте новый репозиторий (Ubuntu)
Настройте новый репозиторий для установки SQL Server и обновления.

1. Импорт ключей GPG общедоступный репозиторий.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Используйте одну из следующих команд для настройки репозитория по своему усмотрению.

   | Хранилище | Command |
   |---|---|
   | **CU** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. Запустите **apt get обновления**.

   ```bash
   sudo apt-get update
   ```

## <a name="next-steps"></a>Следующие шаги

После того как настроен правильный репозиторий, можно продолжить [установить](sql-server-linux-setup.md#platforms) или [обновление](sql-server-linux-setup.md#upgrade) SQL Server и все связанные пакеты из нового репозитория.

> [!IMPORTANT]
> На этом этапе, если вы решили использовать одной из статей установки, такие как [краткие руководства](sql-server-linux-setup.md#platforms), помните, что вы уже настроили целевой репозиторий. В учебниках по не нужно повторять этот шаг. Это особенно важно, если настроить хранилище GDR, так как примеры использования использование CU репозитория.

> [!IMPORTANT]
> Любая версия SQL Server 2017 г. до CTP-версии 2.1, необходимо обновить до крайней 2.1 перед обновлением до общедоступной. Другим вариантом является резервное копирование баз данных, удалите предыдущую версию и затем выполнить установку из Общедоступной версии.

Дополнительные сведения об установке 2017 г. SQL Server в Linux см. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).
