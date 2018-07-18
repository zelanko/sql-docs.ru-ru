---
title: Новые возможности в Analytics Platform System — хранилище данных горизонтального масштабирования
description: См. в разделе, новые возможности в Microsoft® платформенной системы аналитики, горизонтальное масштабирование локальное устройство, на котором размещена MPP SQL Server Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b1eee6b3ca692c7935b061696b37842cda0f8326
ms.sourcegitcommit: 1d81c645dd4fb2f0a6f090711719528995a34583
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2018
ms.locfileid: "37137893"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Новые возможности в Analytics Platform System, хранилища данных MPP горизонтального масштабирования
См. в разделе, новые возможности в последние обновления устройства для Microsoft® Analytics Platform System (APS). APS является горизонтальное масштабирование локальное устройство, на котором размещена MPP SQL Server Parallel Data Warehouse. 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"

## <a name="aps-au7"></a>APS AU7
APS 2016 является необходимым условием для обновления до AU7. Ниже приведены возможности APS AU7.

### <a name="auto-create-and-auto-update-statistics"></a>Автоматическое создание и автоматическое обновление статистики
APS AU7 создает и обновляет статистику автоматически, по умолчанию. Чтобы обновить параметры статистики, администраторы могут использовать новые функции коммутатора пункта меню в [Configuration Manager](appliance-configuration.md#CMTasks). [Переключатель](appliance-feature-switch.md) управляет auto-create, автоматическое обновление и поведение асинхронного обновления статистики. Вы также можете обновить параметры статистики с [ALTER DATABASE (Parallel Data Warehouse)](/sql/t-sql/statements/alter-database-parallel-data-warehouse) инструкции.

### <a name="t-sql"></a>T-SQL
Выберите @var теперь поддерживается. Дополнительные сведения см. в разделе [выберите локальная переменная] (/ sql/t-sql/language-elements/select-local-variable-transact-sql) 

Указания запросов HASH и ORDER GROUP теперь поддерживаются. Дополнительные сведения см. в разделе [Hints(Transact-SQL) - запрос] (/ sql/t-sql/запросов/подсказки transact-sql запроса)

### <a name="feature-switch"></a>Функция Switch
APS AU7 вводит переключателя функций в [Configuration Manager](launch-the-configuration-manager.md). AutoStatsEnabled и DmsProcessStopMessageTimeoutInSeconds стали настраиваемых параметров, которые могут быть изменены администраторами.

### <a name="known-issues"></a>Известные проблемы
С программным обеспечением APS AU7, обновление Intel BIOS предоставляется исправления, которые описываются как проблема *атаки упреждающего исполнения на стороне канала*. Цель атаки — воспользоваться, называемых *уязвимости Spectre и Meltdown*. Несмотря на то, что упаковываются вместе с APS, установлено ли обновление BIOS вручную, а не как часть установки программного обеспечения APS AU7.

Корпорация Майкрософт рекомендует всем клиентам установить обновление BIOS. Microsoft замеряли последствия ядра виртуальный адрес затенение (KVAS), службы ядра страницы таблицы косвенного обращения (KPTI) и косвенных ветви прогноза по устранению рисков (IBP) на различных рабочих нагрузок SQL в различных средах. Измерения найти значительное снижение на некоторых рабочих нагрузок. На основе результатов, рекомендуется протестировать производительность эффект включения обновления BIOS, перед их развертыванием в рабочей среде. См. в руководстве по SQL Server [здесь](https://support.microsoft.com/en-us/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"

## <a name="aps-2016"></a>APS 2016
В этом разделе описываются новые функции для AU6 APS 2016.

### <a name="sql-server-2016"></a>SQL Server 2016

APS AU6 запускается на последний выпуск SQL Server 2016 и использует по умолчанию уровне совместимости 130. SQL Server 2016 включает поддержку новых функций, таких как:

- Вторичные индексы для кластеризованных индексов columnstore.
- Kerberos для PolyBase.

### <a name="t-sql"></a>T-SQL
APS AU6 поддерживает эти улучшения совместимости T-SQL.  Эти дополнительные языковые элементы упрощают перенос из SQL Server и другим источникам данных. 

- [Параметры сортировки уровня столбцов SQL][] теперь поддерживаются, а также параметры сортировки Windows.
- [Некластеризованные индексы в кластеризованных индексах columnstore][] повышения производительности запросов, которые производят поиск определенных значений в кластеризованный индекс columnstore. 
- [ВЫБЕРИТЕ... В][] 
- [sp_spaceused()][] отображает пространство на диске используется или зарезервировано в таблицу или базу данных.
- [Широкие таблицы][] поддержки является таким же, как SQL Server 2016. Предыдущее ограничение в 32 КБ для размера строки больше не существует. 

**Типы данных**

- [VARCHAR(max)][], [NVARCHAR(MAX)][] и [VARBINARY(MAX)][]. Эти типы данных больших ОБЪЕКТОВ имеют максимальный размер 2 ГБ. Для загрузки этих объектов используйте [Программа bcp][]. Polybase и dwloader в настоящее время не поддерживают эти типы данных. 
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

### <a name="polybasehadoop-enhancements"></a>Улучшения PolyBase/Hadoop

- Совместимость с Hortonworks HDP 2.4 и HDP 2.5
- Поддержка проверки подлинности Kerberos с помощью учетных данных области базы данных
- Поддержка учетных данных с большими двоичными объектами хранилища Azure

### <a name="install-and-upgrade-enhancements"></a>Установка и обновление усовершенствования

**Архитектура обновления Enterprise** обновления существующие устройства до APS AU6 устанавливает последние версии встроенного по и обновления драйверов, в том числе исправления безопасности. 

Новое устройство с HPE или DELL включает в себя все последние обновления, а также:

- Поколения процессоров, поддерживаемых (Broadwell)
- Обновление до DDR4 DIMM
- Повышение производительности модуля памяти DIMM

**Интеграция**

- Полное доменное имя (FQDN) поддержка делает можно установить доверие домена к устройству. 
- Чтобы использовать полное доменное имя, необходимо выполнить полное обновление и согласиться во время обновления. 

**Уменьшение времени простоя** Установка или обновление до APS AU6 выполняется быстрее и требует меньше времени простоя, чем предыдущие выпуски. Чтобы сократить время простоя, установки или обновления: 

 - Оптимизирует применение обновления WSUS с помощью образа, содержащего все обновления через июня 2016 г.
 - Применяет обновления безопасности с обновлениями драйвера и встроенного по
 - Помещает последних исправлений и служебная программа проверки устройства (ПАВ) на устройстве, так, чтобы они готовы к установке без необходимости загружать их.

::: moniker-end

<!--
Link references to other articles in this same GitHub repo.

The link format that starts with '/sql/what-ever/my-artlcle' is not appropriate for common links within the same repo (as most of these link are).  The first couple links have been edited to show the proper syntax, but all other links in this article need to be similarly edited.
The proper formats have at least two big advantages.  One big advantage is that the proper formats enable the OPS Build system to detect broken links at Pull Request build time, instead of only later during run time.
-->
[database compatibility level 130]: ../t-sql/statements/alter-database-transact-sql-compatibility-level.md
[Параметры сортировки уровня столбцов SQL]: ~/relational-databases/collations/collation-and-unicode-support.md

[Некластеризованные индексы в кластеризованных индексах columnstore]:/sql/t-sql/statements/create-index-transact-sql
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


  

  


