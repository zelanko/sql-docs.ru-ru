---
title: Новые возможности Analytics Platform System — хранилища данных с горизонтальным масштабированием
description: В разделе новые возможности Microsoft® Analytics Platform System масштабирования на локальном устройстве, на котором размещена MPP SQL Server Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c2408e84e7ff81f54ad00a98f85cd8dce7b04131
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2018
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Новые возможности Analytics Platform System масштабируемого хранилища данных MPP
В разделе новые возможности устройства самые последние обновления для Microsoft® Analytics Platform System (APS). APS является виртуальным устройством масштабируемого локальной, на котором размещена MPP SQL Server Parallel Data Warehouse. 


## <a name="aps-au7"></a>APS AU7
APS2016 является необходимым компонентом для обновления до AU7. Ниже приведены новые возможности для APS AU7.

### <a name="auto-create-and-auto-update-statistics"></a>Автоматическое создание и автоматическое обновление статистики
APS AU7 создает и обновляет статистику автоматически, по умолчанию. Чтобы обновить параметры статистики, администраторы могут использовать новые функции коммутатора пункта меню в [Configuration Manager](appliance-configuration.md#CMTasks). [Переключение функции](appliance-feature-switch.md) управляет auto-create, автоматическое обновление и поведение асинхронного обновления статистики. Можно также обновить параметры статистики с [инструкции ALTER DATABASE (Parallel Data Warehouse)](/sql/t-sql/statements/alter-database-parallel-data-warehouse) инструкции.

### <a name="t-sql"></a>T-SQL
Выберите @var теперь поддерживается. Дополнительные сведения см. в разделе [Выберите локальную переменную] (/ sql/t-sql/language-elements/select-local-variable-transact-sql) 

Указания запросов ХЭШ и ORDER GROUP теперь поддерживаются. Дополнительные сведения см. в разделе [Hints(Transact-SQL) - запроса] (/ sql, t-sql и запросов и подсказки transact-sql запроса)

### <a name="feature-switch"></a>Переключение функции
APS AU7 вводит переключение функции в [Configuration Manager](launch-the-configuration-manager.md). AutoStatsEnabled и DmsProcessStopMessageTimeoutInSeconds являются настраиваемые параметры, которые могут быть изменены администраторами.

### <a name="known-issues"></a>Известные проблемы
С программным обеспечением APS AU7 Приносим упаковки и предоставляя обновление Intel BIOS устраняет «Упреждающее исполнение атаки на стороне канала» (также называемого. Spectre и Meltdown уязвимости). Хотя объединенных в один пакет, обновление BIOS установлен вручную и не является частью APS AU7 программного обеспечения. Корпорация Майкрософт не рекомендует всем клиентам, чтобы установить обновление BIOS. Корпорация Майкрософт измеряется эффект ядра виртуальный адрес затенение (KVAS), ядра страницы таблицы косвенного обращения (KPTI) и косвенных ветвь прогноза по устранению рисков (IBP) на различных рабочих нагрузок SQL в различных средах и найти значительное снижение на некоторых рабочие нагрузки. Мы рекомендуем проверить производительность результат использования обновления BIOS, до их развертывания в рабочей среде. Производительность результат использования этих функций слишком велико для существующего приложения, можно использовать изоляция вашим устройством APS из ненадежного кода, выполняемого ли лучше по устранению рисков для вашего приложения. См. руководство по SQL Server [здесь](https://support.microsoft.com/en-us/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

## <a name="aps-2016"></a>APS 2016
Это новые возможности для APS 2016:

### <a name="sql-server-2016"></a>SQL Server 2016

APS 2016 запускается на последний выпуск SQL Server 2016 и использует по умолчанию уровень совместимости 130.  SQL Server 2016 позволяет поддерживать некоторые новые функции, такие как вторичные индексы для кластеризованных индексов columnstore и Kerberos для PolyBase. 


### <a name="t-sql"></a>T-SQL
APS 2016 поддерживает эти улучшения совместимости T-SQL.  Эти дополнительные языковые элементы упрощают процесс миграции с SQL Server и другим источникам данных. 

- [Параметры сортировки уровня столбцов SQL][] теперь поддерживаются в дополнение к параметры сортировки Windows.
- [Некластеризованные индексы для кластеризованных индексов columnstore][] повысить производительность запросов, которые выполняют поиск конкретного значения в кластеризованном индексе. 
- [ВЫБЕРИТЕ... В][] 
- [sp_spaceused()][] отображает место на диске используется или зарезервировано в таблицу или базу данных.
- [Широкие таблицы][] поддержки является таким же, как SQL Server 2016. Предыдущие ограничение 32K для размера строки больше не существует. 

**Типы данных**

- [VARCHAR(max)][], [NVARCHAR(MAX)][] и [VARBINARY(MAX)][]. Эти типы данных больших ОБЪЕКТОВ имеют максимальный размер, равный 2 ГБ. Для загрузки этих объектов используйте [программа bcp][]. Polybase и dwloader в настоящее время не поддерживают эти типы данных. 
- [SYSNAME][]
- [UNIQUEIDENTIFIER][]
- [NUMERIC][] и типов данных DECIMAL.

**Оконные функции**

- [ROWS или RANGE][] в предложении OVER инструкции SELECT.
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

**Функции безопасности**

- [CHECKSUM()][] и [BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

**Дополнительные функции**

- [ФУНКЦИИ NEWID()][]
- [RAND()][]

### <a name="polybasehadoop-enhancements"></a>Усовершенствования PolyBase/Hadoop

- Совместимость с Hortonworks HDP 2.4 и HDP 2.5
- Поддержка проверки подлинности Kerberos через учетные данные уровня базы данных
- Поддержка учетных данных с большими двоичными объектами хранилища Azure

### <a name="install-and-upgrade-enhancements"></a>Установка и обновление усовершенствования

**Архитектура обновления Enterprise** обновление существующего устройства до APS 2016 устанавливает последнюю версию встроенного по и обновления драйверов, включая исправления безопасности. 

Новым устройством из HPE или DELL содержит все последние обновления, а также:

- Создание процессоров, поддерживаемых (Broadwell)
- Обновление до DDR4 модули памяти DIMM
- Повышенная пропускная способность модуля памяти DIMM

**Интеграция**

- Полное доменное имя (FQDN) поддержка делает можно установить доверие домена к устройству. 
- Чтобы использовать полное доменное имя, необходимо выполнить полное обновление и участия в программе во время обновления. 

**Уменьшение времени простоя** Установка или обновление до APS 2016 выполняется быстрее и требует меньше времени простоя, чем предыдущие выпуски. Чтобы уменьшить время простоя, установки или обновления. 

 - И упрощает применение обновлений WSUS с помощью образа, содержащего все обновления через июня 2016 г.
 - Применяет обновления для системы безопасности с обновлениями драйверов и встроенного по
 - Размещает последние исправления и служебную программу проверки устройством (PAV) на устройстве, так, чтобы они готовы к установке с нет необходимости загружать их.


<!--MSDN references-->
[database compatibility level 130]:/sql/t-sql/statements/alter-database-transact-sql-compatibility-level
[Параметры сортировки уровня столбцов SQL]:/sql/relational-databases/collations/collation-and-unicode-support
[Некластеризованные индексы для кластеризованных индексов columnstore]:/sql/t-sql/statements/create-index-transact-sql
[VARCHAR(MAX)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[NVARCHAR(MAX)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[VARBINARY(MAX)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[ВЫБЕРИТЕ... В]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[Широкие таблицы]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[Программа bcp]:/sql/tools/bcp-utility
[UNIQUEIDENTIFIER]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
[NUMERIC]:/sql/t-sql/data-types/decimal-and-numeric-transact-sql
[ROWS или RANGE]:/sql/t-sql/queries/select-over-clause-transact-sql
[FIRST_VALUE]:/sql/t-sql/functions/first-value-transact-sql
[LAST_VALUE]:/sql/t-sql/functions/last-value-transact-sql
[CUME_DIST]:/sql/t-sql/functions/cume-dist-transact-sql
[PERCENT_RANK]:/sql/t-sql/functions/percent-rank-transact-sql
[CHECKSUM()]:/sql/t-sql/functions/checksum-transact-sql
[BINARY_CHECKSUM()]:/sql/t-sql/functions/binary-checksum-transact-sql
[HAS_PERMS_BY_NAME()]:/sql/t-sql/functions/has-perms-by-name-transact-sql
[ФУНКЦИИ NEWID()]:/sql/t-sql/functions/newid-transact-sql
[RAND()]:/sql/t-sql/functions/rand-transact-sql


  

  


