---
title: Настройка репозиториев Linux для SQL Server 2017 и 2019 г. | Документация Майкрософт
description: Проверьте и настройте репозиториях для SQL Server 2019 и SQL Server 2017 в Linux. Исходный репозиторий влияет на версию SQL Server, который применяется во время установки и обновления.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/14/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 5aee3ea6a744c15afce8055d153959b8db9ac66d
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713216"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Настройка репозиториев для установки и обновления SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описываются способы настройки на правильный репозиторий для SQL Server 2017 и SQL Server 2019 установок и обновлений на платформе Linux.

> [!TIP]
> SQL Server 2019 CTP 2.0 уже доступен! Чтобы опробовать, воспользуйтесь этой статьей для настройки нового **mssql-server-preview** репозитория. Установите, следуя инструкциям в [руководство по установке](sql-server-linux-setup.md).

## <a id="repositories"></a> Репозитории

При установке SQL Server в Linux, необходимо настроить репозиторий Microsoft. Этот репозиторий используется для получения пакет ядра СУБД, **mssql-server**и связанные пакеты SQL Server. В настоящее время существует три основных репозиториев:

| Хранилище | Имя | Описание |
|---|---|---|
| **Предварительная версия (2017 г.)** | **mssql-server** | Репозиторий SQL Server 2017 CTP и версии-Кандидата (неподдерживаемые). |
| **Предварительная версия (2019 г.)** | **MSSQL-server-preview** | Версия-Кандидат и CTP-версии SQL Server 2019 репозиторий. |
| **CU** | **mssql-server-2017** | База данных SQL Server 2017 накопительное обновление (CU). |
| **GDR** | **mssql-server-2017-gdr** | SQL Server 2017 GDR репозиторий только критические обновления. |

## <a id="cuversusgdr"></a> Накопительный пакет обновления и GDR

Важно отметить, что два основных типа хранилища для каждого распределения:

- **Накопительным обновлением (CU)**: репозиторий накопительное обновление (CU) содержит пакеты для базового выпуска SQL Server и исправления или улучшения с момента выхода этого выпуска. Накопительные пакеты обновления применяются к окончательной версии, такие как SQL Server 2017. Они выпускаются регулярно выпускать.

- **GDR**: GDR репозиторий содержит пакеты базовый выпуск SQL Server и только критические исправления и обновления для системы безопасности с момента выхода этого выпуска. Эти обновления также добавляются в следующий выпуск CU.

Каждый выпуск в Эквиваленте и GDR содержит полный пакет SQL Server и все выпущенные ранее обновления для этого репозитория. Обновление с версии GDR для накопительное обновление выпуска поддерживается изменение настроенного хранилища SQL Server. Вы также можете [понизить](sql-server-linux-setup.md#rollback) до любого выпуска в ваш основной номер версии (например: 2017).

> [!NOTE]
> Можно обновить с версии GDR CU выпуска в любое время, изменив репозиториев. Обновление с накопительным пакетом обновления версии до версии GDR не поддерживается. 

## <a id="configure"></a> Настройка репозитория

В следующих разделах рассматривается для проверки и настроить репозиторий для следующих поддерживаемых платформ:

- [Red Hat Enterprise Server](#rhel)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#sles)

## <a id="rhel"></a> Настройка репозиториев RHEL
Следуйте инструкциям ниже для настройки репозиториев на Red Hat Enterprise Server (RHEL).

### <a name="check-for-previously-configured-repositories-rhel"></a>Поиск ранее настроенных репозиториев (RHEL)
Сначала проверьте ли вы уже зарегистрировали репозиторию SQL Server.

1. Просмотреть файлы в **/etc/yum.repos.d** каталог с помощью следующей команды:

   ```bash
   sudo ls /etc/yum.repos.d
   ```

2. Найдите файл, который настраивает каталог SQL Server, такие как **mssql-server.repo**.

3. Выводит содержимое файла.

   ```bash
   sudo cat /etc/yum.repos.d/mssql-server.repo
   ```

4. **Имя** свойство является настроенного репозитория. Это можно определить с помощью таблицы в [репозиториев](#repositories) этой статьи.

### <a name="remove-old-repository-rhel"></a>Удалить старые репозитории (RHEL)
При необходимости удалите старое хранилище, выполнив следующую команду.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Эта команда предполагает, что файл, указанный в предыдущем разделе назывался **mssql-server.repo**.

### <a name="configure-new-repository-rhel"></a>Настройка нового репозитория (RHEL)
Настройте новый репозиторий для установки SQL Server и обновления. Используйте один из следующих команд по настройке репозитория по своему усмотрению.

| Хранилище | Версия | Command |
|---|---|---|
| **Предварительная версия (2019 г.)** | 2019 г. | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

## <a id="sles"></a> Настройка репозиториев SLES
Следуйте инструкциям ниже, чтобы настроить репозитории на SLES.

### <a name="check-for-previously-configured-repositories-sles"></a>Поиск ранее настроенных репозиториев (SLES)
Сначала проверьте ли вы уже зарегистрировали репозиторию SQL Server.

1. Используйте **zypper info** для получения сведений о любой ранее настроенного репозитория.

   ```bash
   sudo zypper info mssql-server
   ```

2. **Репозитория** свойство является настроенного репозитория. Это можно определить с помощью таблицы в [репозиториев](#repositories) этой статьи.

### <a name="remove-old-repository-sles"></a>Удалить старые репозитории (SLES)
При необходимости удалите старое хранилище. Используйте один из приведенных ниже команд, в зависимости от типа ранее настроенного репозитория.

| Хранилище | Команда для удаления |
|---|---|
| **Предварительная версия (2017 г.)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **Предварительная версия (2019 г.)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-preview'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

### <a name="configure-new-repository-sles"></a>Настройка нового репозитория (SLES)
Настройте новый репозиторий для установки SQL Server и обновления. Используйте один из следующих команд по настройке репозитория по своему усмотрению.

| Хранилище | Версия | Command |
|---|---|---|
| **Предварительная версия (2019 г.)** | 2019 г. | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

## <a id="ubuntu"></a> Настройка репозиториев Ubuntu
Следуйте инструкциям ниже для настройки репозиториев на Ubuntu.

### <a name="check-for-previously-configured-repositories-ubuntu"></a>Поиск ранее настроенных репозиториев (Ubuntu)
Сначала проверьте ли вы уже зарегистрировали репозиторию SQL Server.

1. Просмотреть содержимое **/etc/apt/sources.list** файла.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Проверьте URL-адрес пакета mssql-server. Это можно определить с помощью таблицы в [репозиториев](#repositories) этой статьи.

### <a name="remove-old-repository-ubuntu"></a>Удалить старые репозитории (Ubuntu)
При необходимости удалите старое хранилище. Используйте один из приведенных ниже команд, в зависимости от типа ранее настроенного репозитория.

| Хранилище | Команда для удаления |
|---|---|
| **Предварительная версия (2017 г.)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |
| **Предварительная версия (2019 г.)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview xenial main'` |
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

### <a name="configure-new-repository-ubuntu"></a>Настройка нового репозитория (Ubuntu)
Настройте новый репозиторий для установки SQL Server и обновления.

1. Импорт общедоступного репозитория ключей GPG.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Используйте один из следующих команд по настройке репозитория по своему усмотрению.

   | Хранилище | Версия | Command |
   |---|---|---|
   | **Предварительная версия (2019 г.)** | 2019 г. | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"` |
   | **CU** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. Запустите **apt-get обновления**.

   ```bash
   sudo apt-get update
   ```

## <a name="next-steps"></a>Следующие шаги

После того как настроен правильный репозиторий, можно перейти к [установить](sql-server-linux-setup.md#platforms) или [обновление](sql-server-linux-setup.md#upgrade) SQL Server и все связанные пакеты из нового репозитория.

> [!IMPORTANT]
> На этом этапе, если вы решили использовать одну из статей установки, такие как [краткие руководства](sql-server-linux-setup.md#platforms), помните, что вы уже настроили целевого репозитория. Не Повторяйте этот шаг в учебниках. Это особенно важно, если настроить хранилище GDR, так как краткие руководства используйте накопительное обновление репозитория.

Дополнительные сведения об установке SQL Server 2017 в Linux см. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).