---
title: "Обновлено — документы по реляционным базам данных | Документация Майкрософт"
description: "Отображение фрагментов обновленного содержимого для последних изменений в документации по реляционным базам данных."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.openlocfilehash: 1fbc7affa833eb34b6e13e28b229d47ac0b05a5c
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Новые и недавно обновленные статьи — документы по реляционным базам данных



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **28.09.2017**&nbsp;–&nbsp;**02.12.2017**
- *Предметная область:* &nbsp; **Реляционные базы данных**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Использование профилировщика XEvent для SSMS](extended-events/use-the-ssms-xe-profiler.md)
2. [Мастер импорта неструктурированных файлов в SQL](import-export/import-flat-file-wizard.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [База данных tempdb](#TitleNum_1)
2. [Руководство по архитектуре управления памятью](#TitleNum_2)
3. [Статистика](#TitleNum_3)
4. [sp_server_diagnostics (Transact-SQL)](#TitleNum_4)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-tempdb-databasedatabasestempdb-databasemd"></a>1. &nbsp; [База данных tempdb](databases/tempdb-database.md)

*Обновление: 2017-11-20* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Далее](#TitleNum_2))

<!-- Source markdown line 121.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5c8bb5f9c40625aaf955295e5b5d03e4257e6c6b 337555ea28f4c3fdd6b78f1bfb4d62607a6bf92d  (PR=4039  ,  Filename=tempdb-database.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=ef1fa818beea435f58986af3379853dc28f5efd8) -->



**Оптимизация производительности базы данных tempdb**

 Размер и физическое размещение базы данных tempdb может влиять на производительность системы. Например, если для базы данных tempdb установлен слишком малый размер, часть системной нагрузки может приходиться на автоувеличение базы данных tempdb до размера, требуемого для поддержки рабочей нагрузки при каждом перезапуске экземпляра ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)].

 По возможности используйте для повышения производительности операций, связанных с увеличением файлов данных, экземпляр [database instant file initialization--../../relational-databases/databases/database-instant-file-initialization.md).

 Заранее выделите место для всех файлов tempdb, установив размер файла в значение, достаточное, чтобы гарантировать обычную рабочую нагрузку в среде. Это предотвращает слишком частое расширение tempdb, которое может повлиять на производительность. Следует установить автоувеличение для базы данных tempdb, но это следует сделать, чтобы увеличить место на диске для незапланированных исключений.

 Файлы данных в каждой группе [filegroup--../../relational-databases/databases/database-files-and-filegroups.md#filegroups) должны быть одинакового размера, поскольку ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] использует алгоритм пропорционального заполнения, который в первую очередь заполняет файлы с большим объемом свободного пространства. Разделение базы данных tempdb на несколько файлов данных равного размера обеспечивает высокую степень параллельной эффективности операций, использующих базу данных tempdb.

 Установите шаг увеличения размера файла на приемлемую величину, чтобы избежать слишком малого увеличения размера файлов базы данных tempdb. Если увеличение размера файла будет идти слишком медленно по сравнению с объемом записываемых в базу tempdb данных, база данных tempdb может требовать постоянного расширения. Это повлияет на производительность.

 Чтобы проверить текущий размер и параметры роста базы данных tempdb, используйте следующий запрос:
```sql
 SELECT name AS FileName,
    size*1.0/128 AS FileSizeinMB,
    CASE max_size
        WHEN 0 THEN 'Autogrowth is off.'
        WHEN -1 THEN 'Autogrowth is on.'
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-memory-management-architecture-guidememory-management-architecture-guidemd"></a>2. &nbsp; [Руководство по архитектуре управления памятью](memory-management-architecture-guide.md)

*Обновлено: 28.11.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 75.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 dd47431ca47eab16af40e41adaeeaf3fc5fb7461 445f013af3bdad65dd3eaf837db7f744b43e8f97  (PR=4113  ,  Filename=memory-management-architecture-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=28cccac53767db70763e5e705b8cc59a83c77317) -->



В предыдущих версиях SQL Server (..!NCLUDE-NotShown--ssVersion2005--../includes/ssversion2005-md.md)], ..!NCLUDE-NotShown--ssKatmai--../includes/ssKatmai-md.md)] и ..!NCLUDE-NotShown--ssKilimanjaro--../includes/ssKilimanjaro-md.md)]) распределение памяти выполнялось с использованием пяти разных механизмов:
-  **Одностраничный распределитель (SPA)**, к которому относится только выделение памяти объемом не больше 8 КБ в процессе ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)]. Пределы физической памяти, используемой SPA, определяют параметры конфигурации *Макс. памяти сервера (МБ)* и *Мин. памяти сервера (МБ)*. Буферный пул был одновременно механизмом для SPA и самым крупным потребителем одностраничных выделений.
-  **Многостраничный распределитель (MPA)** для выделения памяти в объемах больше 8 КБ.
-  **Распределитель CLR**, в том числе кучи SQL CLR и глобального выделения памяти во время инициализации CLR.
-  Выделение памяти для **[thread stacks--../relational-databases/memory-management-architecture-guide.md#stacksizes)** в процессе ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)].
-  **Прямое выделение памяти Windows (DWA)** для запросов на выделение памяти, отправленных напрямую в Windows. Они включают использование кучи Windows и прямое виртуальное выделение от модулей, которые загружаются в процесс ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)]. Примеры таких запросов на выделение включают выделение в библиотеках DLL с расширенными хранимыми процедурами, объекты, созданные с помощью процедур автоматизации (вызовов sp_OA), и выделение со стороны связанных поставщиков сервера.

Начиная с ..!NCLUDE-NotShown--ssSQL11--../includes/sssql11-md.md)], одностраничное, многостраничное выделение и выделение CLR будут объединены в **распределителе страниц "Любой размер"** и станут учитываться в пределах для памяти, управляемых параметрами конфигурации *Макс. памяти сервера (МБ)* и *Мин. памяти сервера (МБ)*. Это изменение позволяет более точно измерять размер для всех требований к памяти, которые проходят через диспетчер памяти .!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)].



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-statisticsstatisticsstatisticsmd"></a>3. &nbsp; [Статистика](statistics/statistics.md)

*Обновлено: 27.11.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_2) | [Далее](#TitleNum_4))

<!-- Source markdown line 48.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1dbe3bd6fdfcd27cf4a597cac5a4a09821b51ba7 971cfccf75fbc8842a0ef020a2bc93992c5f4ad9  (PR=4087  ,  Filename=statistics.md  ,  Dirpath=docs\relational-databases\statistics\  ,  MergeCommitSha40=9fbe5403e902eb996bab0b1285cdade281c1cb16) -->



> [!NOTE]
> Гистограммы в ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] создаются только для одного столбца — первого столбца в наборе ключевых столбцов объекта статистики.

Чтобы создать гистограмму, оптимизатор запросов сортирует значения столбцов, вычисляет количество значений, совпадающих с каждым различающимся значением столбца, а затем осуществляет статистическую обработку значений столбцов с получением непрерывных шагов гистограммы, максимальное количество которых составляет 200. Каждый шаг гистограммы включает диапазон значений столбцов, за которым следует значение столбца, представляющее собой верхнюю границу. В этот диапазон входят все возможные значения столбца между граничными значениями, за исключением самих граничных значений. Наименьшим из отсортированных значений столбца является верхнее граничное значение первого шага гистограммы.

Другими словами, ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] создает **гистограмму** из сортированного набора значений столбцов в три шага:

- **Инициализация гистограммы**: на первом шаге обрабатывается последовательность значений, начиная с начала сортированного набора; собирается до 200 значений *range_high_key*, *equal_rows*, *range_rows* и *distinct_range_rows* (*range_rows* и *distinct_range_rows* всегда равны 0 на этом шаге). Первый шаг заканчивается, когда все входные значения обработаны или найдено 200 значений.
- **Сканирование со слиянием корзин**: каждое дополнительное значение из первого столбца ключа статистики обрабатывается на втором шаге в порядке сортировки; каждое последующее значение либо добавляется в последний диапазон, либо в конце создается новый диапазон (это возможно, потому что входные значения сортированы). Если создается новый диапазон, одна пара существующих, расположенных по соседству диапазонов сворачивается в один. Эта пара диапазонов выбирается с целью уменьшения информационных потерь. Этот способ использует алгоритм *максимальной разности* для сведения к минимуму числа шагов в гистограмме и вместе с тем максимального увеличения разницы между граничными значениями. Число шагов после сворачивания диапазонов на протяжении этого шага остается равным 200.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-spserverdiagnostics-transact-sqlsystem-stored-proceduressp-server-diagnostics-transact-sqlmd"></a>4. &nbsp; [sp_server_diagnostics (Transact-SQL)](system-stored-procedures/sp-server-diagnostics-transact-sql.md)

*Обновлено: 21.11.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_3))

<!-- Source markdown line 157.  ms.author= "edmaca".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d0d97efbb0b16638d0120af9ac5e66ec3bcfa391 b98735ec26a091f8c8c58ca1790243be7942e038  (PR=4052  ,  Filename=sp-server-diagnostics-transact-sql.md  ,  Dirpath=docs\relational-databases\system-stored-procedures\  ,  MergeCommitSha40=45e4efb7aa828578fe9eb7743a1a3526da719555) -->



В примере запроса ниже считываются сводные выходные значения из таблицы:
```sql
SELECT create_time,
       component_name,
       state_desc
FROM SpServerDiagnosticsResult;
```

В примере запроса ниже считываются некоторые подробные выходные сведения из каждого компонента в таблице:
```sql
-- system
select data.value('(/system/@systemCpuUtilization)[1]','bigint') as 'System_CPU',
   data.value('(/system/@sqlCpuUtilization)[1]','bigint') as 'SQL_CPU',
   data.value('(/system/@nonYieldingTasksReported)[1]','bigint') as 'NonYielding_Tasks',
   data.value('(/system/@pageFaults)[1]','bigint') as 'Page_Faults',
   data.value('(/system/@latchWarnings)[1]','bigint') as 'Latch_Warnings',
   data.value('(/system/@BadPagesDetected)[1]','bigint') as 'BadPages_Detected',
   data.value('(/system/@BadPagesFixed)[1]','bigint') as 'BadPages_Fixed'
from SpServerDiagnosticsResult
where component_name like 'system'
go

-- Resource Monitor
select data.value('(./Record/ResourceMonitor/Notification)[1]', 'VARCHAR(max)') AS [Notification],
    data.value('(/resource/memoryReport/entry[@description=''Working Set'']/@value)[1]', 'bigint')/1024 AS [SQL_Mem_in_use_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Paging File'']/@value)[1]', 'bigint')/1024 AS [Avail_Pagefile_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Physical Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_Physical_Mem_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Virtual Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_VAS_MB],
    data.value('(/resource/@lastNotification)[1]','varchar(100)') as 'LastNotification',
    data.value('(/resource/@outOfMemoryExceptions)[1]','bigint') as 'OOM_Exceptions'
from SpServerDiagnosticsResult
where component_name like 'resource'
go

-- Nonpreemptive waits
```







## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новые + обновленные (3+14): **Углубленная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (1+0): **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (87+0): **Analytics Platform System для SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (5+4): **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (0+1): **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (2+2): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (10+9): **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (2+4): **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (4+2): **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (0+1): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (21+0): **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(5+1): **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+1): **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (1+0): **Помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+1): **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2): **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **Data Migration Assistant (DMA) для SQL**](../dma/new-updated-dma.md)
- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


