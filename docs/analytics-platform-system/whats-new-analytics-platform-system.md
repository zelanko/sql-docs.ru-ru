---
title: Новые возможности в Analytics Platform System — хранилище данных горизонтального масштабирования
description: См. в разделе, новые возможности в Microsoft Analytics Platform System, горизонтальное масштабирование локальное устройство, на котором размещена MPP SQL Server Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3731f60047e22da7209b6c131ab93b28a20a99c2
ms.sourcegitcommit: c4870cb5bebf9556cdb4d8b35ffcca265fb07862
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652593"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Новые возможности в Analytics Platform System, хранилища данных MPP горизонтального масштабирования
См. в разделе, новые возможности в последние обновления устройства для Microsoft Analytics Platform System (APS). APS является горизонтальное масштабирование локальное устройство, на котором размещена MPP SQL Server Parallel Data Warehouse. 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"
<a name="h2-aps-cu7.3"></a>
## <a name="aps-cu73"></a>APS CU7.3
Дата выпуска - декабря 2018 г.

### <a name="common-subexpression-elimination"></a>Исключение общих частей выражений
APS CU7.3 повышает производительность запросов с исключение общей части выражения в оптимизатор запросов SQL. Улучшение улучшает запросы двумя способами. Первый преимущество заключается в возможности определения и устранения такие выражения помогают сократить время компиляции SQL. Вторым и более важным преимущество в том, что операции перемещения данных для этих избыточных частей выражения исключаются таким образом времени выполнения для запросов становится быстрее. Подробное описание этой функции можно найти [здесь](common-sub-expression-elimination.md).

### <a name="aps-informatica-connector-for-informatica-1020-published"></a>Соединитель APS Informatica для Informatica 10.2.0 публикации
Корпорация Майкрософт выпустила новую версию соединителей Informatica ТД, который работает с Informatica версии 10.2.0 и 10.2.0 исправление 1. Новые соединители можно загрузить из [сайт загрузки](https://www.microsoft.com/download/details.aspx?id=57472).

#### <a name="supported-versions"></a>Поддерживаемые версии

| Версия APS | Informatica PowerCenter | Драйвер |
|:---|:---|:---|
| APS 2016 | 9.6.1 | Собственный клиент SQL Server 11.x |
| APS 2016 и более поздние версии | 10.2.0, 10.2.0 исправление 1 | Собственный клиент SQL Server 11.x |

<a name="h2-aps-cu7.2"></a>
## <a name="aps-cu72"></a>APS CU7.2
Дата выпуска - октября 2018 г.

### <a name="support-for-tls-12"></a>Поддержка TLS 1.2
APS CU7.2 поддерживает TLS 1.2. Клиентский компьютер APS и APS внутриузловой теперь можно задать для обмена данными только через TLS 1.2. Такие средства, как SSDT, служб SSIS и установлены на клиентских компьютерах, которые предназначены для обмена данными только через TLS 1.2 Dwloader теперь можно подключиться к ТД, с помощью TLS 1.2. По умолчанию APS будет поддерживать все версии TLS (1.0, 1.1 и 1.2) для обеспечения обратной совместимости. Если вы хотите задать устройства APS строго использование TLS 1.2, это можно сделать, изменив параметры реестра. 

Дополнительные сведения см. в разделе [Настройка TLS 1.2 на APS](configure-tls12-aps.md).

### <a name="hadoop-encryption-zone-support-for-polybase"></a>Поддерживает зоны шифрования Hadoop для PolyBase
PolyBase теперь может обмениваться данными с зоны шифрования Hadoop. См. в разделе APS изменения конфигурации, которые требуются в [настроить безопасность Hadoop](polybase-configure-hadoop-security.md#encryptionzone).

### <a name="insert-select-maxdop-options"></a>Параметры maxdop INSERT-Select
Мы добавили [переключатель](appliance-feature-switch.md) , позволяет выбрать параметры maxdop больше 1 для операций insert-select. Теперь вы можете задать параметр maxdop 0, 1, 2 или 4. Значение по умолчанию равно 1.

> [!IMPORTANT]  
> Увеличение maxdop может иногда привести медленнее операций или ошибки взаимоблокировок. Если это происходит, измените параметр обратно на maxdop 1 и повторите операцию.

### <a name="columnstore-index-health-dmv"></a>Работоспособности индексов ColumnStore динамическое административное Представление
Можно просмотреть, используя сведения о работоспособности columnstore index **dm_pdw_nodes_db_column_store_row_group_physical_stats** динамического административного представления. Используйте следующее представление для определения фрагментации и решить, когда для перестроения или реорганизации индекса columnstore.

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

### <a name="polybase-date-range-increase-for-orc-and-parquet-files"></a>PolyBase увеличение диапазон дат для файлов ORC и Parquet
Чтение, Импорт и экспорт типов данных даты, с помощью PolyBase, теперь поддерживает даты до 1970-01-01 и после 2038-01-20 для типов файлов ORC и Parquet.

### <a name="ssis-destination-adapter-for-sql-server-2017-as-target"></a>Адаптер загрузки данных служб SSIS для SQL Server 2017 в качестве целевого объекта
Новый адаптер назначения APS служб SSIS, которая поддерживает SQL Server 2017, как цель развертывания можно загрузить из [сайт загрузки](https://www.microsoft.com/download/details.aspx?id=57472).

<a name="h2-aps-cu7.1"></a>
## <a name="aps-cu71"></a>APS CU7.1
Дата выпуска - июля 2018 г.

### <a name="dbcc-commands-do-not-consume-concurrency-slots-behavior-change"></a>Команды DBCC не используют слоты выдачи (изменение поведения)
APS поддерживает подмножество T-SQL, [команды DBCC](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-transact-sql) например [DBCC DROPCLEANBUFFERS](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql). Ранее, будет использовать эти команды [слот выдачи](https://docs.microsoft.com/sql/analytics-platform-system/workload-management?view=aps-pdw-2016-au7#concurrency-slots) уменьшению числа пользователь загружает и запросы, которые могут выполняться. `DBCC` Команды теперь выполняются в локальной очереди, которое использует пользователь слот выдачи, повышая общую производительность выполнения запросов.

### <a name="replaces-some-metadata-calls-with-catalog-objects"></a>Заменяет некоторые вызовы метаданных объектов каталога
Использование объектов каталога для вызовов метаданных вместо использования SMO показали повышение производительности в APS. Начиная с CU7.1, некоторые из этих вызовов метаданных теперь используют объекты каталога по умолчанию. Это поведение можно отключить, [переключатель](appliance-feature-switch.md) Если клиенты, использующие запросы метаданных столкнетесь с проблемами.

### <a name="bug-fixes"></a>Исправления ошибок
Мы обновили для SQL Server 2016 с пакетом обновления 2 CU2 с APS CU7.1. Обновление устраняет некоторые проблемы, описанные ниже.

| Заголовок | Описание |
|:---|:---|
| **Взаимоблокировки задачи переноса кортежей кортежа** |Обновление устраняет вероятность, что долгосрочные взаимоблокировки в распределенной транзакции и кортежа задачи переноса кортежей фоновый поток. После установки CU7.1, клиенты, которые работают TF634 остановить кортежей в качестве параметра запуска SQL Server или глобальный флаг трассировки можно безопасно удалить его. | 
| **Определенные lag или lead запрос завершится с ошибкой** |Некоторые запросы в таблицах CCI с вложенной lag или lead функции, которые бы ошибка теперь исправлена этого обновления. | 


<a name="h2-aps-au7"></a>
## <a name="aps-au7"></a>APS AU7
Дата выпуска - май 2018 г.

APS 2016 является необходимым условием для обновления до AU7. Ниже приведены новые возможности в APS AU7.

### <a name="auto-create-and-auto-update-statistics"></a>Автоматическое создание и автоматическое обновление статистики
APS AU7 создает и обновляет статистику автоматически, по умолчанию. Чтобы обновить параметры статистики, администраторы могут использовать новые функции коммутатора пункта меню в [Configuration Manager](appliance-configuration.md#CMTasks). [Переключатель](appliance-feature-switch.md) управляет auto-create, автоматическое обновление и поведение асинхронного обновления статистики. Вы также можете обновить параметры статистики с [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) инструкции.

### <a name="t-sql"></a>T-SQL
Выберите @var теперь поддерживается. Дополнительные сведения см. в разделе [выберите локальной переменной](/sql/t-sql/language-elements/select-local-variable-transact-sql) 

Указания запросов HASH и ORDER GROUP теперь поддерживаются. Дополнительные сведения см. в разделе [Hints(Transact-SQL) - запросов ](/sql/t-sql/queries/hints-transact-sql-query)

### <a name="feature-switch"></a>Функция Switch
APS AU7 вводит переключателя функций в [Configuration Manager](launch-the-configuration-manager.md). AutoStatsEnabled и DmsProcessStopMessageTimeoutInSeconds стали настраиваемых параметров, которые могут быть изменены администраторами.

### <a name="known-issues"></a>Известные проблемы
С программным обеспечением APS AU7, обновление Intel BIOS предоставляется исправления, которые описываются как проблема *атаки упреждающего исполнения на стороне канала*. Цель атаки — воспользоваться, называемых *уязвимости Spectre и Meltdown*. Несмотря на то, что упаковываются вместе с APS, установлено ли обновление BIOS вручную, а не как часть установки программного обеспечения APS AU7.

Корпорация Майкрософт рекомендует всем клиентам установить обновление BIOS. Microsoft замеряли последствия ядра виртуальный адрес затенение (KVAS), службы ядра страницы таблицы косвенного обращения (KPTI) и косвенных ветви прогноза по устранению рисков (IBP) на различных рабочих нагрузок SQL в различных средах. Измерения найти значительное снижение на некоторых рабочих нагрузок. На основе результатов, рекомендуется протестировать производительность эффект включения обновления BIOS, перед их развертыванием в рабочей среде. См. в руководстве по SQL Server [здесь](https://support.microsoft.com/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"
<a name="h2-aps-au6"></a>
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

- [VARCHAR(max)][], [NVARCHAR(MAX)][] и [VARBINARY(MAX)][]. Эти типы данных больших ОБЪЕКТОВ имеют максимальный размер 2 ГБ. Для загрузки этих объектов используйте [Программа bcp][]. PolyBase и dwloader в настоящее время не поддерживают эти типы данных. 
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


  

  


