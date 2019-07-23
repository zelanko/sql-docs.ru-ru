---
title: Заметки о выпуске для SQL Server 2017 в Linux
description: Эта статья содержит заметки о выпуске и поддерживаемые функции для SQL Server 2017, работающих в Linux. Заметки о выпуске включены для последней версии и нескольких предыдущих выпусков.
author: VanMSFT
ms.author: vanto
ms.date: 06/25/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: 5b6fce0bdde7e320eea0371125a61627652de80d
ms.sourcegitcommit: d667fa9d6f1c8035f15fdb861882bd514be020d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388410"
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Заметки о выпуске для SQL Server 2017 в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Следующие заметки о выпуске [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] применимы к работе в Linux. Эта статья разбивается на разделы для каждого выпуска. В общедоступном выпуске содержатся подробные сведения о поддержке и известных проблемах. Каждое накопительное обновление (CU) или выпуск общего распространения (GDR) содержит ссылку на статью поддержки, в которой описаны изменения CU, а также ссылки на загружаемые файлы пакета Linux.

> [!TIP]
> Эти заметки о выпуске [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] предназначены специально для выпусков. Дополнительные сведения о новом [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]см. в разделе Заметки о выпуске [для SQL Server 2019 предварительной версии в Linux](sql-server-linux-release-notes-2019.md?view=sql-server-ver15).

## <a name="supported-platforms"></a>Поддерживаемые платформы

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7,3, 7,4, 7,5 или 7,6 Server | XFS или EXT4 | [Руководства по установке](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server версии 12, SP2 | XFS или EXT4 | [Руководства по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04 LTS | XFS или EXT4 | [Руководства по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема DOCKER 1.8 + в Windows, Mac или Linux | Н/Д | [Руководства по установке](quickstart-install-connect-docker.md) | 

> [!TIP]
> Дополнительные сведения см. в требованиях к [системе](sql-server-linux-setup.md#system) для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux. Последнюю политику поддержки для [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]см. в разделе [Политика технической поддержки для Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Инструменты

Большинство существующих клиентских средств, предназначенных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для эффективной [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] работы в Linux, могут эффективно работать. Некоторые средства могут иметь определенные требования к версии для работы с Linux. Полный список [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] средств см. в разделе [средства и служебные программы SQL для SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Журнал выпусков

В следующей таблице перечислены журналы выпусков [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]для.

| Выпуск               | Version       | Дата выпуска |
|-----------------------|---------------|--------------|
| [CU15](#CU15)         | 14.0.3162.1   | 2019-05-23   |
| [CU14](#CU14)         | 14.0.3076.1   | 2019-03-25   |
| [CU13](#CU13)         | 14.0.3048.4   | 2018-12-18   |
| [CU12](#CU12)         | 14.0.3045.24  | 2018-10-24   |
| [CU11](#CU11)         | 14.0.3038.14  | 2018-09-20   |
| [CU10](#CU10)         | 14.0.3037.1   | 2018-08-27   |
| [CU9 — GDR2](#CU9-GDR2) | 14.0.3035.2   | 2018-08-18   |
| [GDR2](#GDR2)         | 14.0.2002.14  | 2018-08-18   |
| [CU9](#CU9)           | 14.0.3030.27  | 2018-07-18   |
| [CU8](#CU8)           | 14.0.3029.16  | 2018-06-21   |
| [И НАКОПИТЕЛЬНЫМ](#CU7)           | 14.0.3026.27  | 2018-05-24   |
| [CU6](#CU6)           | 14.0.3025.34  | 2018-04-19   |
| [CU5](#CU5)           | 14.0.3023.8   | 2018-03-20   |
| [CU4](#CU4)           | 14.0.3022.28  | 2018-02-20   |
| [CU3](#CU3)           | 14.0.3015.40  | 2018-01-03   |
| [GDR1](#GDR1)         | 14.0.2000.63  | 2018-01-03   |
| [CU2](#CU2)           | 14.0.3008.27  | 2017-11-28   |
| [CU1](#CU1)           | 14.0.3006.16  | 2017-10-24   |
| [ОБЩЕДОСТУПНОЙ ВЕРСИИ](#GA)             | 14.0.1000.169 | 2017-10-02   |

## <a id="cuinstall"></a>Установка обновлений

Если вы настроили репозиторий Cu (**MSSQL-Server-2017**), при выполнении новых установок вы получите последнюю [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] версию Cu пакетов. По умолчанию для всех статей [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] по установке пакетов в Linux используется репозиторий Cu. Если вы настроили репозиторий GDR (**MSSQL-Server-2017-GDR**), вы получите только критические обновления безопасности, выпущенные с момента выхода общедоступной версии. Если требуются обновления для CU контейнеров DOCKER или GDR, см. раздел официальные образы для [Microsoft SQL Server на Linux для подсистемы DOCKER](https://hub.docker.com/r/microsoft/mssql-server). Дополнительные сведения о конфигурации репозитория см. в статье [Настройка репозиториев для SQL Server на Linux](sql-server-linux-change-repo.md).

При обновлении существующих [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] пакетов выполните соответствующую команду обновления для каждого пакета, чтобы получить последнюю Cu. Конкретные инструкции по обновлению для каждого пакета см. в следующих руководствах по установке:

- [Установка пакета SQL Server](sql-server-linux-setup.md#upgrade)
- [Установка пакета полнотекстового поиска](sql-server-linux-setup-full-text-search.md)
- [Установка служб SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Включить агент SQL Server](sql-server-linux-setup-sql-agent.md)

## <a id="CU15"></a>CU15 (Май 2019)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 15 (CU15). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3162.1. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/en-us/help/4498951](https://support.microsoft.com/en-us/help/4498951)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3162.1-1 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3162.1-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3162.1-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3162.1-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3162.1-1 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3162.1-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3162.1-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3162.1-1.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3162.1-1 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3162.1-1_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3162.1-1_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3162.1-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU14"></a>CU14 (Мар 2019)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 14 (CU14). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3076.1. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4484710](https://support.microsoft.com/help/4484710)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3076.1-2 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3076.1-2 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3076.1-2 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3076.1-2_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3076.1-2_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3076.1-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU13"></a>CU13 (декабрь 2018)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 13 (CU13). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3048.4. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4466404](https://support.microsoft.com/help/4466404)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3048.4-1 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3048.4-1 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3048.4-1 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3048.4-1_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3048.4-1_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3048.4-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU12"></a>CU12 (Oct 2018)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 12 (CU12). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3045.24. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4464082](https://support.microsoft.com/help/4464082)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3045.24-1 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3045.24-1 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3045.24-1 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3045.24-1_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3045.24-1_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3045.24-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU11"></a>CU11 (Сентябрь 2018)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 11 (CU11). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3038.14. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4462262](https://support.microsoft.com/help/4462262)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3038.14-2 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3038.14-2 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3038.14-2 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3038.14-2_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3038.14-2_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3038.14-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU10"></a>CU10 (2018 августа)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 10 (Cu10). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3037.1. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4342123](https://support.microsoft.com/help/4342123)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3037.1-2 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3037.1-2 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3037.1-2 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3037.1-2_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU9-GDR2"></a>CU9-GDR2 (2018 августа)

Это обновление безопасности, которое также включает ранее выпущенную CU (CU9) для [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3035.2. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4293805](https://support.microsoft.com/help/4293805)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3035.2-1 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm)| 
| Пакет SLES RPM | 14.0.3035.2-1 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3035.2-1 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3035.2-1_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3035.2-1_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3035.2-1_amd64.deb)<br/> |

## <a id="GDR2"></a>GDR2 (2018 августа)

Это обновление для системы безопасности включает только исправления безопасности GDR2 (и GDR1) для [!INCLUDE[ssSQL17](../includes/sssql17-md.md)].  [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.2002.14. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4293803](https://support.microsoft.com/help/4293803)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.2002.14-1 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.2002.14-1 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.2002.14-1 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2002.14-1_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2002.14-1_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2002.14-1_amd64.deb) |

## <a id="CU9"></a>CU9 (Июл 2018)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 9 (CU9). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3030.27. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4341265](https://support.microsoft.com/help/4341265)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3030.27-1 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3030.27-1 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3030.27-1 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3030.27-1_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3030.27-1_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3030.27-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU8"></a>CU8 (июнь 2018)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 8 (CU8). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3029.16. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4338363](https://support.microsoft.com/help/4338363)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3029.16-1 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3029.16-1 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3029.16-1 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3029.16-1_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3029.16-1_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3029.16-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU7"></a>И НАКОПИТЕЛЬНЫМ (Май 2018)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 7 (и накопительным). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3026.27. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4229789](https://support.microsoft.com/help/4229789)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3026.27-2 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3026.27-2 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3026.27-2 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a>CU6 (Апрель 2018)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 6 (CU6). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3025.34. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4101464](https://support.microsoft.com/help/4101464)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3025.34-3 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3025.34-3 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3025.34-3 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a>CU5 (Мар 2018)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 5 (CU5). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3023.8. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4092643](https://support.microsoft.com/help/4092643)см. в разделе.

### <a name="known-upgrade-issue"></a>Известная ошибка обновления

При обновлении предыдущей версии до CU5 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может не запуститься со следующей ошибкой:

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

Чтобы устранить эту ошибку, включите агент SQL Server и перезапустите [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью следующих команд:

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl start mssql-server
```

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3023.8-5 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3023.8-5 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3023.8-5 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3023.8-5_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3023.8-5_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3023.8-5_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU4"></a>CU4 (Фев 2018)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 4 (CU4). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3022.28. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4056498](https://support.microsoft.com/help/4056498)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

> [!NOTE]
> Начиная с CU4, агент SQL Server больше не устанавливается как отдельный пакет. Он устанавливается вместе с пакетом Engine и должен быть включен для использования.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3022.28-2 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3022.28-2 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3022.28-2 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3022.28-2_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3022.28-2_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3022.28-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GDR1"></a>GDR1 (Янв 2018)

Это обновление безопасности, которое включает в себя только исправления [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]безопасности GDR1. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.2000.63. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4057122](https://support.microsoft.com/help/4057122)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.2000.63-3 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.2000.63-3 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.2000.63-3 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2000.63-3_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2000.63-3_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2000.63-3_amd64.deb) |

## <a id="CU3"></a>CU3 (Янв 2018)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 3 (CU3). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3015.40. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4052987](https://support.microsoft.com/help/4052987)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3015.40-1 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM агент SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3015.40-1 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM агент SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3015.40-1 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[агент SQL Server пакет Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a>CU2 (2017 ноября)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 2 (CU2). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3008.27. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/4052574](https://support.microsoft.com/help/4052574)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3008.27-1 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM агент SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3008.27-1 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM агент SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3008.27-1 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[агент SQL Server пакет Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a>CU1 (Oct 2017)

Это накопительный выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]обновления 1 (CU1). [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.3006.16. Сведения об исправлениях и улучшениях в этом выпуске [https://support.microsoft.com/help/KB4053439](https://support.microsoft.com/help/4038634)см. в разделе.

### <a name="package-details"></a>Сведения о пакете

Для установки вручную или автономного пакета можно загрузить пакеты RPM и Debian со сведениями, приведенными в следующей таблице.

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.3006.16-3 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM агент SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3006.16-3 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM агент SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.3006.16-3 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[агент SQL Server пакет Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a>GA (Oct 2017)

Это выпуск [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]общедоступной версии. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Версия для этого выпуска — 14.0.1000.169.

### <a name="package-details"></a>Сведения о пакете

Сведения о пакете и адреса загрузки для пакетов RPM и Debian перечислены в следующей таблице. Обратите внимание, что эти пакеты не нужно скачивать напрямую, если вы выполните действия, описанные в следующих руководствах по установке:

- [Установка пакета SQL Server](sql-server-linux-setup.md)
- [Установка пакета полнотекстового поиска](sql-server-linux-setup-full-text-search.md)
- [Установка пакета агент SQL Server](sql-server-linux-setup-sql-agent.md)
- [Установка служб SQL Server Integration Services](sql-server-linux-setup-ssis.md)

| Пакет | Версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM для Red Hat | 14.0.1000.169-2 | [Пакет RPM для модуля](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM агент SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.1000.169-2 | [пакет обновления ядра СУБД MSSQL-Server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM высокого уровня доступности](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM для полнотекстового поиска](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM агент SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Пакет Ubuntu 16,04 Debian | 14.0.1000.169-2 | [Пакет Debian Engine](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[Пакет Debian высокого уровня доступности](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[Пакет Debian для полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[агент SQL Server пакет Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a name="Unsupported"></a>Неподдерживаемые функции & Services

Следующие функции и службы недоступны в Linux во время общедоступного выпуска. Поддержка этих функций будет постоянно включена с течением времени.

| Область | Неподдерживаемая функция или служба |
|-----|-----|
| **Ядро СУБД** | Репликация транзакций |
| &nbsp; | Репликация слиянием |
| &nbsp; | Отслеживание измененных данных (см. агент SQL Server) |
| &nbsp; | База данных Stretch |
| &nbsp; | PolyBase |
| &nbsp; | Распределенный запрос с сторонними подключениями |
| &nbsp; | Связанные серверы с источниками данных, отличными от[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL и т. д.) |
| &nbsp; | FileTable, FILESTREAM |
| &nbsp; | Сборки CLR с набором разрешений EXTERNAL_ACCESS или UNSAFE |
| &nbsp; | Buffer Pool Extension |
| **Агент SQL Server** |  Подсистемы CmdExec, PowerShell, агент чтения очереди, SSIS, SSAS, SSRS |
| &nbsp; | Предупреждения |
| &nbsp; | Агент чтения журнала. |
| &nbsp; | Система отслеживания измененных данных (CDC) |
| &nbsp; | Управляемое резервное копирование |
| **Обеспечение высокого уровня доступности** | Зеркальное отображение базы данных  |
| **безопасность** | расширенное управление ключами |
| &nbsp; | Проверка подлинности AD для связанных серверов | 
| &nbsp; | Проверка подлинности AD для групп доступности (групп доступности) | 
| &nbsp; | сторонние средства AD (Centrify, Vintela, Поверброкер) | 
| **Обслуживание** | Обозреватель SQL Server |
| &nbsp; | Службы SQL Server R |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Службы Master Data Services |
| &nbsp; | Координатор распределенных транзакций (DTC) |

## <a name="known-issues"></a>Известные проблемы

В следующих разделах описаны известные проблемы с выпуском общедоступной версии [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] в Linux.

#### <a name="general"></a>Общие

- Длина имени узла, в которой [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] установлено значение, не должна превышать 15 символов. 

    - **Решение**: Измените имя в/ЕТК/хостнаме на не более 15 символов.

- Ручное задание системного времени в обратном времени приведет [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] к прекращению обновления внутреннего системного времени в. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]

    - **Решение**: Перезапустите [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

- Поддерживаются только экземпляры с одним экземпляром.

    - **Решение**: Если на одном узле требуется несколько экземпляров, рассмотрите возможность использования виртуальных машин или контейнеров DOCKER. 

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Configuration Manager не удается подключиться [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] к в Linux.

- Язык по умолчанию для имени входа **SA** — английский.

    - **Решение**: Измените язык имени входа **SA** с помощью инструкции **ALTER LOGIN** .

#### <a name="databases"></a>Базы данных

- База данных master не может быть перемещена с помощью служебной программы MSSQL-CONF. Другие системные базы данных можно перемещать с помощью MSSQL-CONF.

- При восстановлении базы данных, для которой была создана [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] резервная копия в Windows, необходимо использовать предложение **WITH MOVE** в инструкции Transact-SQL.

- Распределенные транзакции, для которых необходима служба Microsoft координатор распределенных транзакций, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не поддерживаются в ОС Linux. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]поддерживается [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для связанных серверов, если они не используют DTC. Дополнительные сведения см. в разделе распределенные транзакции, для [которых служба Microsoft координатор распределенных транзакций не поддерживается в SQL Server, работающих под управлением Linux](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/).

- Некоторые алгоритмы (комплекты шифров) для защиты транспортного уровня (TLS) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не работают должным образом в Linux. Это приводит к сбоям подключения при попытке подключения к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], а также к проблемам подключения между репликами в группах с высоким уровнем доступности.

   - **Решение**: Измените скрипт конфигурации **MSSQL. conf** для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux, чтобы отключить проблемные комплекты шифров, выполнив следующие действия.

      1. Добавьте следующий объект в/Вар/ОПТ/мсскл/мсскл.конф.

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

- [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]базы данных в Windows, которые используют выполняющуюся в памяти OLTP, [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] нельзя восстановить в Linux. Чтобы восстановить [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] базу данных, использующую выполняющуюся в памяти OLTP, сначала обновите базы [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] данных до [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] или в Windows, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] прежде чем перемещать их в в Linux с помощью операции резервного копирования, восстановления или отсоединения.

- В настоящее время Linux не поддерживается для **управления групповыми операциями** с правами пользователя.

#### <a name="networking"></a>Работа с сетью

Функции, затрагивающие исходящие TCP-подключения из процесса sqlservr, такие как связанные серверы или группы доступности, могут не работать, если выполняются оба следующих условия.

1. Целевой сервер указывается в качестве имени узла, а не IP-адреса.

1. В ядре для экземпляра источника отключен протокол IPv6. Чтобы проверить, включена ли в системе поддержка протокола IPv6, необходимо выполнить все следующие тесты:

   - `cat /proc/cmdline`выводит на печать значение параметра Boot cmdline текущего ядра. Выходные данные не должны содержать `ipv6.disable=1`.
   - Каталог/proc/sys/NET/IPv6/должен существовать.
   - Программа на языке C, `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` которая вызывает метод, должна быть выполнена успешно — syscall должен возвращать объект демона! =-1 и не завершать его ошибкой с помощью еафносуппорт.

Точная ошибка зависит от функции. Для связанных серверов этот манифест является ошибкой времени ожидания входа. Для групп `ALTER AVAILABILITY GROUP JOIN` доступности DDL на вторичном сервере будет завершаться сбоем через 5 минут с ошибкой времени ожидания конфигурации загрузки.

Чтобы обойти эту ошибку, выполните одно из следующих действий.

1. Используйте IP-адреса вместо имен узлов, чтобы указать целевой объект подключения TCP.

1. Включите протокол IPv6 в ядре, удалив `ipv6.disable=1` в поле Boot cmdline. Способ этого зависит от дистрибутива Linux и загрузчика, например GRUB. Если необходимо отключить протокол IPv6, его можно отключить, задав `net.ipv6.conf.all.disable_ipv6 = 1` в конфигурации (например `/etc/sysctl.conf`, `sysctl` ). Это по-прежнему помешает сетевому адаптеру системы получить IPv6-адрес, но разрешить работу функций sqlservr.

#### <a name="network-file-system-nfs"></a>Сетевая файловая система (NFS)
При использовании удаленных общих папок **NFS** в рабочей среде Обратите внимание на следующие требования к поддержке.

- Используйте NFS версии **4,2 или более поздней**. Более старые версии NFS не поддерживают необходимые функции, такие как фаллокате и создание разреженных файлов, общие для современных файловых систем.
- Разместите только каталоги **/Вар/ОПТ/мсскл** на подключении NFS. Другие файлы, такие как [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] системные двоичные файлы, не поддерживаются.
- Убедитесь, что клиенты NFS используют параметр "NOLOCK" при подключении удаленной общей папки.

#### <a name="localization"></a>Локализация

- Если языковой стандарт не является английским (en_US) во время установки, необходимо использовать кодировку UTF-8 в сеансе bash или терминале. При использовании кодировки ASCII может появиться сообщение об ошибке следующего вида:

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Если вы не можете использовать кодировку UTF-8, запустите программу установки с помощью переменной среды MSSQL_LCID, чтобы указать выбранный язык.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- При выполнении программы установки MSSQL-conf и выполнении установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]на языке, отличном от английского, после локализованного текста отображаются неверные расширенные символы: "Настройка SQL Server...". Или для установок, отличных от латинских, предложение может отсутствовать полностью. В отсутствующем предложении должна отобразиться следующая локализованная строка: "Идентификатор процесса лицензирования успешно обработан. Новый выпуск — [\<имя\> выпуска]. Эта строка выводится только для информационных целей, а следующее [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] накопительное обновление будет устранено для всех языков. Это не влияет на успешное выполнение установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . 

#### <a name="full-text-search"></a>Компонент Full-text Search

- В этом выпуске доступны не все фильтры, включая фильтры для документов Office. Список поддерживаемых фильтров см. [в статье установка SQL Server полнотекстового поиска в Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a id="ssis"></a> Службы SQL Server Integration Services

- Пакет **MSSQL-Server-не** поддерживается в SuSE в этом выпуске. Сейчас она поддерживается в Ubuntu и на Red Hat Enterprise Linux (RHEL).

- При обновлении [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в Linux CTP 2,1 и более поздних версиях пакеты могут использовать подключения ODBC в Linux. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Эта функция была протестирована с драйверами ODBC для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и MySQL, но она также должна работать с любым драйвером ODBC для Юникода, который отслеживает спецификацию ODBC. Во время разработки можно указать либо имя DSN, либо строку подключения для подключения к данным ODBC. также можно использовать проверку подлинности Windows. Дополнительные сведения см. в записи [блога о поддержке ODBC в Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Следующие функции не поддерживаются в этом выпуске при запуске пакетов служб SSIS в Linux:
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]База данных каталога
  - Запланированное выполнение пакета агентом SQL
  - Проверка подлинности Windows
  - Сторонние компоненты
  - Система отслеживания измененных данных (CDC)
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]Scale Out
  - Пакет дополнительных компонентов Azure для служб SSIS
  - Поддержка Hadoop и HDFS
  - Соединитель Microsoft Connector для SAP BW

Список встроенных компонентов служб SSIS, которые в настоящее время не поддерживаются или поддерживаются с ограничениями, см. в статье [ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md#components).

Дополнительные сведения о службах SSIS в Linux см. в следующих статьях:
-   [Запись блога с объявлением о поддержке служб SSIS для Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Установка SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md)
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)

#### <a id="ssms"></a> SQL Server Management Studio (SSMS)

К [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Windows, подключенным к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ОС Linux, применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилище данных управления (MDW) и сборщик данных в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] не поддерживаются. 

- [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]Компоненты пользовательского интерфейса, имеющие параметры проверки подлинности Windows или журнала событий Windows, не работают с Linux. Эти функции по-прежнему можно использовать с другими параметрами, такими как имена входа SQL. 

- Число хранящихся файлов журнала не может быть изменено.

## <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, ознакомьтесь со следующими краткими руководствами.

- [Установка на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запуск в DOCKER](quickstart-install-connect-ubuntu.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [Запуск и подключение — облако](quickstart-install-connect-clouds.md)

Ответы на часто задаваемые вопросы см. в [SQL Server на Linux часто задаваемых](sql-server-linux-faq.md)вопросов.
