---
title: Новые возможности
description: Узнайте, что нового в microsoft Analytics Platform System, масштабном емкостном приборе, в котором размещается хранилище параллельных данных сервера MPP S'L Server.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: faf3bd1f487fb5c850759fdde3ddecd32bdd3b1f
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625539"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Что нового в системе аналитической платформы, масштабном хранилище данных MPP
Узнайте, что нового в последних обновлениях приборов для системы платформы Microsoft Analytics (APS). APS — это масштабное использование прибора, в котором размещается параллельный склад параллельных данных MPP S'L Server. 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"
<a name="h2-aps-cu7.6"></a>
## <a name="aps-cu76"></a>APS CU7.6
Дата выпуска - апрель 2020 г.

### <a name="rename-column"></a>Переименование столбца
После обновления до CU7.6 клиенты смогут переименовать столбец созданной пользователем таблицы. Смотрите [RENAME (Трансакт-СЗЛ)](https://docs.microsoft.com/sql/t-sql/statements/rename-transact-sql) для синтаксиса, примеров, ограничений и дополнительной информации.

### <a name="alter-view"></a>Изменить представление
Теперь клиенты смогут изменять представления. Для получения [дополнительной информации см.](https://docs.microsoft.com/sql/t-sql/statements/alter-view-transact-sql)

<a name="h2-aps-cu7.5"></a>
## <a name="aps-cu75"></a>APS CU7.5
Дата выпуска - сентябрь 2019 г.

### <a name="alter-external-data-source"></a>Alter Внешний источник данных
Клиенты смогут изменять определение внешних источников данных с обновлением CU7.5. Клиенты с высокой доступностью узла имен Hadoop теперь могут изменять источник данных, чтобы изменить аргументы, когда происходит сбой. Для APS можно изменить только LOCATION, RESOURCE_MANAGER_LOCATION и CREDENTIAL. Для получения дополнительной [информации отсм.](https://docs.microsoft.com/sql/t-sql/statements/alter-external-data-source-transact-sql?view=sql-server-2017)

### <a name="cdh-515-and-516-support-with-polybase"></a>Поддержка CDH 5.15 и 5.16 с PolyBase
PolyBase на APS с обновлением CU7.5 теперь поддерживает CDH 5.15 и 5.16 версии дистрибутива Hadoop от Cloudera. Используйте вариант 6 для версий CDH 5.x. 

### <a name="try_convert-and-try_cast-support"></a>поддержка Try_Convert и Try_Cast
CU7.5 APS теперь поддерживает [TRY_CAST](https://docs.microsoft.com/sql/t-sql/functions/try-cast-transact-sql?view=sql-server-2017) и [TRY_CONVERT](https://docs.microsoft.com/sql/t-sql/functions/try-convert-transact-sql?view=sql-server-2017) функции tsql. Обе эти функции возвращают значение, преобразованное в указанный тип данных, если преобразование успешно; в противном случае, возвращаетнул нулевую.

<a name="h2-aps-cu7.4"></a>
## <a name="aps-cu74"></a>APS CU7.4
Дата выпуска - май 2019 г.

### <a name="loading-large-rows-with-dwloader"></a>Загрузка больших рядов с dwloader
Начиная с APS CU7.4, клиенты смогут использовать новый dwloader для загрузки строк в таблицы, которые больше, чем 32 КБ (32 768 байтов). Новый dwloader поддерживает переключатель -l, который принимает значение integer между 32768 и 33554432 (в байтах) для загрузки строк больше, чем 32 КБ. Только использовать эту опцию при загрузке больших строк (больше, чем 32 КБ), как этот переключатель будет выделять больше памяти на клиенте и сервере и может замедлить нагрузки. Вы можете скачать новый dwloader с [сайта загрузки](https://www.microsoft.com/download/details.aspx?id=57472).  

### <a name="hdp-30-and-31-support-with-polybase"></a>Поддержка HDP 3.0 и 3.1 с PolyBase
PolyBase на APS теперь поддерживает HDP 3.0 и 3.1 с этим обновлением. Используйте вариант 7 для версий HDP 3.x. Для получения дополнительной информации смотрите страницу [подключения PolyBase.](https://docs.microsoft.com/sql/database-engine/configure-windows/polybase-connectivity-configuration-transact-sql)

### <a name="utf16-file-support-with-polybase"></a>Поддержка файлов UTF16 с PolyBase
PolyBase теперь поддерживает чтение делимитированных текстовых файлов, которые находятся в кодировании UTF16 (LE). Просчитайте [создать внешний формат файла](https://docs.microsoft.com/sql/t-sql/statements/create-external-file-format-transact-sql) для деталей настройки. 

<a name="h2-aps-cu7.3"></a>
## <a name="aps-cu73"></a>APS CU7.3
Дата выпуска - декабрь 2018 г.

### <a name="common-subexpression-elimination"></a>Исключение общих частей выражений
APS CU7.3 улучшает производительность запроса с помощью общего устранения субэкспрессии в оптимизаторе запросов S'L. Улучшение улучшает запросы двумя способами. Первое преимущество заключается в том, что способность выявлять и устранять такие выражения помогает сократить время компиляции S'L. Вторым и более важным преимуществом являются операции движения данных для этих избыточных субвыражений, таким образом, время выполнения запросов становится более быстрым. Подробное объяснение этой функции можно найти [здесь](common-sub-expression-elimination.md).

### <a name="aps-informatica-connector-for-informatica-1020-published"></a>Опубликован разъем APS Informatica для Informatica 10.2.0
Мы выпустили новую версию разъемов Informatica для APS, которая работает с версией Informatica 10.2.0 и 10.2.0 Hotfix 1. Новые разъемы можно скачать с [сайта загрузки](https://www.microsoft.com/download/details.aspx?id=57472).

#### <a name="supported-versions"></a>Поддерживаемые версии

| Версия APS | Informatica PowerCenter | Драйвер |
|:---|:---|:---|
| APS 2016 | 9.6.1 | Родной клиент сервера 11.x |
| APS 2016 и более поздние | 10.2.0, 10.2.0 Hotfix 1 | Родной клиент сервера 11.x |

<a name="h2-aps-cu7.2"></a>
## <a name="aps-cu72"></a>APS CU7.2
Дата выпуска - октябрь 2018 г.

### <a name="support-for-tls-12"></a>Поддержка TLS 1.2
APS CU7.2 поддерживает TLS 1.2. Клиентская машина для apS и APS внутриузловой связи теперь может быть установлена для связи только по TLS1.2. Такие инструменты, как SSDT, SSIS и Dwloader, установленные на клиентских машинах, которые настроены на связь только по TLS 1.2, теперь могут подключаться к APS с помощью TLS 1.2. По умолчанию APS будет поддерживать все версии TLS (1.0, 1.1 и 1.2) для обратной совместимости. Если вы хотите настроить прибор APS для строгого использования TLS 1.2, вы можете сделать это, изменив настройки реестра. 

Для получения дополнительной [информации](configure-tls12-aps.md)см.

### <a name="hadoop-encryption-zone-support-for-polybase"></a>Поддержка зоны шифрования Hadoop для PolyBase
Теперь PolyBase может общаться с зонами шифрования Hadoop. См. изменения конфигурации APS, необходимые для [настройки безопасности Hadoop.](polybase-configure-hadoop-security.md#encryptionzone)

### <a name="insert-select-maxdop-options"></a>Варианты максимального максдопа Вставить-Выберите
Мы добавили [переключатель функции,](appliance-feature-switch.md) который позволяет выбрать параметры maxdop больше, чем 1 для вставки выбора операций. Теперь можно установить настройку maxdop до 0, 1, 2 или 4. Значение по умолчанию — 1.

> [!IMPORTANT]  
> Увеличение maxdop иногда может привести к более медленным операциям или ошибкам тупика. Если это происходит, измените настройку обратно на maxdop 1 и повторно попробуйте операцию.

### <a name="columnstore-index-health-dmv"></a>Индекс здоровья ColumnStore DMV
Вы можете просмотреть информацию о здоровье индекса **columnstore,** используя dm_pdw_nodes_db_column_store_row_group_physical_stats dmv. Используйте следующее представление для определения фрагментации и принятия решения о том, когда перестроить или реорганизовать индекс столбцов.

```sql
create view dbo.vCS_rg_physical_stats
as 
with cte
as
(
select   tb.[name]                    AS [logical_table_name]
,        rg.[row_group_id]            AS [row_group_id]
,        rg.[state]                   AS [state]
,        rg.[state_desc]              AS [state_desc]
,        rg.[total_rows]              AS [total_rows]
,        rg.[trim_reason_desc]        AS trim_reason_desc
,        mp.[physical_name]           AS physical_name
FROM    sys.[schemas] sm
JOIN    sys.[tables] tb               ON  sm.[schema_id]          = tb.[schema_id]                             
JOIN    sys.[pdw_table_mappings] mp   ON  tb.[object_id]          = mp.[object_id]
JOIN    sys.[pdw_nodes_tables] nt     ON  nt.[name]               = mp.[physical_name]
JOIN    sys.[dm_pdw_nodes_db_column_store_row_group_physical_stats] rg      ON  rg.[object_id]     = nt.[object_id]
                                                                            AND rg.[pdw_node_id]   = nt.[pdw_node_id]
                                        AND rg.[pdw_node_id]    = nt.[pdw_node_id]                                          
)
select *
from cte;
```

### <a name="polybase-date-range-increase-for-orc-and-parquet-files"></a>Расширение диапазона дат PolyBase для файлов ORC и Parquet
Чтение, импорт и экспорт типов дат с использованием PolyBase теперь поддерживает даты до 1970-01-01 и после 2038-01-20 для типов файлов ORC и Parquet.

### <a name="ssis-destination-adapter-for-sql-server-2017-as-target"></a>Адаптер назначения SSIS для S'L Server 2017 в качестве целевого
Новый адаптер назначения APS SSIS, который поддерживает S'L Server 2017 в качестве цели развертывания, может быть загружен с [сайта загрузки.](https://www.microsoft.com/download/details.aspx?id=57472)

<a name="h2-aps-cu7.1"></a>
## <a name="aps-cu71"></a>APS CU7.1
Дата выпуска - Июль 2018

### <a name="dbcc-commands-do-not-consume-concurrency-slots-behavior-change"></a>Команды DBCC не потребляют слоты для параллелизма (изменение поведения)
APS поддерживает подмножество команд T-S'L [DBCC,](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-transact-sql) таких как [DBCC DROPCLEANBUFFERS.](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql) Раньше эти команды потребляли [слот выдачи](https://docs.microsoft.com/sql/analytics-platform-system/workload-management?view=aps-pdw-2016-au7#concurrency-slots), уменьшая количество пользовательских нагрузок и запросов, которые можно было выполнить. Команды `DBCC` теперь работают в локальной очереди, которая не потребляет слот для параллелизма пользователя, улучшая общую производительность выполнения запроса.

### <a name="replaces-some-metadata-calls-with-catalog-objects"></a>Заменяет некоторые вызовы метаданных на объекты каталога
Использование объектов каталога для вызовов метаданных вместо использования SMO показало улучшение производительности apS. Начиная с CU7.1, некоторые из этих вызовов метаданных теперь используют объекты каталога по умолчанию. Это поведение может быть отключено [при переключении функций,](appliance-feature-switch.md) если клиенты, использующие запросы метаданных, столкнулись с какими-либо проблемами.

### <a name="bug-fixes"></a>Исправления ошибок
Мы переоделись в s'L Server 2016 SP2 CU2 с APS CU7.1. Обновление фиксирует некоторые проблемы, описанные ниже.

| Заголовок | Описание |
|:---|:---|
| **Потенциальный тупик туплята** |Обновление фиксирует длительную возможность взаимоблокировки в распределенной транзакции и туплоги фоновый поток. После установки CU7.1, клиенты, которые использовали TF634, чтобы остановить тупл-ковер в качестве параметра запуска сервера s'L Server или глобального флага трассировки, могут безопасно удалить его. | 
| **Неудается определенному запросу запаздывания/свинца** |Некоторые запросы в таблицах CCI с вложенными функциями запаздывания/свинца, которые будут исправлены, теперь исправлены с помощью этого обновления. | 


<a name="h2-aps-au7"></a>
## <a name="aps-au7"></a>APS AU7
Дата выпуска - май 2018 г.

APS 2016 является необходимым условием для обновления до AU7. Ниже приведены новые функции в APS AU7:

### <a name="auto-create-and-auto-update-statistics"></a>Статистика автоматического создания и автоматического обновления
APS AU7 создает и обновляет статистику автоматически, по умолчанию. Для обновления настроек статистики администраторы могут использовать новый элемент меню коммутатора функций в [диспетчере конфигурации.](appliance-configuration.md#CMTasks) Переключатель [функции](appliance-feature-switch.md) управляет автоматическим созданием, автоматическим обновлением и асинхронным поведением статистики. Вы также можете обновить настройки статистики с помощью оператора [ALTER DATABASE (Параллельный хранилище данных).](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)

### <a name="t-sql"></a>T-SQL
Выбор @var теперь поддерживается. Для получения дополнительной информации [см.](/sql/t-sql/language-elements/select-local-variable-transact-sql) 

Подсказки запроса HASH и ORDER GROUP теперь поддерживаются. Для получения дополнительной [информации см. Подсказки (Трансакт-СЗЛ) - Запрос](/sql/t-sql/queries/hints-transact-sql-query)

### <a name="feature-switch"></a>Переключатель функций
APS AU7 вводит переключатель функций в [настройке manager.](launch-the-configuration-manager.md) AutoStatsEnabled и DmsProcessStopMessageTimeoutInSeconds теперь настраиваемые варианты, которые могут быть изменены администраторами.

### <a name="known-issues"></a>Известные проблемы
С программным обеспечением APS AU7 предоставляется обновление Intel BIOS, которое исправляет проблему, описанную как *спекулятивные атаки бокового канала выполнения.* Атаки направлены на использование так *называемых уязвимостей Spectre и Meltdown.* Несмотря на то, что обновление BIOS упаковано вместе с APS, устанавливается вручную, а не как часть установки программного обеспечения APS AU7.

Корпорация Майкрософт рекомендует всем клиентам установить обновленную BIOS. Корпорация Майкрософт измерила влияние виртуального адреса Ядра (KVAS), направления таблицы ядра (KPTI) и косвенного смягчения прогноза филиала (IBP) на различные рабочие нагрузки S'L в различных средах. Измерения выявили значительное ухудшение на некоторых рабочих нагрузках. На основе полученных результатов рекомендуется проверить эффект производительности, позволяющий обновлять BIOS перед развертыванием в производственной среде. См. Руководство сервера S'L [здесь](https://support.microsoft.com/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"
<a name="h2-aps-au6"></a>
## <a name="aps-2016"></a>APS 2016
В этом разделе описаны новые функции для APS 2016-AU6.

### <a name="sql-server-2016"></a>SQL Server 2016

APS AU6 работает на последнем выпуске S'L Server 2016 и использует уровень совместимости базы данных по умолчанию 130. S'L Server 2016 обеспечивает поддержку новых функций, таких как:

- Вторичные индексы для кластерных индексов столбцов.
- Керберос для PolyBase.

### <a name="t-sql"></a>T-SQL
APS AU6 поддерживает эти улучшения совместимости T-S'SL.  Эти дополнительные языковые элементы упрощают миграцию из сервера S'L и других источников данных. 

- В дополнение к коллажам Windows, в дополнение к коллажам Windows, в настоящее время поддерживается [коллажа на уровне столбцов.][]
- [Некластерные индексы на кластерных индексах столбцов][] улучшают производительность запросов, которые ищут определенные значения в кластерном индексе столбцов. 
- [SELECT...INTO;][] 
- [sp_spaceused ()][] отображает дисковое пространство, используемое или зарезервированное в таблице или базе данных.
- [Широкая][] поддержка таблиц такая же, как и S'L Server 2016. Предыдущий лимит 32 K для размера строки больше не существует. 

**Типы данных**

- [ВАРЧАР (MAX)][], [NVARCHAR (MAX)][] и [VARBINARY (MAX)][]. Эти типы LOB данных имеют максимальный размер 2 ГБ. Для загрузки этих объектов используйте [bcp Utility.][] PolyBase и dwloader в настоящее время не поддерживают эти типы данных. 
- [SYSNAME][]
- [Uniqueidentifier][]
- Типы данных [NUMERIC][] и DECIMAL.

**Оконные функции**

- [ROWS или RANGE][] в пункте OVER заявления SELECT.
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

**Функции безопасности**

- [ЧЕКСУМ ()][] и [BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

**Дополнительные функции**

- [НЬЮИД()][]
- [RAND()][]

### <a name="polybasehadoop-enhancements"></a>Улучшения PolyBase/Hadoop

- Совместимость с Hortonworks HDP 2.4 и HDP 2.5
- Поддержка Kerberos с помощью учетных данных с базой данных
- Поддержка учетных данных с Azure Storage Blobs

### <a name="install-and-upgrade-enhancements"></a>Установка и обновление усовершенствований

**Обновления архитектуры предприятия** Обновление существующего прибора до APS AU6 устанавливает новейшие обновления прошивки и драйверов, которые включают исправления безопасности. 

Новый прибор от HPE или DELL включает в себя все последние обновления плюс:

- Поддержка процессоров последнего поколения (Broadwell)
- Обновление до DDR4 DIMMs
- Улучшенная пропускная вышивка DIMM

**Интеграция**

- Полностью квалифицированная поддержка доменного имени (ФЗДН) позволяет настроить домен доверия к прибору. 
- Для использования F-DN необходимо сделать полное обновление и отказаться в ходе обновления. 

**Сокращение простоев** Установка или обновление до APS AU6 происходит быстрее и требует меньше простоев, чем предыдущие релизы. Чтобы сократить время простоя, установите или модернизируйте: 

 - Оптимизация применения обновлений WSUS с помощью изображения, содержащего все обновления до июня 2016 года
 - Применяет обновления безопасности с драйвером и обновлениями прошивки
 - Размещает последние hotfixes и утилиту проверки прибора (PAV) на вашем приборе, чтобы они были готовы к установке без необходимости их загрузки.

::: moniker-end

<!--
Link references to other articles in this same GitHub repo.

The link format that starts with '/sql/what-ever/my-artlcle' is not appropriate for common links within the same repo (as most of these link are).  The first couple links have been edited to show the proper syntax, but all other links in this article need to be similarly edited.
The proper formats have at least two big advantages.  One big advantage is that the proper formats enable the OPS Build system to detect broken links at Pull Request build time, instead of only later during run time.
-->
[database compatibility level 130]: ../t-sql/statements/alter-database-transact-sql-compatibility-level.md
[Коллации на уровне колонки S'L]: ~/relational-databases/collations/collation-and-unicode-support.md

[Некластерные индексы на кластерных индексах столбцов]:/sql/t-sql/statements/create-index-transact-sql
[ВАРЧАР (МАКС)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[НВАРЧАР (MAX)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[ВАРБИНАР (МАКС)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[SELECT...INTO;]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[Широкие таблицы]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[bcp Утилита]:/sql/tools/bcp-utility
[Uniqueidentifier]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
[NUMERIC]:/sql/t-sql/data-types/decimal-and-numeric-transact-sql
[ROWS или RANGE]:/sql/t-sql/queries/select-over-clause-transact-sql
[FIRST_VALUE]:/sql/t-sql/functions/first-value-transact-sql
[LAST_VALUE]:/sql/t-sql/functions/last-value-transact-sql
[CUME_DIST]:/sql/t-sql/functions/cume-dist-transact-sql
[PERCENT_RANK]:/sql/t-sql/functions/percent-rank-transact-sql
[ЧЕКСУМ()]:/sql/t-sql/functions/checksum-transact-sql
[BINARY_CHECKSUM()]:/sql/t-sql/functions/binary-checksum-transact-sql
[HAS_PERMS_BY_NAME()]:/sql/t-sql/functions/has-perms-by-name-transact-sql
[НЬЮИД()]:/sql/t-sql/functions/newid-transact-sql
[RAND()]:/sql/t-sql/functions/rand-transact-sql


  

  


