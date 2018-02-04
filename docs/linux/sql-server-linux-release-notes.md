---
title: "Заметки о выпуске для 2017 г. SQL Server в Linux | Документы Microsoft"
description: "В этом разделе содержатся заметки о выпуске и поддерживаемых функций для ОС Linux 2017 г. SQL Server. Заметки о выпуске включаются самым последним выпуском и несколько предыдущих выпусков."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/09/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.workload: Active
ms.openlocfilehash: 661c3797ef0881efd49921231c2899f5391e4e27
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Заметки о выпуске для 2017 г. SQL Server в Linux

Следующие замечания к выпуску применяются для ОС Linux 2017 г. SQL Server. Ниже раздел разбит на разделы для каждого выпуска. Выпуск общедоступной версии имеет подробные поддержки и известные проблемы в списке. Каждый выпуск накопительное обновление (CU) имеет ссылку поддержки раздел, описывающий CU изменения, а также ссылки для загрузки пакета Linux.

## <a name="supported-platforms"></a>Поддерживаемые платформы

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 или 7.4 станции, серверов и настольных компьютеров | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| Сервер Linux версии 12 SUSE Enterprise с пакетом обновления 2 | EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема docker 1.8 + в Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!TIP]
> Дополнительные сведения см. в статье [требования к системе для](sql-server-linux-setup.md#system) для SQL Server в Linux. Последние политика поддержки для SQL Server 2017 г. в разделе [политика технической поддержки для Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="supported-client-tools"></a>Поддерживаемые клиентские средства

| Инструмент | Минимальная версия |
|-----|-----|
| [SQL Server Management Studio (SSMS) для Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools для Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Код Visual Studio](https://code.visualstudio.com) с [mssql расширения](https://aka.ms/mssql-marketplace) | последние |

## <a name="release-history"></a>История выпусков

В следующей таблице перечислены журнал выпуска для 2017 г. SQL Server.

| Выпуск | Версия | Дата выпуска |
|-----|-----|-----|
| [CU3](#CU3) | 14.0.3015.40| 1-2018 |
| [CU2](#CU2) | 14.0.3008.27 | 11-2017 |
| [CU1](#CU1) | 14.0.3006.16 | 10-2017 |
| [GA](#GA) | 14.0.1000.169 | 10-2017 |

## <a id="cuinstall"></a>Как установить накопительные пакеты обновления

Если вы настроили репозиторий накопительный пакет обновления, то будут получены последнее накопительное обновление пакетов SQL Server при выполнении новых установок. Накопительный пакет обновления репозитория значение по умолчанию для всех статей пакет установки для SQL Server в Linux. Дополнительные сведения о настройке хранилища см. в разделе [источника репозиториев](sql-server-linux-setup.md#repositories).

При обновлении существующих пакетов SQL Server, выполните команду соответствующие обновления для каждого пакета получить последний накопительный пакет обновления. Определенное обновление инструкции для каждого пакета см. в следующих руководствах установки:

- [Установить пакет SQL Server](sql-server-linux-setup.md#upgrade)
- [Установить пакет Full-text Search](sql-server-linux-setup-full-text-search.md)
- [Установить пакет агента SQL Server](sql-server-linux-setup-sql-agent.md)
- [Установка служб SQL Server Integration Services](sql-server-linux-setup-ssis.md)

## <A id="CU2"></a>Накопительный пакет обновления 3 (января 2018)

Это накопительный пакет обновления 3 (CU3) выпуска 2017 г. SQL Server. Версия ядра SQL Server для этого выпуска, 14.0.3015.40. Сведения о исправления и улучшения в этом выпуске см. в разделе [https://support.microsoft.com/en-us/help/4052987](https://support.microsoft.com/en-us/help/4052987).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вне сети или вручную можно загрузить пакеты RPM и Debian с информацией в таблице ниже:

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3015.40-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3015.40-1 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3015.40-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <A id="CU2"></a>Накопительный пакет обновления 2 (ноябрь 2017 г.)

Это накопительный пакет обновления 2 (CU2) выпуска 2017 г. SQL Server. Версия ядра SQL Server для этого выпуска, 14.0.3008.27. Сведения о исправления и улучшения в этом выпуске см. в разделе [https://support.microsoft.com/help/4052574](https://support.microsoft.com/help/4052574).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вне сети или вручную можно загрузить пакеты RPM и Debian с информацией в таблице ниже:

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3008.27-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3008.27-1 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3008.27-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <A id="CU1"></a>Накопительный пакет обновления 1 (октябрь 2017 г.)

Это накопительный пакет обновления 1 (CU1) выпуска 2017 г. SQL Server. Версия ядра SQL Server для этого выпуска, 14.0.3006.16. Сведения о исправления и улучшения в этом выпуске см. в разделе [https://support.microsoft.com/help/4038634](https://support.microsoft.com/help/4038634).

### <a name="package-details"></a>Сведения о пакете

Для установки пакетов вне сети или вручную можно загрузить пакеты RPM и Debian с информацией в таблице ниже:

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3006.16-3 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.3006.16-3 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.3006.16-3 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a>Глобальный Администратор (октябрь 2017 г.)

Это общая доступность (GA) выпуска 2017 г. SQL Server. Версия ядра SQL Server для этого выпуска, 14.0.1000.169.

### <a name="package-details"></a>Сведения о пакете

Сведения о пакете и адреса для пакеты RPM и Debian, перечислены в следующей таблице. Обратите внимание, что не требуется непосредственно загрузить эти пакеты при использовании действия в следующих руководствах по установке:

- [Установить пакет SQL Server](sql-server-linux-setup.md)
- [Установить пакет Full-text Search](sql-server-linux-setup-full-text-search.md)
- [Установить пакет агента SQL Server](sql-server-linux-setup-sql-agent.md)
- [Установка служб SQL Server Integration Services](sql-server-linux-setup-ssis.md)

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.1000.169-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.1000.169-2 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.1000.169-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

### <a name="Unsupported"></a>Неподдерживаемые функции и службы

Следующие функции и службы недоступны в Linux в настоящее время. Со временем будет более включена поддержка этих возможностей.

| Область | Неподдерживаемые функции или службы |
|-----|-----|
| **Компонент Database engine** | Репликация транзакций |
| &nbsp; | Репликация слиянием |
| &nbsp; | Растяжение базы данных |
| &nbsp; | Polybase |
| &nbsp; | Распределенный запрос с подключениями сторонних поставщиков |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL, и т. д.) |
| &nbsp; | Таблицы filetable, FILESTREAM |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| &nbsp; | Расширение буферного пула |
| **Агент SQL Server** |  Подсистемы: CmdExec, PowerShell, агент чтения очереди, служб SSIS, SSAS, SSRS |
| &nbsp; | Предупреждения |
| &nbsp; | Агент чтения журнала. |
| &nbsp; | Система отслеживания измененных данных |
| &nbsp; | Управляемое резервное копирование |
| **Обеспечение высокого уровня доступности** | Зеркальное отображение базы данных  |
| **Безопасность** | расширенное управление ключами |
| &nbsp; | Проверки подлинности AD для связанных серверов | 
| &nbsp; | Проверки подлинности AD для групп доступности (и действий) | 
| &nbsp; | инструменты сторонних AD (Centrify Vintela, Powerbroker) | 
| **Службы** | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Службы Master Data Services |

### <a name="known-issues"></a>Известные проблемы

В следующих разделах описаны известные проблемы с выпуском Общая доступность (GA) 2017 г. SQL Server в Linux.

#### <a name="general"></a>Общие сведения

- Обновление до выпуска общедоступной версии 2017 г. SQL Server поддерживается только из CTP-версии 2.1 или более поздней версии. 

- Длина имени узла, где SQL Server, установленных нуждается в 15 символов или меньше. 

    - **Разрешение**: измените имя в/etc/hostname на что-нибудь 15 или меньше знаков.

- Вручную системное время обратной вовремя, то SQL Server остановить обновление внутреннего системного времени в SQL Server.

    - **Разрешение**: перезапустите SQL Server.

- Поддерживаются только один экземпляр установки.

    - **Разрешение**: Если вы хотите иметь более одного экземпляра на конкретном узле, рассмотрите возможность использования виртуальных машин или контейнеры Docker. 

- Диспетчер конфигурации SQL Server не удается подключиться к SQL Server в Linux.

- Язык по умолчанию **sa** входа является английский язык.

    - **Разрешение**: изменить язык **sa** входа с **ALTER LOGIN** инструкции.

#### <a name="databases"></a>Базы данных

- Не удается переместить базу данных master с помощью служебной программы mssql conf. Другие системные базы данных можно переместить с конфигурацией mssql

- При восстановлении базы данных, которая была создана резервная копия на сервере SQL Server в Windows, необходимо использовать **WITH MOVE** предложение в инструкции Transact-SQL.

- Распределенные транзакции, требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на ОС Linux. SQL Server до SQL Server, связанные серверы поддерживаются в том случае, если только они включают DTC. Дополнительные сведения см. в разделе [распределенных транзакций требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на Linux](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/).

- Некоторые алгоритмы (шифров) Transport Layer Security (TLS) не работают должным образом с SQL Server в Linux. В результате ошибок соединения при попытке подключения к SQL Server, а также проблем с установлением соединения между репликами в группах высокого уровня доступности.

   - **Разрешение**: изменение **mssql.conf** сценария настройки для SQL Server в Linux отключение проблемный шифров, следующим образом:

      1. Добавьте следующую строку /var/opt/mssql/mssql.conf.

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

- Нельзя восстановить базы данных SQL Server 2014 на Windows, который In-memory OLTP 2017 г. SQL Server в Linux. Чтобы восстановить базу данных SQL Server 2014, которая в памяти OLTP, сначала обновите базы данных в SQL Server 2016 или 2017 г. SQL Server в Windows до перемещения их в SQL Server в Linux через резервного копирования и восстановления или отсоединения и присоединения.

- Разрешение пользователя **ADMINISTER BULK OPERATIONS** не поддерживается на платформе Linux в настоящее время.

#### <a name="networking"></a>Работа с сетью

Функции, которые включают исходящие соединения TCP из sqlservr процесса, таких как связанные серверы или группы доступности может работать не так, если выполняются следующие условия:

1. Имя узла и IP-адрес не указан целевой сервер.

1. Исходный экземпляр имеет протокол IPv6 отключен в ядре. Чтобы проверить, имеет ли ваша система ядра включен протокол IPv6, необходимо передать следующие тесты:

   - `cat /proc/cmdline`напечатает cmdline загрузки текущего ядра. Выходные данные не должны содержать `ipv6.disable=1`.
   - / Proc/sys/net/ipv6-каталог должен существовать.
   - Программе на языке C, который вызывает `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` должны выполняться успешно - syscall должен возвратить fd! = -1 и не завершаются EAFNOSUPPORT.

Точная ошибка зависит от компонента. Для связанных серверов это проявляющийся как ошибка времени ожидания входа в систему. Для групп доступности `ALTER AVAILABILITY GROUP JOIN` DDL на сервере-получателе после 5 минут с ошибку времени ожидания загрузки конфигурации будут завершаться сбоем.

Чтобы обойти эту проблему, выполните одно из следующих действий.

1. Используйте IP-адреса вместо имен узлов для указания целевого объекта соединения по протоколу TCP.

1. Включить протокол IPv6 в ядре, удалив `ipv6.disable=1` из cmdline загрузки. Способ сделать это зависит от дистрибутив Linux и загрузчика, например grub. Если вы хотите IPv6 отключена, можно отключить его, установив `net.ipv6.conf.all.disable_ipv6 = 1` в `sysctl` конфигурации (например `/etc/sysctl.conf`). Это будет по-прежнему предотвратить попадание IPv6-адрес сетевого адаптера в системе, но разрешить выполнение sqlservr компонентов.

#### <a name="network-file-system-nfs"></a>Сетевой файловой системы (NFS)
Если вы используете **сетевой файловой системы (NFS)** удаленные общие ресурсы в рабочей среде, ознакомьтесь со следующими требованиями поддержки:

- Использование NFS версии **4.2 или более поздней версии**. NFS более ранних версий не поддерживают необходимые компоненты, такие как fallocate и создания разреженный файл, общие для современных файловых систем.
- Найдите только **/var/opt/mssql** каталогов на подключения NFS. Другие файлы, такие как системные файлы SQL Server и не поддерживаются.
- Убедитесь, что клиенты NFS использовать параметр «nolock» при подключении к удаленной общей папке.

#### <a name="localization"></a>Локализация

- Если язык не английский (en_us) во время установки, необходимо использовать кодировку UTF-8 в сеанс/терминала bash. Если используется кодировка ASCII, может появится сообщение об ошибке следующего вида:

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Если не удается использовать кодировку UTF-8, запустите программу установки с помощью переменной среды MSSQL_LCID для указания Выбор языка.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- При установке mssql conf и выполнению установки локализованной SQL Server, неправильные символы национального алфавита отображаются после локализованный текст «Настройка SQL Server...». Или для установок на основе нелатинских предложение может отсутствовать полностью. Отсутствует предложение должны отображаться следующие Локализованная строка: «лицензирования продукта успешно обработана.  Новый выпуск [\<имя\> выпуск]». Эта строка выводится только в информационных целях и далее накопительное обновление SQL Server решает эту для всех языков. Это не влияет на установки SQL Server каким-либо образом. 

#### <a name="full-text-search"></a>Full-Text Search

- В этом выпуске, включая фильтры для документов Office доступны не все фильтры. Список поддерживаемых фильтров см. в разделе [установить SQL Server Full-Text Search в Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a id="ssis"></a> Службы SQL Server Integration Services

- **Mssql сервер является** пакет не поддерживается в этой версии для SUSE. В настоящее время поддерживается на Ubuntu и в Red Hat Enterprise Linux (RHEL).

- С помощью служб SSIS на Linux CTP-версии 2.1 обновления и более поздних версий пакетов служб SSIS можно использовать подключения ODBC в Linux. Эта функциональность была протестирована с SQL Server и драйверы MySQL ODBC, но также требуются для работы с любой драйвер ODBC Юникода, отслеживающее спецификации ODBC. Во время разработки укажите имя источника данных или строку подключения для подключения к данным ODBC; Можно также использовать проверку подлинности Windows. Дополнительные сведения см. в разделе [записи блога Представляем поддержка ODBC в Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Следующие функции не поддерживаются в этом выпуске при запуске пакетов служб SSIS в Linux:
  - База данных каталога служб SSIS
  - Выполнение запланированного пакета агентом SQL
  - Проверка подлинности Windows.
  - Компоненты сторонних разработчиков
  - Система отслеживания измененных данных (CDC)
  - Масштабирование служб SSIS
  - Пакет дополнительных компонентов Azure для служб SSIS
  - Поддержка Hadoop и HDFS
  - Соединитель Microsoft Connector для SAP BW

Список встроенных компонентов служб SSIS, в настоящее время не поддерживаются или поддерживаются ограниченно см. в разделе [ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md#components).

Дополнительные сведения о служб SSIS в Linux см. в следующих статьях:
-   [Представляем post блог поддержку SSIS для Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Установка SQL Server Integration Services (SSIS) для Linux](sql-server-linux-setup-ssis.md)
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)

В SSMS для подключения к SQL Server в Linux Windows применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщика данных в среде SSMS не поддерживаются. 

- Компоненты пользовательского интерфейса среды SSMS с проверкой подлинности Windows или параметры журнала событий Windows не поддерживают работу с Linux. Эти функции по-прежнему можно использовать с другими действиями, например имена входа SQL. 

- Невозможно изменить количество файлов журнала для хранения.

### <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. следующие примеры использования:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)
