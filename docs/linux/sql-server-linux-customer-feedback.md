---
title: Отзывы пользователей для SQL Server для Linux | Документы Microsoft
description: Описывает способы сбора и настроен на платформе Linux отзывы пользователей SQL Server.
author: annashres
ms.author: anshrest
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.openlocfilehash: f495899a262ae31c99ee2409a06dcd09ee6c44c4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="customer-feedback-for-sql-server-on-linux"></a>Отзывы пользователей для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

По умолчанию Microsoft SQL Server собирает сведения о том, как пользователи используют приложение. В частности, SQL Server собирает сведения об установке, использовании и производительности. Эти сведения помогают корпорации Майкрософт улучшать продукты и удовлетворять ожидания клиентов. Например, корпорация Майкрософт собирает сведения о кодах ошибок, с которыми сталкиваются пользователи. Это помогает нам исправлять вызвавшие их проблемы, улучшать качество документации об использовании SQL Server и определять, нужно ли добавить в продукт новые возможности, которые будут полезны нашим клиентам.

Данный документ содержит сведения о какие сведения собираются и как настроить Microsoft SQL Server в Linux для отправки, собранных сведений в корпорацию Майкрософт. 2017 г. SQL Server включает в себя заявление о конфиденциальности, которая объясняет, какие сведения, нам сделать и не собираются от пользователей. Ознакомьтесь с заявлением о конфиденциальности.

При этом, используя этот механизм, корпорация Майкрософт не собирает следующие данные:

- любые значения из пользовательских таблиц;
- любые учетные данные или другие параметры аутентификации;
- личные сведения (PII).

SQL Server 2017 всегда собирает и отправляет сведения о ходе установки. Это помогает нам быстро обнаруживать и исправлять любые проблемы, которые возникают у клиентов при установке. 2017 г. SQL Server можно настроить таким образом, не отправлять сведения (для отдельного экземпляра каждого сервера) в корпорацию Майкрософт через **mssql conf**. MSSQL conf — это сценарий конфигурации, который устанавливается вместе с SQL Server 2017 г. для Red Hat Enterprise Linux, SUSE Linux Enterprise Server и Ubuntu.

> [!NOTE]
> Вы можете отключить отправку данных в корпорацию Майкрософт только в платной версии SQL Server.

## <a name="disable-customer-feedback"></a>Отключить отправку отзывов пользователей

Этот параметр позволяет изменить, если SQL Server отправляет отзыв в корпорацию Майкрософт, или нет. По умолчанию это значение равным true. Чтобы изменить значение, выполните следующие команды:

### <a name="on-red-hat-suse-and-ubuntu"></a>В Red Hat и SUSE, Ubuntu

1. Запустите сценарий mssql conf как корень с **задать** для **telemetry.customerfeedback**. Следующий пример отключает отзывы пользователей, указав **false**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>Для Docker
Чтобы отключить отправку отзывов в docker необходимо иметь Docker [сохранить данные](sql-server-linux-configure-docker.md). 

1. Добавить `mssql.conf` файла со строками `[telemetry]` и `customerfeedback = false` в каталоге узла:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```
2. Запустите образа контейнера
   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```
   
## <a name="local-audit-for-sql-server-on-linux-usage-feedback-collection"></a>Локальный аудита для SQL Server для сбора отзывов об использовании Linux

2017 г. Microsoft SQL Server содержит компоненты, доступа к Интернету, которые могут собирать и отправлять в корпорацию Майкрософт сведения о компьютере или устройстве («Стандартные сведения о компьютере»). Компонент локального аудита отзывов о SQL Server использование коллекции может записывать данные, собранные службой в указанной папке представления данных (журнал), которое будет отправляться в корпорацию Майкрософт. Локальный аудит позволяет клиентам просмотреть все данные, которые корпорация Майкрософт собирает с помощью этой функции для обеспечения соответствия, выполнения нормативных требований или соблюдения конфиденциальности.

В SQL Server в Linux локальный аудита настраивается на уровне экземпляра для SQL Server Database Engine. Другие компоненты SQL Server и средства SQL Server имеют возможность локального аудита для сбора отзывов об использовании.

### <a name="enable-local-audit"></a>Включить локальный аудита

Этот параметр включает локальные аудита и позволяет задать каталог, где создаются журналы аудита локальной.

1. Создайте целевой каталог для локальных журналов. В следующем примере создается новый **/tmp/аудита** каталога:

   ```bash
   sudo mkdir /tmp/audit
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

1. Запустите сценарий mssql conf как корень с **задать** для **telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>Для Docker
Чтобы включить локальный аудита на docker необходимо иметь Docker [сохранить данные](sql-server-linux-configure-docker.md). 

1. Целевой каталог для новых журналов аудита локального будет находиться в контейнере. Создайте целевой каталог для локальных журналов в каталоге узла на компьютере. В следующем примере создается новый **/audit** каталога:

   ```bash
   sudo mkdir <host directory>/audit
   ```

   
1. Добавить `mssql.conf` файла со строками `[telemetry]` и `userrequestedlocalauditdirectory = <host directory>/audit` в каталоге узла:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```
2. Запустите образа контейнера
   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```
   
## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о SQL Server в Linux см. в разделе [Обзор SQL Server в Linux](sql-server-linux-overview.md).
