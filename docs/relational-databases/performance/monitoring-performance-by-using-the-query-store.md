---
title: Мониторинг производительности с использованием хранилища запросов | Документация Майкрософт
ms.custom: ''
ms.date: 11/29/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Query Store
- Query Store, described
ms.assetid: e06344a4-22a5-4c67-b6c6-a7060deb5de6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e36a66564564bb468592df491e12d97a87d5dc4b
ms.sourcegitcommit: c7febcaff4a51a899bc775a86e764ac60aab22eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/30/2018
ms.locfileid: "52711505"
---
# <a name="monitoring-performance-by-using-the-query-store"></a>Мониторинг производительности с использованием хранилища запросов
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Хранилище запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет подробные сведения о выборе и производительности плана запроса. Оно упрощает устранение неполадок с производительностью, помогая быстро находить разницу в производительности, вызванную изменением плана запроса. Хранилище запросов автоматически собирает журнал запросов, планов и статистики выполнения, сохраняя эти данные для просмотра. Данные разделяются по временным диапазонам, благодаря чему вы можете просматривать закономерности использования и узнавать об изменениях плана запроса на сервере. Хранилище запросов можно настроить с помощью инструкции [ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md) . 
  
 Сведения о работе с хранилищем запросов в Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)] см. в разделе [Работа с хранилищем запросов в Базе данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-operate-query-store/).  
 
> [!IMPORTANT]
> Если вы используете хранилище запросов для JIT-анализа рабочих нагрузок в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], запланируйте установку исправлений масштабируемости производительности (см. [статью базы знаний 4340759](https://support.microsoft.com/help/4340759)) как можно скорее. 
  
##  <a name="Enabling"></a> Включение хранилища запросов  
 Хранилище запросов неактивно для новых баз данных по умолчанию.  
  
#### <a name="use-the-query-store-page-in-includessmanstudiofullincludesssmanstudiofull-mdmd"></a>Использование страницы "Хранилище запросов" в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши базу данных и выберите пункт **Свойства**.  
  
    > [!NOTE]  
    > Требуется [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] версии не ниже 16.  
  
2.  В диалоговом окне **Свойства базы данных** перейдите на страницу **Хранилище запросов** .  
  
3.  В поле **Режим работы (запрошенный)** выберите значение **Вкл**.  
  
#### <a name="use-transact-sql-statements"></a>Использование инструкций Transact-SQL  
  
Используйте инструкцию **ALTER DATABASE** , чтобы включить хранилище запросов. Пример:  
  
```sql  
ALTER DATABASE AdventureWorks2012 SET QUERY_STORE = ON;  
```  
  
Другие параметры синтаксиса, связанные с хранилищем запросов, см. в разделе [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
> [!NOTE]  
> Нельзя включить хранилище запросов для базы данных **master** или **tempdb** .  
 
> [!IMPORTANT]
> Дополнительные сведения о включении хранилища запросов и настройке в соответствии с требованиями рабочей нагрузки см. в [рекомендациях по использованию хранилища запросов](../../relational-databases/performance/best-practice-with-the-query-store.md#Configure).
 
## <a name="About"></a> Сведения о хранилище запросов  
 Планы выполнения для любого специального запроса в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно меняются со временем по разным причинам, например из-за изменения статистики, схемы, создания и удаления индексов и т. д. В кэше процедур (где хранятся кэшированные планы запросов) хранится только последний план выполнения. Планы исключаются из кэша планов из-за нехватки памяти. В результате устранение проблем со снижением производительности запросов, вызванным изменениями планов выполнения, может оказаться сложным и требующим много времени.  
  
 Так как хранилище запросов сохраняет несколько планов выполнения на запрос, оно может принудительно применить политики, чтобы заставить процессор запросов использовать конкретный план выполнения для запроса. Это называется принудительным выполнением плана. Принудительное выполнение плана в хранилище запросов обеспечивается с использованием механизма, аналогичного указанию запроса [USE PLAN](../../t-sql/queries/hints-transact-sql-query.md) , но не требует изменений в приложениях пользователей. Принудительное выполнение плана может решить проблему со снижением производительности запросов, вызванным изменением плана за очень короткий период времени.  

> [!NOTE]
> Хранилище запросов собирает планы для инструкций DML, в частности для SELECT, INSERT, UPDATE, DELETE, MERGE и BULK INSERT.

 **Статистика ожидания** является другим источником сведений, помогающим устранять неполадки с производительностью в SQL Server. Довольно долго статистика ожидания была доступна только на уровне экземпляра, что затрудняло обратное отслеживание до фактического запроса. В SQL Server 2017 и базе данных SQL Azure мы добавили в хранилище запросов еще одно измерение, отслеживающее статистику ожидания. 

 Ниже перечислены стандартные сценарии использования хранилища запросов.  
  
-   Быстрый поиск и устранение снижения производительности планов путем принудительного выполнения предыдущего плана запроса. Исправление запросов, производительность которых была недавно снижена из-за изменений в планах выполнения.  
-   Определение количества выполнений запросов за заданный период времени и помощь DBA в устранении неполадок с производительностью ресурсов.  
-   Определение первых *n* запросов (по времени выполнения, потреблению памяти и т. д.) за последние *x* часов.  
-   Аудит журнала планов запросов для указанного запроса.  
-   Анализ шаблонов использования ресурсов (ЦП, операций ввода-вывода и памяти) для определенной базы данных.  
-   Определение первых n-запросов, ожидающих ресурсы. 
-   Понимание характера ожидания для определенного запроса или плана.
  
Хранилище запросов содержит три хранилища:
- **хранилище планов** для сохранения сведений о планах выполнения;     
- **хранилище статистики времени выполнения** для сохранения статистических сведений о выполнении;    
- **хранилище статистики ожидания** для сохранения статистических сведений об ожидании.     
 
Количество уникальных планов, которые можно сохранить для запроса в хранилище планов, ограничено параметром конфигурации **max_plans_per_query** . Для повышения производительности сведения записываются в хранилища асинхронно. Для уменьшения использования свободного места статистические данные времени выполнения в хранилище вычисляются для фиксированного интервала времени. Сведения в этих хранилищах видны при запросе представлений каталога в хранилище запросов.  
  
Следующий запрос возвращает сведения о запросах и планах в хранилище запросов.  
  
```sql  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
INNER JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
INNER JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
 
##  <a name="Regressed"></a> Использование функции "Регрессионные запросы"  
Включив хранилище запросов, обновите информацию о базе данных на панели обозревателя объектов, чтобы добавить раздел **Хранилище запросов** .  
  
![Дерево хранилища запросов SQL Server 2016 в обозревателе объектов SSMS](../../relational-databases/performance/media/objectexplorerquerystore.PNG "Дерево хранилища запросов SQL Server 2016 в обозревателе объектов SSMS")![Дерево хранилища запросов SQL Server 2017 в обозревателе объектов SSMS](../../relational-databases/performance/media/objectexplorerquerystore_sql17.PNG "Дерево хранилища запросов SQL Server 2017 в обозревателе объектов SSMS") 
  
Выберите пункт **Запросы со сниженной производительностью** , чтобы открыть панель **Запросы со сниженной производительностью** в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. На панели "Запросы со сниженной производительностью" отображаются запросы и планы, сохраненные в хранилище запросов. Воспользуйтесь полями раскрывающегося меню в верхней части, чтобы отфильтровать запросы по различным критериям: **длительность (мс)** (по умолчанию), время ЦП (мс), логические операции чтения (КБ), логические операции записи (КБ), физические операции чтения (КБ), время CLR (мс), DOP, потребление памяти (КБ), количество строк, используемая память журнала (КБ), использование памяти временной БД (КБ), время ожидания (мс).  
Выберите план для просмотра графического плана запросов. Воспользуйтесь соответствующими кнопками, чтобы просмотреть исходный запрос, принудительно выполнить и отменить выполнение плана запроса, переключиться между форматами сетки и диаграммы, сравнить выбранные планы (если выбрано несколько) и обновить экран.  
  
![Регрессивные запросы SQL Server 2016 в обозревателе объектов SSMS](../../relational-databases/performance/media/objectexplorerregressedqueries.PNG "Регрессивные запросы SQL Server 2016 в обозревателе объектов SSMS")  
  
Чтобы принудительно выполнить план, выберите запрос и план, а затем щелкните **Принудительно выполнить план**. Принудительно выполнять можно только те планы, которые были сохранены с помощью функции плана запросов и все еще хранятся в кэше плана запросов.

##  <a name="Waiting"></a> Поиск запросов ожидания

Начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CTP 2.0 и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], в хранилище запросов доступна статистика ожидания каждого запроса. Типы ожидания в хранилище запросов объединены в **категории ожидания**. Сопоставление категорий ожидания с типами ожидания доступно в [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md#wait-categories-mapping-table).

Выберите **Статистика ожидания запросов**, чтобы открыть панель **Статистика ожидания запросов** в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] v18 или более поздней версии. Панель статистики ожидания запросов показывает диаграмму с главными категориями ожидания в хранилище запросов. Воспользуйтесь раскрывающимся меню в верхней части, чтобы выбрать критерий для времени ожидания: среднее, максимальное, минимальное, стандартное отклонение и **общее** (по умолчанию).

 ![Статистика ожидания запросов SQL Server 2017 в обозревателе объектов SSMS](../../relational-databases/performance/media/query-store-waits.PNG "Статистика ожидания запросов SQL Server 2017 в обозревателе объектов SSMS")

Выберите категорию ожидания, нажав на диаграмму, и откроется подробное представление для выбранной категории ожидания. На новой диаграмме будут отображаться запросы, входящие в эту категорию ожидания. 
  
 ![Подробное представление статистики ожидания запросов SQL Server 2017 в обозревателе объектов SSMS](../../relational-databases/performance/media/query-store-waits-detail.PNG "Подробное представление статистики ожидания запросов SQL Server 2017 в обозревателе объектов SSMS")

Воспользуйтесь раскрывающимся меню в верхней части для фильтрации запросов по различным критериям времени ожидания для выбранной категории: среднее, максимальное, минимальное, стандартное отклонение и **общее** (по умолчанию). Выберите план для просмотра графического плана запросов. С помощью кнопок можно просмотреть исходный запрос, принудительно применить и отменить план запросов, а также обновить отображаемые на экране сведения.  

**Категории ожидания** объединяют разные типы ожидания в контейнеры схожего характера. В разных категориях ожидания требуются разные виды последующего анализа для устранения проблемы, но типы ожидания из одной категории имеют очень схожие процедуры устранения неполадок. Определение затронутого запроса с наибольшим уровнем ожидания позволит успешно завершать подобные расследования.

Ниже приведено несколько примеров того, как можно получить дополнительные аналитические сведения о рабочей нагрузке до и после введения категорий ожидания в хранилище запросов.

|||| 
|-|-|-|  
|Предыдущая процедура|Новая процедура|Действие|
|Высокий уровень ожиданий RESOURCE_SEMAPHORE на базу данных|Высокий уровень ожиданий памяти в хранилище запросов для конкретных запросов|Найдите в хранилище запросов те запросы, которые используют больше всего памяти. Вероятнее всего, эти запросы препятствуют дальнейшей обработке затронутых запросов. Рекомендуется использовать указание запроса MAX_GRANT_PERCENT для этих запросов или затронутых запросов.|
|Высокий уровень ожиданий LCK_M_X на базу данных|Высокий уровень ожиданий блокировки в хранилище запросов для конкретных запросов|Проверьте текст затронутых запросов и выявите целевые сущности. Найдите в хранилище запросов другие запросы, изменяющие ту же сущность, которые часто выполняются и (или) имеют большую длительность. Найдя такие запросы, рекомендуется изменить логику приложения, чтобы улучшить параллелизм, или использовать менее строгий уровень изоляции.|
|Высокий уровень ожиданий PAGEIOLATCH_SH на базу данных|Высокий уровень ожиданий ввода-вывода буфера в хранилище запросов для конкретных запросов|Найдите в хранилище запросов запросы с большим числом физических операций чтения. Если они соответствуют запросам с высоким уровнем ожиданий ввода-вывода, рекомендуется ввести индекс для базовой сущности, чтобы выполнять поиск вместо сканирования и этим минимизировать временные затраты ввода-вывода для запросов.|
|Высокий уровень ожиданий SOS_SCHEDULER_YIELD на базу данных|Высокий уровень ожиданий ЦП в хранилище запросов для конкретных запросов|Найдите в хранилище запросов те запросы, которые используют больше всего ресурсов ЦП. Выявите те из них, у которых высокое использование ЦП коррелирует с высоким уровнем ожидания ЦП для затронутых запросов. Уделите внимание оптимизации запросов — может иметь место регрессия плана или отсутствующий индекс.|

##  <a name="Options"></a> Параметры конфигурации 
Для настройки хранилища запросов доступны следующие параметры.

*OPERATION_MODE*  
Может быть равен **READ_WRITE** (по умолчанию) или READ_ONLY.  
  
*CLEANUP_POLICY (STALE_QUERY_THRESHOLD_DAYS)*  
Настройте аргумент `STALE_QUERY_THRESHOLD_DAYS`, чтобы указать длительность хранения данных в хранилище запросов в днях. Значение по умолчанию — 30. Для выпуска [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic Edition значение по умолчанию — **7** дней.
  
*DATA_FLUSH_INTERVAL_SECONDS*  
Определяет частоту, с которой данные, записанные в хранилище запросов, сохраняются на диск. Для оптимизации производительности данные, собранные хранилищем запросов, асинхронно записываются на диск. Частота, с которой происходит эта асинхронная передача, настраивается с помощью `DATA_FLUSH_INTERVAL_SECONDS`. Значение по умолчанию ― **900** (15 минут).  
  
*MAX_STORAGE_SIZE_MB*  
Настраивает максимальный размер хранилища запросов. Если данные в хранилище запросов достигают размера `MAX_STORAGE_SIZE_MB`, хранилище запроса автоматически изменяет состояние с "Чтение и запись" на "Только чтение" и останавливает сбор новых данных.  Значение по умолчанию — 100 МБ. Для выпуска [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition значение по умолчанию — **1 ГБ**, а для выпуска [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic Edition — **10 МБ**.
  
*INTERVAL_LENGTH_MINUTES*  
Определяет временной интервал вычисления статистических данных о среде выполнения в хранилище запросов. Для оптимизации использования свободного места статистические данные времени выполнения в хранилище вычисляются для фиксированного интервала времени. Этот интервал настраивается с помощью параметра `INTERVAL_LENGTH_MINUTES`. Значение по умолчанию — **60**. 
  
*SIZE_BASED_CLEANUP_MODE*  
Определяет, будет ли автоматически активирована очистка, когда общий объем данных приблизится к верхней границе ограничения. Может иметь значение **AUTO** (по умолчанию) или OFF.  
  
*QUERY_CAPTURE_MODE*  
Определяет запросы, собираемые в хранилище запросов (все запросы или только важные запросы), основываясь на показателях выполнения и потребления ресурсов; определяет отслеживание текущих запросов без добавления новых. Может иметь значение **ALL** (регистрировать все запросы), AUTO (игнорировать редкие запросы и запросы с малой продолжительностью компиляции и выполнения) или NONE (остановить регистрацию новых запросов). Значение по умолчанию для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) — ALL, а для Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)] — AUTO.
  
*MAX_PLANS_PER_QUERY*  
Целое число, представляющее максимальное количество поддерживаемых планов для каждого запроса. Значение по умолчанию — **200**.  
 
*WAIT_STATS_CAPTURE_MODE*  
Определяет, будет ли хранилище запросов перехватывать данные статистики ожидания. Может иметь значение OFF или **ON** (по умолчанию).  
 
Запросите представление **sys.database_query_store_options** , чтобы определить текущие параметры хранилища запросов. В представлении [sys.database_query_store_options](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md) можно посмотреть о значениях дополнительные сведения.  
  
Дополнительные сведения о настройке параметров с помощью инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в разделе [Управление параметрами](#OptionMgmt).  
  
## <a name="Related"></a> Связанные представления, функции и процедуры  
 Просматривать хранилище запросов и управлять им можно с помощью [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] или следующих представлений и процедур.  

### <a name="query-store-functions"></a>Функции хранилища запросов  
 Функции помогают работать с хранилищем запросов. 
 
||| 
|-|-|  
|[sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL)](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)|| 
  
### <a name="query-store-catalog-views"></a>Представления каталога хранилища запросов  
 В представлениях каталога отображаются сведения о хранилище запросов.  

||| 
|-|-|  
|[sys.database_query_store_options (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)|[sys.query_context_settings (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)|  
|[sys.query_store_plan (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)|[sys.query_store_query (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)|  
|[sys.query_store_query_text (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)|[sys.query_store_runtime_stats (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)|  
|[sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)|[sys.query_store_runtime_stats_interval (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)|  
  
### <a name="query-store-stored-procedures"></a>Хранимые процедуры в хранилище запросов,  
 Хранимые процедуры служат для настройки хранилища запросов.  

||| 
|-|-|  
|[sp_query_store_flush_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)|[sp_query_store_reset_exec_stats (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)|  
|[sp_query_store_force_plan (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)|[sp_query_store_unforce_plan (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)|  
|[sp_query_store_remove_plan (Transct-SQL)](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)|[sp_query_store_remove_query (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)|  
 
##  <a name="Scenarios"></a> Основные сценарии использования  
  
###  <a name="OptionMgmt"></a> Управление параметрами  
 В этом разделе представлены некоторые рекомендации по управлению самой функцией хранилища запросов.  
  
 **Активно ли сейчас хранилище запросов?**  
  
 Данные в хранилище запросов содержатся в базе данных пользователя, поэтому их размер ограничен (настраивается с помощью `MAX_STORAGE_SIZE_MB`). Если размер данных в хранилище запросов достигнет предела, хранилище запросов автоматически изменит состояние с read-write на read-only и перестанет собирать новые данные.  
  
 Выполните запрос [sys.database_query_store_options](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md), чтобы определить, активно ли хранилище запросов, и узнать, собирается ли сейчас статистика среды выполнения.  
  
```sql  
SELECT actual_state, actual_state_desc, readonly_reason,   
    current_storage_size_mb, max_storage_size_mb  
FROM sys.database_query_store_options;  
```  
  
 Состояние хранилища запросов определяется в столбце actual_state. Если состояние не соответствует требуемому, дополнительные сведения можно просмотреть в столбце `readonly_reason`.   
Если размер хранилища запросов превышает квоту, хранилище переходит в режим "только чтение" (read_only).  
  
 **Получение параметров запросов**  
  
 Чтобы найти подробные сведения о состоянии хранилища запросов, выполните следующую команду в базе данных пользователя.  
  
```sql  
SELECT * FROM sys.database_query_store_options;  
```  
  
 **Задание интервала для хранилища запросов**  
  
 Вы можете переопределить интервал для объединения статистики времени выполнения запросов (по умолчанию — 60 минут).  
  
```sql  
ALTER DATABASE <database_name>   
SET QUERY_STORE (INTERVAL_LENGTH_MINUTES = 15);  
```  
  
 > [!NOTE]
 > Для параметра "`INTERVAL_LENGTH_MINUTES`" запрещены целочисленные значения. Используйте одно из следующих значений: 1, 5, 10, 15, 30, 60 или 1440 минут.  
  
 Новое значение интервала находится в представлении **sys.database_query_store_options** .  
  
 **Использование пространства в хранилище запросов**  
  
 Чтобы проверить текущий размер хранилища запросов и установленное ограничение, выполните следующую инструкцию в пользовательской базе данных.  
  
```sql  
SELECT current_storage_size_mb, max_storage_size_mb   
FROM sys.database_query_store_options;  
```  
  
 Если хранилище запросов заполнено, используйте следующую инструкцию для его расширения.  
  
```sql  
ALTER DATABASE <database_name>   
SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <new_size>);  
```  
  
 **Задание всех параметров для хранилища запросов**  
  
 Вы можете задать несколько параметров хранилища запросов одновременно с помощью одной инструкции ALTER DATABASE.  
  
```sql  
ALTER DATABASE <database name>   
SET QUERY_STORE (  
    OPERATION_MODE = READ_WRITE,  
    CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 30),  
    DATA_FLUSH_INTERVAL_SECONDS = 3000,  
    MAX_STORAGE_SIZE_MB = 500,  
    INTERVAL_LENGTH_MINUTES = 15,  
    SIZE_BASED_CLEANUP_MODE = AUTO,  
    QUERY_CAPTURE_MODE = AUTO,  
    MAX_PLANS_PER_QUERY = 1000,
    WAIT_STATS_CAPTURE_MODE = ON 
);  
```  
  
 **Очистка пространства**  
  
 Внутренние таблицы хранилища запросов создаются в группе файлов PRIMARY во время создания базы данных, и эту конфигурацию невозможно изменить позже. Если у вас заканчивается место, следует удалить более старые данные из хранилища запросов с помощью следующей инструкции.  
  
```sql  
ALTER DATABASE <db_name> SET QUERY_STORE CLEAR;  
```  
  
 Кроме того, можно очистить только данные ad-hoc-запросов, так как они менее актуальны для оптимизации запросов и анализа планов, но занимают столько же места.  
  
 **Удаление нерегламентированных запросов** . Эта функция удаляет запросы, которые были выполнены только один раз более 24 часов назад.  
  
```sql  
DECLARE @id int  
DECLARE adhoc_queries_cursor CURSOR   
FOR   
SELECT q.query_id  
FROM sys.query_store_query_text AS qt  
JOIN sys.query_store_query AS q   
    ON q.query_text_id = qt.query_text_id  
JOIN sys.query_store_plan AS p   
    ON p.query_id = q.query_id  
JOIN sys.query_store_runtime_stats AS rs   
    ON rs.plan_id = p.plan_id  
GROUP BY q.query_id  
HAVING SUM(rs.count_executions) < 2   
AND MAX(rs.last_execution_time) < DATEADD (hour, -24, GETUTCDATE())  
ORDER BY q.query_id ;  
  
OPEN adhoc_queries_cursor ;  
FETCH NEXT FROM adhoc_queries_cursor INTO @id;  
WHILE @@fetch_status = 0  
    BEGIN   
        PRINT @id  
        EXEC sp_query_store_remove_query @id  
        FETCH NEXT FROM adhoc_queries_cursor INTO @id  
    END   
CLOSE adhoc_queries_cursor ;  
DEALLOCATE adhoc_queries_cursor;  
```  
  
 Вы можете определить собственную процедуру с другой логикой для очистки данных, которые вам больше не нужны.  
  
 В примере выше используется расширенная хранимая процедура **sp_query_store_remove_query** для удаления ненужных данных. Также можно использовать следующие процедуры:  
  
-   **sp_query_store_reset_exec_stats** — чтобы удалить статистику времени выполнения для указанного плана;  
-   **sp_query_store_remove_plan** — чтобы удалить отдельный план.  
 
  
###  <a name="Peformance"></a> Аудит производительности и устранение проблем  
 Хранилище запросов ведет журнал компиляции и метрик выполнения во время выполнения запросов, что позволяет анализировать использование рабочей нагрузки.  
  
 **Последние *n* запросов, выполненных в базе данных.**  
  
```sql  
SELECT TOP 10 qt.query_sql_text, q.query_id,   
    qt.query_text_id, p.plan_id, rs.last_execution_time  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id  
ORDER BY rs.last_execution_time DESC;  
```  
  
 **Сколько раз выполнен каждый запрос?**  
  
```sql  
SELECT q.query_id, qt.query_text_id, qt.query_sql_text,   
    SUM(rs.count_executions) AS total_execution_count  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id  
GROUP BY q.query_id, qt.query_text_id, qt.query_sql_text  
ORDER BY total_execution_count DESC;  
```  
  
 **У скольких запросов самое высокое значение среднего времени выполнения за последний час?**  
  
```sql  
SELECT TOP 10 rs.avg_duration, qt.query_sql_text, q.query_id,  
    qt.query_text_id, p.plan_id, GETUTCDATE() AS CurrentUTCTime,   
    rs.last_execution_time   
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id  
WHERE rs.last_execution_time > DATEADD(hour, -1, GETUTCDATE())  
ORDER BY rs.avg_duration DESC;  
```  
  
 **У скольких запросов самое высокое значение среднего количества операций чтения среди физических операций ввода-вывода за последние 24 часа с соответствующим числом строк и выполнений?**  
  
```sql  
SELECT TOP 10 rs.avg_physical_io_reads, qt.query_sql_text,   
    q.query_id, qt.query_text_id, p.plan_id, rs.runtime_stats_id,   
    rsi.start_time, rsi.end_time, rs.avg_rowcount, rs.count_executions  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id   
JOIN sys.query_store_runtime_stats_interval AS rsi   
    ON rsi.runtime_stats_interval_id = rs.runtime_stats_interval_id  
WHERE rsi.start_time >= DATEADD(hour, -24, GETUTCDATE())   
ORDER BY rs.avg_physical_io_reads DESC;  
```  
  
 **У скольких запросов несколько планов?** Эти запросы особенно интересны, так как они являются кандидатами на снижение из-за изменения выбранного плана. Следующий запрос определяет данные запросы со всеми планами.  
  
```sql  
WITH Query_MultPlans  
AS  
(  
SELECT COUNT(*) AS cnt, q.query_id   
FROM sys.query_store_query_text AS qt  
JOIN sys.query_store_query AS q  
    ON qt.query_text_id = q.query_text_id  
JOIN sys.query_store_plan AS p  
    ON p.query_id = q.query_id  
GROUP BY q.query_id  
HAVING COUNT(distinct plan_id) > 1  
)  
  
SELECT q.query_id, object_name(object_id) AS ContainingObject,   
    query_sql_text, plan_id, p.query_plan AS plan_xml,  
    p.last_compile_start_time, p.last_execution_time  
FROM Query_MultPlans AS qm  
JOIN sys.query_store_query AS q  
    ON qm.query_id = q.query_id  
JOIN sys.query_store_plan AS p  
    ON q.query_id = p.query_id  
JOIN sys.query_store_query_text qt   
    ON qt.query_text_id = q.query_text_id  
ORDER BY query_id, plan_id;  
```  
  
 **У каких запросов недавно понизилась производительность (в сравнении с данными другой точки во времени)?** Следующий пример запроса возвращает все запросы, для которых время выполнения удвоилось за последние 48 часов из-за изменения выбранного плана. Запрос сравнивает все интервалы статистики времени выполнения.  
  
```sql  
SELECT   
    qt.query_sql_text,   
    q.query_id,   
    qt.query_text_id,   
    rs1.runtime_stats_id AS runtime_stats_id_1,  
    rsi1.start_time AS interval_1,   
    p1.plan_id AS plan_1,   
    rs1.avg_duration AS avg_duration_1,   
    rs2.avg_duration AS avg_duration_2,  
    p2.plan_id AS plan_2,   
    rsi2.start_time AS interval_2,   
    rs2.runtime_stats_id AS runtime_stats_id_2  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p1   
    ON q.query_id = p1.query_id   
JOIN sys.query_store_runtime_stats AS rs1   
    ON p1.plan_id = rs1.plan_id   
JOIN sys.query_store_runtime_stats_interval AS rsi1   
    ON rsi1.runtime_stats_interval_id = rs1.runtime_stats_interval_id   
JOIN sys.query_store_plan AS p2   
    ON q.query_id = p2.query_id   
JOIN sys.query_store_runtime_stats AS rs2   
    ON p2.plan_id = rs2.plan_id   
JOIN sys.query_store_runtime_stats_interval AS rsi2   
    ON rsi2.runtime_stats_interval_id = rs2.runtime_stats_interval_id  
WHERE rsi1.start_time > DATEADD(hour, -48, GETUTCDATE())   
    AND rsi2.start_time > rsi1.start_time   
    AND p1.plan_id <> p2.plan_id  
    AND rs2.avg_duration > 2*rs1.avg_duration  
ORDER BY q.query_id, rsi1.start_time, rsi2.start_time;  
```  
  
 Если вы хотите просмотреть производительность всех регрессий (а не только тех, которые связаны с изменением выбранного плана), удалите условие `AND p1.plan_id <> p2.plan_id` из предыдущего запроса.  

 **Какие запросы ожидают больше всего?**
Этот запрос возвращает 10 ведущих запросов, ожидающих больше всего. 
 
 ```sql 
  SELECT TOP 10
    qt.query_text_id,
    q.query_id,
    p.plan_id,
    sum(total_query_wait_time_ms) AS sum_total_wait_ms
FROM sys.query_store_wait_stats ws
JOIN sys.query_store_plan p ON ws.plan_id = p.plan_id
JOIN sys.query_store_query q ON p.query_id = q.query_id
JOIN sys.query_store_query_text qt ON q.query_text_id = qt.query_text_id
GROUP BY qt.query_text_id, q.query_id, p.plan_id
ORDER BY sum_total_wait_ms DESC
 ```
 
 **У каких запросов недавно понизилась производительность (в недавних данных в сравнении с историческими)?** Следующий запрос сравнивает периоды выполнения на основе выполнения запросов. В этом примере запрос сравнивает статистику выполнения за последний период (1 час) и аналогичную статистику за более ранний период (последний день), чтобы определить запросы, которые привели к увеличению продолжительности рабочей нагрузки ( `additional_duration_workload`). Эти метрики подсчитываются путем умножения разницы между средним последним выполнением и средним выполнением по журналу на количество последних выполнений. Фактически они представляют количество последних выполнений с дополнительной длительностью по сравнению с журналом:  
  
```sql  
--- "Recent" workload - last 1 hour  
DECLARE @recent_start_time datetimeoffset;  
DECLARE @recent_end_time datetimeoffset;  
SET @recent_start_time = DATEADD(hour, -1, SYSUTCDATETIME());  
SET @recent_end_time = SYSUTCDATETIME();  
  
--- "History" workload  
DECLARE @history_start_time datetimeoffset;  
DECLARE @history_end_time datetimeoffset;  
SET @history_start_time = DATEADD(hour, -24, SYSUTCDATETIME());  
SET @history_end_time = SYSUTCDATETIME();  
  
WITH  
hist AS  
(  
    SELECT   
        p.query_id query_id,   
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration,   
        SUM(rs.count_executions) count_executions,  
        COUNT(distinct p.plan_id) num_plans   
     FROM sys.query_store_runtime_stats AS rs  
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id  
    WHERE  (rs.first_execution_time >= @history_start_time   
               AND rs.last_execution_time < @history_end_time)  
        OR (rs.first_execution_time <= @history_start_time   
               AND rs.last_execution_time > @history_start_time)  
        OR (rs.first_execution_time <= @history_end_time   
               AND rs.last_execution_time > @history_end_time)  
    GROUP BY p.query_id  
),  
recent AS  
(  
    SELECT   
        p.query_id query_id,   
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration,   
        SUM(rs.count_executions) count_executions,  
        COUNT(distinct p.plan_id) num_plans   
    FROM sys.query_store_runtime_stats AS rs  
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id  
    WHERE  (rs.first_execution_time >= @recent_start_time   
               AND rs.last_execution_time < @recent_end_time)  
        OR (rs.first_execution_time <= @recent_start_time   
               AND rs.last_execution_time > @recent_start_time)  
        OR (rs.first_execution_time <= @recent_end_time   
               AND rs.last_execution_time > @recent_end_time)  
    GROUP BY p.query_id  
)  
SELECT   
    results.query_id query_id,  
    results.query_text query_text,  
    results.additional_duration_workload additional_duration_workload,  
    results.total_duration_recent total_duration_recent,  
    results.total_duration_hist total_duration_hist,  
    ISNULL(results.count_executions_recent, 0) count_executions_recent,  
    ISNULL(results.count_executions_hist, 0) count_executions_hist   
FROM  
(  
    SELECT  
        hist.query_id query_id,  
        qt.query_sql_text query_text,  
        ROUND(CONVERT(float, recent.total_duration/  
                   recent.count_executions-hist.total_duration/hist.count_executions)  
               *(recent.count_executions), 2) AS additional_duration_workload,  
        ROUND(recent.total_duration, 2) total_duration_recent,   
        ROUND(hist.total_duration, 2) total_duration_hist,  
        recent.count_executions count_executions_recent,  
        hist.count_executions count_executions_hist     
    FROM hist   
        JOIN recent   
            ON hist.query_id = recent.query_id   
        JOIN sys.query_store_query AS q   
            ON q.query_id = hist.query_id  
        JOIN sys.query_store_query_text AS qt   
            ON q.query_text_id = qt.query_text_id      
) AS results  
WHERE additional_duration_workload > 0  
ORDER BY additional_duration_workload DESC  
OPTION (MERGE JOIN);  
```  
 
###  <a name="Stability"></a> Обеспечение стабильной производительности запросов  
Вы могли заметить, что для запросов, которые выполняются несколько раз, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует разные планы. Это приводит к изменению уровня потребления ресурсов и продолжительности выполнения. В хранилище запросов вы можете быстро узнать, когда произошло снижение производительности, а также определить оптимальный план за интересующий вас период. Затем вы можете принудительно выполнить этот оптимальный план для последующего выполнения запроса.  
  
Вы можете также определить несоответствующую производительность запросов для запроса с параметрами (заданными автоматически или вручную). Разнообразие планов позволяет выбрать такой план, который будет достаточно быстрым и эффективным для всех (или большинства) значений параметров. Принудительное выполнение такого плана обеспечит прогнозируемую производительность в самых разных пользовательских сценариях.  
  
 ### <a name="force-a-plan-for-a-query-apply-forcing-policy"></a>Принудительное применение плана запроса (применение политики принудительного выполнения).

Если план для определенного запроса выполняется принудительно, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается принудительно применить план в оптимизаторе. Если это не удастся сделать, будет порождено событие XEvent и оптимизация будет выполнена как обычно.

```sql  
EXEC sp_query_store_force_plan @query_id = 48, @plan_id = 49;  
```  
  
При использовании **sp_query_store_force_plan** можно принудительно выполнять только планы, записанные хранилищем запросов в качестве плана для этого запроса. Другими словами, доступные для запроса планы — это планы, которые уже использовались для выполнения этого запроса, когда хранилище запросов было активно.  
  
### <a name="remove-plan-forcing-for-a-query"></a>Отмена принудительного применения плана для запроса

Чтобы снова использовать оптимизатор запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для вычисления оптимального плана запросов, используйте **sp_query_store_unforce_plan** для отмены принудительного выполнения плана, выбранного для запроса.  
  
```sql  
EXEC sp_query_store_unforce_plan @query_id = 48, @plan_id = 49;  
```  
  
## <a name="see-also"></a>См. также:  
 [Рекомендации по хранилищу запросов](../../relational-databases/performance/best-practice-with-the-query-store.md)   
 [Использование хранилища запросов с выполняющейся в памяти OLTP](../../relational-databases/performance/using-the-query-store-with-in-memory-oltp.md)   
 [Сценарии использования хранилища запросов](../../relational-databases/performance/query-store-usage-scenarios.md)   
 [Сбор данных в хранилище запросов](../../relational-databases/performance/how-query-store-collects-data.md)   
 [Query Store Stored Procedures (Transact-SQL)](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  (Хранимые процедуры хранилища запросов (Transact-SQL))  
 [Query Store Catalog Views (Transact-SQL) ](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)  (Представления каталогов хранилища запросов (Transact-SQL))  
 [Monitor and Tune for Performance](../../relational-databases/performance/monitor-and-tune-for-performance.md)  (Мониторинг и настройка производительности)  
 [Средства контроля и настройки производительности](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)   
 [Открытие монитора активности (среда SQL Server Management Studio)](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)   
 [Динамическая статистика запросов](../../relational-databases/performance/live-query-statistics.md)   
 [Монитор активности](../../relational-databases/performance-monitor/activity-monitor.md)   
 [sys.database_query_store_options (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)  
 [Управление хранилищем запросов в базе данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-operate-query-store/) 
  
