---
title: Заметки о выпуске для предварительной версии SQL Server 2019 на платформе Linux | Документация Майкрософт
description: Эта статья содержит заметки о выпуске и поддерживаемых функций для предварительной версии SQL Server 2019 под управлением Linux. Заметки о выпуске включены для последнего выпуска и несколько предыдущих выпусков.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 8d041e9554b976f46b121f2c39d8170183b85c6e
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66110223"
---
# <a name="release-notes-for-sql-server-2019-preview-on-linux"></a>Заметки о выпуске для предварительной версии SQL Server 2019 в Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md)]

Следующие заметки о выпуске применимы к SQL Server 2019 preview под управлением Linux. В этой статье разбивается на разделы для каждого выпуска. Каждый выпуск содержит ссылки поддержки статьи, описывающие CU изменения, а также ссылки на Linux, файлы для загрузки пакета.

> [!TIP]
> Дополнительные сведения о новых возможностях Linux SQL Server 2019, см. в разделе [новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).

## <a name="supported-platforms"></a>Поддерживаемые платформы

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, 7.4, 7.5 или 7.6 Server | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server до версии 12 SP2 | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Docker Engine 1.8 + на Windows, Mac или Linux | Н/Д | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!TIP]
> Дополнительные сведения см. в [требования к системе](sql-server-linux-setup.md#system) для SQL Server в Linux. Последнюю политику поддержки для SQL Server 2017, см. в разделе [политики технической поддержки для Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Инструменты

Большинство существующих клиентских средств, предназначенных для SQL Server без проблем можете ориентироваться на SQL Server на Linux. Некоторые средства могут занимать определенную версию для работы с Linux. Полный список средств SQL Server, см. в разделе [SQL средства и служебные программы для SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>История выпусков

В следующей таблице перечислены журнал выпуска для предварительной версии SQL Server 2019 выпусков CTP.

| Выпуск               | Version       | Дата выпуска |
|-----------------------|---------------|--------------|
| [CTP-ВЕРСИИ 3.0](#CTP30)     | 15.0.1600.8  | 2019-5-22    |
| [CTP-ВЕРСИИ 2.5](#CTP25)     | 15.0.1500.28  | 2019-4-24    |
| [CTP 2.4](#CTP24)     | 15.0.1400.75  | 2019-3-27    |
| [CTP-ВЕРСИИ 2.3](#CTP23)     | 15.0.1300.359 | 2019-3-01    |
| [CTP-ВЕРСИИ 2.2](#CTP22)     | 15.0.1200.24  | 2018-12-11   |
| [CTP-ВЕРСИИ 2.1](#CTP21)     | 15.0.1100.94  | 2018-11-06   |
| [CTP-ВЕРСИИ 2.0](#CTP20)     | 15.0.1000.34  | 2018-09-24   |

## <a id="cuinstall"></a> Установка обновлений

Если вы настроили репозиторий предварительной версии (**mssql-server-preview**), то вы получите последнюю версию пакетов CTP-версии SQL Server, при выполнении новых установок. Если требуется, чтобы образы контейнеров Docker, см. официальные образы для [Microsoft SQL Server в Linux для подсистемы Docker](https://hub.docker.com/r/microsoft/mssql-server/). Дополнительные сведения о конфигурации хранилища, см. в разделе [Настройка репозиториев для SQL Server в Linux](sql-server-linux-change-repo.md).

При обновлении существующих пакетов SQL Server, выполните команду соответствующие обновления для каждого пакета получить новейший пакет CU. Инструкции по обновлению, определенных для каждого пакета см. следующие руководства по установке:

- [Установите пакет SQL Server](sql-server-linux-setup.md#upgrade)
- [Установите пакет Full-text Search](sql-server-linux-setup-full-text-search.md)
- [Установка служб SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Установка предварительной версии SQL Server 2019 R для служб машинного обучения и поддержки Python в Linux](sql-server-linux-setup-machine-learning.md)
- [Включить агент SQL Server](sql-server-linux-setup-sql-agent.md)
- [Настройка для PolyBase Linux](../relational-databases/polybase/polybase-linux-setup.md)

## <a id="CTP30"></a> CTP-версии 3.0 (мая 2019 г.)

В следующих разделах приведены расположения пакетов и известные проблемы в CTP-версии 3.0 выпуске. Дополнительные сведения о новых возможностях для Linux на SQL Server 2019, см. в разделе [новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1600.8-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[Пакет PolyBase RPM](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1600.8-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[Пакет PolyBase RPM](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| Пакет Debian Ubuntu 16.04 | 15.0.1600.8-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1600.8-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1600.8-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1600.8-1_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1600.8-1_amd64.deb)</br>[Debian пакета расширения Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1600.8-1_amd64.deb)</br>[Пакет PolyBase RPM](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1600.8-1_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a id="msdtc"></a> Служба координатора распределенных транзакций

В настоящее время MSDTC требует транзакции должны быть без проверки подлинности. Например если используется связанный сервер с SQL Server на Windows для SQL Server в Linux или использовать клиентское приложение Windows для запуска распределенной транзакции в SQL Server в Linux, MSDTC в Windows server или клиента, то требуется использовать параметр «No Требуется проверка подлинности».

## <a id="CTP25"></a> CTP-версии 2.5 (апреля 2019 г.)

В следующих разделах приведены расположения пакетов и известные проблемы для CTP-версии 2.5 выпуске. Дополнительные сведения о новых возможностях для Linux на SQL Server 2019, см. в разделе [новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1500.28-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[Пакет PolyBase RPM](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1500.28-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[Пакет PolyBase RPM](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| Пакет Debian Ubuntu 16.04 | 15.0.1500.28-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1500.28-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1500.28-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1500.28-1_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1500.28-1_amd64.deb)</br>[Debian пакета расширения Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1500.28-1_amd64.deb)</br>[Пакет PolyBase RPM](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1500.28-1_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a id="msdtc"></a> Служба координатора распределенных транзакций

В настоящее время MSDTC требует транзакции должны быть без проверки подлинности. Например если используется связанный сервер с SQL Server на Windows для SQL Server в Linux или использовать клиентское приложение Windows для запуска распределенной транзакции в SQL Server в Linux, MSDTC в Windows server или клиента, то требуется использовать параметр «No Требуется проверка подлинности».

## <a id="CTP24"></a> CTP 2.4 (марта 2019 г.)

В следующих разделах приведены расположения пакетов и известные проблемы для CTP 2.4 выпуске. Дополнительные сведения о новых возможностях для Linux на SQL Server 2019, см. в разделе [новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1400.75-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1400.75-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| Пакет Debian Ubuntu 16.04 | 15.0.1400.75-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1400.75-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1400.75-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1400.75-2_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1400.75-2_amd64.deb)</br>[Debian пакета расширения Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1400.75-2_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a id="msdtc"></a> Служба координатора распределенных транзакций

В настоящее время MSDTC требует транзакции должны быть без проверки подлинности. Например если используется связанный сервер с SQL Server на Windows для SQL Server в Linux или использовать клиентское приложение Windows для запуска распределенной транзакции в SQL Server в Linux, MSDTC в Windows server или клиента, то требуется использовать параметр «No Требуется проверка подлинности».

## <a id="CTP23"></a> CTP-версии 2.3 (февраля 2019 г.)

В следующих разделах приведены расположения пакетов и известные проблемы для CTP-версия 2.3 выпуске. Дополнительные сведения о новых возможностях для Linux на SQL Server 2019, см. в разделе [новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1300.359-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1300.359-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| Пакет Debian Ubuntu 16.04 | 15.0.1300.359-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1300.359-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1300.359-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1300.359-1_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1300.359-1_amd64.deb)</br>[Debian пакета расширения Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1300.359-1_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a id="msdtc"></a> Служба координатора распределенных транзакций

В настоящее время MSDTC требует транзакции должны быть без проверки подлинности. Например если используется связанный сервер с SQL Server на Windows для SQL Server в Linux или использовать клиентское приложение Windows для запуска распределенной транзакции в SQL Server в Linux, MSDTC в Windows server или клиента, то требуется использовать параметр «No Требуется проверка подлинности».

## <a id="CTP22"></a> CTP-версии 2.2 (декабря 2018 г.)

В следующих разделах приведены расположения пакетов и известные проблемы для CTP-версии 2.2 выпуске. Дополнительные сведения о новых возможностях для Linux на SQL Server 2019, см. в разделе [новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1200.24-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1200.24-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| Пакет Debian Ubuntu 16.04 | 15.0.1200.24-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1200.24-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1200.24-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1200.24-2_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1200.24-2_amd64.deb)</br>[Debian пакета расширения Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1200.24-2_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a id="msdtc"></a> Служба координатора распределенных транзакций

В настоящее время MSDTC требует транзакции должны быть без проверки подлинности. Например если используется связанный сервер с SQL Server на Windows для SQL Server в Linux или использовать клиентское приложение Windows для запуска распределенной транзакции в SQL Server в Linux, MSDTC в Windows server или клиента, то требуется использовать параметр «No Требуется проверка подлинности».

## <a id="CTP21"></a> CTP-версии 2.1 (ноября 2018 г.)

В следующих разделах приведены расположения пакетов и известные проблемы для CTP 2.1 выпуске. Дополнительные сведения о новых возможностях для Linux на SQL Server 2019, см. в разделе [новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1100.94-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1100.94-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Пакет Debian Ubuntu 16.04 | 15.0.1100.94-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1100.94-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1100.94-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1100.94-1_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1100.94-1_amd64.deb)</br>[Debian пакета расширения Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1100.94-1_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a name="microsoft-distributed-transaction-coordinator"></a>Служба координатора распределенных транзакций

В настоящее время MSDTC требует транзакции должны быть без проверки подлинности. Например если используется связанный сервер с SQL Server на Windows для SQL Server в Linux или использовать клиентское приложение Windows для запуска распределенной транзакции в SQL Server в Linux, MSDTC в Windows server или клиента, то требуется использовать параметр «No Требуется проверка подлинности».

## <a id="CTP20"></a> CTP-версии 2.0 (сентября 2018 г.)

В следующих разделах приведены расположения пакетов и известные проблемы для CTP-версии 2.0 выпуске. Дополнительные сведения о новых возможностях для Linux на SQL Server 2019, см. в разделе [новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1000.34-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1000.34-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Пакет Debian Ubuntu 16.04 | 15.0.1000.34-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1000.34-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1000.34-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1000.34-2_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1000.34-2_amd64.deb)</br>[Debian пакета расширения Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1000.34-2_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a name="microsoft-distributed-transaction-coordinator"></a>Служба координатора распределенных транзакций

В настоящее время MSDTC требует транзакции должны быть без проверки подлинности. Например если используется связанный сервер с SQL Server на Windows для SQL Server в Linux или использовать клиентское приложение Windows для запуска распределенной транзакции в SQL Server в Linux, MSDTC в Windows server или клиента, то требуется использовать параметр «No Требуется проверка подлинности».

## <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. в разделе следующих кратких руководств:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустить в Docker](quickstart-install-connect-ubuntu.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [Запуск и подключение — облако](quickstart-install-connect-clouds.md)

Ответы на часто задаваемые вопросы см. в разделе [SQL Server на Linux часто задаваемые вопросы о](sql-server-linux-faq.md).
