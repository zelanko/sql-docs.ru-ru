---
title: Настройка сбора данных об использовании и данных диагностики для SQL Server на Linux
description: Сведения о том, как собираются и настраиваются данные об использовании и данные диагностики для SQL Server в Linux.
ms.custom: seo-lt-2019
author: VanMSFT
ms.author: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 96c58159a020ba11708b12a4e5732438044b3291
ms.sourcegitcommit: 22102f25db5ccca39aebf96bc861c92f2367c77a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2020
ms.locfileid: "92115743"
---
# <a name="configure-usage--diagnostic-data-collection-for-sql-server-on-linux"></a>Настройка сбора данных об использовании и данных диагностики для SQL Server на Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

По умолчанию Microsoft SQL Server собирает сведения о том, как пользователи используют приложение. В частности, SQL Server собирает сведения об установке, использовании и производительности. Эти сведения помогают корпорации Майкрософт улучшать продукты и удовлетворять ожидания клиентов. Например, корпорация Майкрософт собирает сведения о кодах ошибок, с которыми сталкиваются пользователи. Это помогает нам исправлять вызвавшие их проблемы, улучшать качество документации об использовании SQL Server и определять, нужно ли добавить в продукт новые возможности, которые будут полезны нашим клиентам.

В этом документе приводятся сведения о том, какие данные собираются и как настроить в Microsoft SQL Server на Linux отправку собранных данных в корпорацию Майкрософт. Для SQL Server 2017 действует заявление о конфиденциальности, в котором описывается, какие сведения мы собираем и не собираем от пользователей. Дополнительные сведения см. в [заявлении о конфиденциальности](../sql-server/sql-server-privacy.md).

При этом, используя этот механизм, корпорация Майкрософт не собирает следующие данные:

- любые значения из пользовательских таблиц;
- любые учетные данные или другие параметры аутентификации;
- личные сведения (PII).

SQL Server 2017 всегда собирает и отправляет сведения о ходе установки. Это помогает нам быстро обнаруживать и исправлять любые проблемы, которые возникают у клиентов при установке. С помощью **mssql-conf** сервер SQL Server 2017 можно настроить так, чтобы он не отправлял в корпорацию Майкрософт какие-либо сведения. Такое поведение настраивается отдельно для каждого экземпляра сервера. mssql-conf — это скрипт настройки, который устанавливается вместе с SQL Server 2017 для Red Hat Enterprise Linux, SUSE Linux Enterprise Server и Ubuntu.

> [!NOTE]
> Вы можете отключить отправку данных в корпорацию Майкрософт только в платной версии SQL Server.

## <a name="disable-usage-and-diagnostic-data-collection"></a>Отключение сбора данных об использовании и данных диагностики

С помощью этого параметра можно включить или отключить отправку данных об использовании и данных диагностики из SQL Server в корпорацию Майкрософт. По умолчанию он имеет значение True. Чтобы изменить значение, выполните следующие команды:

> [!IMPORTANT]
> Отключить сбор данных об использовании и данных диагностики для бесплатных выпусков SQL Server, Express и Developer, невозможно.

### <a name="on-red-hat-suse-and-ubuntu"></a>В Red Hat, SUSE и Ubuntu

1. Запустите скрипт mssql-conf от имени привилегированного пользователя с помощью команды **set** для **telemetry.customerfeedback**. В приведенном ниже примере сбор данных об использовании и данных диагностики отключается путем указания значения **false**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>В Docker
Чтобы отключить сбор данных об использовании и данных диагностики в Docker, необходимо настроить в Docker [сохранение данных](./sql-server-linux-docker-container-deployment.md). 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Добавьте файл `mssql.conf` со строками `[telemetry]` и `customerfeedback = false` в каталог узла:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```

2. Запустите образ контейнера:

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Добавьте файл `mssql.conf` со строками `[telemetry]` и `customerfeedback = false` в каталог узла:

   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```

2. Запустите образ контейнера:

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
   ```

::: moniker-end

## <a name="local-audit-for-sql-server-on-linux-usage-and-diagnostic-data-collection"></a>Локальный аудит для сбора данных об использовании и данных диагностики SQL Server на Linux

Microsoft SQL Server 2017 включает в себя функции, которые могут собирать и отправлять в Майкрософт сведения о компьютере или устройстве пользователя через Интернет (далее — "стандартные сведения о компьютере"). Компонент локального аудита для сбора данных об использовании и диагностических данных SQL Server позволяет записывать собранные службой данные в указанную папку. Эти данные (журналы) будут отправлены в корпорацию Майкрософт. Локальный аудит позволяет клиентам просмотреть все данные, которые корпорация Майкрософт собирает с помощью этой функции для обеспечения соответствия, выполнения нормативных требований или соблюдения конфиденциальности.

В SQL Server на Linux локальный аудит настраивается на уровне экземпляра для ядра СУБД SQL Server. Другие компоненты и средства SQL Server не имеют функций локального аудита для сбора данных об использовании и диагностических данных.

### <a name="enable-local-audit"></a>Включение локального аудита

Этот параметр позволяет включить локальный аудит и указать каталог, в котором создаются журналы локального аудита.

1. Создайте целевой каталог для новых журналов локального аудита. В следующем примере создается каталог **/tmp/audit**:

   ```bash
   sudo mkdir /tmp/audit
   ```

2. Задайте пользователя **mssql** в качестве владельца и группы каталога:

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

3. Запустите скрипт mssql-conf от имени привилегированного пользователя с командой **set** для **telemetry.userrequestedlocalauditdirectory**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

4. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>В Docker
Чтобы включить локальный аудит в Docker, необходимо настроить в Docker [сохранение данных](./sql-server-linux-docker-container-deployment.md). 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Целевой каталог для новых журналов локального аудита будет находиться в контейнере. Создайте целевой каталог для новых журналов локального аудита в каталоге узла на вашем компьютере. В следующем примере создается каталог **/audit**:

   ```bash
   sudo mkdir <host directory>/audit
   ```

1. Добавьте файл `mssql.conf` со строками `[telemetry]` и `userrequestedlocalauditdirectory = <host directory>/audit` в каталог узла:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```

1. Запустите образ контейнера:

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Целевой каталог для новых журналов локального аудита будет находиться в контейнере. Создайте целевой каталог для новых журналов локального аудита в каталоге узла на вашем компьютере. В следующем примере создается каталог **/audit**:

   ```bash
   sudo mkdir <host directory>/audit
   ```

1. Добавьте файл `mssql.conf` со строками `[telemetry]` и `userrequestedlocalauditdirectory = <host directory>/audit` в каталог узла:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```

1. Запустите образ контейнера:

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
   ```

::: moniker-end

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения об SQL Server на Linux см. в статье [Обзор SQL Server на Linux](sql-server-linux-overview.md).