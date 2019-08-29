---
title: Заметки о выпуске для SQL Server 2019 в Linux
description: Эта статья содержит заметки о выпуске и поддерживаемые функции для SQL Server 2019 в Linux. Приведены заметки о выпуске для последнего и нескольких предыдущих выпусков.
author: VanMSFT
ms.author: vanto
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: af3b6f82e3b76e2dd2b11403bccf4b3e0885912e
ms.sourcegitcommit: cbbb210c0315f9e2be2b9cd68db888ac53429814
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2019
ms.locfileid: "69890900"
---
# <a name="release-notes-for-sql-server-2019-on-linux"></a>Заметки о выпуске для SQL Server 2019 в Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md)]

Следующие заметки о выпуске применимы к версии SQL Server 2019, работающей в Linux. Эта статья разбита на разделы для каждого выпуска. Каждый выпуск содержит ссылку на статью поддержки, где описаны изменения накопительного пакета обновления, а также ссылки на скачиваемые файлы пакета Linux.

> [!TIP]
> Сведения о новых возможностях Linux в SQL Server 2019 см. в статье [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).

## <a name="supported-platforms"></a>Поддерживаемые платформы

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, 7.4, 7.5 или 7.6 Server | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server версии 12 с пакетом обновления 2 (SP2) | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема Docker Engine 1.8+ на базе Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!TIP]
> Дополнительные сведения см. в [требованиях к системе](sql-server-linux-setup.md#system) для SQL Server на базе Linux. Актуальную политику поддержки для SQL Server 2017, см. в статье [Политика технической поддержки для Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Инструменты

Большинство существующих клиентских средств, предназначенных для SQL Server, могут без проблем работать с SQL Server, выполняющимся в Linux. Некоторые средства для нормальной работы с Linux могут иметь определенные требования к версиям. Полный список средств SQL Server см. в статье [Средства и служебные программы SQL для SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>История выпусков

В следующей таблице указана история выпусков для выпусков предварительной версии SQL Server 2019.

| Выпуск                   | Версия       | Дата выпуска |
|---------------------------|---------------|--------------|
| [Релиз-кандидат](#rc)  | 15.0.1900.25  | 2019-8-21    |
| [CTP 3.2](#CTP32)         | 15.0.1800.32  | 2019-7-24    |
| [CTP 3.1](#CTP31)         | 15.0.1700.37  | 2019-6-26    |
| [CTP 3.0](#CTP30)         | 15.0.1600.8   | 2019-5-22    |
| [CTP 2.5](#CTP25)         | 15.0.1500.28  | 2019-4-24    |
| [CTP 2.4](#CTP24)         | 15.0.1400.75  | 2019-3-27    |
| [CTP 2.3](#CTP23)         | 15.0.1300.359 | 2019-3-01    |
| [CTP 2.2](#CTP22)         | 15.0.1200.24  | 2018-12-11   |
| [CTP 2.1](#CTP21)         | 15.0.1100.94  | 2018-11-06   |
| [CTP 2.0](#CTP20)         | 15.0.1000.34  | 2018-09-24   |

## <a id="cuinstall"></a> Установка обновлений

Если вы настроили репозиторий предварительных версий (**mssql-server-preview**), то получите последние пакеты CTP SQL Server при выполнении новых установок. Если вам требуются образы контейнеров Docker, см. официальные образы для [Microsoft SQL Server на Linux для подсистемы Docker](https://hub.docker.com/r/microsoft/mssql-server/). Дополнительные сведения о настройке репозиториев см. в статье [Настройка репозиториев для установки и обновления SQL Server на Linux.](sql-server-linux-change-repo.md)

При обновлении существующих пакетов SQL Server выполните соответствующую команду обновления для каждого пакета, чтобы получить последний накопительный пакет обновления. Конкретные инструкции по обновлению для каждого пакета см. в следующих руководствах по установке.

- [Установка пакета SQL Server](sql-server-linux-setup.md#upgrade)
- [Установка пакета полнотекстового поиска](sql-server-linux-setup-full-text-search.md)
- [Установка служб SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Установка поддержки R и Python для Служб машинного обучения предварительной версии SQL Server 2019 в Linux](sql-server-linux-setup-machine-learning.md)
- [Установка пакета PolyBase](../relational-databases/polybase/polybase-linux-setup.md)
- [Включение агента SQL Server](sql-server-linux-setup-sql-agent.md)

## <a id="rc"></a> Релиз-кандидат (август 2019 г.)

В следующих разделах приведены сведения о расположениях пакетов и известных проблемах в релиз-кандидате. Дополнительные сведения о новых возможностях для Linux в SQL Server 2019 см. в статье [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для ручной или автономной установки пакета можно скачать пакеты RPM и Debian, используя сведения из следующей таблицы.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1900.25-1 | [Пакет RPM подсистемы](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1900.25-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1900.25-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1900.25-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1900.25-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1900.25-1.x86_64.rpm)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1900.25-1.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1900.25-1 | [Пакет RPM подсистемы mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1900.25-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1900.25-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1900.25-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1900.25-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1900.25-1.x86_64.rpm)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1900.25-1.x86_64.rpm)|
| Пакет Ubuntu 16.04 Debian | 15.0.1900.25-1 | [Пакет подсистемы Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1900.25-1_amd64.deb)</br>[Пакет Debian высокой доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1900.25-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1900.25-1_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1900.25-1_amd64.deb)</br>[Пакет Debian расширяемости Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1900.25-1_amd64.deb)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1900.25-1_amd64.deb)|

## <a id="CTP32"></a> CTP 3.2 (июль 2019 г.)

В следующих разделах приведены сведения о расположениях пакетов и известных проблемах в выпуске CTP 3.2. Дополнительные сведения о новых возможностях для Linux в SQL Server 2019 см. в статье [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для ручной или автономной установки пакета можно скачать пакеты RPM и Debian, используя сведения из следующей таблицы.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1800.32-1 | [Пакет RPM подсистемы](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1800.32-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1800.32-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1800.32-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1800.32-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1800.32-1.x86_64.rpm)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1800.32-1.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1800.32-1 | [Пакет RPM подсистемы mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1800.32-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1800.32-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1800.32-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1800.32-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1800.32-1.x86_64.rpm)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1800.32-1.x86_64.rpm)|
| Пакет Ubuntu 16.04 Debian | 15.0.1800.32-1 | [Пакет подсистемы Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1800.32-1_amd64.deb)</br>[Пакет Debian высокой доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1800.32-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1800.32-1_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1800.32-1_amd64.deb)</br>[Пакет Debian расширяемости Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1800.32-1_amd64.deb)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1800.32-1_amd64.deb)|

## <a id="CTP31"></a> CTP 3.1 (июнь 2019 г.)

В следующих разделах приведены сведения о расположениях пакетов и известных проблемах в выпуске CTP 3.1. Дополнительные сведения о новых возможностях для Linux в SQL Server 2019 см. в статье [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для ручной или автономной установки пакета можно скачать пакеты RPM и Debian, используя сведения из следующей таблицы.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1700.37-2 | [Пакет RPM подсистемы](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1700.37-2.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1700.37-2.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1700.37-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1700.37-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1700.37-2.x86_64.rpm)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1700.37-2.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1700.37-2 | [Пакет RPM подсистемы mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1700.37-2.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1700.37-2.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1700.37-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1700.37-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1700.37-2.x86_64.rpm)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1700.37-2.x86_64.rpm)|
| Пакет Ubuntu 16.04 Debian | 15.0.1700.37-2 | [Пакет подсистемы Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1700.37-2_amd64.deb)</br>[Пакет Debian высокой доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1700.37-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1700.37-2_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1700.37-2_amd64.deb)</br>[Пакет Debian расширяемости Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1700.37-2_amd64.deb)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1700.37-2_amd64.deb)|

## <a id="CTP30"></a> CTP 3.0 (май 2019 г.)

В следующих разделах приведены сведения о расположениях пакетов и известных проблемах в выпуске CTP 3.0. Дополнительные сведения о новых возможностях для Linux в SQL Server 2019 см. в статье [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для ручной или автономной установки пакета можно скачать пакеты RPM и Debian, используя сведения из следующей таблицы.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1600.8-1 | [Пакет RPM подсистемы](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1600.8-1 | [Пакет RPM подсистемы mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| Пакет Ubuntu 16.04 Debian | 15.0.1600.8-1 | [Пакет подсистемы Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1600.8-1_amd64.deb)</br>[Пакет Debian высокой доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1600.8-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1600.8-1_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1600.8-1_amd64.deb)</br>[Пакет Debian расширяемости Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1600.8-1_amd64.deb)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1600.8-1_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a id="msdtc"></a> Координатор распределенных транзакций (Майкрософт)

Сейчас MSDTC требует, чтобы транзакции не проходили проверку подлинности. Например, если вы используете связанный сервер из SQL Server на базе Windows в SQL Server на базе Linux или используете клиентское приложение Windows для запуска распределенной транзакции в SQL Server на базе Linux, то для MSDTC на сервере/клиенте Windows необходимо использовать параметр "Проверка подлинности не требуется".

## <a id="CTP25"></a> CTP 2.5 (апрель 2019 г.)

В следующих разделах приведены сведения о расположениях пакетов и известных проблемах в выпуске CTP 2.5. Дополнительные сведения о новых возможностях для Linux в SQL Server 2019 см. в статье [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для ручной или автономной установки пакета можно скачать пакеты RPM и Debian, используя сведения из следующей таблицы.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1500.28-1 | [Пакет RPM подсистемы](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1500.28-1 | [Пакет RPM подсистемы mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| Пакет Ubuntu 16.04 Debian | 15.0.1500.28-1 | [Пакет подсистемы Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1500.28-1_amd64.deb)</br>[Пакет Debian высокой доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1500.28-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1500.28-1_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1500.28-1_amd64.deb)</br>[Пакет Debian расширяемости Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1500.28-1_amd64.deb)</br>[Пакет RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1500.28-1_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a id="msdtc"></a> Координатор распределенных транзакций (Майкрософт)

Сейчас MSDTC требует, чтобы транзакции не проходили проверку подлинности. Например, если вы используете связанный сервер из SQL Server на базе Windows в SQL Server на базе Linux или используете клиентское приложение Windows для запуска распределенной транзакции в SQL Server на базе Linux, то для MSDTC на сервере/клиенте Windows необходимо использовать параметр "Проверка подлинности не требуется".

## <a id="CTP24"></a> CTP 2.4 (март 2019 г.)

В следующих разделах приведены сведения о расположениях пакетов и известных проблемах в выпуске CTP 2.4. Дополнительные сведения о новых возможностях для Linux в SQL Server 2019 см. в статье [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для ручной или автономной установки пакета можно скачать пакеты RPM и Debian, используя сведения из следующей таблицы.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1400.75-2 | [Пакет RPM подсистемы](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1400.75-2 | [Пакет RPM подсистемы mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| Пакет Ubuntu 16.04 Debian | 15.0.1400.75-2 | [Пакет подсистемы Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1400.75-2_amd64.deb)</br>[Пакет Debian высокой доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1400.75-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1400.75-2_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1400.75-2_amd64.deb)</br>[Пакет Debian расширяемости Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1400.75-2_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a id="msdtc"></a> Координатор распределенных транзакций (Майкрософт)

Сейчас MSDTC требует, чтобы транзакции не проходили проверку подлинности. Например, если вы используете связанный сервер из SQL Server на базе Windows в SQL Server на базе Linux или используете клиентское приложение Windows для запуска распределенной транзакции в SQL Server на базе Linux, то для MSDTC на сервере/клиенте Windows необходимо использовать параметр "Проверка подлинности не требуется".

## <a id="CTP23"></a> CTP 2.3 (февраль 2019 г.)

В следующих разделах приведены сведения о расположениях пакетов и известных проблемах в выпуске CTP 2.3. Дополнительные сведения о новых возможностях для Linux в SQL Server 2019 см. в статье [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для ручной или автономной установки пакета можно скачать пакеты RPM и Debian, используя сведения из следующей таблицы.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1300.359-1 | [Пакет RPM подсистемы](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1300.359-1 | [Пакет RPM подсистемы mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| Пакет Ubuntu 16.04 Debian | 15.0.1300.359-1 | [Пакет подсистемы Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1300.359-1_amd64.deb)</br>[Пакет Debian высокой доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1300.359-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1300.359-1_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1300.359-1_amd64.deb)</br>[Пакет Debian расширяемости Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1300.359-1_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a id="msdtc"></a> Координатор распределенных транзакций (Майкрософт)

Сейчас MSDTC требует, чтобы транзакции не проходили проверку подлинности. Например, если вы используете связанный сервер из SQL Server на базе Windows в SQL Server на базе Linux или используете клиентское приложение Windows для запуска распределенной транзакции в SQL Server на базе Linux, то для MSDTC на сервере/клиенте Windows необходимо использовать параметр "Проверка подлинности не требуется".

## <a id="CTP22"></a> CTP 2.2 (декабрь 2018 г.)

В следующих разделах приведены сведения о расположениях пакетов и известных проблемах в выпуске CTP 2.2. Дополнительные сведения о новых возможностях для Linux в SQL Server 2019 см. в статье [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для ручной или автономной установки пакета можно скачать пакеты RPM и Debian, используя сведения из следующей таблицы.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1200.24-2 | [Пакет RPM подсистемы](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1200.24-2 | [Пакет RPM подсистемы mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| Пакет Ubuntu 16.04 Debian | 15.0.1200.24-2 | [Пакет подсистемы Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1200.24-2_amd64.deb)</br>[Пакет Debian высокой доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1200.24-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1200.24-2_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1200.24-2_amd64.deb)</br>[Пакет Debian расширяемости Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1200.24-2_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a id="msdtc"></a> Координатор распределенных транзакций (Майкрософт)

Сейчас MSDTC требует, чтобы транзакции не проходили проверку подлинности. Например, если вы используете связанный сервер из SQL Server на базе Windows в SQL Server на базе Linux или используете клиентское приложение Windows для запуска распределенной транзакции в SQL Server на базе Linux, то для MSDTC на сервере/клиенте Windows необходимо использовать параметр "Проверка подлинности не требуется".

## <a id="CTP21"></a> CTP 2.1 (ноябрь 2018 г.)

В следующих разделах приведены сведения о расположениях пакетов и известных проблемах в выпуске CTP 2.1. Дополнительные сведения о новых возможностях для Linux в SQL Server 2019 см. в статье [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для ручной или автономной установки пакета можно скачать пакеты RPM и Debian, используя сведения из следующей таблицы.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1100.94-1 | [Пакет RPM подсистемы](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1100.94-1 | [Пакет RPM подсистемы mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Пакет Ubuntu 16.04 Debian | 15.0.1100.94-1 | [Пакет подсистемы Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1100.94-1_amd64.deb)</br>[Пакет Debian высокой доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1100.94-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1100.94-1_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1100.94-1_amd64.deb)</br>[Пакет Debian расширяемости Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1100.94-1_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a name="microsoft-distributed-transaction-coordinator"></a>Координатор распределенных транзакций (Майкрософт)

Сейчас MSDTC требует, чтобы транзакции не проходили проверку подлинности. Например, если вы используете связанный сервер из SQL Server на базе Windows в SQL Server на базе Linux или используете клиентское приложение Windows для запуска распределенной транзакции в SQL Server на базе Linux, то для MSDTC на сервере/клиенте Windows необходимо использовать параметр "Проверка подлинности не требуется".

## <a id="CTP20"></a> CTP 2.0 (сентябрь 2018 г.)

В следующих разделах приведены сведения о расположениях пакетов и известных проблемах в выпуске CTP 2.0. Дополнительные сведения о новых возможностях для Linux в SQL Server 2019 см. в статье [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Сведения о пакете

Для ручной или автономной установки пакета можно скачать пакеты RPM и Debian, используя сведения из следующей таблицы.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 15.0.1000.34-2 | [Пакет RPM подсистемы](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Пакет SLES RPM | 15.0.1000.34-2 | [Пакет RPM подсистемы mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM высокой доступности](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM расширяемости](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Пакет RPM расширяемости Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Пакет Ubuntu 16.04 Debian | 15.0.1000.34-2 | [Пакет подсистемы Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1000.34-2_amd64.deb)</br>[Пакет Debian высокой доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1000.34-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1000.34-2_amd64.deb)</br>[Пакет Debian расширяемости](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1000.34-2_amd64.deb)</br>[Пакет Debian расширяемости Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1000.34-2_amd64.deb)|

### <a name="known-issues"></a>Известные проблемы

#### <a name="microsoft-distributed-transaction-coordinator"></a>Координатор распределенных транзакций (Майкрософт)

Сейчас MSDTC требует, чтобы транзакции не проходили проверку подлинности. Например, если вы используете связанный сервер из SQL Server на базе Windows в SQL Server на базе Linux или используете клиентское приложение Windows для запуска распределенной транзакции в SQL Server на базе Linux, то для MSDTC на сервере/клиенте Windows необходимо использовать параметр "Проверка подлинности не требуется".

## <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, ознакомьтесь со следующими краткими руководствами.

- [Установка в Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка в SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запуск в Docker](quickstart-install-connect-ubuntu.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [Запуск и подключение — облако](quickstart-install-connect-clouds.md)

Ответы на часто задаваемые вопросы об SQL Server на Linux см. в [этой статье](sql-server-linux-faq.md).
