---
title: Заметки о выпуске для SQL Server 2017 на платформе Linux | Документация Майкрософт
description: В этой статье содержатся заметки о выпуске и поддерживаемые функции для SQL Server 2017 на платформе Linux. Заметки о выпуске включены для последнего выпуска и несколько предыдущих выпусков.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 08/14/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: d21f9edbc35ecf8f13d6f96f1d4f3ec9c85f31e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752452"
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Заметки о выпуске для SQL Server 2017 в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Следующие заметки о выпуске применяются к SQL Server 2017 на платформе Linux. В этой статье разбивается на разделы для каждого выпуска. Выпуск общедоступной версии подробные поддерживаемости и известные проблемы в списке. Каждый пакет обновления (CU) или выпуска для общего распространения (GDR) имеет ссылки поддержки статьи, описывающие CU изменения, а также ссылки на Linux, файлы для загрузки пакета.

> [!TIP]
> Эти заметки о выпуске предназначены специально для выпусков SQL Server 2017. Дополнительные сведения о новом выпуске предварительной версии SQL Server 2019 см. в разделе [заметки о выпуске для предварительной версии SQL Server 2019 в Linux](sql-server-linux-release-notes-2019.md?view=sql-server-ver15).

## <a name="supported-platforms"></a>Поддерживаемые платформы

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 или 7.4, рабочая станция, сервер и рабочего стола | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server до версии 12 SP2 | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Docker Engine 1.8 + на Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!TIP]
> Дополнительные сведения см. в [требования к системе](sql-server-linux-setup.md#system) для SQL Server в Linux. Последнюю политику поддержки для SQL Server 2017, см. в разделе [политики технической поддержки для Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Инструменты

Большинство существующих клиентских средств, предназначенных для SQL Server без проблем можете ориентироваться на SQL Server на Linux. Некоторые средства могут занимать определенную версию для работы с Linux. Полный список средств SQL Server, см. в разделе [SQL средства и служебные программы для SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>История выпусков

Ниже перечислены История выпусков SQL Server 2017.

| Выпуск               | Версия       | Дата выпуска |
|-----------------------|---------------|--------------|
| [CU11](#CU11)         | 14.0.3038.14  | 2018-09-20   |
| [CU10](#CU10)         | 14.0.3037.1   | 2018-08-27   |
| [CU9 GDR2](#CU9-GDR2) | 14.0.3035.2   | 2018-08-18   |
| [GDR2](#GDR2)         | 14.0.2002.14  | 2018-08-18   |
| [CU9](#CU9)           | 14.0.3030.27  | 2018-07-18   |
| [CU8](#CU8)           | 14.0.3029.16  | 2018-06-21   |
| [НАКОПИТЕЛЬНЫМ ПАКЕТОМ ОБНОВЛЕНИЯ 7](#CU7)           | 14.0.3026.27  | 2018-05-24   |
| [CU6](#CU6)           | 14.0.3025.34  | 2018-04-19   |
| [CU5](#CU5)           | 14.0.3023.8   | 2018-03-20   |
| [CU4](#CU4)           | 14.0.3022.28  | 2018-02-20   |
| [CU3](#CU3)           | 14.0.3015.40  | 2018-01-03   |
| [GDR1](#GDR1)         | 14.0.2000.63  | 2018-01-03   |
| [CU2](#CU2)           | 14.0.3008.27  | 2017-11-28   |
| [CU1](#CU1)           | 14.0.3006.16  | 2017-10-24   |
| [ОБЩЕДОСТУПНАЯ ВЕРСИЯ](#GA)             | 14.0.1000.169 | 2017-10-02   |

## <a id="cuinstall"></a> Установка обновлений

Если вы настроили хранилище накопительное обновление (**mssql-server-2017**), то вы получите последнюю версию пакетов и накопительным Обновлением SQL Server, при выполнении новых установок. Накопительное обновление репозитория по умолчанию для всех статей пакет установки для SQL Server в Linux. Если вы настроили репозиторий GDR (**mssql-server-2017-gdr**), вы получите только критические обновления, выпущенные с момента выхода общедоступной версии. Если вам требуется контейнера Docker и накопительным Обновлением обновления GDR, см. официальные образы для [Microsoft SQL Server в Linux для подсистемы Docker](https://hub.docker.com/r/microsoft/mssql-server). Дополнительные сведения о конфигурации хранилища, см. в разделе [Настройка репозиториев для SQL Server в Linux](sql-server-linux-change-repo.md).

При обновлении существующих пакетов SQL Server, выполните команду соответствующие обновления для каждого пакета получить новейший пакет CU. Инструкции по обновлению, определенных для каждого пакета см. следующие руководства по установке:

- [Установите пакет SQL Server](sql-server-linux-setup.md#upgrade)
- [Установите пакет Full-text Search](sql-server-linux-setup-full-text-search.md)
- [Установка служб SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Включить агент SQL Server](sql-server-linux-setup-sql-agent.md)

## <a id="CU11"></a> CU11 (сентября 2018 г.)

Это накопительное обновление 11 (CU11) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3038.14. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/en-us/help/4462262 ](https://support.microsoft.com/en-us/help/4462262).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3038.14-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3038.14-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3038.14-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3038.14-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU10"></a> CU10 (августа 2018 г.)

Это накопительный пакет обновления 10 (CU10) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3037.1. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/en-us/help/4342123 ](https://support.microsoft.com/en-us/help/4342123).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3037.1-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3037.1-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3037.1-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3037.1-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU9-GDR2"></a> CU9-GDR2 (августа 2018 г.)

Это обновление безопасности, которая также включает ранее выпущенные (CU9) и накопительным Обновлением для SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3035.2. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/en-us/help/4293805 ](https://support.microsoft.com/en-us/help/4293805).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3035.2-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm)| 
| Пакет SLES RPM | 14.0.3035.2-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3035.2-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3035.2-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3035.2-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3035.2-1_amd64.deb)<br/> |

## <a id="GDR2"></a> GDR2 (августа 2018 г.)

Это обновление безопасности, которое включает только исправления безопасности GDR2 (и GDR1) для SQL Server 2017.  Версия ядра SQL Server для этого выпуска — 14.0.2002.14. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/en-us/help/4293803 ](https://support.microsoft.com/en-us/help/4293803).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.2002.14-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.2002.14-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.2002.14-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2002.14-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2002.14-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2002.14-1_amd64.deb) |

## <a id="CU9"></a> CU9 (июля 2018 г.)

Это накопительный пакет обновления 9 (CU9) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3030.27. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/en-us/help/4341265 ](https://support.microsoft.com/en-us/help/4341265).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3030.27-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3030.27-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3030.27-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3030.27-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3030.27-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3030.27-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU8"></a> CU8 (июня 2018 г.)

Это накопительный пакет обновления 8 (CU8) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3029.16. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/en-us/help/4338363 ](https://support.microsoft.com/en-us/help/4338363).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3029.16-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3029.16-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3029.16-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3029.16-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3029.16-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3029.16-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU7"></a> Накопительным пакетом обновления 7 (мая 2018 г.)

Это накопительный пакет обновления 7 (CU7) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3026.27. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/en-us/help/4229789 ](https://support.microsoft.com/en-us/help/4229789).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3026.27-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3026.27-2 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3026.27-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a> CU6 (апрель 2018 г.)

Это накопительный пакет обновления 6 (CU6) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3025.34. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4101464 ](https://support.microsoft.com/help/4101464).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3025.34-3 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3025.34-3 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3025.34-3 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a> CU5 (март 2018 г.)

Это накопительное обновление 5 (CU5) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3023.8. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4092643 ](https://support.microsoft.com/help/4092643).

### <a name="known-upgrade-issue"></a>Известные проблемы

При обновлении с предыдущего выпуска до CU5, SQL Server не запустится со следующей ошибкой:

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

Чтобы устранить эту ошибку, включите агента SQL Server и перезапустите SQL Server с помощью следующих команд:

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

## <a id="CU4"></a> Накопительным пакетом обновления 4 (февраль 2018 г.)

Это накопительный пакет обновления 4 (CU4) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3022.28. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/en-us/help/4056498 ](https://support.microsoft.com/en-us/help/4056498).

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

Это обновление безопасности, который содержит исключительно GDR1, исправления безопасности для SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.2000.63. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/en-us/help/4057122 ](https://support.microsoft.com/en-us/help/4057122).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.2000.63-3 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.2000.63-3 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.2000.63-3 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2000.63-3_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2000.63-3_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2000.63-3_amd64.deb) |

## <a id="CU3"></a> Накопительным пакетом обновления 3 (января 2018 г.)

Это накопительный пакет обновления 3 (CU3) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3015.40. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/en-us/help/4052987 ](https://support.microsoft.com/en-us/help/4052987).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3015.40-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3015.40-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3015.40-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[Пакет Debian агента сервера SQL](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a> Накопительным пакетом обновления 2 (ноябрь 2017 г.)

Это накопительный пакет обновления 2 (CU2) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3008.27. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/4052574 ](https://support.microsoft.com/help/4052574).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3008.27-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3008.27-1 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3008.27-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[Пакет Debian агента сервера SQL](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a> CU1 (октябрь 2017 г.)

Это накопительный пакет обновления 1 (CU1) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.3006.16. Сведения о исправления и улучшения в этом выпуске, см. в разделе [ https://support.microsoft.com/help/KB4053439 ](https://support.microsoft.com/help/4038634).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вручную или автономном режиме вы можете скачать пакеты RPM и Debian с информацией в следующей таблице:

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3006.16-3 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3006.16-3 | [пакет RPM ядра MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM поиска полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3006.16-3 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[Пакет Debian агента сервера SQL](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a> Общедоступной версии (октябрь 2017 г.)

Это общая доступность (GA) выпуск SQL Server 2017. Версия ядра SQL Server для этого выпуска — 14.0.1000.169.

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
| **Компонент Database engine** | Репликация транзакций |
| &nbsp; | Репликация слиянием |
| &nbsp; | Базы данных Stretch |
| &nbsp; | PolyBase |
| &nbsp; | Распределенный запрос с подключениями независимых поставщиков |
| &nbsp; | Связанные серверы к источникам данных, отличных от SQL Server |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL и т д.) |
| &nbsp; | Filetable FILESTREAM |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| &nbsp; | Buffer Pool Extension |
| **Агент SQL Server** |  Подсистемы: CmdExec, PowerShell, агент чтения очереди, служб SSIS, SSAS, SSRS |
| &nbsp; | видны узлы |
| &nbsp; | Агент чтения журнала. |
| &nbsp; | Система отслеживания измененных данных |
| &nbsp; | Управляемое резервное копирование |
| **Обеспечение высокого уровня доступности** | Зеркальное отображение базы данных  |
| **безопасность** | расширенное управление ключами |
| &nbsp; | Проверка подлинности AD для связанных серверов | 
| &nbsp; | Проверка подлинности AD для групп доступности (группы доступности) | 
| &nbsp; | инструменты сторонних AD (Centrify, Vintela, Powerbroker) | 
| **службы** | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Службы Master Data Services |
| &nbsp; | Координатор распределенных транзакций (DTC) |

## <a name="known-issues"></a>Известные проблемы

Ниже описываются известные проблемы, Общая доступность (GA) версия SQL Server 2017 в Linux.

#### <a name="general"></a>Общие

- Обновление до выпуска общедоступной версии SQL Server 2017 поддерживается только из CTP 2.1 или более поздней версии. 

- Длина имени узла, где SQL Server, установленных должно превышать 15 знаков или меньше. 

    - **Разрешение**: измените имя в/etc/имя узла на что-то 15 или меньше знаков.

- Задания вручную системное время назад во времени приведет к SQL Server остановить обновление внутреннего системного времени в SQL Server.

    - **Разрешение**: перезапустите SQL Server.

- Поддерживаются только один экземпляр установки.

    - **Разрешение**: Если вы хотите иметь более одного экземпляра на конкретном узле, рассмотрите возможность использования виртуальных машин или контейнеров Docker. 

- Диспетчер конфигурации SQL Server не удается подключиться к SQL Server в Linux.

- Язык по умолчанию **sa** входа в систему на английском языке.

    - **Разрешение**: изменить язык **sa** входа с помощью **ALTER LOGIN** инструкции.

#### <a name="databases"></a>Базы данных

- С помощью служебной программы mssql-conf нельзя перемещать базы данных master. Другой системной базе данных можно перемещать с помощью mssql-conf.

- При восстановлении базы данных, которая была создана резервная в SQL Server в Windows, необходимо использовать **WITH MOVE** предложения в инструкции Transact-SQL.

- Распределенные транзакции, требующие службы координатора распределенных транзакций не поддерживаются в SQL Server на Linux. SQL Server до SQL Server, связанные серверы поддерживаются в том случае, если они включают DTC. Дополнительные сведения см. в разделе [распределенные транзакции, требующие службы координатора распределенных транзакций не поддерживаются в SQL Server на Linux](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/).

- Определенные алгоритмы (шифров) для безопасности транспортного уровня (TLS) не работают должным образом с SQL Server в Linux. Это приведет к сбоям подключения при попытке подключения к SQL Server, а также проблем с установлением соединения между репликами в групп высокого уровня доступности.

   - **Разрешение**: изменение **mssql.conf** сценарий конфигурации для SQL Server в Linux, чтобы отключить проблемных комплекты шифров, следующим образом:

      1. Добавьте следующий код /var/opt/mssql/mssql.conf.

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. Перезапустите SQL Server с помощью следующей команды.

      ```bash
      sudo systemctl restart mssql-server
      ```

- Невозможно восстановить базы данных SQL Server 2014 в Windows, используйте In-memory OLTP в SQL Server 2017 в Linux. Чтобы восстановить базу данных SQL Server 2014, которая в памяти OLTP, сначала обновите базы данных в SQL Server 2016 или SQL Server 2017 в Windows перед их перемещением SQL Server в Linux с помощью резервного копирования и восстановления или отсоединения и присоединения.

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
- Найдите только **/var/opt/mssql** каталоги на подключения NFS. Другие файлы, например системные файлы SQL Server и не поддерживаются.
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

- При установке mssql-conf и выполнения локализованной установки SQL Server, неправильные символы расширенного набора выводятся после локализованный текст, «Настройка SQL Server …». Или, для установок на основе Нелатинские могут отсутствовать предложения полностью. Отсутствует предложение должен отображать следующие Локализованная строка: «идентификатор Процесса лицензирования успешно обработан.  Новый выпуск [\<имя\> edition]». Эта строка выводится только в информационных целях и далее накопительное обновление SQL Server решает эту проблему для всех языков. Это не влияет на установки SQL Server любым способом. 

#### <a name="full-text-search"></a>Компонент Full-text Search

- В этом выпуске, включая фильтры для документов Office доступны не все фильтры. Список поддерживаемых фильтров, см. в разделе [установить SQL Server Full-Text Search в Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a id="ssis"></a> Службы SQL Server Integration Services

- **Mssql-server находится** пакет не поддерживается в SUSE в этом выпуске. В настоящее время поддерживается в Ubuntu и на Red Hat Enterprise Linux (RHEL).

- С помощью служб SSIS на Linux CTP 2.1 обновления и более поздних версий пакетов служб SSIS можно использовать подключения ODBC в Linux. Эта функциональность была протестирована с SQL Server и драйверы MySQL ODBC, но также должен работать с любой драйвер ODBC Юникода, отслеживающее спецификации ODBC. Во время разработки можно предоставить имя DSN или строки подключения для подключения к данным ODBC; Можно также использовать проверку подлинности Windows. Дополнительные сведения см. в разделе [записи блога о выходе поддержки ODBC в Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Следующие функции не поддерживаются в этом выпуске при запуске пакетов служб SSIS в Linux:
  - База данных каталога служб SSIS
  - Выполнение запланированного пакетов с агента SQL Server
  - Проверка подлинности Windows.
  - Компоненты независимых производителей
  - Система отслеживания измененных данных (CDC)
  - SSIS Scale Out
  - Пакет дополнительных компонентов Azure для служб SSIS
  - Поддержка Hadoop и HDFS
  - Соединитель Microsoft Connector для SAP BW

Список встроенных компонентов служб SSIS, пока не поддерживаются, или, которые поддерживаются с ограничениями, см. в разделе [ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md#components).

Дополнительные сведения о службах SSIS на платформе Linux см. в разделе со следующими статьями:
-   [Блог блога с объявлением о поддержке SSIS для Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Установка SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md)
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)

#### <a name="-a-idssmsa-sql-server-management-studio-ssms"></a>< a id = «ssms» ></a> SQL Server Management Studio (SSMS)

Для SSMS в Windows, подключенных к SQL Server для Linux применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщика данных в среде SSMS не поддерживаются. 

- Компоненты пользовательского интерфейса среды SSMS, проверка подлинности Windows или параметры журнала событий Windows не работают с Linux. Эти функции по-прежнему можно использовать с другими параметрами, например имена входа SQL. 

- Невозможно изменить количество файлов журнала для хранения.

## <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. в разделе следующих кратких руководств:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустить в Docker](quickstart-install-connect-ubuntu.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)
- [Запуск и подключение — облако](quickstart-install-connect-clouds.md)

Ответы на часто задаваемые вопросы см. в разделе [SQL Server на Linux часто задаваемые вопросы о](sql-server-linux-faq.md).
