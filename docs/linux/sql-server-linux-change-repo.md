---
title: Настройка репозиториев Linux для SQL Server 2017 и 2019 г. | Документация Майкрософт
description: Проверьте и настройте репозиториях для SQL Server 2019 и SQL Server 2017 в Linux. Исходный репозиторий влияет на версию SQL Server, который применяется во время установки и обновления.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/11/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
zone_pivot_groups: ld2-linux-distribution
ms.openlocfilehash: 5e21110eb8a24c736b08833d10b509b5494adc48
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713334"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Настройка репозиториев для установки и обновления SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

::: zone pivot="ld2-rhel"
В этой статье описываются способы настройки на правильный репозиторий для SQL Server 2017 и SQL Server 2019 установок и обновлений на платформе Linux. В верхней, находится выбранная **Red Hat (RHEL)** .
::: zone-end

::: zone pivot="ld2-sles"
В этой статье описываются способы настройки на правильный репозиторий для SQL Server 2017 и SQL Server 2019 установок и обновлений на платформе Linux. В верхней, находится выбранная **SUSE (SLES)** .
::: zone-end

::: zone pivot="ld2-ubuntu"
В этой статье описываются способы настройки на правильный репозиторий для SQL Server 2017 и SQL Server 2019 установок и обновлений на платформе Linux. В верхней, находится выбранная **Ubuntu**.
::: zone-end

> [!TIP]
> Предварительная версия SQL Server 2019 уже доступен! Чтобы опробовать, воспользуйтесь этой статьей для настройки нового **mssql-server-preview** репозитория. Установите, следуя инструкциям в [руководство по установке](sql-server-linux-setup.md).

## <a id="repositories"></a> Репозитории

При установке SQL Server в Linux, необходимо настроить репозиторий Microsoft. Этот репозиторий используется для получения пакет ядра СУБД, **mssql-server**и связанные пакеты SQL Server. В настоящее время существует три основных репозиториев:

| Хранилище | Имя | Описание |
|---|---|---|
| **Предварительная версия (2017 г.)** | **mssql-server** | Репозиторий SQL Server 2017 CTP и версии-Кандидата (неподдерживаемые). |
| **Предварительная версия (2019 г.)** | **mssql-server-preview** | SQL Server 2019 предварительной версии и версии-КАНДИДАТА репозитория. |
| **CU** | **mssql-server-2017** | База данных SQL Server 2017 накопительное обновление (CU). |
| **GDR** | **mssql-server-2017-gdr** | SQL Server 2017 GDR репозиторий только критические обновления. |

## <a id="cuversusgdr"></a> Накопительный пакет обновления и GDR

Важно отметить, что два основных типа хранилища для каждого распределения:

- **Накопительные пакеты обновления (CU)** : Накопительное обновление (CU) хранилища содержит пакеты для базового выпуска SQL Server и исправления или улучшения с момента выхода этого выпуска. Накопительные пакеты обновления применяются к окончательной версии, такие как SQL Server 2017. Они выпускаются регулярно выпускать.

- **GDR**: GDR репозитория содержит пакеты базовый выпуск SQL Server и только критические исправления и обновления для системы безопасности с момента выхода этого выпуска. Эти обновления также добавляются в следующий выпуск CU.

Каждый выпуск в Эквиваленте и GDR содержит полный пакет SQL Server и все выпущенные ранее обновления для этого репозитория. Обновление с версии GDR для накопительное обновление выпуска поддерживается изменение настроенного хранилища SQL Server. Вы также можете [понизить](sql-server-linux-setup.md#rollback) до любого выпуска в ваш основной номер версии (например: 2017).

> [!NOTE]
> Можно обновить с версии GDR CU выпуска в любое время, изменив репозиториев. Обновление с накопительным пакетом обновления версии до версии GDR не поддерживается.

## <a name="configure-repositories"></a>Настройка репозиториев

::: zone pivot="ld2-rhel"
Следуйте инструкциям в следующих разделах для настройки репозиториев на Red Hat Enterprise Server (RHEL).
::: zone-end

::: zone pivot="ld2-sles"
Следуйте инструкциям в следующих разделах для настройки репозиториев на SUSE Linux Enterprise Server (SLES).
::: zone-end

::: zone pivot="ld2-ubuntu"
Следуйте инструкциям в следующих разделах для настройки репозиториев на Ubuntu.
::: zone-end

## <a name="check-for-previously-configured-repositories"></a>Проверьте ранее настроенные репозиториев

<!--RHEL-->
::: zone pivot="ld2-rhel"
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

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
Сначала проверьте ли вы уже зарегистрировали репозиторию SQL Server.

1. Используйте **zypper info** для получения сведений о любой ранее настроенного репозитория.

   ```bash
   sudo zypper info mssql-server
   ```

2. **Репозитория** свойство является настроенного репозитория. Это можно определить с помощью таблицы в [репозиториев](#repositories) этой статьи.

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
Сначала проверьте ли вы уже зарегистрировали репозиторию SQL Server.

1. Просмотреть содержимое **/etc/apt/sources.list** файла.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Проверьте URL-адрес пакета mssql-server. Это можно определить с помощью таблицы в [репозиториев](#repositories) этой статьи.

::: zone-end

## <a name="remove-old-repository"></a>Удалить старые репозитории

<!--RHEL-->
::: zone pivot="ld2-rhel"
При необходимости удалите старое хранилище, выполнив следующую команду.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Эта команда предполагает, что файл, указанный в предыдущем разделе назывался **mssql-server.repo**.

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
При необходимости удалите старое хранилище. Используйте один из приведенных ниже команд, в зависимости от типа ранее настроенного репозитория.

| Хранилище | Команда для удаления |
|---|---|
| **Предварительная версия (2017 г.)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **Предварительная версия (2019 г.)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-preview'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
При необходимости удалите старое хранилище. Используйте один из приведенных ниже команд, в зависимости от типа ранее настроенного репозитория.

| Хранилище | Команда для удаления |
|---|---|
| **Предварительная версия (2017 г.)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |
| **Предварительная версия (2019 г.)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview xenial main'` |
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

::: zone-end

## <a name="configure-new-repository"></a>Настройка нового репозитория

<!--RHEL-->
::: zone pivot="ld2-rhel"
Настройте новый репозиторий для установки SQL Server и обновления. Используйте один из следующих команд по настройке репозитория по своему усмотрению.

| Хранилище | Version | Command |
|---|---|---|
| **Предварительная версия (2019 г.)** | 2019 г. | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
Настройте новый репозиторий для установки SQL Server и обновления. Используйте один из следующих команд по настройке репозитория по своему усмотрению.

| Хранилище | Version | Command |
|---|---|---|
| **Предварительная версия (2019 г.)** | 2019 г. | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
Настройте новый репозиторий для установки SQL Server и обновления.

1. Импорт общедоступного репозитория ключей GPG.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Используйте один из следующих команд по настройке репозитория по своему усмотрению.

   | Хранилище | Version | Command |
   |---|---|---|
   | **Предварительная версия (2019 г.)** | 2019 г. | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"` |
   | **CU** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. Запустите **apt-get обновления**.

   ```bash
   sudo apt-get update
   ```

::: zone-end

## <a name="next-steps"></a>Следующие шаги

После того как настроен правильный репозиторий, можно перейти к [установить](sql-server-linux-setup.md#platforms) или [обновление](sql-server-linux-setup.md#upgrade) SQL Server и все связанные пакеты из нового репозитория.

::: zone pivot="ld2-rhel"
> [!IMPORTANT]
> На этом этапе, если вы решили использовать [быстрого запуска RHEL](quickstart-install-connect-red-hat.md), помните, что вы уже настроили целевого репозитория. Не Повторяйте этот шаг в учебниках. Это особенно важно, если настроить хранилище GDR, так как это краткое руководство использует накопительное обновление репозитория.
::: zone-end

::: zone pivot="ld2-sles"
> [!IMPORTANT]
> На этом этапе, если вы решили использовать [быстрого запуска SLES](quickstart-install-connect-suse.md), помните, что вы уже настроили целевого репозитория. Не Повторяйте этот шаг в учебниках. Это особенно важно, если настроить хранилище GDR, так как это краткое руководство использует накопительное обновление репозитория.
::: zone-end

::: zone pivot="ld2-ubuntu"
> [!IMPORTANT]
> На этом этапе, если вы решили использовать [быстрого запуска Ubuntu](quickstart-install-connect-ubuntu.md), помните, что вы уже настроили целевого репозитория. Не Повторяйте этот шаг в учебниках. Это особенно важно, если настроить хранилище GDR, так как это краткое руководство использует накопительное обновление репозитория.
::: zone-end

Дополнительные сведения об установке SQL Server 2017 в Linux см. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).
