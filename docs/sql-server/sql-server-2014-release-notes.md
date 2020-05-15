---
title: Заметки о выпуске SQL Server 2014 | Документация Майкрософт
description: В этих заметках о выпуске содержится описание известных проблем, которое необходимо прочитать перед установкой или диагностикой выпусков Microsoft SQL Server 2014 (12.x).
ms.custom: ''
ms.date: 03/15/2018
ms.prod: sql
ms.technology: install
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: bf4c4922-80b3-4be3-bf71-228247f97004
author: rothja
ms.author: jroth
monikerRange: = sql-server-2014 || = sqlallproducts-allversions
ms.openlocfilehash: 6346b8e611fc70f07211abe3060781d548a6a929
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "83001144"
---
# <a name="sql-server-2014-release-notes"></a>SQL Server 2014 Release Notes
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]
В этой статье описываются известные проблемы с выпусками [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], включая связанные пакеты обновления.

## <a name="sql-server-2014-service-pack-2-sp2"></a>SQL Server 2014 с пакетом обновления 2 (SP2)

SQL Server 2014 с пакетом обновления 2 (SP2) включает в себя выпущенные пакеты исправлений для SQL Server 2014 с пакетом обновления 1 (SP1) и накопительным пакетом обновления 7. Этот выпуск содержит улучшения в плане производительности, масштабируемости и диагностики, основанные на отзывах клиентов и сообщества SQL.

### <a name="performance-and-scalability-improvements-in-sp2"></a>Улучшения производительности и масштабируемости в пакете обновления 2 (SP2)

|Компонент|Описание|Дополнительные сведения|
|---|---|---|
|Автоматическое секционирование программной архитектуры NUMA|Вы можете автоматически настраивать программную архитектуру NUMA в системах с 8 или более ЦП в каждом узле NUMA.|[Архитектура Soft-NUMA (SQL Server)](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)|
|Buffer Pool Extension|Позволяет масштабировать буферный пул SQL Server сверх 8 ТБ.|[Расширение буферного пула](https://docs.microsoft.com/sql/database-engine/configure-windows/buffer-pool-extension)|
|Динамическое масштабирование объектов в памяти| Позволяет динамически секционировать объекты в памяти в соответствии с числом узлов и ядер. Это улучшение устраняет необходимость в использовании флага трассировки 8048 начиная с выпуска SQL Server 2014 с пакетом обновления 2 (SP2).|[Динамическое масштабирование объектов в памяти](https://blogs.msdn.microsoft.com/sql_server_team/dynamic-memory-object-scaling/)|
|Указание MAXDOP для команд DBCC CHECK*|Это улучшение полезно при выполнении команды DBCC CHECKDB с параметром MAXDOP, значение которого отлично от sp_configure.|[Указания (Transact-SQL) — запросы](https://docs.microsoft.com/sql/t-sql/queries/hints-transact-sql-query)|
|Улучшение, касающееся спин-блокировки SOS_RWLock|Устраняет необходимость в использовании спин-блокировки для SOS_RWLock. Вместо этого можно использовать методы без блокировки, аналогичные применяемым в выполняющейся памяти OLTP. |[Переработка SOS_RWLock](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/)|
|Собственная реализация пространственных запросов|Значительное повышение производительности пространственных запросов.|[Увеличение производительности пространственных запросов в SQL Server 2012 и 2014](https://support.microsoft.com/help/3107399/spatial-performance-improvements-in-sql-server-2012-and-2014)

### <a name="supportability-and-diagnostics-improvements-in-sp2"></a>Расширение поддерживаемых функций и диагностических возможностей в пакете обновления 2 (SP2)

|Компонент|Описание|Дополнительные сведения|
|---|---|---|
|Запись времени ожидания AlwaysOn в журнал|Добавлена новая возможность записи в журнал сообщений об истечении времени ожидания аренды. Записываются текущее время и ожидаемое время продления. |[Улучшены возможности диагностики, связанные с временем ожидания аренды группы доступности AlwaysOn](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/)
|Расширенные события и счетчики производительности AlwaysOn|Новые расширенные события и счетчики производительности AlwaysOn помогают устранять проблемы с задержками AlwaysOn. |Статьи базы знаний [3107172](https://support.microsoft.com/help/3107172/improve-tempdb-spill-diagnostics-by-using-extended-events-in-sql-serve) и [3107400](https://support.microsoft.com/help/3107400/improved-tempdb-spill-diagnostics-in-showplan-xml-schema-in-sql-server)
|Очистка отслеживания изменений|Новая хранимая процедура sp_flush_CT_internal_table_on_demand очищает внутренние таблицы отслеживания изменений по требованию.|[Статья базы знаний 3173157](https://support.microsoft.com/help/3173157/adds-a-stored-procedure-for-the-manual-cleanup-of-the-change-tracking)
|Клонирование базы данных|Используйте новую команду DBCC для устранения неполадок существующих рабочих баз данных путем клонирования схемы, метаданных и статистики, но не данных. Клонированные базы данных не предназначены для использования в рабочих средах.|[Статья базы знаний 3177838](https://support.microsoft.com/help/3177838/how-to-use-dbcc-clonedatabase-to-generate-a-schema-and-statistics-only)
|Новые функции динамического управления|Новая функция динамического управления sys.dm_db_incremental_stats_properties предоставляет сведения о каждой секции для сбора добавочной статистики.|[Статья базы знаний 3170114](https://support.microsoft.com/help/3170114/update-to-add-dmf-sys-dm-db-incremental-stats-properties-in-sql-server)
|Функция динамического управления для получения входного буфера в SQL Server|Доступна новая функция динамического управления, позволяющая получать входной буфер для сеанса или запроса (sys.dm_exec_input_buffer). Она функционально эквивалентна команде DBCC INPUTBUFFER.|[sys.dm_exec_input_buffer](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-input-buffer-transact-sql)
|Поддержка DROP DDL для репликации|Позволяет удалять таблицу, включенную в качестве статьи в публикацию репликации транзакций, из базы данных и публикации.|[Статья базы знаний 3170123](https://support.microsoft.com/help/3170123/supports-drop-table-ddl-for-articles-that-are-included-in-transactiona)
|Разрешение на мгновенную инициализацию файлов в учетной записи службы SQL|Укажите, должна ли действовать мгновенная инициализация файлов (IFI) при запуске службы SQL Server.|[Инициализация файлов базы данных](https://docs.microsoft.com/sql/relational-databases/databases/database-instant-file-initialization)
|Временно предоставляемые буферы памяти — обработка ошибок|Вы можете использовать указания диагностики при выполнении запросов, ограничивая временно предоставляемые буферы памяти во избежание состязания за ресурсы памяти.|[Статья базы знаний 3107401](https://support.microsoft.com/help/3107401/new-query-memory-grant-options-are-available-min-grant-percent-and-max)
|Упрощенное профилирование выполнения запросов по операторам |Оптимизирует сбор статистики выполнения запросов по операторам, например фактического числа строк.|[Developers Choice: Query progress - anytime, anywhere](https://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/) (Выбор разработчика: ход выполнения запроса — всегда и везде).
|Диагностика выполнения запросов|В планах выполнения запросов теперь указываются фактические считанные строки, что упрощает устранение неполадок, связанных с производительностью запросов.|[Статья базы знаний 3107397](https://support.microsoft.com/help/3107397/improved-diagnostics-for-query-execution-plans-that-involve-residual-p)
|Диагностика выполнения запросов для временной записи в tempdb|В предупреждении хэша и предупреждениях сортировки теперь есть дополнительные столбцы для получения статистики по физическим операциям ввода-вывода, отслеживания используемой памяти и затронутых строк. |[Оптимизация диагностики временной записи в temptdb](https://support.microsoft.com/help/3107172/improve-tempdb-spill-diagnostics-by-using-extended-events-in-sql-serve)
|Поддержка tempdb |Используйте новое сообщение в журнале ошибок для получения числа файлов tempdb и изменений в файлах данных tempdb при запуске сервера.|[Статья базы знаний 2963384](https://support.microsoft.com/help/2963384/fix-sql-server-crashes-when-the-log-file-of-tempdb-database-is-full-in)


Кроме того, обратите внимание на указанные ниже исправления.
- Стек вызовов Xevent теперь содержит имена модулей и смещение вместо абсолютных адресов.
- Улучшенная корреляция между расширенными событиями и динамическими административными представлениями диагностики: поля query_hash и query_plan_hash используются в качестве уникальных идентификаторов запроса. Динамическое административное представление определяет их как varbinary(8), а XEvent определяет их как UINT64. Так как в SQL Server не используется тип "unsigned bigint" (большое целое число без знака), приведение иногда не работает. Это улучшение представляет новые столбцы действий и фильтров XEvent, эквивалентные query_hash и query_plan_hash, кроме случая, когда они определены как INT64. Это исправление помогает коррелировать запросы между событиями XE и динамическими административными представлениями.
- Поддержка кодировки UTF-8 в BULK INSERT и BCP: BULK INSERT и BCP теперь поддерживают экспорт и импорт данных в кодировке UTF-8.

### <a name="download-pages-and-more-information-for-sp2"></a>Страницы загрузки и дополнительные сведения для пакета обновления 2 (SP2)

- [Скачать пакет обновления 2 (SP2) для Microsoft SQL Server 2014](https://www.microsoft.com/download/details.aspx?id=53168)
- [Доступен SQL Server 2014 с пакетом обновления 2 (SP2)](https://www.microsoft.com/download/details.aspx?id=53167)
- [SQL Server 2012 Express с пакетом обновлений 2 (SP2)](https://www.microsoft.com/download/details.aspx?id=53167)
- [Пакет дополнительных компонентов SQL Server 2014 с пакетом обновления 2 (SP2)](https://www.microsoft.com/download/details.aspx?id=53164)
- [Построитель отчетов для SQL Server 2014 с пакетом обновления 2 (SP2)](https://www.microsoft.com/download/details.aspx?id=53163)
- [Надстройка служб SQL Server 2014 с пакетом обновления 2 (SP2) Reporting Services для Microsoft Sharepoint](https://www.microsoft.com/download/details.aspx?id=53162)
- [Семантическая статистика языка SQL Server 2014 с пакетом обновления 2 (SP2)](https://www.microsoft.com/download/details.aspx?id=53165)
- [Сведения о выпуске SQL Server 2014 с пакетом обновления 2 (SP2)](https://support.microsoft.com/help/3171021/sql-server-2014-service-pack-2-release-information)

## <a name="sql-server-2014-service-pack-1-sp1"></a>SQL Server 2014 с пакетом обновления 1 (SP1)

SQL Server 2014 с пакетом обновления 1 (SP1) включает в себя исправления из накопительных пакетов обновления 1–5 для SQL Server 2014, а также пакет исправлений, выпущенных ранее в составе SQL Server 2012 с пакетом обновления 2 (SP2).

> [!NOTE]
> Если для экземпляра SQL Server включен каталог SSISDB и при обновлении до пакета обновления 1 (SP1) возникает ошибка установки, выполните соответствующие инструкции в статье [Ошибка 912 или 3417 при установке SQL Server 2014 с пакетом обновления 1 (SP1)](https://support.microsoft.com/help/3018269/error-912-or-3417-when-you-install-sql-server-2014-sp1-build-12-0-4050/).

### <a name="download-pages-and-more-information-for-sp1"></a>Страницы загрузки и дополнительные сведения для пакета обновления 1 (SP1)

- [Скачать пакет обновления 1 (SP1) для Microsoft SQL Server 2014](https://www.microsoft.com/download/details.aspx?id=46694)
- [Выпущен пакет обновления 1 (SP1) для SQL Server 2014 — обновлено](https://blogs.msdn.microsoft.com/sqlreleaseservices/sql-server-2014-service-pack-1-has-released-updated/)
- [Microsoft SQL Server 2014 Express с пакетом обновления 1 (SP1)](https://www.microsoft.com/download/details.aspx?id=42299)
- [Пакет дополнительных компонентов для Microsoft SQL Server 2014 с пакетом обновления 1 (SP1)](https://www.microsoft.com/download/details.aspx?id=46696)


## <a name="before-you-install-sql-server-2014-rtm"></a>Действия перед установкой SQL Server 2014 RTM

### <a name="limitations-and-restrictions-in-sql-server-2014-rtm"></a>Ограничения в SQL Server 2014 RTM

1.  Обновление с версии SQL Server 2014 CTP 1 до SQL Server 2014 RTM НЕ поддерживается.  
2.  Параллельная установка версии SQL Server 2014 CTP 1 с SQL Server 2014 RTM НЕ поддерживается.  
3.  Присоединение или восстановление базы данных версии SQL Server 2014 CTP 1 в SQL Server 2014 RTM НЕ поддерживаются.  

**Решение:** Нет.

#### <a name="upgrading-from-sql-server-2014-ctp-2-to-sql-server-rtm"></a>Обновление с версии SQL Server 2014 CTP 2 до версии SQL Server RTM
Обновление полностью поддерживается. В частности, можно:

1.  присоединить базу данных версии SQL Server 2014 CTP 2 к экземпляру SQL Server 2014 RTM;    
2.  восстановить резервную копию базы данных, созданную в версии SQL Server 2014 CTP 2, в экземпляре SQL Server 2014 RTM;    
3.  обновить до версии SQL Server 2014 RTM на месте;
4.  последовательно обновить до версии SQL Server 2014 RTM; Необходимо переключиться в режим перехода на другой ресурс вручную перед началом последовательного обновления. Подробные сведения см. в статье [Модернизация или обновление серверов группы доступности при минимальных значениях времени простоя и потери данных](https://msdn.microsoft.com/library/dn178483.aspx).    
5.  Данные, собранные наборами элементов сбора данных о производительности транзакций, которые установлены в выпуске SQL Server 2014 CTP 2, нельзя просмотреть с помощью среды SQL Server Management Studio из SQL Server 2014 RTM, и наоборот.
  
#### <a name="downgrading-from-sql-server-2014-rtm-to-sql-server-2014-ctp-2"></a>Переход с версии SQL Server 2014 RTM на более раннюю версию SQL Server 2014 CTP 2  
Это действие не поддерживается.  
  
**Решение:** Обходного решения для перехода на более раннюю версию не существует. Перед обновлением до версии SQL Server 2014 RTM рекомендуется создать резервную копию базы данных.  
  
#### <a name="incorrect-version-of-streaminsight-client-on-sql-server-2014-mediaisocab"></a>Неправильная версия клиента StreamInsight на носителе SQL Server 2014/ISO/CAB  
На носителе SQL Server/ISO/CAB (StreamInsight\\\<архитектура\>\\\<код языка\>) находится неправильная версия StreamInsight.msi и StreamInsightClient.msi.  
  
**Решение:** Скачайте правильную версию со [страницы скачивания пакета дополнительных компонентов SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=306709) и установите ее.  
  
### <a name="product-documentation-rtm"></a><a name="ProdDoc"></a>Документация по версии RTM
  
Содержимое построителя отчетов и PowerPivot недоступно на некоторых языках. 

**Проблема**. Содержимое построителя отчетов недоступно на следующих языках:  
  
-   греческий (el-GR);  
-   норвежский (букмол) (nb-NO);  
-   финский (fi-FI);  
-   датский (da-DK).  
  
В [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]это содержимое находилось в CHM-файле, поставляемом вместе с продуктом, и данные языки поддерживались. CHM-файлы больше не поставляются вместе с продуктом, и содержимое построителя отчетов доступно только в MSDN. MSDN не поддерживает данные языки. Построитель отчетов также удален из TechNet и больше не доступен на этих поддерживаемых языках.  
  
**Решение:** Нет.  
  
**Проблема**. Содержимое Power Pivot недоступно на следующих языках:
  
-   греческий (el-GR);  
-   норвежский (букмол) (nb-NO);  
-   финский (fi-FI);  
-   датский (da-DK).  
-   Чешский (cs-CZ)  
-   Венгерский (hu-HU)  
-   Нидерландский (nl-NL)  
-   Польский (pl-PL)  
-   Шведский (sv-SE)  
-   Турецкий (tr-TR)  
-   Португальский (Португалия) (pt-PT)  
  
В [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]это содержимое находилось в TechNet и данные языки поддерживались. Это содержимое удалено из TechNet и больше не доступно на этих поддерживаемых языках.  
  
**Решение:** Нет.  
  
### <a name="database-engine-rtm"></a><a name="DBEngine"></a>Ядро СУБД (RTM)
  
#### <a name="changes-made-for-standard-edition-in-sql-server-2014-rtm"></a>Изменения, внесенные в выпуск Standard в версии SQL Server 2014 RTM  
В версии SQL Server 2014 Standard реализованы следующие изменения:  
  
-   Функция расширения буферного пула допускает максимальный размер, который в четыре раза больше настроенной памяти.    
-   Максимальный объем памяти увеличен с 64 до 128 ГБ.  
 
#### <a name="memory-optimization-advisor-flags-default-constraints-as-incompatible"></a>Помощник по оптимизации памяти помечает ограничения по умолчанию как несовместимые  
**Проблема**. Помощник по оптимизации памяти в SQL Server Management Studio помечает все заданные по умолчанию ограничения как несовместимые. Не все ограничения по умолчанию поддерживаются в оптимизированных для памяти таблицах. Помощник не различает поддерживаемые типы ограничений по умолчанию и те из них, которые не поддерживаются. Среди ограничений по умолчанию поддерживаются все константы, выражения и встроенные функции, которые поддерживаются в скомпилированных в собственном коде хранимых процедурах. Чтобы просмотреть список функций, поддерживаемых в скомпилированных в собственном коде хранимых процедурах, см. статью [Поддерживаемые конструкции для хранимых процедур, скомпилированных в собственном коде](https://msdn.microsoft.com/library/dn452279(v=sql.120).aspx).  
  
**Решение:** Если с помощью помощника требуется определить причины блокировок, то следует пропускать совместимые ограничения по умолчанию. Чтобы использовать помощник по оптимизации памяти для переноса таблиц, в которых есть совместимые ограничения по умолчанию и нет никаких других причин блокировки, выполните следующие действия.  
  
1.  Удалите ограничения по умолчанию из определения таблицы.    
2.  Используйте помощник, чтобы формировать скрипт переноса для таблицы.    
3.  Добавьте обратно в скрипт переноса ограничения по умолчанию.    
4.  Выполните скрипт переноса.  
  
#### <a name="informational-message-file-access-denied-incorrectly-reported-as-an-error-in-the-sql-server-2014-error-log"></a>Информационное сообщение "В доступе к файлу отказано" неверно определяется в журнале ошибок SQL Server 2014 как ошибка.  
**Проблема**. При перезапуске сервера, на котором находятся базы данных с оптимизированными для памяти таблицами, в журнале ошибок SQL Server 2014 может отображаться следующий тип сообщений об ошибках:  
  
```  
[ERROR]Unable to delete file C:\Program Files\Microsoft SQL   
Server\....old.dll. This error may be due to a previous failure to unload   
memory-optimized table DLLs.  
```  
Это, по сути, информационное сообщение. Никаких действий пользователя при его появлении не требуется.  
  
**Решение:** Нет. Это информационное сообщение.  
  
#### <a name="missing-index-details-incorrectly-report-included-columns-for-memory-optimized-table"></a>Сведения об отсутствующих индексах неправильно указывают включенные столбцы для оптимизированной для памяти таблицы  
**Проблема**. Если SQL Server 2014 обнаружит отсутствующий индекс в оптимизированной для памяти таблице, он укажет его в файле SHOWPLAN_XML, а также в динамических административных представлениях отсутствующих индексов, например sys.dm_db_missing_index_details. В некоторых случаях сведения об отсутствующих индексах будут содержать включенные столбцы. Так как все столбцы неявно включены во все индексы оптимизированных для памяти таблиц, явно указывать включенные столбцы с оптимизированными для памяти индексами нельзя.  
  
**Решение:** Не указывайте предложение INCLUDE с индексами в оптимизированных для памяти таблицах.  
  
#### <a name="missing-index-details-omit-missing-indexes-when-a-hash-index-exists-but-is-not-suitable-for-the-query"></a>В сведениях об отсутствующих индексах пропускаются отсутствующие индексы, если хэш-индекс имеется, но не подходит для запроса  
**Проблема**. Если индекс HASH присутствует в столбцах оптимизированной для памяти таблицы, указанной в запросе, но его нельзя использовать для запроса, SQL Server 2014 не всегда сообщает об отсутствующем индексе в SHOWPLAN_XML и в динамическом административном представлении sys.dm_db_missing_index_details.  
  
В частности, если запрос содержит предикаты равенства, которые включают подмножество ключевых столбцов индекса, или если он содержит предикаты неравенства, которые включают ключевые столбцы индекса, то индекс HASH нельзя использовать с исходном виде, а для эффективного выполнения запроса потребуется другой индекс.  
  
**Решение:** Если используются хэш-индексы, проверьте запросы и планы запросов, чтобы определить, следует ли выполнять операции поиска в индексе в подмножестве ключей индекса или операции поиска в индексе в предикатах неравенства. Если необходимо осуществлять поиск в подмножестве ключа индекса, то используйте либо индекс NONCLUSTERED, либо индекс HASH именно в тех столбцах, в которых требуется выполнять поиск. Если необходимо осуществлять поиск в предикате неравенства, то вместо индекса HASH используйте индекс NONCLUSTERED.  
  
#### <a name="failure-when-using-a-memory-optimized-table-and-memory-optimized-table-variable-in-the-same-query-if-the-database-option-read_committed_snapshot-is-set-to-on"></a>Ошибки при использовании оптимизированной для памяти таблицы и переменной оптимизированной для памяти таблицы в одном запросе, если параметру базы данных READ_COMMITTED_SNAPSHOT присвоено значение ON  
**Проблема**. Если параметру базы данных READ_COMMITTED_SNAPSHOT присвоено значение ON и в одном запросе происходит обращение к оптимизированной для памяти таблице и переменной оптимизированной для памяти таблицы вне контекста транзакции пользователя, может возникнуть следующая ошибка:  
  
```  
Msg 41359  
A query that accesses memory optimized tables using the READ COMMITTED  
isolation level, cannot access disk based tables when the database option  
READ_COMMITTED_SNAPSHOT is set to ON. Provide a supported isolation level  
for the memory optimized table using a table hint, such as WITH (SNAPSHOT).  
```  
  
**Решение:** Либо используйте табличное указание WITH (SNAPSHOT) с переменной таблицы, либо присвойте параметру базы данных MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT значение ON с помощью следующей инструкции:  
  
```  
ALTER DATABASE CURRENT   
SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON  
```  
  
#### <a name="procedure-and-query-execution-statistics-for-natively-compiled-stored-procedures-record-worker-time-in-multiples-of-1000"></a>Статистика выполнения процедур и запросов для скомпилированных в собственном коде хранимых процедур формирует запись времени рабочего потока, кратное 1000  
**Проблема**. После включения сбора статистики выполнения процедур или запросов для скомпилированных в машинном коде хранимых процедур с помощью sp_xtp_control_proc_exec_stats или sp_xtp_control_query_exec_stats значение *_worker_time отображается как кратное 1000 в динамических административных представлениях sys.dm_exec_procedure_stats и sys.dm_exec_query_stats. Выполнения запросов, время рабочей роли которых меньше 500 микросекунд будет отображаться как значение worker_time, равное 0.  
  
**Решение:** Нет. Не следует считать верным значение worker_time, указанное в динамических административных представлениях статистики выполнения для краткосрочных запросов из скомпилированных в собственном коде хранимых процедур.  
  
#### <a name="error-with-showplan_xml-for-natively-compiled-stored-procedures-that-contain-long-expressions"></a>Ошибка с SHOWPLAN_XML для скомпилированных в собственном коде хранимых процедур, которые содержат длинные выражения  
**Проблема**. Если скомпилированная в машинном коде хранимая процедура содержит длинное выражение, получение SHOWPLAN_XML для процедуры с помощью параметра T-SQL SET SHOWPLAN_XML ON или параметра "Показать предполагаемый план выполнения" в Management Studio может привести к возникновению следующей ошибки:  
  
```  
Msg 41322. MAT/PIT export/import encountered a failure for memory  
optimized table or natively compiled stored procedure with object ID  
278292051 in database ID 6. The error code was  
0xc00cee81.  
```  
  
**Решение:** Два предлагаемых решения:  
  
1.  Заключить выражение в скобки, как в приведенном далее примере:  
  
    Вместо:  
  
    ```  
    SELECT @v0 + @v1 + @v2 + ... + @v199  
    ```  
  
    Запись:  
  
    ```  
    SELECT((@v0 + ... + @v49) + (@v50 + ... + @v99)) + ((@v100 + ... + @v149) + (@v150 + ... + @v199))  
    ```  
  
2.  Создайте вторую процедуру с немного упрощенным выражением для showplan — в общих чертах план должен быть таким же. Например, вместо:  
  
    ```  
    SELECT @v0 +@v1 +@v2 +...+@v199  
    ```  
  
    Запись:  
  
    ```  
    SELECT @v0 +@v1  
    ```  
  
#### <a name="using-a-string-parameter-or-variable-with-datepart-and-related-functions-in-a-natively-compiled-stored-procedure-results-in-an-error"></a>Использование строкового параметра или переменной с DATEPART и связанными функциями в скомпилированной в собственном коде хранимой процедуре приводит к ошибке  
**Проблема**. При использовании строкового параметра или переменной со встроенными функциями DATEPART, DAY, MONTH и YEAR внутри скомпилированной в собственном коде хранимой процедуры выводится сообщение об ошибке, в котором указывается, что тип данных datetimeoffset не поддерживается скомпилированными в собственном коде хранимыми процедурами.  
  
**Решение:** Назначьте строковой параметр или переменную новой переменной типа datetime2 и используйте эту переменную в функции DATEPART, DAY, MONTH или YEAR. Пример:  
  
```  
DECLARE @d datetime2 = @string  
DATEPART(weekday, @d)  
```  
  
#### <a name="native-compilation-advisor-flags-delete-from-clauses-incorrectly"></a>Помощник по компиляции в собственный код неправильно помечает предложения DELETE FROM  
**Проблема**. Помощник по компиляции в собственный код неправильно помечает предложения DELETE FROM внутри хранимой процедуры как несовместимые.  
  
**Решение:** Нет.  
  
#### <a name="register-through-ssms-adds-dac-meta-data-with-mismatched-instance-ids"></a>При регистрации через среду SSMS добавляются метаданные приложения уровня данных с несовпадающими идентификаторами экземпляра  
**Проблема**. При регистрации или удалении пакета приложения уровня данных (DACPAC) с помощью среды SQL Server Management Studio таблицы SYSDAC* не обновляются правильно, чтобы позволить пользователю выполнять запросы к журналу DACPAC базы данных.  Instance_id для sysdac_history_internal и sysdac_instances_internal не совпадают, из-за чего соединение невозможно.  
  
**Решение:** Эта проблема исправлена в платформе [Data-Tier Application Framework](https://www.microsoft.com/download/details.aspx?id=42295), которая распространяется в составе пакета дополнительных компонентов.  После применения обновления все новые записи журнала будут использовать значение, указанное для instance_id в таблице sysdac_instances_internal.  
  
Если уже имеется проблема с несовпадающими значениями instance_id, единственным способом устранить их является подключиться к серверу от имени пользователя с правами на запись в базу данных MSDB и исправить значения instance_id на верные.  Если вы получаете несколько событий регистрации и отмены регистрации из одной и той же базы данных, необходимо изучить значения даты и времени, чтобы определить, какие записи соответствуют текущему значению instance_id.  
  
1.  Подключитесь к серверу в среде SQL Server Management Studio с помощью имени входа, которое имеет разрешения на обновление в MSDB.    
2.  Открытие нового запроса в базе данных MSDB.    
3.  Выполните этот запрос для просмотра всех активных экземпляров приложения уровня данных.  Найдите экземпляр, который требуется исправить, и запишите значение instance_id:  
  
    `select * from` sysdac_instances_internal  
  
4.  Выполните этот запрос, чтобы отобразить все записи журнала.  
  
    `select * from` sysdac_history_internal  
  
5.  Определите строки, которые должны соответствовать исправляемому экземпляру. 
6.  Обновите значение sysdac_history_internal.instance_id, задав значение, которое вы записали на шаге 3 (из таблицы sysdac_instances_internal):  
  
    `update` sysdac_history_internal `set` instance_id = "\<значение с шага 3\>" `where` \<выражение, соответствующее строкам, которые нужно обновить\>  
  
### <a name="reporting-services-rtm"></a><a name="SSRS"></a>Службы Reporting Services (RTM)
  
#### <a name="the-sql-server-2012-reporting-services-native-mode-report-server-cannot-run-side-by-side-with-sql-server-2014-reporting-services-sharepoint-components"></a>Сервер отчетов служб SQL Server 2012 Reporting Services в собственном режиме не может работать параллельно с компонентами SharePoint служб SQL Server 2014 Reporting Services  
**Проблема**. Выполняемая в собственном режиме служба Windows [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SQL Server Reporting Services (ReportingServicesService.exe) не запускается, если на том же сервере установлены компоненты SharePoint служб [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
**Решение:** Удалите компоненты SharePoint [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и перезапустите службу Windows для Microsoft SQL Server 2012 Reporting Services.  
  
**Дополнительные сведения:**  
  
Службы [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в собственном режиме не могут работать параллельно со следующими компонентами:  
  
-   надстройка [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint;    
-   общая служба SharePoint для [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
При параллельной установке служба Windows для служб [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], работающих в собственном режиме, не запускается. В журнале событий Windows будут сообщения, похожие на показанные здесь:  
  
```  
Log Name:   Application  
Source:          Report Server (<SQL instance ID>)  
Event ID:        117  
Task Category:   Startup/Shutdown  
Level:           Error  
Keywords:        Classic  
Description:     The report server database is an invalid version.  
  
Log Name:      Application  
Source:        Report Server (<SQL instance ID>)  
Event ID:      107  
Task Category: Management  
Level:         Error  
Keywords:      Classic  
Description:   Report Server (DENALI) cannot connect to the report server database.  
```  
  
Дополнительные сведения см. в разделе [Рекомендации, советы и сведения по устранению неполадок со службами SQL Server 2014 Reporting Services](https://go.microsoft.com/fwlink/?LinkID=391254).  
  
#### <a name="required-upgrade-order-for-multi-node-sharepoint-farm-to-sql-server-2014-reporting-services"></a>Требуемый порядок обновления для фермы SharePoint с несколькими узлами до служб SQL Server 2014 Reporting Services  
**Проблема**. Подготовка отчета к просмотру в ферме с несколькими узлами завершается ошибкой, если экземпляры общей службы SharePoint служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] обновляются перед всеми экземплярами надстройки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint.  
  
**Решение:** В ферме SharePoint с несколькими узлами:  
  
1.  Сначала обновите все экземпляры надстройки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint.    
2.  Затем обновите все экземпляры общей службы SharePoint служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
Дополнительные сведения см. в разделе [Рекомендации, советы и сведения по устранению неполадок со службами SQL Server 2014 Reporting Services](https://go.microsoft.com/fwlink/?LinkID=391254).  
  
### <a name="sql-server-2014-rtm-on-azure-virtual-machines"></a><a name="AzureVM"></a>SQL Server 2014 RTM на виртуальных машинах Azure  
  
#### <a name="the-add-azure-replica-wizard-returns-an-error-when-configuring-an-availability-group-listener-in-azure"></a>Мастер добавления реплики Azure возвращает ошибку при настройке прослушивателя группы доступности в Azure  
**Проблема**. Если для группы доступности существует прослушиватель, при попытке настроить его в Azure мастер добавления реплики Azure вернет ошибку.  
  
Это происходит потому, что прослушиватели групп доступности требуют назначения одного IP-адреса в каждой подсети, в которой размещены реплики группы доступности, включая подсеть Azure.  
  
**Решение:**  
  
1.  На странице прослушивателя назначьте свободный статический IP-адрес из подсети Azure, в которой будет размещаться реплика группы доступности, прослушивателю группы доступности.  
  
    Это решение позволит мастеру завершить добавление реплики в Azure.  
  
2.  Когда мастер завершит работу, необходимо будет закончить настройку прослушивателя в Azure, как описано в статье [Настройка прослушивателя внутреннего балансировщика нагрузки для групп доступности AlwaysOn в Azure](https://msdn.microsoft.com/library/dn376546.aspx).  
  
### <a name="analysis-services-rtm"></a><a name="SSAS"></a>Службы Analysis Services (RTM)
  
#### <a name="msolap5-must-be-downloaded-installed-and-registered-for-a-sharepoint-2010-new-farm-configured-with-sql-server-2014"></a>MSOLAP.5 необходимо скачать, установить и зарегистрировать для новой фермы SharePoint 2010, настроенной с SQL Server 2014  
**Проблема**.  
  
-   В ферме SharePoint 2010, настроенной с развертыванием SQL Server 2014 RTM, книги PowerPivot не могут подключаться к моделям данных, так как не установлен поставщик, указанный в строке подключения.  
  
**Решение:**  
  
1.  Загрузите поставщик MSOLAP.5 из пакета дополнительных компонентов [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] . Установите поставщик на серверах приложений, на которых запущены службы Excel. Дополнительные сведения см. в подразделе "Поставщик Microsoft Analysis Services OLE DB для Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)" [Пакет дополнительных компонентов Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)](https://www.microsoft.com/download/details.aspx?id=35580).  
  
2.  Зарегистрируйте MSOLAP.5 в качестве надежного поставщика в службах Excel SharePoint. Дополнительные сведения см. в разделе [Добавление MSOLAP.5 в качестве надежного поставщика данных в службах Excel Services](https://technet.microsoft.com/library/hh758436.aspx).  
  
**Дополнительные сведения:**  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] содержит MSOLAP.6. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] и [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssGemini](../includes/ssgemini-md.md)] используют MSOLAP.5. Если MSOLAP.5 не установлен на компьютере, где работают службы Excel, то службы Excel не могут загружать модели данных.  
  
#### <a name="msolap5-must-be-downloaded-installed-and-registered-for-a-sharepoint-2013-new-farm-configured-with-sql-server-2014"></a>MSOLAP.5 необходимо скачать, установить и зарегистрировать для новой фермы SharePoint 2013, настроенной с SQL Server 2014  
**Проблема**.  
  
-   В ферме SharePoint 2013, настроенной с развертыванием [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] , книги Excel, обращающиеся к поставщику MSOLAP.5, не могут подключаться к моделям данных, так как не установлен поставщик, указанный в строке подключения.  
  
**Решение:**  
  
1.  Загрузите поставщик MSOLAP.5 из пакета дополнительных компонентов [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] . Установите поставщик на серверах приложений, на которых запущены службы Excel. Дополнительные сведения см. в подразделе "Поставщик Microsoft Analysis Services OLE DB для Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)" [Пакет дополнительных компонентов Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)](https://www.microsoft.com/download/details.aspx?id=35580).  
  
2.  Зарегистрируйте MSOLAP.5 в качестве надежного поставщика в службах Excel SharePoint. Дополнительные сведения см. в разделе [Добавление MSOLAP.5 в качестве надежного поставщика данных в службах Excel Services](https://technet.microsoft.com/library/hh758436.aspx).  
  
**Дополнительные сведения:**  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] содержит MSOLAP.6. но книги PowerPivot SQL Server 2014 используют MSOLAP.5. Если MSOLAP.5 не установлен на компьютере, где работают службы Excel, то службы Excel не могут загружать модели данных.  
  
#### <a name="corrupt-data-refresh-schedules-rtm"></a>Повреждение расписаний обновления данных (RTM)
**Проблема**.  
  
-   Изменяется расписание обновления, и расписание становится поврежденным и недоступным.  
  
**Решение:**  
  
1.  В Microsoft Excel очистите пользовательские дополнительные свойства. См. раздел "Решение" в статье базы знаний [2927748](https://support.microsoft.com/kb/2927748).  
  
**Дополнительные сведения:**  
  
-    Если сериализованная длина расписания обновления меньше, чем у исходного расписания, при изменении расписания обновления данных в книге размер буфера неправильно обновляется, и новые сведения о расписании объединяются со сведениями старого расписания, в результате чего оно становится поврежденным.  
  
### <a name="data-quality-services-rtm"></a><a name="DQS"></a>Службы Data Quality Services (RTM)
  
#### <a name="no-cross-version-support-for-data-quality-services-in-master-data-services"></a>Отсутствие перекрестной поддержки версий для служб Data Quality Services в службах Master Data Services  
**Проблема**. Следующие сценарии не поддерживаются.  
  
-   Службы Master Data Services 2014, размещенные в базе данных компонента SQL Server Database Engine в SQL Server 2012 с установленными службами Data Quality Services 2012.  
  
-   Службы Master Data Services 2012, размещенные в базе данных ядра СУБД SQL Server в SQL Server 2014 с установленными службами Data Quality Services 2014.  
  
**Решение:** Используйте версию служб Master Data Services, совпадающую с версией базы данных ядра СУБД и служб Data Quality Services.  
  
### <a name="upgrade-advisor-issues-rtm"></a><a name="UA"></a>Проблемы с помощником по обновлению (RTM)
  
#### <a name="sql-server-2014-upgrade-advisor-reports-irrelevant-upgrade-issues-for-sql-server-reporting-services"></a>Помощник по обновлению SQL Server 2014 сообщает о несущественных проблемах с обновлением для служб SQL Server Reporting Services  
**Проблема**. Помощник по обновлению SQL Server (SSUA), поставляемый с носителем SQL Server 2014, неправильно сообщает о ряде ошибок при анализе сервера служб SQL Server Reporting Services.  
  
**Решение:** Эта ошибка исправлена в помощнике по обновлению SQL Server в [пакете дополнительных компонентов SQL Server 2014 для SSUA](https://go.microsoft.com/fwlink/?LinkID=306709).  
  
#### <a name="sql-server-2014-upgrade-advisor-reports-an-error-when-analyzing-sql-server-integration-services-server"></a>Помощник по обновлению SQL Server 2014 сообщает об ошибке при анализе сервера служб SQL Server Integration Services  
**Проблема**. Помощник по обновлению SQL Server (SSUA), поставляемый на носителе SQL Server 2014, сообщает об ошибке при анализе сервера SQL Server Integration Services.  Сообщение, отображаемое пользователю:  
  
```  
The installed version of Integration Services does not support Upgrade Advisor.   
The assembly information is "Microsoft.SqlServer.ManagedDTS, Version=11.0.0.0,   
Culture=neutral, PublicKeyToken=89845dcd8080cc91  
```  
  
**Решение:** Эта ошибка исправлена в помощнике по обновлению SQL Server в [пакете дополнительных компонентов SQL Server 2014 для SSUA](https://go.microsoft.com/fwlink/?LinkID=306709).  
  
[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
