---
title: Заметки о выпуске для SQL Server 2017 на платформе Linux | Документация Майкрософт
description: В этой статье содержатся заметки о выпуске и поддерживаемые функции для SQL Server 2017 на платформе Linux. Заметки о выпуске включены для последнего выпуска и несколько предыдущих выпусков.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/18/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: e13ee9f8046eb53db8e59ee33b3039757bbc4aa4
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64776184"
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Заметки о выпуске для SQL Server 2017 в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Следующие заметки о выпуске применяются к [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] под управлением Linux. В этой статье разбивается на разделы для каждого выпуска. Выпуск общедоступной версии подробные поддерживаемости и известные проблемы в списке. Каждый пакет обновления (CU) или выпуска для общего распространения (GDR) имеет ссылки поддержки статьи, описывающие CU изменения, а также ссылки на Linux, файлы для загрузки пакета.

> [!TIP]
> Эти заметки о выпуске предназначены специально для [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] освобождает. Дополнительные сведения о новом [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], см. в разделе [заметки о выпуске для предварительной версии SQL Server 2019 в Linux](sql-server-linux-release-notes-2019.md?view=sql-server-ver15).

## <a name="supported-platforms"></a>Поддерживаемые платформы

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, 7.4, 7.5 или 7.6 Server | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server до версии 12 SP2 | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Docker Engine 1.8 + на Windows, Mac или Linux | Н/Д | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!TIP]
> Дополнительные сведения см. в [требования к системе](sql-server-linux-setup.md#system) для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux. Для последней политике поддержки для [!INCLUDE[ssSQL17](../includes/sssql17-md.md)], см. в разделе [политики технической поддержки для Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Инструменты

Большинство существующих клиентских средств, предназначенных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] легко можно ориентироваться [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] под управлением Linux. Некоторые средства могут занимать определенную версию для работы с Linux. Полный список [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] средства, см. в разделе [SQL средства и служебные программы для SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>История выпусков

В следующей таблице перечислены История выпусков для [!INCLUDE[ssSQL17](../includes/sssql17-md.md)].

| Выпуск               | Version       | Дата выпуска |
|-----------------------|---------------|--------------|
| [CU14](#CU14)         | 14.0.3076.1   | 2019-03-25   |
| [CU13](#CU13)         | 14.0.3048.4   | 2018-12-18   |
| [CU12](#CU12)         | 14.0.3045.24  | 2018-10-24   |
| [CU11](#CU11)         | 14.0.3038.14  | 2018-09-20   |
| [CU10](#CU10)         | 14.0.3037.1   | 2018-08-27   |
| [CU9-GDR2](#CU9-GDR2) | 14.0.3035.2   | 2018-08-18   |
| [GDR2](#GDR2)         | 14.0.2002.14  | 2018-08-18   |
| [CU9](#CU9)           | 14.0.3030.27  | 2018-07-18   |
| [CU8](#CU8)           | 14.0.3029.16  | 2018-06-21   |
| [CU7](#CU7)           | 14.0.3026.27  | 2018-05-24   |
| [CU6](#CU6)           | 14.0.3025.34  | 2018-04-19   |
| [CU5](#CU5)           | 14.0.3023.8   | 2018-03-20   |
| [CU4](#CU4)           | 14.0.3022.28  | 2018-02-20   |
| [CU3](#CU3)           | 14.0.3015.40  | 2018-01-03   |
| [GDR1](#GDR1)         | 14.0.2000.63  | 2018-01-03   |
| [CU2](#CU2)           | 14.0.3008.27  | 2017-11-28   |
| [CU1](#CU1)           | 14.0.3006.16  | 2017-10-24   |
| [ОБЩЕДОСТУПНАЯ ВЕРСИЯ](#GA)             | 14.0.1000.169 | 2017-10-02   |

## <a id="cuinstall"></a> Установка обновлений

Если вы настроили хранилище накопительное обновление (**mssql-server-2017**), то вы получите новейший пакет CU из [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] пакеты при выполнении новых установок. Накопительное обновление репозитория задается по умолчанию для всех пакетов установки статей для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux. Если вы настроили репозиторий GDR (**mssql-server-2017-gdr**), вы получите только критические обновления, выпущенные с момента выхода общедоступной версии. Если вам требуется контейнера Docker и накопительным Обновлением обновления GDR, см. официальные образы для [Microsoft SQL Server в Linux для подсистемы Docker](https://hub.docker.com/r/microsoft/mssql-server). Дополнительные сведения о конфигурации хранилища, см. в разделе [Настройка репозиториев для SQL Server в Linux](sql-server-linux-change-repo.md).

Если вы обновляете существующий [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] пакеты, выполните команду соответствующие обновления для каждого пакета получить новейший пакет CU. Инструкции по обновлению, определенных для каждого пакета см. следующие руководства по установке:

- [Установите пакет SQL Server](sql-server-linux-setup.md#upgrade)
- [Установите пакет Full-text Search](sql-server-linux-setup-full-text-search.md)
- [Установка служб SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Включить агент SQL Server](sql-server-linux-setup-sql-agent.md)

## <a id="CU14"></a> CU14 (марта 2018 г.)

Это выпуск накопительного пакета обновления 14 (CU14) [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3076.1. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4484710 ](https://support.microsoft.com/help/4484710).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3076.1-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3076.1-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3076.1-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3076.1-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3076.1-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3076.1-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU13"></a> CU13 (декабря 2018 г.)

Это накопительное обновление 13 (CU13) версия [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3048.4. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4466404 ](https://support.microsoft.com/help/4466404).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3048.4-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3048.4-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3048.4-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3048.4-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3048.4-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3048.4-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU12"></a> CU12 (октября 2018 г.)

Это — это накопительный пакет обновления 12 (CU12) версия [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3045.24. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4464082 ](https://support.microsoft.com/help/4464082).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3045.24-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3045.24-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3045.24-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3045.24-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3045.24-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3045.24-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU11"></a> CU11 (сентября 2018 г.)

Это накопительное обновление 11 (CU11) версия [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3038.14. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4462262 ](https://support.microsoft.com/help/4462262).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3038.14-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3038.14-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3038.14-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3038.14-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3038.14-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3038.14-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU10"></a> CU10 (августа 2018 г.)

Это выпуск накопительного обновления 10 (CU10) [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3037.1. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4342123 ](https://support.microsoft.com/help/4342123).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3037.1-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3037.1-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3037.1-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3037.1-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU9-GDR2"></a> CU9-GDR2 (августа 2018 г.)

Это обновление безопасности, которая также включает ранее выпущенные (CU9) и накопительным Обновлением для [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3035.2. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4293805 ](https://support.microsoft.com/help/4293805).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3035.2-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm)| 
| Пакет SLES RPM | 14.0.3035.2-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3035.2-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3035.2-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3035.2-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3035.2-1_amd64.deb)<br/> |

## <a id="GDR2"></a> GDR2 (августа 2018 г.)

Это обновление безопасности, содержащую только исправления безопасности GDR2 (и GDR1) для [!INCLUDE[ssSQL17](../includes/sssql17-md.md)].  [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.2002.14. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4293803 ](https://support.microsoft.com/help/4293803).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.2002.14-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.2002.14-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.2002.14-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2002.14-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2002.14-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2002.14-1_amd64.deb) |

## <a id="CU9"></a> CU9 (июля 2018 г.)

Это — это накопительный пакет обновления 9 (CU9) версия [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3030.27. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4341265 ](https://support.microsoft.com/help/4341265).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3030.27-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3030.27-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3030.27-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3030.27-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3030.27-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3030.27-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU8"></a> CU8 (июня 2018 г.)

Это — это накопительный пакет обновления 8 (CU8) версия [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3029.16. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4338363 ](https://support.microsoft.com/help/4338363).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3029.16-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3029.16-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3029.16-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3029.16-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3029.16-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3029.16-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU7"></a> Накопительным пакетом обновления 7 (мая 2018 г.)

Это выпуск накопительного пакета обновления 7 (CU7) [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3026.27. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4229789 ](https://support.microsoft.com/help/4229789).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3026.27-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3026.27-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3026.27-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a> CU6 (апреля 2018 г.)

Это — это накопительный пакет обновления 6 (CU6) версия [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3025.34. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4101464 ](https://support.microsoft.com/help/4101464).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3025.34-3 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3025.34-3 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3025.34-3 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a> CU5 (марта 2018 г.)

Это накопительное обновление 5 (CU5) версия [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3023.8. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4092643 ](https://support.microsoft.com/help/4092643).

### <a name="known-upgrade-issue"></a>Известные проблемы

При обновлении с предыдущего выпуска до CU5, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] могут не запускаться со следующей ошибкой:

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

Чтобы устранить эту ошибку, включите агента SQL Server и перезапустите [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , выполнив следующие команды:

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl start mssql-server
```

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3023.8-5 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3023.8-5 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3023.8-5 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3023.8-5_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3023.8-5_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3023.8-5_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU4"></a> Накопительным пакетом обновления 4 (февраля 2018 г.)

Это — это накопительный пакет обновления 4 (CU4) версия [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3022.28. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4056498 ](https://support.microsoft.com/help/4056498).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

> [!NOTE]
> Начиная с накопительным пакетом обновления 4 агента SQL Server больше не устанавливается как отдельный пакет. Он устанавливается с пакетом ядра и должны быть доступны для использования.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3022.28-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3022.28-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3022.28-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3022.28-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3022.28-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3022.28-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GDR1"></a> GDR1 (января 2018 г.)

Это обновление системы безопасности, который содержит исключительно GDR1, исправления безопасности для [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.2000.63. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4057122 ](https://support.microsoft.com/help/4057122).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.2000.63-3 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.2000.63-3 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.2000.63-3 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2000.63-3_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2000.63-3_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2000.63-3_amd64.deb) |

## <a id="CU3"></a> Накопительным пакетом обновления 3 (января 2018 г.)

Это накопительный пакет обновления 3 (CU3) выпуска [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3015.40. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4052987 ](https://support.microsoft.com/help/4052987).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3015.40-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3015.40-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3015.40-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[Пакет Debian агента сервера SQL](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a> Накопительным пакетом обновления 2 (ноября 2017 г.)

Это — это накопительный пакет обновления 2 (CU2) версия [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3008.27. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4052574 ](https://support.microsoft.com/help/4052574).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3008.27-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3008.27-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3008.27-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[Пакет Debian агента сервера SQL](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a> CU1 (октября 2017 г.)

Это — это накопительный пакет обновления 1 (CU1) версия [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3006.16. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/KB4053439 ](https://support.microsoft.com/help/4038634).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3006.16-3 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3006.16-3 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3006.16-3 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[Пакет Debian агента сервера SQL](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a> Общедоступная версия (октября 2017 г.)

Это общая доступность (GA) выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.1000.169.

### <a name="package-details"></a>Сведения о пакете

Сведения о пакете и адреса для пакетов RPM и Debian, перечислены в следующей таблице. Обратите внимание на то, что вам нужно загружать эти пакеты непосредственно в том случае, если использовать описанные в следующих руководствах по установке:

- [Установите пакет SQL Server](sql-server-linux-setup.md)
- [Установите пакет Full-text Search](sql-server-linux-setup-full-text-search.md)
- [Установите пакет агента SQL Server](sql-server-linux-setup-sql-agent.md)
- [Установка служб SQL Server Integration Services](sql-server-linux-setup-ssis.md)

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.1000.169-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.1000.169-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.1000.169-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[Пакет Debian агента сервера SQL](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a name="Unsupported"></a> Неподдерживаемые функции и службы

Следующие функции и службы недоступны в Linux во время выпуска общедоступной версии. Со временем будет все чаще включена поддержка этих возможностей.

| Область | Неподдерживаемой функцией или службы |
|-----|-----|
| **Ядро СУБД** | Репликация транзакций |
| &nbsp; | Репликация слиянием |
| &nbsp; | Измененных данных (см. в разделе агента SQL Server) |
| &nbsp; | Базы данных Stretch |
| &nbsp; | PolyBase |
| &nbsp; | Распределенный запрос с подключениями независимых поставщиков |
| &nbsp; | Связанные серверы к источникам данных, отличных от [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL и т д.) |
| &nbsp; | Filetable FILESTREAM |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| &nbsp; | Buffer Pool Extension |
| **Агент SQL Server** |  Подсистемы: CmdExec, PowerShell, агент чтения очереди, служб SSIS, SSAS, SSRS |
| &nbsp; | Предупреждения |
| &nbsp; | Агент чтения журнала. |
| &nbsp; | Система отслеживания измененных данных (CDC) |
| &nbsp; | Управляемое резервное копирование |
| **Обеспечение высокого уровня доступности** | Зеркальное отображение базы данных  |
| **безопасность** | расширенное управление ключами |
| &nbsp; | Проверка подлинности AD для связанных серверов | 
| &nbsp; | Проверка подлинности AD для групп доступности (группы доступности) | 
| &nbsp; | инструменты сторонних AD (Centrify, Vintela, Powerbroker) | 
| **Службы** | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Службы Master Data Services |
| &nbsp; | Координатор распределенных транзакций (DTC) |

## <a name="known-issues"></a>Известные проблемы

В следующих разделах описаны известные проблемы, Общая доступность (GA) версия [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] в Linux.

#### <a name="general"></a>Общие

- Длина имени узла где [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] установленных должно превышать 15 знаков или меньше. 

    - **Разрешение**: Измените имя в /etc/hostname на что-то 15 или меньше знаков.

- Задания вручную системное время назад во времени приведет к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] остановить обновление внутреннего системного времени в пределах [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

    - **Разрешение**: Перезапустите [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

- Поддерживаются только один экземпляр установки.

    - **Разрешение**: Если вы хотите иметь более одного экземпляра на конкретном узле, рассмотрите возможность использования виртуальных машин или контейнеров Docker. 

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager не удается подключиться к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux.

- Язык по умолчанию **sa** входа в систему на английском языке.

    - **Разрешение**: Изменить язык **sa** входа с помощью **ALTER LOGIN** инструкции.

#### <a name="databases"></a>Базы данных

- С помощью служебной программы mssql-conf нельзя перемещать базы данных master. Другой системной базе данных можно перемещать с помощью mssql-conf.

- При восстановлении базы данных, которая была создана резервная в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на Windows, необходимо использовать **WITH MOVE** предложения в инструкции Transact-SQL.

- Распределенные транзакции, требующие службы координатора распределенных транзакций не поддерживаются в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] под управлением Linux. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Чтобы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] связанные серверы поддерживаются в том случае, если они включают DTC. Дополнительные сведения см. в разделе [распределенные транзакции, требующие службы координатора распределенных транзакций не поддерживаются в SQL Server на Linux](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/).

- Некоторые алгоритмы (шифров) для безопасности транспортного уровня (TLS) не работают должным образом с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux. Это приводит к ошибкам соединения, при попытке подключения к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], а также проблем с установлением соединения между репликами в групп высокого уровня доступности.

   - **Разрешение**: Изменить **mssql.conf** сценарий конфигурации для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux, чтобы отключить проблемных комплекты шифров, следующим образом:

      1. Добавьте следующий код /var/opt/mssql/mssql.conf.

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. Перезапустите [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью следующей команды.

      ```bash
      sudo systemctl restart mssql-server
      ```

- [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] нельзя восстановить базы данных на Windows, используйте In-memory OLTP [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] в Linux. Чтобы восстановить [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] базы данных, использующей OLTP в памяти, сначала обновить базы данных для [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] или [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] на Windows, прежде чем их [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на платформе Linux с помощью резервного копирования и восстановления или отсоединения и присоединения.

- Разрешение пользователя **ADMINISTER BULK OPERATIONS** не поддерживается на платформе Linux в настоящее время.

#### <a name="networking"></a>Работа с сетью

Функции, которые включают в себя исходящие соединения TCP из процесса sqlservr, такие как связанные серверы или группы доступности, может не работать, если выполняются следующие условия:

1. Целевой сервер указан как имя узла и не IP-адресом.

1. Исходный экземпляр имеет протокол IPv6 отключен в ядре. Чтобы проверить, имеет ли ваша система включен в ядре протокол IPv6, необходимо передать все следующие тесты:

   - `cat /proc/cmdline` будет печататься в командную строку загрузки текущего ядра. Выходные данные не должно содержать `ipv6.disable=1`.
   - / Proc/sys/net/ipv6/каталог должен существовать.
   - C программу, вызывающую `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` должны завершиться успешно - syscall должен возвращать fd! = -1 и не завершится ошибкой и EAFNOSUPPORT.

Конкретная ошибка зависит от компонента. Для связанных серверов это объявляется в качестве ошибки времени ожидания входа. Для групп доступности `ALTER AVAILABILITY GROUP JOIN` DDL на вторичной реплике завершится ошибкой после 5 минут к ошибке времени ожидания загрузки конфигурации.

Чтобы обойти эту проблему, выполните одно из следующих действий.

1. Используйте IP-адреса вместо имен узлов, чтобы указать целевой объект подключения TCP.

1. Включите протокол IPv6 в ядре, удалив `ipv6.disable=1` из cmdline загрузки. Способ сделать это зависит от дистрибутива Linux и загрузчик, например grub. Если вы хотите IPv6 должно быть отключено, вы все еще можете отключить его, задав `net.ipv6.conf.all.disable_ipv6 = 1` в `sysctl` конфигурации (например `/etc/sysctl.conf`). Это будет по-прежнему предотвратить получение IPv6-адрес сетевого адаптера компьютера, но разрешить работу с помощью функций sqlservr.

#### <a name="network-file-system-nfs"></a>Сетевой файловой системы (NFS)
Если вы используете **сетевой файловой системы (NFS)** удаленные общие ресурсы в рабочей среде, ознакомьтесь со следующими требованиями поддержки:

- Использование NFS версии **4.2 или более поздней версии**. Более старые версии NFS не поддерживают необходимые функции, такие как fallocate и создания разреженный файл, общие для современных файловых систем.
- Найдите только **/var/opt/mssql** каталоги на подключения NFS. Других файлов, таких как [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] системные файлы и не поддерживаются.
- Убедитесь, что NFS-клиенты использовать параметр «nolock», при подключении к удаленной общей папке.

#### <a name="localization"></a>Локализация

- Если язык не английский (en_us) во время установки, необходимо использовать кодировку UTF-8 в сеансе bash или окне терминала. Если используется кодировка ASCII, может появиться следующее сообщение об ошибке:

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Если нельзя использовать кодировку UTF-8, запустите программу установки, с помощью переменной среды MSSQL_LCID для указания на выбранном языке.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- При запуске программы установки mssql-conf и выполнению локализованной установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], после локализованного текста, «Настройка SQL Server …» отображаются неверные символы национального алфавита. Или, для установок на основе Нелатинские могут отсутствовать предложения полностью. Отсутствует предложение должен отображать локализованную следующую строку: «Идентификатор Процесса лицензирования успешно обработан. Новый выпуск [\<имя\> edition]». Эта строка представляет собой выходные данные только в информационных целях и следующей [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] накопительное обновление решает эту проблему для всех языков. Это не влияет на установке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] любым способом. 

#### <a name="full-text-search"></a>Компонент Full-text Search

- В этом выпуске, включая фильтры для документов Office доступны не все фильтры. Список поддерживаемых фильтров, см. в разделе [установить SQL Server Full-Text Search в Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a id="ssis"></a> Службы SQL Server Integration Services

- **Mssql-server находится** пакет не поддерживается в SUSE в этом выпуске. В настоящее время поддерживается в Ubuntu и на Red Hat Enterprise Linux (RHEL).

- С помощью [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на Linux CTP 2.1 обновления и более поздних версиях [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] пакеты могут использовать подключения ODBC в Linux. Эта функциональность была протестирована с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и драйверы MySQL ODBC, но также предполагается, что для работы с любой драйвер ODBC Юникода, отслеживающее спецификации ODBC. Во время разработки можно предоставить имя DSN или строки подключения для подключения к данным ODBC; Можно также использовать проверку подлинности Windows. Дополнительные сведения см. в разделе [записи блога о выходе поддержки ODBC в Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Следующие функции не поддерживаются в этом выпуске при запуске пакетов служб SSIS в Linux:
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] База данных каталога
  - Выполнение запланированного пакетов с агента SQL Server
  - Проверка подлинности Windows
  - Компоненты независимых производителей
  - Система отслеживания измененных данных (CDC)
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Горизонтальное масштабирование
  - Пакет дополнительных компонентов Azure для служб SSIS
  - Поддержка Hadoop и HDFS
  - Соединитель Microsoft Connector для SAP BW

Список встроенных компонентов служб SSIS, пока не поддерживаются, или, которые поддерживаются с ограничениями, см. в разделе [ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md#components).

Дополнительные сведения о службах SSIS на платформе Linux см. в разделе со следующими статьями:
-   [Блог блога с объявлением о поддержке SSIS для Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Установка SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md)
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)

#### <a id="ssms"></a> SQL Server Management Studio (SSMS)

Следующие ограничения применяются к [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] на Windows, подключенных к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщик данных в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] не поддерживаются. 

- [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Компоненты пользовательского интерфейса, проверки подлинности Windows или параметры журнала событий Windows не работают с Linux. Эти функции по-прежнему можно использовать с другими параметрами, например имена входа SQL. 

- Невозможно изменить количество файлов журнала для хранения.

## <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. в разделе следующих кратких руководств:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустить в Docker](quickstart-install-connect-ubuntu.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [Запуск и подключение — облако](quickstart-install-connect-clouds.md)

Ответы на часто задаваемые вопросы см. в разделе [SQL Server на Linux часто задаваемые вопросы о](sql-server-linux-faq.md).
