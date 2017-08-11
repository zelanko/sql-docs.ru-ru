---
title: "Заметки о выпуске для 2017 г. SQL Server в Linux | Документы Microsoft"
description: "В этом разделе содержатся заметки о выпуске и поддерживаемых функций для ОС Linux 2017 г. SQL Server. Заметки о выпуске предназначены для версии-кандидата 2 и более ранние версии."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/07/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.translationtype: MT
ms.sourcegitcommit: 8397673c7ed9dfe8ae02871f9077ed7286e49863
ms.openlocfilehash: baa5826e9722bfb23afacf729d80bebf88985ed3
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Заметки о выпуске для 2017 г. SQL Server в Linux

Следующие замечания к выпуску применяются для ОС Linux 2017 г. SQL Server. Этот выпуск поддерживает многие функции ядра СУБД SQL Server для Linux. Ниже раздел разбит на разделы для каждого выпуска, начиная с самой последнем выпуске версии-кандидата 2. См. информацию в каждом разделе Поддерживаемые платформы, инструменты, возможности и известные проблемы.

В следующей таблице перечислены выпуски SQL Server 2017 г., описанные в этом разделе.

| Выпуск | Версия | Дата выпуска |
|-----|-----|-----|
| [ВЕРСИЯ-КАНДИДАТ 2](#RC2) | 14.0.900.75 | 8-2017 |
| [ВЕРСИЯ-КАНДИДАТ 1](#RC1) | 14.0.800.90 | 7-2017 |
| [CTP-ВЕРСИИ 2.1](#ctp21) | 14.0.600.250 | 5-2017 |
| [CTP 2.0](#ctp20) | 14.0.500.272 | 4-2017 |
| [CTP-ВЕРСИИ 1.4](#ctp14) | 14.0.405.198 | 3-2017 |
| [CTP-ВЕРСИИ 1.3](#ctp13) | 14.0.304.138 | 2-2017 |
| [CTP-ВЕРСИИ 1.2](#ctp12) | 14.0.200.24 | 1-2017 |
| [CTP-ВЕРСИИ 1.1](#ctp11) | 14.0.100.187 | 12-2016 |
| [CTP-ВЕРСИИ 1.0](#ctp10) | 14.0.1.246 | 11-2016 |

## <a id="RC2"></a>Версия-кандидат 2 (август 2017 г.)

Версия ядра SQL Server для этого выпуска, 14.0.900.75.

### <a name="supported-platforms"></a>Поддерживаемые платформы

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, рабочей станции, серверов и настольных компьютеров | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| Сервер Linux версии 12 SUSE Enterprise с пакетом обновления 2 | EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема docker 1.8 + в Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!NOTE]
> Необходимо по крайней мере 3,25 ГБ памяти для запуска SQL Server в Linux.
> Модуль SQL Server был протестирован 1,5 ТБ памяти в данный момент.

### <a name="package-details"></a>Сведения о пакете

Сведения о пакете и адреса для пакеты RPM и Debian, перечислены в следующей таблице. Обратите внимание, что не требуется непосредственно загрузить эти пакеты при использовании действия в следующих руководствах по установке:

- [Установить пакет SQL Server](sql-server-linux-setup.md)
- [Установить пакет Full-text Search](sql-server-linux-setup-full-text-search.md)
- [Установить пакет агента SQL Server](sql-server-linux-setup-sql-agent.md)

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.900.75-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.900.75-1 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.900.75-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.900.75-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.900.75-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.900.75-1_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.900.75-1_amd64.deb) |

### <a name="supported-client-tools"></a>Поддерживаемые клиентские средства

| Инструмент | Минимальная версия |
|-----|-----|
| [SQL Server Management Studio (SSMS) для Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools для Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Код Visual Studio](https://code.visualstudio.com) с [mssql расширения](https://aka.ms/mssql-marketplace) | последние |

### <a name="unsupported-features-and-services"></a>Неподдерживаемые функции и службы

Следующие функции и службы недоступны в Linux в настоящее время. Во время месячную периодичность обновления программы предварительного просмотра будет более включена поддержка этих возможностей.

| Область | Неподдерживаемые функции или службы |
|-----|-----|
| **Компонент Database engine** | Репликация транзакций |
| &nbsp; | Репликация слиянием |
| &nbsp; | Растяжение базы данных |
| &nbsp; | Polybase |
| &nbsp; | Распределенный запрос с подключениями сторонних поставщиков |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL, и т. д.) |
| &nbsp; | Таблицы filetable |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| &nbsp; | Расширение буферного пула |
| **Агент SQL Server** |  Подсистемы: CmdExec, PowerShell, агент чтения очереди, служб SSIS, SSAS, SSRS |
| &nbsp; | Предупреждения |
| &nbsp; | Агент чтения журнала. |
| &nbsp; | Система отслеживания измененных данных |
| &nbsp; | Управляемое резервное копирование |
| **Обеспечение высокого уровня доступности** | Зеркальное отображение базы данных  |
| **Безопасность** | расширенное управление ключами |
| **Службы** | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Службы Data Quality Services |
| &nbsp; | Службы Master Data Services |

### <a name="known-issues"></a>Известные проблемы

В следующих разделах описаны известные проблемы в этом выпуске SQL Server, RC2 2017 г. в Linux.

#### <a name="general"></a>Общие сведения

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

- Распределенные транзакции, требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на ОС Linux. SQL Server до SQL Server, поддерживаются распределенные транзакции.

- Некоторые алгоритмы (шифров) Transport Layer Security (TLS) не работают должным образом с SQL Server в Linux. В результате ошибок соединения при попытке подключения к SQL Server, а также проблем с установлением соединения между репликами в группах высокого уровня доступности.

   - **Разрешение**: изменение **mssql.conf** сценария настройки для SQL Server в Linux отключение проблемный шифров, следующим образом:

      1. Добавьте следующую строку /var/opt/mssql/mssql.conf.

      ```
      [network]
      tlsciphers=ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

      1. Перезапустите SQL Server с помощью следующей команды.
   
      ```
      sudo systemctl restart mssql-server
      ```

- Нельзя восстановить базы данных SQL Server 2014 на Windows, который In-memory OLTP 2017 г. SQL Server в Linux. Чтобы восстановить базу данных SQL Server 2014, которая в памяти OLTP, сначала обновите базы данных в SQL Server 2016 или 2017 г. SQL Server в Windows до перемещения их в SQL Server в Linux через резервного копирования и восстановления или отсоединения и присоединения.

#### <a name="remote-database-files"></a>Файлы удаленной базы данных

- Размещение файлов базы данных на NFS-сервера в этом выпуске не поддерживается. Сюда относится использование NFS для общего диска отказоустойчивой кластеризации, а также баз данных на некластеризованные экземпляры. Мы работаем над включением поддержки сервера NFS в будущих выпусках.

#### <a name="localization"></a>Локализация

- Если язык не английский (en_us) во время установки, необходимо использовать кодировку UTF-8 в сеанс/терминала bash. Если используется кодировка ASCII, может появится сообщение об ошибке следующего вида:

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Если не удается использовать кодировку UTF-8, запустите программу установки с помощью переменной среды MSSQL_LCID для указания Выбор языка.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

#### <a name="full-text-search"></a>Full-Text Search
- В этом выпуске, включая фильтры для документов Office доступны не все фильтры. Список поддерживаемых фильтров см. в разделе [установить SQL Server Full-Text Search в Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a name="sql-server-integration-services-ssis"></a>Службы SQL Server Integration Services
Может запускать пакеты служб SSIS в Linux. Дополнительные сведения см. в следующих статьях:
-   [Представляем post блог поддержку SSIS для Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Установка SQL Server Integration Services (SSIS) для Linux](sql-server-linux-setup-ssis.md)
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)

Учтите следующие известные проблемы в этом выпуске.

- **Mssql сервер является** пакет поддерживается на Ubuntu и Red Hat Enterprise Linux (RHEL) в этом выпуске.

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

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
В SSMS для подключения к SQL Server в Linux Windows применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщика данных в среде SSMS не поддерживаются. 

- Компоненты пользовательского интерфейса среды SSMS с проверкой подлинности Windows или параметры журнала событий Windows не поддерживают работу с Linux. Эти функции по-прежнему можно использовать с другими действиями, например имена входа SQL. 

- Невозможно изменить количество файлов журнала для хранения.

### <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. в следующих учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Разделение панель график](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="RC1"></a>Версия-кандидат 1 (июля 2017 г.)
Версия ядра SQL Server для этого выпуска, 14.0.800.90.

### <a name="supported-platforms"></a>Поддерживаемые платформы 

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, рабочей станции, серверов и настольных компьютеров | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| Сервер Linux версии 12 SUSE Enterprise с пакетом обновления 2 | EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема docker 1.8 + в Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!NOTE]
> Необходимо по крайней мере 3,25 ГБ памяти для запуска SQL Server в Linux.
> Модуль SQL Server был протестирован до 1 ТБ памяти в данный момент.

### <a name="package-details"></a>Сведения о пакете
Сведения о пакете и адреса для пакеты RPM и Debian, перечислены в следующей таблице. Обратите внимание, что не требуется непосредственно загрузить эти пакеты при использовании действия в следующих руководствах по установке:

- [Установить пакет SQL Server](sql-server-linux-setup.md)
- [Установить пакет Full-text Search](sql-server-linux-setup-full-text-search.md)
- [Установить пакет агента SQL Server](sql-server-linux-setup-sql-agent.md)

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.800.90-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.800.90-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.800.90-2.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.800.90-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.800.90-2.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.800.90-2 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.800.90-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.800.90-2.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.800.90-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.800.90-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.800.90-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.800.90-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.800.90-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.800.90-2_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.800.90-2_amd64.deb) |

### <a name="supported-client-tools"></a>Поддерживаемые клиентские средства

| Инструмент | Минимальная версия |
|-----|-----|
| [SQL Server Management Studio (SSMS) для Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools для Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Код Visual Studio](https://code.visualstudio.com) с [mssql расширения](https://aka.ms/mssql-marketplace) | последние |

### <a name="unsupported-features-and-services"></a>Неподдерживаемые функции и службы
Следующие функции и службы недоступны в Linux в настоящее время. Во время месячную периодичность обновления программы предварительного просмотра будет более включена поддержка этих возможностей.

| Область | Неподдерживаемые функции или службы |
|-----|-----|
| **Компонент Database engine** | Репликация транзакций |
| &nbsp; | Репликация слиянием |
| &nbsp; | Растяжение базы данных |
| &nbsp; | Polybase |
| &nbsp; | Распределенный запрос |
| &nbsp; | Машинного обучения служб |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL, и т. д.) |
| &nbsp; | Таблицы filetable |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| **Агент SQL Server** |  Подсистемы: CmdExec, PowerShell, агент чтения очереди, служб SSIS, SSAS, SSRS |
| &nbsp; | Предупреждения |
| &nbsp; | Агент чтения журнала. |
| &nbsp; | Система отслеживания измененных данных |
| &nbsp; | Управляемое резервное копирование |
| **Обеспечение высокого уровня доступности** | Зеркальное отображение базы данных  |
| &nbsp; | Последовательное обновление группы доступности |
| **Безопасность** | расширенное управление ключами |
| **Службы** | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Службы Data Quality Services |
| &nbsp; | Службы Master Data Services |

### <a name="known-issues"></a>Известные проблемы
В следующих разделах описаны известные проблемы в этом выпуске SQL Server, RC1 2017 г. в Linux.

#### <a name="general"></a>Общие сведения
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

- Не удается переместить системные базы данных с помощью служебной программы mssql conf.

- При восстановлении базы данных, которая была создана резервная копия на сервере SQL Server в Windows, необходимо использовать **WITH MOVE** предложение в инструкции Transact-SQL.

- Распределенные транзакции, требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на ОС Linux. SQL Server до SQL Server, поддерживаются распределенные транзакции.

#### <a name="remote-database-files"></a>Файлы удаленной базы данных

- Размещение файлов базы данных на NFS-сервера в этом выпуске не поддерживается. Сюда относится использование NFS для общего диска отказоустойчивой кластеризации, а также баз данных на некластеризованные экземпляры. Мы работаем над включением поддержки сервера NFS в будущих выпусках.

#### <a name="cross-platform-availability-groups-and-distributed-availability-groups"></a>Группы доступности межплатформенные и распределенные группы доступности

- Вследствие известных проблем Создание группы доступности с репликами на экземпляры, размещенные в Windows и Linux не работает в данном выпуске. Сюда входят распределенные группы доступности. Исправление будут доступны в будущих версия-кандидат сборки. 

#### <a name="server-collation"></a>Параметры сортировки сервера

- При MSSQL_COLLATION с помощью переопределения, либо при выполнении установки локализованные (не на английском языке), возможно SQL Server столкнутся взаимоблокировка при попытке установить параметры сортировки сервера, который создает дамп. Установка завершена успешно, однако параметры сортировки сервера будет не присвоено значение. Достаточно просто запустите. / mssql conf set-параметры сортировки и введите имя параметров сортировки, требуемого при появлении запроса (имя параметров сортировки можно найти в журнале ошибок в строке: «Предпринимается попытка изменить параметры сортировки по умолчанию для...»). 
 
#### <a name="localization"></a>Локализация

- Если язык не английский (en_us) во время установки, необходимо использовать кодировку UTF-8 в сеанс/терминала bash. Если используется кодировка ASCII, может появится сообщение об ошибке следующего вида:

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Если не удается использовать кодировку UTF-8, запустите программу установки с помощью переменной среды MSSQL_LCID для указания Выбор языка.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

#### <a name = "fci"></a>Общие обновления экземпляра диска кластера

В версии RC1 агентом ресурсов кластера задает имя виртуального сервера, как и в экземпляре отказоустойчивого кластера в Windows. До версии-кандидата 1 `@@servername` на общем диске кластера вернул определенного узла именем, после отработки отказа `@@servername` возвращается другое значение. В версии-кандидата 1 serverName экземпляра общего диска кластера с именем ресурса обновляется, при добавлении ресурса в кластер. По этой причине кластера будет необходимо перезапустить SQL Server после отработки отказа вручную во время обновления — как показано ниже:

1. Сначала обновите узел получателя (пассивного) кластера.
   - Обновление **mssql server** пакета.
   - Обновление **mssql-server-ha** пакета.
1. Вручную перехода на обновленный узел.
   `pcs resource move <resourceName>`
   - Изначально сбой ресурса, потому что агент ресурсов проверяет serverName фактического и ожидаемого. Ожидаемое имя сервера будут отличаться.
   - Кластер будет перезапущена ресурсов SQL Server на том же узле. Это позволит обновить имя сервера.
1. Обновите другой узел. 
   - Обновление **mssql server** пакета.
   - Обновление **mssql-server-ha** пакета.
1. Удалите ограничение, добавленные вручную ресурсов перемещения. В разделе [отказоустойчивого кластера вручную](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md#failManual).
2. При желании ошибкой обратно в исходный основной узел. 

#### <a name="availability-group"></a>Группа доступности

В Linux последовательное обновление SQL Server 2017 г CTP-версии 2.1 для версии-кандидата 1 не поддерживается. После обновления вторичной реплики, отключится от первичной реплики до обновления первичной реплики. Корпорация Майкрософт планирует устранить эту проблему в будущих выпусках.

#### <a name="full-text-search"></a>Full-Text Search
- В этом выпуске, включая фильтры для документов Office доступны не все фильтры. Список поддерживаемых фильтров см. в разделе [установить SQL Server Full-Text Search в Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a name="sql-server-integration-services-ssis"></a>Службы SQL Server Integration Services

- **Mssql сервер является** пакет не поддерживается в этой версии для SUSE. В настоящее время поддерживается на Ubuntu и в Red Hat Enterprise Linux (RHEL).

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

Дополнительные сведения о служб SSIS в Linux см. в следующих статьях:
-   [Установка SQL Server Integration Services (SSIS) для Linux](sql-server-linux-setup-ssis.md)
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
В SSMS для подключения к SQL Server в Linux Windows применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщика данных в среде SSMS не поддерживаются. 

- Компоненты пользовательского интерфейса среды SSMS с проверкой подлинности Windows или параметры журнала событий Windows не поддерживают работу с Linux. Эти функции по-прежнему можно использовать с другими действиями, например имена входа SQL. 

- Невозможно изменить количество файлов журнала для хранения.

### <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. в следующих учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Разделение панель график](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp21"></a>CTP-версии 2.1 (май 2017 г.)
Версия ядра SQL Server для этого выпуска, 14.0.600.250.

### <a name="supported-platforms"></a>Поддерживаемые платформы 

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, рабочей станции, серверов и настольных компьютеров | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| Сервер Linux версии 12 SUSE Enterprise с пакетом обновления 2 | EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема docker 1.8 + в Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!NOTE]
> Необходимо по крайней мере 3,25 ГБ памяти для запуска SQL Server в Linux.
> Модуль SQL Server был протестирован до 1 ТБ памяти в данный момент.

### <a name="package-details"></a>Сведения о пакете
Сведения о пакете и адреса для пакеты RPM и Debian, перечислены в следующей таблице. Необходимо выполнить действия в следующих руководствах установки происходит непосредственная загрузка этих пакетов:

- [Установить пакет SQL Server](sql-server-linux-setup.md)
- [Установить пакет Full-text Search](sql-server-linux-setup-full-text-search.md)
- [Установить пакет агента SQL Server](sql-server-linux-setup-sql-agent.md)

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.600.250-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.600.250-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.600.250-2.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.600.250-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.600.250-2.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.600.250-2 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.600.250-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.600.250-2.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.600.250-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.600.250-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.600.250-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.600.250-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.600.250-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.600.250-2_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.600.250-2_amd64.deb) |

### <a name="supported-client-tools"></a>Поддерживаемые клиентские средства

| Инструмент | Минимальная версия |
|-----|-----|
| [SQL Server Management Studio (SSMS) для Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools для Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Код Visual Studio](https://code.visualstudio.com) с [mssql расширения](https://aka.ms/mssql-marketplace) | Последнюю версию (1.12) |

### <a name="unsupported-features-and-services"></a>Неподдерживаемые функции и службы
Следующие функции и службы недоступны в Linux в настоящее время. Во время месячную периодичность обновления программы предварительного просмотра будет более включена поддержка этих возможностей.

| Область | Неподдерживаемые функции или службы |
|-----|-----|
| **Компонент Database engine** | Репликация |
| &nbsp; | Растяжение базы данных |
| &nbsp; | Polybase |
| &nbsp; | Распределенный запрос |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL, и т. д.) |
| &nbsp; | Таблицы filetable |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| **Обеспечение высокого уровня доступности** | Зеркальное отображение базы данных  |
| **Безопасность** | Проверка подлинности Active Directory |
| &nbsp; | Проверка подлинности Windows. |
| &nbsp; | расширенное управление ключами |
| &nbsp; | Использование сертификата, предоставленного пользователем для SSL или TLS |
| **Службы** | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Службы Data Quality Services |
| &nbsp; | Службы Master Data Services |

### <a name="known-issues"></a>Известные проблемы
В следующих разделах описаны известные проблемы с этим выпуском SQL Server 2017 г CTP-версии 2.1 в Linux.

#### <a name="general"></a>Общие сведения
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
- Не удается переместить системные базы данных с помощью служебной программы mssql conf.

- При восстановлении базы данных, которая была создана резервная копия на сервере SQL Server в Windows, необходимо использовать **WITH MOVE** предложение в инструкции Transact-SQL.

- Распределенные транзакции, требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на ОС Linux. SQL Server до SQL Server, поддерживаются распределенные транзакции.

#### <a name="always-on-availability-group"></a>Всегда в группе доступности
- `sys.fn_hadr_backup_is_preffered_replica`не работает для `CLUSTER_TYPE=NONE` или `CLUSTER_TYPE=EXTERNAL` тем, что он использует реестр кластера WSFC реплицируются ключа, которого не доступен. Мы работаем над предоставляет аналогичные функциональные возможности через другую функцию. 

#### <a name="full-text-search"></a>Full-Text Search
- В этом выпуске, включая фильтры для документов Office доступны не все фильтры. Список поддерживаемых фильтров см. в разделе [установить SQL Server Full-Text Search в Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a name="sql-agent"></a>Агент SQL Server
- Следующие компоненты и подсистемах задания агента SQL Server не поддерживаются в настоящее время на платформе Linux:

    - Подсистемы: CmdExec, PowerShell, распространитель репликации, моментальных снимков, слияния, агент чтения очереди, служб SSIS, SSAS, SSRS
    - Предупреждения
    - DB Mail
    - Агент чтения журнала. 
    - Система отслеживания измененных данных

#### <a name="sqlpackage"></a>SqlPackage
- Используя программу SqlPackage необходимо указать абсолютный путь к файлам. Относительные пути будут сопоставления файлов «/ tmp/sqlpackage. \<кода \> /system/system32» папки. 

  - **Разрешение**: использовать абсолютные пути.

- SqlPackage показывает расположение файлов с «C:\\"префикс.

#### <a name="ssis"></a> Службы SQL Server Integration Services
Может запускать пакеты служб SSIS в Linux. Дополнительные сведения см. в разделе [блога post Представляем поддержку SSIS для Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). Учтите следующие известные проблемы в этом выпуске.

- **Mssql сервер является** пакета поддерживаются только для Ubuntu на данный момент.

- Следующие функции не поддерживаются при выполнении пакетов служб SSIS в Linux:
  - Базы данных каталога служб SSIS
  - Планирование выполнения пакетов агентом SQL
  - Проверка подлинности Windows.
  - Компоненты сторонних разработчиков
  - Драйверов ODBC
  - Диспетчер соединений ODBC, источника и назначения (поддерживается с помощью служб SSIS при обновлении 2.1 Linux CTP-версия)
  - Система отслеживания измененных данных (CDC)
  - Масштабирование
  - Пакет дополнительных компонентов Azure
  - Поддержка Hadoop и HDFS
  - Соединитель Microsoft Connector для SAP BW

С помощью служб SSIS на Linux CTP-версии 2.1 обновления пакетов служб SSIS можно использовать подключения ODBC в Linux. Дополнительные сведения см. в разделе [записи блога Представляем поддержка ODBC в Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
В SSMS для подключения к SQL Server в Linux Windows применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщика данных в среде SSMS не поддерживаются. 

- Компоненты пользовательского интерфейса среды SSMS с проверкой подлинности Windows или параметры журнала событий Windows не поддерживают работу с Linux. Эти функции по-прежнему можно использовать с другими действиями, например имена входа SQL. 

- Невозможно изменить количество файлов журнала для хранения.

### <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. в следующих учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Разделение панель график](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp20"></a>CTP 2.0 (апрель 2017 г.)
Версия ядра SQL Server для этого выпуска, 14.0.500.272.

### <a name="supported-platforms"></a>Поддерживаемые платформы 

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, рабочей станции, серверов и настольных компьютеров | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| Сервер Linux версии 12 SUSE Enterprise с пакетом обновления 2 | EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS и 16.10 | EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема docker 1.8 + в Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Необходимо по крайней мере 3,25 ГБ памяти для запуска SQL Server в Linux.
> Модуль SQL Server был протестирован до 1 ТБ памяти в данный момент.

### <a name="package-details"></a>Сведения о пакете
Сведения о пакете и адреса для пакеты RPM и Debian, перечислены в следующей таблице. Обратите внимание, что не требуется непосредственно загрузить эти пакеты при использовании действия в следующих руководствах по установке:

- [Установить пакет SQL Server](sql-server-linux-setup.md)
- [Установить пакет Full-text Search](sql-server-linux-setup-full-text-search.md)
- [Установить пакет агента SQL Server](sql-server-linux-setup-sql-agent.md)

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.500.272-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.500.272-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.500.272-2.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.500.272-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.500.272-2.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.500.272-2 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.500.272-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.500.272-2.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.500.272-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.500.272-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.500.272-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.500.272-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.500.272-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.500.272-2_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.500.272-2_amd64.deb) |
| Пакет Debian Ubuntu 16.10 | 14.0.500.272-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.500.272-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.500.272-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.500.272-2_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.500.272-2_amd64.deb) |

### <a name="supported-client-tools"></a>Поддерживаемые клиентские средства

| Инструмент | Минимальная версия |
|-----|-----|
| [SQL Server Management Studio (SSMS) для Windows — версия-кандидат 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools для Visual Studio — версия-кандидат 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Код Visual Studio](https://code.visualstudio.com) с [mssql расширения](https://aka.ms/mssql-marketplace) | Последнюю версию (0.2.1) |

> [!NOTE] 
> SQL Server Management Studio и SQL Server Data Tools указанная выше подходят выпуска, поэтому не рекомендуется использовать в производственной среде.

### <a name="unsupported-features-and-services"></a>Неподдерживаемые функции и службы
Следующие функции и службы недоступны в Linux в настоящее время. Во время месячную периодичность обновления программы предварительного просмотра будет более включена поддержка этих возможностей.

| Область | Неподдерживаемые функции или службы |
|-----|-----|
| **Компонент Database engine** | Репликация |
| &nbsp; | Растяжение базы данных |
| &nbsp; | Polybase |
| &nbsp; | Распределенный запрос |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL, и т. д.) |
| &nbsp; | Таблицы filetable |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| **Обеспечение высокого уровня доступности** | Зеркальное отображение базы данных  |
| **Безопасность** | Проверка подлинности Active Directory |
| &nbsp; | Проверка подлинности Windows. |
| &nbsp; | расширенное управление ключами |
| &nbsp; | Использование сертификата, предоставленного пользователем для SSL или TLS |
| **Службы** | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Службы Integration Services | 
| &nbsp; | Службы Data Quality Services |
| &nbsp; | Службы Master Data Services |

### <a name="known-issues"></a>Известные проблемы
В следующих разделах описаны известные проблемы с этим выпуском SQL Server 2017 г CTP 2.0 в Linux.

#### <a name="general"></a>Общие сведения
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
- Не удается переместить системные базы данных с помощью служебной программы mssql conf.

- При восстановлении базы данных, которая была создана резервная копия на сервере SQL Server в Windows, необходимо использовать **WITH MOVE** предложение в инструкции Transact-SQL.

- Распределенные транзакции, требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на ОС Linux. SQL Server до SQL Server, поддерживаются распределенные транзакции.

#### <a name="always-on-availability-group"></a>Всегда в группе доступности
- Все конфигурации высокого уровня ДОСТУПНОСТИ — это означает, что группы доступности добавляется как ресурс кластера Pacemaker - создан с пакетами CTP2.0 операционных систем не имеют обратной совместимости с использованием нового пакета. Удалите все ранее настроенные кластерных ресурсов и создавать новые группы доступности с `CLUSTER_TYPE=EXTERNAL`. В разделе [Настройка AlwaysOn группы доступности для SQL Server в Linux](sql-server-linux-availability-group-configure-ha.md).
- Группы доступности, созданных с помощью `CLUSTER_TYPE=NONE` и не были добавлены как ресурсы кластера будет продолжать работать после обновления. Рекомендуется использовать в сценариях чтения шкалы. В разделе [группы доступности чтения шкалы Настройка для SQL Server в Linux](sql-server-linux-availability-group-configure-rs.md).
- `sys.fn_hadr_backup_is_preffered_replica`не работает для `CLUSTER_TYPE=NONE` или `CLUSTER_TYPE=EXTERNAL` тем, что он использует реестр кластера WSFC реплицируются ключа, которого не доступен. Мы работаем над предоставляет аналогичные функциональные возможности через другую функцию. 

#### <a name="full-text-search"></a>Full-Text Search
- В этом выпуске, включая фильтры для документов Office доступны не все фильтры. Список поддерживаемых фильтров см. в разделе [установить SQL Server Full-Text Search в Linux](sql-server-linux-setup-full-text-search.md#filters).

- Средства разбиения по словам корейского занимает несколько секунд для загрузки и приводит к ошибке при первом использовании. После первоначальной ошибки он должен работать нормально.

#### <a name="sql-agent"></a>Агент SQL Server
- Следующие компоненты и подсистемах задания агента SQL Server не поддерживаются в настоящее время на платформе Linux:

    - Подсистемы: CmdExec, PowerShell, распространитель репликации, моментальных снимков, слияния, агент чтения очереди, служб SSIS, SSAS, SSRS
    - Предупреждения
    - DB Mail
    - Агент чтения журнала. 
    - Система отслеживания измененных данных

#### <a name="sqlpackage"></a>SqlPackage
- Используя программу SqlPackage необходимо указать абсолютный путь к файлам. Относительные пути будут сопоставления файлов «/ tmp/sqlpackage. \<кода \> /system/system32» папки. 

    - **Разрешение**: использовать абсолютные пути.

- SqlPackage показывает расположение файлов с «C:\\"префикс.

    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
В SSMS для подключения к SQL Server в Linux Windows применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщика данных в среде SSMS не поддерживаются. 

- Компоненты пользовательского интерфейса среды SSMS с проверкой подлинности Windows или параметры журнала событий Windows не поддерживают работу с Linux. Эти функции по-прежнему можно использовать с другими действиями, например имена входа SQL. 

- Невозможно изменить количество файлов журнала для хранения.

### <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. в следующих учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Разделение панель график](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp14"></a>CTP-версии 1.4 (март 2017 г.)
Версия ядра SQL Server для этого выпуска, 14.0.405.198.

### <a name="supported-platforms"></a>Поддерживаемые платформы 

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, рабочей станции, серверов и настольных компьютеров | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| Сервер Linux версии 12 SUSE Enterprise с пакетом обновления 2 | EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS и 16.10 | EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема docker 1.8 + в Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Необходимо по крайней мере 3,25 ГБ памяти для запуска SQL Server в Linux.
> Модуль SQL Server был протестирован до 1 ТБ памяти в данный момент.

### <a name="package-details"></a>Сведения о пакете
Сведения о пакете и адреса для пакеты RPM и Debian, перечислены в следующей таблице. Обратите внимание, что необходимо загрузить эти пакеты напрямую при использовании действия установки проведет ниже
-   [Установить пакет SQL Server](sql-server-linux-setup.md)
-   [Установить пакет Full-text Search](sql-server-linux-setup-full-text-search.md)
-   [Установить пакет агента SQL Server](sql-server-linux-setup-sql-agent.md)

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.405.200-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.405.200-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.405.200-1.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.405.200-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.405.200-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.405.200-1 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.405.200-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.405.200-1.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.405.200-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.405.200-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.405.200-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.405.200-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.405.200-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.405.200-1_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.405.200-1_amd64.deb) |
| Пакет Debian Ubuntu 16.10 | 14.0.405.200-1 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.405.200-1_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.405.200-1_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.405.200-1_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.405.200-1_amd64.deb) |

### <a name="supported-client-tools"></a>Поддерживаемые клиентские средства

| Инструмент | Минимальная версия |
|-----|-----|
| [SQL Server Management Studio (SSMS) для Windows — версия-кандидат 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools для Visual Studio — версия-кандидат 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Код Visual Studio](https://code.visualstudio.com) с [mssql расширения](https://aka.ms/mssql-marketplace) | Последнюю версию (0.2.1) |

> [!NOTE] 
> SQL Server Management Studio и SQL Server Data Tools указанная выше подходят выпуска, поэтому не рекомендуется использовать в производственной среде.

### <a name="unsupported-features-and-services"></a>Неподдерживаемые функции и службы
Следующие функции и службы недоступны в Linux в настоящее время. Во время месячную периодичность обновления программы предварительного просмотра будет более включена поддержка этих возможностей.

| Область | Неподдерживаемые функции или службы |
|-----|-----|
| **Компонент Database engine** | Репликация |
| &nbsp; | Растяжение базы данных |
| &nbsp; | Polybase |
| &nbsp; | Распределенный запрос |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL, и т. д.) |
| &nbsp; | Таблицы filetable |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| **Обеспечение высокого уровня доступности** | Зеркальное отображение базы данных  |
| **Безопасность** | Проверка подлинности Active Directory |
| &nbsp; | Проверка подлинности Windows. |
| &nbsp; | расширенное управление ключами |
| &nbsp; | Использование сертификата, предоставленного пользователем для SSL или TLS |
| **Службы** | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Службы Integration Services | 
| &nbsp; | Службы Data Quality Services |
| &nbsp; | Службы Master Data Services |

### <a name="known-issues"></a>Известные проблемы
В следующих разделах описаны известные проблемы с этим выпуском SQL Server 2017 г CTP-версии 1.4 в Linux.

#### <a name="general"></a>Общие сведения
- Длина имени узла, где SQL Server, установленных нуждается в 15 символов или меньше. 

    - **Разрешение**: измените имя в/etc/hostname на что-нибудь 15 или меньше знаков.

- Не выполняйте команду `ALTER SERVICE MASTER KEY REGENERATE`. Нет известных ошибку, которая приведет к SQL Server, чтобы стать нестабильным. Если необходимо выполнить повторное создание главного ключа службы, вы должны резервное копирование файлов базы данных, удалить и повторно установить SQL Server и восстановите файлы базы данных.

- Вручную системное время обратной вовремя, то SQL Server остановить обновление внутреннего системного времени в SQL Server.

    - **Разрешение**: перезапустите SQL Server.

- Некоторые имена часовых поясов в Linux не соответствуют точно имена часовых поясов Windows.

    - **Разрешение**: использовать имена часовых поясов из столбца TZID "сопоставления для: таблица раздел Windows на [кодовые страницы документации](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- SQL Server Engine ожидает, что строки в текстовых файлах, подлежащего прерыванию с CR-LF (форматирование линий стиль Windows).

- Поддерживаются только один экземпляр установки.

    - **Разрешение**: Если вы хотите иметь более одного экземпляра на конкретном узле, рассмотрите возможность использования виртуальных машин или контейнеры Docker. 

- Все файлы журналов и журналы ошибок, закодированы в кодировке UTF-16.

- Диспетчер конфигурации SQL Server не удается подключиться к SQL Server в Linux.

- **CREATE ASSEMBLY** не будут работать при попытке использовать файл. Используйте **FROM \<bits\>**  метод вместо сейчас. 

#### <a name="databases"></a>Базы данных
- Не удается переместить системные базы данных с помощью служебной программы mssql conf.

- При восстановлении базы данных, которая была создана резервная копия на сервере SQL Server в Windows, необходимо использовать **WITH MOVE** предложение в инструкции Transact-SQL.

- Распределенные транзакции, требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на ОС Linux. SQL Server до SQL Server, поддерживаются распределенные транзакции.

#### <a name="always-on-availability-group"></a>Всегда в группе доступности
- Группы доступности AlwaysOn кластеризованные ресурсы в Linux, которые были созданы с CTP-версии 1.3, будут завершаться сбоем после обновления HA пакета (mssql-server-ha). 

   - **Разрешение**: перед обновлением пакета высокого уровня ДОСТУПНОСТИ, задайте параметр ресурса кластера `notify=true`. 
   
      - В следующем примере задается параметр ресурса кластера для ресурса с именем **ag1** RHEL или Ubuntu: 

      ```bash
      sudo pcs resource update ag1-master notify=true
      ```

      - Для SLES, обновите конфигурацию ресурсов группы доступности для добавления `notify=true`.  

      ```bash
      crm configure edit ms-ag_cluster 
      ```

      Добавить `notify=true` и сохранить конфигурацию ресурсов.

- Если в режиме синхронной фиксации реплик группы доступности AlwaysOn в Linux могут применяться потери данных. Подробности см. в соответствии с дистрибутива Linux. 

   - [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   - [SLES](sql-server-linux-availability-group-cluster-sles.md)
   - [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

#### <a name="full-text-search"></a>Full-Text Search
- В этом выпуске, включая фильтры для документов Office доступны не все фильтры. Список поддерживаемых фильтров см. в разделе [установить SQL Server Full-Text Search в Linux](sql-server-linux-setup-full-text-search.md#filters).

- Средства разбиения по словам корейского занимает несколько секунд для загрузки и приводит к ошибке при первом использовании. После первоначальной ошибки он должен работать нормально.

#### <a name="sql-agent"></a>Агент SQL Server
- Следующие компоненты и подсистемах задания агента SQL Server не поддерживаются в настоящее время на платформе Linux:
    - Подсистемы: CmdExec, PowerShell, распространитель репликации, моментальных снимков, слияния, агент чтения очереди, служб SSIS, SSAS, SSRS
    - Предупреждения
    - DB Mail
    - Доставка журналов
    - Агент чтения журнала. 
    - Система отслеживания измененных данных

#### <a name="in-memory-oltp"></a>In-Memory OLTP
- Базы данных OLTP в памяти могут создаваться только в каталоге /var/opt/mssql. Дополнительные сведения см. на сайте [разделе OLTP в памяти](sql-server-linux-performance-get-started.md#use-in-memory-oltp).

#### <a name="sqlpackage"></a>SqlPackage
- Используя программу SqlPackage необходимо указать абсолютный путь к файлам. Относительные пути будут сопоставления файлов «/ tmp/sqlpackage. \<кода \> /system/system32» папки. 

    - **Разрешение**: использовать абсолютные пути.

- SqlPackage показывает расположение файлов с «C:\\"префикс.

    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
В SSMS для подключения к SQL Server в Linux Windows применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщика данных в среде SSMS не поддерживается. 

- Компоненты пользовательского интерфейса среды SSMS с проверкой подлинности Windows или параметры журнала событий Windows не поддерживают работу с Linux. Эти функции по-прежнему можно использовать с другими действиями, например имена входа SQL. 

- В обозревателе файлов будет ограничен «C:\\» области, которое разрешается/var/opt/mssql/в Linux. Для использования другими путями, создание сценариев работы пользовательского интерфейса и замена C:\\ пути с путями Linux. Затем выполните скрипт вручную в среде SSMS.

- Невозможно изменить количество файлов журнала для хранения.

### <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. в следующих учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Разделение панель график](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp13"></a>CTP-версии 1.3 (февраля 2017 г.)
Версия ядра SQL Server для этого выпуска, 14.0.304.138.

### <a name="supported-platforms"></a>Поддерживаемые платформы 

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, рабочей станции, серверов и настольных компьютеров | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| Сервер Linux версии 12 SUSE Enterprise с пакетом обновления 2 | EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS и 16.10 | EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема docker 1.8 + в Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Необходимо по крайней мере 3,25 ГБ памяти для запуска SQL Server в Linux.
> Модуль SQL Server был протестирован до 1 ТБ памяти в данный момент.

### <a name="package-details"></a>Сведения о пакете
Сведения о пакете и адреса для пакеты RPM и Debian, перечислены в следующей таблице. Обратите внимание, что не требуется загрузить пакеты напрямую при использовании действия, описанные в [руководства по установке](sql-server-linux-setup.md).

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.304.138-1 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.304.138-1.x86_64.rpm)</br>[пакет MSSQL-server-высокой доступности высокого уровня доступности об/мин](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.304.138-1.x86_64.rpm)</br>[MSSQL-server-fts пакета RPM Full-text Search](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.304.138-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.304.138-1 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.304.138-1.x86_64.rpm)</br>[пакет MSSQL-server-высокой доступности высокого уровня доступности об/мин](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.304.138-1.x86_64.rpm)</br>[MSSQL-server-fts пакета RPM Full-text Search](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.304.138-1.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.304.138-1 | [пакет Debian ядра сервера MSSQL](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.304.138-1_amd64.deb)</br>[MSSQL-server-высокой доступности высокого уровня доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.304.138-1_amd64.deb)</br>[пакет Debian MSSQL-server-fts Full-text Search](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.304.138-1_amd64.deb) |
| Пакет Debian Ubuntu 16.10 | 14.0.304.138-1 | [пакет Debian ядра сервера MSSQL](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.304.138-1_amd64.deb)</br>[MSSQL-server-высокой доступности высокого уровня доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.304.138-1_amd64.deb)</br>[пакет Debian MSSQL-server-fts Full-text Search](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.304.138-1_amd64.deb) |

### <a name="supported-client-tools"></a>Поддерживаемые клиентские средства

| Инструмент | Минимальная версия |
|-----|-----|
| [SQL Server Management Studio (SSMS) для Windows — версия-кандидат 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools для Visual Studio — версия-кандидат 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Код Visual Studio](https://code.visualstudio.com) с [mssql расширения](https://aka.ms/mssql-marketplace) | Последнюю версию (0.2.1) |

> [!NOTE] 
> SQL Server Management Studio и SQL Server Data Tools указанная выше подходят выпуска, поэтому не рекомендуется использовать в производственной среде.

### <a name="unsupported-features-and-services"></a>Неподдерживаемые функции и службы
Следующие функции и службы недоступны в Linux в настоящее время. Во время месячную периодичность обновления программы предварительного просмотра будет более включена поддержка этих возможностей.

| Область | Неподдерживаемые функции или службы |
|-----|-----|
| **Компонент Database engine** | Репликация |
| &nbsp; | Растяжение базы данных |
| &nbsp; | Polybase |
| &nbsp; | Распределенный запрос |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL, и т. д.) |
| &nbsp; | Таблицы filetable |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| **Обеспечение высокого уровня доступности** | Зеркальное отображение базы данных  |
| **Безопасность** | Проверка подлинности Active Directory |
| &nbsp; | Проверка подлинности Windows. |
| &nbsp; | расширенное управление ключами |
| &nbsp; | Использование сертификата, предоставленного пользователем для SSL или TLS |
| **Службы** | SQL Server, агент |
| &nbsp; | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Службы Integration Services | 
| &nbsp; | Службы Data Quality Services |
| &nbsp; | Службы Master Data Services |

### <a name="known-issues"></a>Известные проблемы
В следующих разделах описаны известные проблемы с этим выпуском SQL Server 2017 г CTP-версии 1.3 в Linux.

#### <a name="general"></a>Общие сведения
- Длина имени узла, где SQL Server, установленных нуждается в 15 символов или меньше. 

    - **Разрешение**: измените имя в/etc/hostname на что-нибудь 15 или меньше знаков.

- Не выполняйте команду `ALTER SERVICE MASTER KEY REGENERATE`. Нет известных ошибку, которая приведет к SQL Server, чтобы стать нестабильным. Если необходимо выполнить повторное создание главного ключа службы, вы должны резервное копирование файлов базы данных, удалить и повторно установить SQL Server и восстановите файлы базы данных.

- Вручную системное время обратной вовремя, то SQL Server остановить обновление внутреннего системного времени в SQL Server.

    - **Разрешение**: перезапустите SQL Server.

- Некоторые имена часовых поясов в Linux не соответствуют точно имена часовых поясов Windows.

    - **Разрешение**: использовать имена часовых поясов из столбца TZID "сопоставления для: таблица раздел Windows на [кодовые страницы документации](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- SQL Server Engine ожидает, что строки в текстовых файлах, подлежащего прерыванию с CR-LF (форматирование линий стиль Windows).

- Поддерживаются только один экземпляр установки.

    - **Разрешение**: Если вы хотите иметь более одного экземпляра на конкретном узле, рассмотрите возможность использования виртуальных машин или контейнеры Docker. 

- Все файлы журналов и журналы ошибок, закодированы в кодировке UTF-16.

- Диспетчер конфигурации SQL Server не удается подключиться к SQL Server в Linux.

- **CREATE ASSEMBLY** не будут работать при попытке использовать файл. Используйте **FROM \<bits\>**  метод вместо сейчас. 

#### <a name="databases"></a>Базы данных
- Изменение расположения файлов данных и журналов базы данных TempDB не поддерживается.

- Не удается переместить системные базы данных с помощью служебной программы mssql conf.

- При восстановлении базы данных, которая была создана резервная копия на сервере SQL Server в Windows, необходимо использовать **WITH MOVE** предложение в инструкции Transact-SQL.

- Распределенные транзакции, требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на ОС Linux. SQL Server до SQL Server, поддерживаются распределенные транзакции.

- Если в режиме синхронной фиксации реплик группы доступности AlwaysOn в Linux могут применяться потери данных. См. 
 
   - [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   - [SLES](sql-server-linux-availability-group-cluster-sles.md)
   - [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   
#### <a name="full-text-search"></a>Full-Text Search
- В этом выпуске, включая фильтры для документов Office доступны не все фильтры. Список поддерживаемых фильтров см. в разделе [установить SQL Server Full-Text Search в Linux](sql-server-linux-setup-full-text-search.md#filters).

- Средства разбиения по словам корейского занимает несколько секунд для загрузки и приводит к ошибке при первом использовании. После первоначальной ошибки он должен работать нормально.

#### <a name="in-memory-oltp"></a>In-Memory OLTP
- Базы данных OLTP в памяти могут создаваться только в каталоге /var/opt/mssql. Дополнительные сведения см. на сайте [разделе OLTP в памяти](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- Используя программу SqlPackage необходимо указать абсолютный путь к файлам. Относительные пути будут сопоставления файлов «/tmp/sqlpackage./ <code/> /system/system32» папки. 

    - **Разрешение**: использовать абсолютные пути.

- SqlPackage показывает расположение файлов с «C:\\"префикс.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD и BCP и ODBC 
- SQL Server командной строки средства (mssql-tools) и драйвер ODBC (msodbcsql) зависит от пользовательского диспетчера драйверов unixODBC. Это приводит к конфликтам при наличии ранее установленного диспетчера драйверов unixODBC. 

    - **Разрешение**: на Ubuntu, конфликт устраняется автоматически. При появлении запроса о необходимости удаления существующего диспетчера драйверов unixODBC, введите «y» и продолжите установку. На RedHat, необходимо удалить существующий диспетчер драйверов unixODBC вручную с помощью `yum remove unixODBC`. Мы работаем над исправления это ограничение для RHEL и SUSE и должны иметь обновление для вас скоро.  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
В SSMS для подключения к SQL Server в Linux Windows применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщика данных в среде SSMS не поддерживается. 

- Компоненты пользовательского интерфейса среды SSMS с проверкой подлинности Windows или параметры журнала событий Windows не поддерживают работу с Linux. Эти функции по-прежнему можно использовать с другими действиями, например имена входа SQL. 

- Агент SQL Server еще не поддерживается. Таким образом функциональные возможности агента SQL Server в среде SSMS не работает на платформе Linux на данный момент.

- В обозревателе файлов будет ограничен «C:\\» области, которое разрешается/var/opt/mssql/в Linux. Для использования другими путями, создание сценариев работы пользовательского интерфейса и замена C:\\ пути с путями Linux. Затем выполните скрипт вручную в среде SSMS.

- Невозможно изменить количество файлов журнала для хранения.

### <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. в следующих учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Разделение панель график](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp12-ctp-12-january-2017"></a><a id="ctp12">CTP-версии 1.2 (января 2017 г.)
Версия ядра SQL Server для этого выпуска, 14.0.200.24.

### <a name="supported-platforms"></a>Поддерживаемые платформы 

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, рабочей станции, серверов и настольных компьютеров | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| Сервер Linux версии 12 SUSE Enterprise с пакетом обновления 2 | EXT4 | [Руководство по установке](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS и 16.10 | EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема docker 1.8 + в Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Необходимо по крайней мере 3,25 ГБ памяти для запуска SQL Server в Linux.
> Модуль SQL Server только был протестирован до 256 ГБ памяти на данный момент.

### <a name="package-details"></a>Сведения о пакете
Сведения о пакете и адреса для пакеты RPM и Debian, перечислены в следующей таблице. Обратите внимание, что не требуется загрузить пакеты напрямую при использовании действия, описанные в [руководства по установке](sql-server-linux-setup.md).

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM | 14.0.200.24-2 | [пакет RPM ядра сервера MSSQL 14.0.200.24-2](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.200.24-2.x86_64.rpm)</br>[пакет RPM высокого уровня доступности сервера MSSQL 14.0.200.24-2](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.200.24-2.x86_64.rpm) | 
| Пакет Debian | 14.0.200.24-2 | [пакет Debian Engine 14.0.200.24-2 MSSQL сервера](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.200.24-2_amd64.deb) |

### <a name="supported-client-tools"></a>Поддерживаемые клиентские средства

| Инструмент | Минимальная версия |
|-----|-----|
| [SQL Server Management Studio (SSMS) для Windows — версия-кандидат 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools для Visual Studio — версия-кандидат 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Код Visual Studio](https://code.visualstudio.com) с [mssql расширения](https://aka.ms/mssql-marketplace) | Последнюю версию (0.2) |

> [!NOTE] 
> SQL Server Management Studio и SQL Server Data Tools указанная выше подходят выпуска, поэтому не рекомендуется использовать в производственной среде.

### <a name="unsupported-features-and-services"></a>Неподдерживаемые функции и службы
Следующие функции и службы недоступны в Linux в настоящее время. Во время месячную периодичность обновления программы предварительного просмотра будет более включена поддержка этих возможностей.

| Область | Неподдерживаемые функции или службы |
|-----|-----|
| **Компонент Database engine** | Компонент Full-text Search |
| &nbsp; | Репликация |
| &nbsp; | Растяжение базы данных |
| &nbsp; | Polybase |
| &nbsp; | Распределенный запрос |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL, и т. д.) |
| &nbsp; | Таблицы filetable |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| **Обеспечение высокого уровня доступности** | Группы доступности AlwaysOn |
| &nbsp; | Зеркальное отображение базы данных  |
| **Безопасность** | Проверка подлинности Active Directory |
| &nbsp; | Проверка подлинности Windows. |
| &nbsp; | расширенное управление ключами |
| &nbsp; | Использование сертификата, предоставленного пользователем для SSL или TLS |
| **Службы** | SQL Server, агент |
| &nbsp; | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Службы Integration Services | 
| &nbsp; | Службы Data Quality Services |
| &nbsp; | Службы Master Data Services |

### <a name="known-issues"></a>Известные проблемы
В следующих разделах описаны известные проблемы с этим выпуском SQL Server 2017 г CTP-версии 1.2 в Linux.

#### <a name="general"></a>Общие сведения
- Длина имени узла, где SQL Server, установленных нуждается в 15 символов или меньше. 

    - **Разрешение**: измените имя в/etc/hostname на что-нибудь 15 или меньше знаков.

- Не выполняйте команду `ALTER SERVICE MASTER KEY REGENERATE`. Нет известных ошибку, которая приведет к SQL Server, чтобы стать нестабильным. Если необходимо выполнить повторное создание главного ключа службы, вы должны резервное копирование файлов базы данных, удалить и повторно установить SQL Server и восстановите файлы базы данных.

- Имя ресурса для ресурса SQL изменен с ocf:sql:fci на ocf:mssql:fci. Дополнительные сведения о настройке отказоустойчивого кластера общего диска можно найти [здесь](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-shared-disk-cluster-red-hat-7-configure).

- Вручную системное время обратной вовремя, то SQL Server остановить обновление внутреннего системного времени в SQL Server.

    - **Разрешение**: перезапустите SQL Server.

- Некоторые имена часовых поясов в Linux не соответствуют точно имена часовых поясов Windows.

    - **Разрешение**: использовать имена часовых поясов из столбца TZID "сопоставления для: таблица раздел Windows на [кодовые страницы документации](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- SQL Server Engine ожидает, что строки в текстовых файлах, подлежащего прерыванию с CR-LF (форматирование линий стиль Windows).

- Поддерживаются только один экземпляр установки.

    - **Разрешение**: Если вы хотите иметь более одного экземпляра на конкретном узле, рассмотрите возможность использования виртуальных машин или контейнеры Docker. 

- Все файлы журналов и журналы ошибок, закодированы в кодировке UTF-16.

- Диспетчер конфигурации SQL Server не удается подключиться к SQL Server в Linux.

- **CREATE ASSEMBLY** не будут работать при попытке использовать файл. Используйте **FROM \<bits\>**  метод вместо сейчас. 

#### <a name="databases"></a>Базы данных
- Изменение расположения файлов данных и журналов базы данных TempDB не поддерживается.

- Не удается переместить системные базы данных с помощью служебной программы mssql conf.

- При восстановлении базы данных, которая была создана резервная копия на сервере SQL Server в Windows, необходимо использовать **WITH MOVE** предложение в инструкции Transact-SQL.

- Распределенные транзакции, требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на ОС Linux. SQL Server до SQL Server, поддерживаются распределенные транзакции.

#### <a name="in-memory-oltp"></a>In-Memory OLTP
- Базы данных OLTP в памяти могут создаваться только в каталоге /var/opt/mssql. Эти базы данных также должен быть «C:\\» нотации, если ссылка. Дополнительные сведения см. на сайте [разделе OLTP в памяти](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- Используя программу SqlPackage необходимо указать абсолютный путь к файлам. Относительные пути будут сопоставления файлов «/ tmp/sqlpackage. \<кода \> /system/system32» папки. 

    - **Разрешение**: использовать абсолютные пути.

- SqlPackage показывает расположение файлов с «C:\\"префикс.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD и BCP и ODBC 
- Если у вас есть более старой версии средства командной строки SQL Server (mssql инструменты) и драйвер ODBC (msodbcsql), вы установили пользовательских unixODBC диспетчера драйверов (unixODBC-utf16). Это может вызвать потенциальный конфликт, как мы больше не используется диспетчер драйверов. 

    - **Разрешение**: Ubuntu и SLES, конфликт устраняется автоматически. При появлении запроса о необходимости удаления существующего диспетчера драйверов unixODBC, введите «y» и продолжите установку. На RedHat, необходимо удалить существующий диспетчер драйверов unixODBC вручную с помощью `yum remove unixODBC-utf16 unixODBC-utf16-devel` и повторить попытку установки.
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
В SSMS для подключения к SQL Server в Linux Windows применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщика данных в среде SSMS не поддерживается. 

- Компоненты пользовательского интерфейса среды SSMS с проверкой подлинности Windows или параметры журнала событий Windows не поддерживают работу с Linux. Эти функции по-прежнему можно использовать с другими действиями, например имена входа SQL. 

- Агент SQL Server еще не поддерживается. Таким образом функциональные возможности агента SQL Server в среде SSMS не работает на платформе Linux на данный момент.

- В обозревателе файлов будет ограничен «C:\\» области, которое разрешается/var/opt/mssql/в Linux. Для использования другими путями, создание сценариев работы пользовательского интерфейса и замена C:\\ пути с путями Linux. Затем выполните скрипт вручную в среде SSMS.

### <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. в следующих учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Разделение панель график](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp11-ctp-11-december-2016"></a><a id="ctp11">CTP-версии 1.1 (декабря 2016 г.)
Версия ядра SQL Server для этого выпуска, 14.0.100.187.

### <a name="supported-platforms"></a>Поддерживаемые платформы 

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux, рабочей станции, серверов и настольных компьютеров | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| Ubuntu 16.04LTS и 16.10 | EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема docker 1.8 + в Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Необходимо по крайней мере 3,25 ГБ памяти для запуска SQL Server в Linux.
> Модуль SQL Server только был протестирован до 256 ГБ памяти на данный момент.

### <a name="package-details"></a>Сведения о пакете
Сведения о пакете и адреса для пакеты RPM и Debian, перечислены в следующей таблице. Обратите внимание, что не требуется загрузить пакеты напрямую при использовании действия, описанные в [руководства по установке](sql-server-linux-setup.md).

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM | 14.0.100.187-1 | [пакет RPM ядра сервера MSSQL 14.0.100.187-1](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.100.187-1.x86_64.rpm)</br>[пакет RPM высокого уровня доступности сервера MSSQL 14.0.100.187-1](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.100.187-1.x86_64.rpm) | 
| Пакет Debian | 14.0.100.187-1 | [пакет Debian Engine 14.0.100.187-1 MSSQL сервера](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.100.187-1_amd64.deb) |

### <a name="supported-client-tools"></a>Поддерживаемые клиентские средства

| Инструмент | Минимальная версия |
|-----|-----|
| [SQL Server Management Studio (SSMS) для Windows — версия-кандидат 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools для Visual Studio — версия-кандидат 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Код Visual Studio](https://code.visualstudio.com) с [mssql расширения](https://aka.ms/mssql-marketplace) | Последнюю версию (0.2) |

> [!NOTE] 
> SQL Server Management Studio и SQL Server Data Tools указанная выше подходят выпуска, поэтому не рекомендуется использовать в производственной среде.

### <a name="unsupported-features-and-services"></a>Неподдерживаемые функции и службы
Следующие функции и службы недоступны в Linux в настоящее время. Во время месячную периодичность обновления программы предварительного просмотра будет более включена поддержка этих возможностей.

| Область | Неподдерживаемые функции или службы |
|-----|-----|
| **Компонент Database engine** | Компонент Full-text Search |
| &nbsp; | Репликация |
| &nbsp; | Растяжение базы данных |
| &nbsp; | Polybase |
| &nbsp; | Распределенный запрос |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL, и т. д.) |
| &nbsp; | Таблицы filetable |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| **Обеспечение высокого уровня доступности** | Группы доступности AlwaysOn |
| &nbsp; | Зеркальное отображение базы данных  |
| **Безопасность** | Проверка подлинности Active Directory |
| &nbsp; | Проверка подлинности Windows. |
| &nbsp; | расширенное управление ключами |
| &nbsp; | Использование сертификата, предоставленного пользователем для SSL или TLS |
| **Службы** | SQL Server, агент |
| &nbsp; | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Службы Integration Services | 
| &nbsp; | Службы Data Quality Services |
| &nbsp; | Службы Master Data Services |

### <a name="known-issues"></a>Известные проблемы
В следующих разделах описаны известные проблемы с этим выпуском SQL Server 2017 г CTP-версии 1.1 в Linux.

#### <a name="general"></a>Общие сведения
- Длина имени узла, где SQL Server, установленных нуждается в 15 символов или меньше. 

    - **Разрешение**: измените имя в/etc/hostname на что-нибудь 15 или меньше знаков.

- Не выполняйте команду `ALTER SERVICE MASTER KEY REGENERATE`. Нет известных ошибку, которая приведет к SQL Server, чтобы стать нестабильным. Если необходимо выполнить повторное создание главного ключа службы, вы должны резервное копирование файлов базы данных, удалить и повторно установить SQL Server и восстановите файлы базы данных.

- Имя ресурса для ресурса SQL изменен с ocf:sql:fci на ocf:mssql:fci. Дополнительные сведения о настройке отказоустойчивого кластера общего диска можно найти [здесь](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-shared-disk-cluster-red-hat-7-configure).

- Вручную системное время обратной вовремя, то SQL Server остановить обновление внутреннего системного времени в SQL Server.

    - **Разрешение**: перезапустите SQL Server.

- Некоторые имена часовых поясов в Linux не соответствуют точно имена часовых поясов Windows.

    - **Разрешение**: использовать имена часовых поясов из столбца TZID "сопоставления для: таблица раздел Windows на [кодовые страницы документации](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- SQL Server Engine ожидает, что строки в текстовых файлах, подлежащего прерыванию с CR-LF (форматирование линий стиль Windows).

- Поддерживаются только один экземпляр установки.

    - **Разрешение**: Если вы хотите иметь более одного экземпляра на конкретном узле, рассмотрите возможность использования виртуальных машин или контейнеры Docker. 

- Все файлы журналов и журналы ошибок, закодированы в кодировке UTF-16.

- Диспетчер конфигурации SQL Server не удается подключиться к SQL Server в Linux.

- **CREATE ASSEMBLY** не будут работать при попытке использовать файл. Используйте **FROM \<bits\>**  метод вместо сейчас. 

#### <a name="databases"></a>Базы данных
- Изменение расположения файлов данных и журналов базы данных TempDB не поддерживается.

- Не удается переместить системные базы данных с помощью служебной программы mssql conf.

- При восстановлении базы данных, которая была создана резервная копия на сервере SQL Server в Windows, необходимо использовать **WITH MOVE** предложение в инструкции Transact-SQL.

- Распределенные транзакции, требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на ОС Linux. SQL Server до SQL Server, поддерживаются распределенные транзакции.

#### <a name="in-memory-oltp"></a>In-Memory OLTP
- Базы данных OLTP в памяти могут создаваться только в каталоге /var/opt/mssql. Эти базы данных также должен быть «C:\" нотации, если ссылка. Дополнительные сведения см. на сайте [разделе OLTP в памяти](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- Используя программу SqlPackage необходимо указать абсолютный путь к файлам. Относительные пути будут сопоставления файлов «/ tmp/sqlpackage. \<кода \> /system/system32» папки. 

    - **Разрешение**: использовать абсолютные пути.

- SqlPackage показывает расположение файлов с «C:\\"префикс.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD и BCP и ODBC 
- SQL Server командной строки средства (mssql-tools) и драйвер ODBC (msodbcsql) зависит от пользовательского диспетчера драйверов unixODBC. Это приводит к конфликтам при наличии ранее установленного диспетчера драйверов unixODBC. 

    - **Разрешение**: на Ubuntu, конфликт устраняется автоматически. При появлении запроса о необходимости удаления существующего диспетчера драйверов unixODBC, введите «y» и продолжите установку. На RedHat, необходимо удалить существующий диспетчер драйверов unixODBC вручную с помощью `yum remove unixODBC`. Мы работаем над исправления это ограничение для RHEL и SUSE и должны иметь обновление для вас скоро.  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
В SSMS для подключения к SQL Server в Linux Windows применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщика данных в среде SSMS не поддерживается. 

- Компоненты пользовательского интерфейса среды SSMS с проверкой подлинности Windows или параметры журнала событий Windows не поддерживают работу с Linux. Эти функции по-прежнему можно использовать с другими действиями, например имена входа SQL. 

- Агент SQL Server еще не поддерживается. Таким образом функциональные возможности агента SQL Server в среде SSMS не работает на платформе Linux на данный момент.

- В обозревателе файлов будет ограничен «C:\\» области, которое разрешается/var/opt/mssql/в Linux. Для использования другими путями, создание сценариев работы пользовательского интерфейса и замена C:\\ пути с путями Linux. Затем выполните скрипт вручную в среде SSMS.

v

![Разделение панель график](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp10-ctp-10-november-2016"></a><a id="ctp10">CTP-версии 1.0 (ноябрь 2016 г.)
Версия ядра SQL Server для этого выпуска, 14.0.1.246.

### <a name="supported-platforms"></a>Поддерживаемые платформы 

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.2 станции, серверов и настольных компьютеров | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
| Ubuntu 16.04LTS | EXT4 | [Руководство по установке](quickstart-install-connect-ubuntu.md) | 
| Подсистема docker 1.8 + в Windows, Mac или Linux | Недоступно | [Руководство по установке](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Необходимо по крайней мере 3,25 ГБ памяти для запуска SQL Server в Linux.
> Модуль SQL Server только был протестирован до 256 ГБ памяти на данный момент.

### <a name="package-details"></a>Сведения о пакете
Сведения о пакете и адреса для пакеты RPM и Debian, перечислены в следующей таблице. Обратите внимание, что не требуется загрузить пакеты напрямую при использовании действия, описанные в [руководства по установке](sql-server-linux-setup.md).

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет RPM | 14.0.1.246-6 | [пакет RPM ядра сервера MSSQL 14.0.1.246-6](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.1.246-6.x86_64.rpm)</br>[пакет RPM высокого уровня доступности сервера MSSQL 14.0.1.246-6](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.1.246-6.x86_64.rpm) | 
| Пакет Debian | 14.0.1.246-6 | [пакет Debian Engine 14.0.1.246-6 MSSQL сервера](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.1.246-6_amd64.deb) |

### <a name="supported-client-tools"></a>Поддерживаемые клиентские средства

| Инструмент | Минимальная версия |
|-----|-----|
| [SQL Server Management Studio (SSMS) для Windows — версия-кандидат 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools для Visual Studio — версия-кандидат 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Код Visual Studio](https://code.visualstudio.com) с [mssql расширения](https://aka.ms/mssql-marketplace) | Последнюю версию (0.1.5) |

> [!NOTE] 
> SQL Server Management Studio и SQL Server Data Tools указанная выше подходят выпуска, поэтому не рекомендуется использовать в производственной среде.

### <a name="unsupported-features-and-services"></a>Неподдерживаемые функции и службы
Следующие функции и службы недоступны в Linux в настоящее время. Во время месячную периодичность обновления программы предварительного просмотра будет более включена поддержка этих возможностей.

| Область | Неподдерживаемые функции или службы |
|-----|-----|
| **Компонент Database engine** | Компонент Full-text Search |
| &nbsp; | Репликация |
| &nbsp; | Растяжение базы данных |
| &nbsp; | Polybase |
| &nbsp; | Распределенный запрос |
| &nbsp; | Системные расширенные хранимые процедуры (XP_CMDSHELL, и т. д.) |
| &nbsp; | Таблицы filetable |
| &nbsp; | Задать сборки среды CLR с EXTERNAL_ACCESS или UNSAFE разрешение |
| **Обеспечение высокого уровня доступности** | Группы доступности AlwaysOn |
| &nbsp; | Зеркальное отображение базы данных  |
| **Безопасность** | Проверка подлинности Active Directory |
| &nbsp; | Проверка подлинности Windows. |
| &nbsp; | расширенное управление ключами |
| &nbsp; | Использование сертификата, предоставленного пользователем для SSL или TLS |
| **Службы** | SQL Server, агент |
| &nbsp; | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Службы Integration Services | 
| &nbsp; | Службы Data Quality Services |
| &nbsp; | Службы Master Data Services |

### <a name="known-issues"></a>Известные проблемы
В следующих разделах описаны известные проблемы в этом выпуске SQL Server 2017 г CTP 1 в Linux.

#### <a name="general"></a>Общие сведения
- Длина имени узла, где SQL Server, установленных нуждается в 15 символов или меньше. 

    - **Разрешение**: измените имя в/etc/hostname на что-нибудь 15 или меньше знаков.

- Вручную системное время обратной вовремя, то SQL Server остановить обновление внутреннего системного времени в SQL Server.

    - **Разрешение**: перезапустите SQL Server.

- Некоторые имена часовых поясов в Linux не соответствуют точно имена часовых поясов Windows.

    - **Разрешение**: использовать имена часовых поясов из столбца TZID "сопоставления для: таблица раздел Windows на [кодовые страницы документации](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- SQL Server Engine ожидает, что строки в текстовых файлах, подлежащего прерыванию с CR-LF (форматирование линий стиль Windows).

- Поддерживаются только один экземпляр установки.

    - **Разрешение**: Если вы хотите иметь более одного экземпляра на конкретном узле, рассмотрите возможность использования виртуальных машин или контейнеры Docker. 

- Все файлы журналов и журналы ошибок, закодированы в кодировке UTF-16.

- Диспетчер конфигурации SQL Server не удается подключиться к SQL Server в Linux.

- **CREATE ASSEMBLY** не будут работать при попытке использовать файл. Используйте **FROM \<bits\>**  метод вместо сейчас.

#### <a name="databases"></a>Базы данных
- Изменение расположения файлов данных и журналов базы данных TempDB не поддерживается.

- Не удается переместить системные базы данных с помощью служебной программы mssql conf.

- При восстановлении базы данных, которая была создана резервная копия на сервере SQL Server в Windows, необходимо использовать **WITH MOVE** предложение в инструкции Transact-SQL.

- Распределенные транзакции, требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на ОС Linux. SQL Server до SQL Server, поддерживаются распределенные транзакции.

#### <a name="in-memory-oltp"></a>In-Memory OLTP
- Базы данных OLTP в памяти могут создаваться только в каталоге /var/opt/mssql. Эти базы данных также должен быть «C:\\» нотации, если ссылка. Дополнительные сведения см. на сайте [разделе OLTP в памяти](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- Используя программу SqlPackage требуется указать абсолютный путь для файлов. Относительные пути будут сопоставления файлов «/ tmp/sqlpackage. \<кода \> /system/system32» папки. 

    - **Разрешение**: использовать абсолютные пути.

- SqlPackage показывает расположение файлов с «C:\\"префикс.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD и BCP и ODBC 
- SQL Server командной строки средства (mssql-tools) и драйвер ODBC (msodbcsql) зависит от пользовательского диспетчера драйверов unixODBC. Это приводит к конфликтам при наличии ранее установленного диспетчера драйверов unixODBC. 

    - **Разрешение**: на Ubuntu, конфликт устраняется автоматически. При появлении запроса о необходимости удаления существующего диспетчера драйверов unixODBC, введите «y» и продолжите установку. На RedHat, необходимо удалить существующий диспетчер драйверов unixODBC вручную с помощью `yum remove unixODBC`. Мы работаем над исправления это ограничение для RHEL и SUSE и должны иметь обновление для вас скоро.  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
В SSMS для подключения к SQL Server в Linux Windows применяются следующие ограничения.

- Планы обслуживания не поддерживаются.

- Хранилища данных управления (MDW) и сборщика данных в среде SSMS не поддерживается. 

- Компоненты пользовательского интерфейса среды SSMS с проверкой подлинности Windows или параметры журнала событий Windows не поддерживают работу с Linux. Эти функции по-прежнему можно использовать с другими действиями, например имена входа SQL. 

- Агент SQL Server еще не поддерживается. Таким образом функциональные возможности агента SQL Server в среде SSMS не работает на платформе Linux на данный момент.

- В обозревателе файлов будет ограничен «C:\\» области, которое разрешается/var/opt/mssql/в Linux. Для использования другими путями, создание сценариев работы пользовательского интерфейса и замена C:\\ пути с путями Linux. Затем выполните скрипт вручную в среде SSMS.

### <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, см. в следующих учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

