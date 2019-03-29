---
title: Отзывы по SQL Server в Linux | Документация Майкрософт
description: Описывает способы сбора отзывов пользователей SQL Server и настроена на платформе Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: a8e5d547ed3d25e5bddd467f8e41baed40a340fa
ms.sourcegitcommit: a9a03f9a7ec4dad507d2dfd5ca33571580114826
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2019
ms.locfileid: "58566373"
---
# <a name="customer-feedback-for-sql-server-on-linux"></a>Отзывы по SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

По умолчанию Microsoft SQL Server собирает сведения о том, как пользователи используют приложение. В частности, SQL Server собирает сведения об установке, использовании и производительности. Эти сведения помогают корпорации Майкрософт улучшать продукты и удовлетворять ожидания клиентов. Например, корпорация Майкрософт собирает сведения о кодах ошибок, с которыми сталкиваются пользователи. Это помогает нам исправлять вызвавшие их проблемы, улучшать качество документации об использовании SQL Server и определять, нужно ли добавить в продукт новые возможности, которые будут полезны нашим клиентам.

Этот документ содержит сведения о какие сведения собираются и как настроить Microsoft SQL Server в Linux, чтобы отправить то собранные сведения в корпорацию Майкрософт. SQL Server 2017 включает в себя заявление о конфиденциальности, объясняет, какие сведения, мы и не собираются от пользователей. Дополнительные сведения см. в разделе [заявление о конфиденциальности](https://go.microsoft.com/fwlink/?LinkID=868444).

При этом, используя этот механизм, корпорация Майкрософт не собирает следующие данные:

- любые значения из пользовательских таблиц;
- любые учетные данные или другие параметры аутентификации;
- личные сведения (PII).

SQL Server 2017 всегда собирает и отправляет сведения о ходе установки. Это помогает нам быстро обнаруживать и исправлять любые проблемы, которые возникают у клиентов при установке. Можно настроить SQL Server 2017 не отправляемое сведения (для каждого экземпляра каждого сервера) корпорации Майкрософт через **mssql-conf**. MSSQL-conf — это сценарий конфигурации, который устанавливается вместе с SQL Server 2017 для Red Hat Enterprise Linux, SUSE Linux Enterprise Server и Ubuntu.

> [!NOTE]
> Вы можете отключить отправку данных в корпорацию Майкрософт только в платной версии SQL Server.

## <a name="disable-customer-feedback"></a>Отключить отправку отзывов пользователей

Этот параметр позволяет изменять, если SQL Server отправляет отзыв в корпорацию Майкрософт, или нет. По умолчанию это значение на true. Чтобы изменить значение, выполните следующие команды:

> [!IMPORTANT]
> Можно не отключить отзывов пользователей бесплатно выпусков SQL Server, Express и Developer.

### <a name="on-red-hat-suse-and-ubuntu"></a>В Red Hat, SUSE и Ubuntu

1. Запустите сценарий mssql-conf в качестве привилегированного пользователя с **задать** команду для **telemetry.customerfeedback**. Следующий пример отключает отзывы клиентов, указав **false**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>В Docker
Чтобы отключить отправку отзывов пользователей в docker, необходимо иметь Docker [сохранить данные](sql-server-linux-configure-docker.md). 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Добавить `mssql.conf` файл со строками `[telemetry]` и `customerfeedback = false` в каталоге узла:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```

2. Запуск образа контейнера

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Добавить `mssql.conf` файл со строками `[telemetry]` и `customerfeedback = false` в каталоге узла:

   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```

2. Запуск образа контейнера

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

::: moniker-end

## <a name="local-audit-for-sql-server-on-linux-usage-feedback-collection"></a>Локальный аудит для SQL Server для сбора отзывов об использовании Linux

Microsoft SQL Server 2017 содержит Интернет-функциями, которые можно собирать и отправлять в Майкрософт сведения о компьютере или устройстве («Стандартные сведения о компьютере»). Компонент локального аудита для сбора отзывов об использовании SQL Server может записывать данные, собранные службой, в указанную папку, представляющие данные (журналы), будут отправляться в корпорацию Майкрософт. Локальный аудит позволяет клиентам просмотреть все данные, которые корпорация Майкрософт собирает с помощью этой функции для обеспечения соответствия, выполнения нормативных требований или соблюдения конфиденциальности.

В SQL Server в Linux локальный Аудит настраивается на уровне экземпляра для ядра СУБД SQL Server. Другие компоненты SQL Server и средств SQL Server не имеют функций локального аудита для сбора отзывов об использовании.

### <a name="enable-local-audit"></a>Включить локальный аудит

Этот параметр позволяет локального аудита и позволяет задать каталог, в которой создаются журналы локального аудита.

1. Создайте целевой каталог для новых журналов локального аудита. В следующем примере создается новый **/tmp/аудита** каталог:

   ```bash
   sudo mkdir /tmp/audit
   ```

2. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

3. Запустите сценарий mssql-conf в качестве привилегированного пользователя с **задать** команду для **telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

4. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>В Docker
Чтобы включить локальный аудит в docker, необходимо иметь Docker [сохранить данные](sql-server-linux-configure-docker.md). 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Целевой каталог для новые журналы локального аудита будет находиться в контейнере. Создайте целевой каталог для нового локального аудита журналов в каталоге узла на вашем компьютере. В следующем примере создается новый **/аудите** каталог:

   ```bash
   sudo mkdir <host directory>/audit
   ```

1. Добавить `mssql.conf` файл со строками `[telemetry]` и `userrequestedlocalauditdirectory = <host directory>/audit` в каталоге узла:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```

1. Запуск образа контейнера

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Целевой каталог для новые журналы локального аудита будет находиться в контейнере. Создайте целевой каталог для нового локального аудита журналов в каталоге узла на вашем компьютере. В следующем примере создается новый **/аудите** каталог:

   ```bash
   sudo mkdir <host directory>/audit
   ```

1. Добавить `mssql.conf` файл со строками `[telemetry]` и `userrequestedlocalauditdirectory = <host directory>/audit` в каталоге узла:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```

1. Запуск образа контейнера

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о SQL Server в Linux, см. в разделе [Общие сведения об SQL Server в Linux](sql-server-linux-overview.md).
