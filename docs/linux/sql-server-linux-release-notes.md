---
title: "Заметки о выпуске для 2017 г. SQL Server в Linux | Документы Microsoft"
description: "В этом разделе содержатся заметки о выпуске и поддерживаемых функций для ОС Linux 2017 г. SQL Server. Заметки о выпуске включаются самым последним выпуском и несколько предыдущих выпусков."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.translationtype: MT
ms.sourcegitcommit: 7811cfe9238c92746673fac4fce40a4af44d6dcd
ms.openlocfilehash: 80c0813accf9f84204f057b9ef4efcad69142ec2
ms.contentlocale: ru-ru
ms.lasthandoff: 10/02/2017

---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Заметки о выпуске для 2017 г. SQL Server в Linux

Следующие замечания к выпуску применяются для ОС Linux 2017 г. SQL Server. Этот выпуск поддерживает многие функции ядра СУБД SQL Server для Linux. Ниже разделе разбивается на разделы для каждого выпуска, начиная с самой последней общие выпуск доступность (GA) и два предыдущих версий. См. информацию в каждом разделе Поддерживаемые платформы, инструменты, возможности и известные проблемы.

В следующей таблице перечислены журнал выпуска для 2017 г. SQL Server.

| Выпуск | Version | Дата выпуска |
|-----|-----|-----|
| [ГЛОБАЛЬНЫЙ АДМИНИСТРАТОР](#GA) | 14.0.1000.169 | 10-2017 |
| [ВЕРСИЯ-КАНДИДАТ 2](#RC2) | 14.0.900.75 | 8-2017 |
| [ВЕРСИЯ-КАНДИДАТ 1](#RC1) | 14.0.800.90 | 7-2017 |
| CTP-ВЕРСИИ 2.1 | 14.0.600.250 | 5-2017 |
| CTP 2.0 | 14.0.500.272 | 4-2017 |
| CTP-ВЕРСИИ 1.4 | 14.0.405.198 | 3-2017 |
| CTP-ВЕРСИИ 1.3 | 14.0.304.138 | 2-2017 |
| CTP-ВЕРСИИ 1.2 | 14.0.200.24 | 1-2017 |
| CTP-ВЕРСИИ 1.1 | 14.0.100.187 | 12-2016 |
| CTP-ВЕРСИИ 1.0 | 14.0.1.246 | 11-2016 |

## <a id="GA"></a>Глобальный Администратор (октябрь 2017 г.)

Это общая проверяется (GA) выпуска 2017 г. SQL Server. Версия ядра SQL Server для этого выпуска, 14.0.1000.169.

### <a name="supported-platforms"></a>Поддерживаемые платформы

| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 или 7.4 станции, серверов и настольных компьютеров | XFS или EXT4 | [Руководство по установке](quickstart-install-connect-red-hat.md) | 
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
| Пакет Red Hat RPM | 14.0.1000.169-2 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Пакет SLES RPM | 14.0.1000.169-2 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Пакет Debian Ubuntu 16.04 | 14.0.1000.169-2 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[Пакет Debian SQL Server, агент](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

### <a name="supported-client-tools"></a>Поддерживаемые клиентские средства

| Инструмент | Минимальная версия |
|-----|-----|
| [SQL Server Management Studio (SSMS) для Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools для Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Код Visual Studio](https://code.visualstudio.com) с [mssql расширения](https://aka.ms/mssql-marketplace) | последние |

### <a name="Unsupported"></a>Неподдерживаемые функции и службы

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
| **SQL Server, агент** |  Подсистемы: CmdExec, PowerShell, агент чтения очереди, служб SSIS, SSAS, SSRS |
| &nbsp; | Предупреждения |
| &nbsp; | Агент чтения журнала. |
| &nbsp; | Система отслеживания измененных данных |
| &nbsp; | Управляемое резервное копирование |
| **Обеспечение высокого уровня доступности** | Зеркальное отображение базы данных  |
| **Безопасность** | расширенное управление ключами |
| &nbsp; | Проверки подлинности AD для связанных серверов | 
| &nbsp; | AD Authenticatin для доступности группы (групп доступности) | 
| **Службы** | Обозреватель SQL Server |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Службы Analysis Services |
| &nbsp; | Службы Reporting Services |
| &nbsp; | Службы Data Quality Services |
| &nbsp; | Службы Master Data Services |

### <a name="known-issues"></a>Известные проблемы

В следующих разделах описаны известные проблемы с выпуском Общи доступность (GA) 2017 г. SQL Server в Linux.

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

- Распределенные транзакции, требуется службу координатора распределенных транзакций не поддерживаются в SQL Server на ОС Linux. SQL Server до SQL Server, поддерживаются распределенные транзакции.

- Некоторые алгоритмы (шифров) Transport Layer Security (TLS) не работают должным образом с SQL Server в Linux. В результате ошибок соединения при попытке подключения к SQL Server, а также проблем с установлением соединения между репликами в группах высокого уровня доступности.

   - **Разрешение**: изменение **mssql.conf** сценария настройки для SQL Server в Linux отключение проблемный шифров, следующим образом:

      1. Добавьте следующую строку /var/opt/mssql/mssql.conf.

      ```
      [network]
      tlsciphers=ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

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

Точная ошибка зависит от компонента. Для связанных серверов это проявляющийся как ошибка времени ожидания входа в систему. Для групп Availbility `ALTER AVAILABILITY GROUP JOIN` DDL на сервере-получателе после 5 минут с ошибку времени ожидания загрузки конфигурации будут завершаться сбоем.

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

- При установке mssql conf и выполнению установки локализованной SQL Server, неправильные символы национального алфавита отображаются после локализованный текст «Настройка SQL Server...». Или для установок на основе нелатинских предложение может отсутствовать полностью. Отсутствует предложение должны отображаться следующие Локализованная строка: «лицензирования продукта успешно обработана.  Новый выпуск [<Name> выпуск]». Эта строка выводится только в информационных целях и далее накопительное обновление SQL Server решает эту для всех языков. Это не влияет на установки SQL Server каким-либо образом. 

#### <a name="full-text-search"></a>Компонент Full-text Search

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

Список встроенных компонентов служб SSIS, в настоящее время не поддерживаются или поддерживаются ограниченно см. в разделе [извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md#components).

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

Чтобы приступить к работе, см. в следующих учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Разделение панель график](./media/sql-server-linux-release-notes/seperationbar3.png)

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
| **SQL Server, агент** |  Подсистемы: CmdExec, PowerShell, агент чтения очереди, служб SSIS, SSAS, SSRS |
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
   
      ```bash
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

#### <a name="full-text-search"></a>Компонент Full-text Search
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
| **SQL Server, агент** |  Подсистемы: CmdExec, PowerShell, агент чтения очереди, служб SSIS, SSAS, SSRS |
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

#### <a name="full-text-search"></a>Компонент Full-text Search
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

