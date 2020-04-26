---
title: SQL Server Profiler | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- traces [SQL Server], SQL Server Profiler
- database monitoring [SQL Server], SQL Server Profiler
- tuning databases [SQL Server], SQL Server Profiler
- SQL Server Profiler
- server performance [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler]
- tracing [SQL Server]
- monitoring performance [SQL Server], SQL Server Profiler
- events [SQL Server], SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
- tools [SQL Server], SQL Server Profiler
- database performance [SQL Server], SQL Server Profiler
- trace [SQL Server]
ms.assetid: 3ad5f33d-559e-41a4-bde6-bb98792f7f1a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c9b0bb789dc7571a988c434f526070546d8db454
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211043"
---
# <a name="sql-server-profiler"></a>Приложение SQL Server Profiler
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] представляет собой развитый интерфейс, предназначенный для создания трассировок и управления ими, а также для анализа и воспроизведения результатов трассировок. События сохраняются в файле трассировки, который затем может быть проанализирован или использован для воспроизведения определенных последовательностей шагов для выявления возникших проблем.  
  
> [!IMPORTANT]  
>  Мы объявляем об устаревании в [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для [!INCLUDE[ssDE](../../includes/ssde-md.md)] захвата трассировки и воспроизведения трассировки. Эти функции будут поддерживаться в следующей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], однако будут удалены в более поздней версии. (с какой именно версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пока не определено). Пространство имен *Microsoft.SqlServer.Management.Trace* , которое содержит объекты трассировки Microsoft SQL Server и Replay, будет также устаревшим. Обратите внимание, что [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для рабочей нагрузки служб Analysis Services не устарел и будет по-прежнему поддерживаться.  
>   
>  В следующей таблице показаны компоненты, с помощью которых мы рекомендуем выполнять захват и воспроизведение данных трассировки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
||||  
|-|-|-|  
|**Функция\Целевая рабочая нагрузка**|**Реляционный механизм**|**Службы Analysis Services**|  
|**Захват трассировки**|Графический пользовательский интерфейс расширенных событий в среде SQL Server Management Studio|Приложение SQL Server Profiler|  
|**Воспроизведение трассировки**|Распределенное воспроизведение|Приложение SQL Server Profiler|  
  
## <a name="benefits-of-sql-server-profiler"></a>Преимущества приложения SQL Server Profiler  
 Приложение Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] — это графический пользовательский интерфейс для трассировки SQL, с помощью которого можно наблюдать за экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] или службами Analysis Services. Приложение позволяет собирать и сохранять данные о каждом событии в файле или в таблице для последующего анализа. Например, с помощью приложения можно следить за производственной средой, чтобы определить, какие хранимые процедуры снижают производительность из-за того, что выполняются слишком медленно. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] используется для таких действий, как:  
  
-   пошаговое выполнение проблемных запросов для поиска источника проблемы;  
  
-   выявление и диагностика медленно работающих запросов;  
  
-   перехват серии инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , ведущих к проблеме. Сохраненную трассировку затем можно использовать для моделирования и диагностики проблемы на тестовом сервере;  
  
-   контроль производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для настройки рабочих нагрузок. Дополнительные сведения о настройке физической структуры базы данных для рабочих нагрузок см. в разделе [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).  
  
-   Анализ счетчиков производительности для диагностики проблем.  
  
 Приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] поддерживает также аудит действий, выполняемых в экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В ходе аудита ведется запись действий, связанных с безопасностью, для дальнейшего просмотра администратором безопасности.  
  
## <a name="sql-server-profiler-concepts"></a>Основные понятия приложения SQL Server Profiler  
 Для использования [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]необходимо понимать термины, описывающие работу данного средства.  
  
> [!NOTE]  
>  При работе с приложением [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]полезно иметь представление о трассировке SQL. Дополнительные сведения см. в статье [SQL Trace](../../relational-databases/sql-trace/sql-trace.md).  
  
 **Событие**  
 Событие — это действие экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Примеры:  
  
-   подключения пользователей, сбои, отключения;  
  
-   инструкции Transact-SQL SELECT, INSERT, UPDATE и DELETE;  
  
-   состояние пакетов вызова удаленных процедур (RPC);  
  
-   запуск или завершение хранимой процедуры;  
  
-   инструкции запуска или завершения в хранимых процедурах;  
  
-   запуск или завершение пакета SQL;  
  
-   запись ошибки в журнал [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   получение блокировки или освобождение объекта базы данных;  
  
-   открытый курсор;  
  
-   проверки права доступа.  
  
 Все данные, создаваемые событием, отображаются в трассировке одной строкой. Эта строка пересекается столбцами данных, подробно описывающими данное событие.  
  
 **EventClass**  
 Класс событий — это тип трассируемого события. Класс событий содержит все данные, которые может сообщить событие. Примеры классов событий:  
  
-   **SQL:BatchCompleted**  
  
-   **Аудит входа в систему**  
  
-   **Аудит выхода из системы**  
  
-   **Lock:Acquired**  
  
-   **Lock:Released**  
  
 **EventCategory**  
 Категория событий определяет способы группировки событий в [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Например, все классы событий блокировок группируются в категории событий **Блокировки** . Однако категории событий существуют только в [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Этот термин не отображает способ группировки событий ядра.  
  
 **DataColumn**  
 Столбец данных — это атрибут классов событий, захваченных при трассировке. Поскольку класс событий определяет тип собираемых данных, не все столбцы данных применимы ко всем классам событий. Например, при трассировке, захватывающей класс событий **Lock:Acquired** , столбец данных **BinaryData** содержит значение идентификатора блокированной страницы или строки, а столбец данных **Integer Data** не содержит никаких значений, поскольку он неприменим к захватываемому классу событий.  
  
 **Шаблон**  
 Шаблон определяет конфигурацию трассировки по умолчанию. А именно, он включает классы событий, которые нужно контролировать в [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Например, можно создать шаблон, указывающий используемые события, столбцы данных и фильтры. Шаблоны не выполняются, а сохраняются в файлах с расширением TDF. После сохранения шаблон управляет захватом данных, если запускается трассировка, основанная на этом шаблоне.  
  
 **Трассировка**  
 Трассировка захватывает данные на основании выбранных классов событий, столбцов данных и фильтров. Например, можно создать трассировку для контроля ошибок исключений. Для этого выберите класс событий **Exception** и столбцы данных **Error**, **State**и **Severity** . Необходимо собирать данные этих трех столбцов, чтобы результаты трассировки содержали значимые данные. Теперь можно запустить трассировку, настроенную таким образом, и собирать данные обо всех событиях класса **Exception** на данном сервере. Данные трассировки можно сохранить или немедленно проанализировать. Трассировки можно воспроизводить впоследствии, хотя некоторые события, например класса **Исключение** , воспроизвести нельзя. Можно также сохранить трассировку как шаблон для построения аналогичных трассировок в будущем.  
  
 В SQL Server предусмотрено два способа трассировки экземпляра SQL Server: с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] или системных хранимых процедур.  
  
 **Filter**  
 При создании трассировки или шаблона можно определить критерии для фильтрации данных, собираемых событием. Чтобы трассировки не становились слишком большими, можно устанавливать фильтры, чтобы собирать только подмножества данных о событиях. Например, в трассировке можно указать определенные имена пользователей Microsoft Windows, тем самым уменьшив объем выходных данных.  
  
 Если фильтр не установлен, то на выход трассировки возвращаются все события выбранных классов событий.  
  
## <a name="sql-server-profiler-tasks"></a>Задачи приложения SQL Server Profiler  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Позволяет получить список предопределенных шаблонов, с помощью которых приложение SQL Server выполняет мониторинг событий определенных типов, а также список разрешений, используемых для воспроизведения трассировок.|[Шаблоны и разрешения приложения SQL Server Profiler](sql-server-profiler-templates-and-permissions.md)|  
|Содержит описание процесса запуска приложения SQL Server Profiler.|[Разрешения, необходимые для запуска приложения SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md)|  
|Содержит описание процесса создания трассировки.|[Создание трассировки (приложение SQL Server Profiler)](create-a-trace-sql-server-profiler.md)|  
|Содержит описание процесса указания определенных событий и столбцов данных для файла трассировки.|[Указание столбцов событий и данных для файла трассировки (приложение SQL Server Profiler)](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)|  
|Содержит описание процесса сохранения результатов трассировки в файл.|[Сохранение результатов трассировки в файл (приложение SQL Server Profiler)](save-trace-results-to-a-file-sql-server-profiler.md)|  
|Содержит описание процесса сохранения результатов трассировки в таблице.|[Сохранение результатов трассировки в таблицу (SQL Server Profiler)](save-trace-results-to-a-table-sql-server-profiler.md)|  
|Содержит описание процесса фильтрации событий в трассировке.|[Фильтрация событий в трассировке (приложение SQL Server Profiler)](filter-events-in-a-trace-sql-server-profiler.md)|  
|Содержит описание процесса просмотра сведений о фильтре.|[Просмотр сведений фильтров (приложение SQL Server Profiler)](view-filter-information-sql-server-profiler.md)|  
|Содержит описание процесса изменения фильтра.|[Изменение фильтра (приложение SQL Server Profiler)](modify-a-filter-sql-server-profiler.md)|  
|Содержит описание процесса установки максимального размера для файла трассировки (приложение SQL Server Profiler).|[Установка максимального размера для файла трассировки (приложение SQL Server Profiler)](set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)|  
|Содержит описание процесса установки максимального размера для таблицы трассировки.|[Установка максимального размера для таблицы трассировки (приложение SQL Server Profiler)](set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)|  
|Содержит описание процесса запуска трассировки.|[Запуск трассировки](start-a-trace.md)|  
|Содержит описание автоматического процесса запуска трассировки после соединения с сервером.|[Автоматически запустить трассировку после соединения с сервером (приложение SQL Server Profiler)](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)|  
|Содержит описание процесса фильтрации событий по времени начала события.|[Фильтрация событий по времени начала (SQL Server Profiler)](filter-events-based-on-the-event-start-time-sql-server-profiler.md)|  
|Содержит описание процесса фильтрации событий по времени окончания события.|[Фильтрация событий по времени окончания (SQL Server Profiler)](filter-events-based-on-the-event-end-time-sql-server-profiler.md)|  
|Содержит описание процесса фильтрации идентификаторов процесса сервера (SPID) в трассировке.|[Фильтрация идентификаторов серверных процессов (SPID) в трассировке (приложение SQL Server Profiler)](filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)|  
|Содержит описание процесса приостановки трассировки.|[Приостановка трассировки (приложение SQL Server Profiler)](pause-a-trace-sql-server-profiler.md)|  
|Содержит описание процесса прекращения трассировки.|[Остановка трассировки (приложение SQL Server Profiler)](stop-a-trace-sql-server-profiler.md)|  
|Содержит описание процесса запуска трассировки после ее приостановки или прекращения.|[Проведение трассировки после паузы или остановки (SQL Server Profiler)](run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)|  
|Содержит описание процесса очистки окна трассировки.|[Очистка окна трассировки (приложение SQL Server Profiler)](clear-a-trace-window-sql-server-profiler.md)|  
|Содержит описание процесса закрытия окна трассировки.|[Закрытие окна трассировки (приложение SQL Server Profiler)](close-a-trace-window-sql-server-profiler.md)|  
|Содержит описание процесса настройки трассировки по умолчанию.|[Установка значений по умолчанию для определения трассировки (приложение SQL Server Profiler)](set-trace-definition-defaults-sql-server-profiler.md)|  
|Содержит описание процесса настройки отображения трассировки по умолчанию.|[Настройка параметров отображения трассировки по умолчанию (приложение SQL Server Profiler)](set-trace-display-defaults-sql-server-profiler.md)|  
|Содержит описание процесса открытия файла трассировки.|[Открытие файла трассировки (приложение SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md)|  
|Содержит описание процесса открытия таблицы трассировки.|[Открытие таблицы трассировки (приложение SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md)|  
|Содержит описание процесса воспроизведения таблицы трассировки.|[Воспроизведение таблицы трассировки (SQL Server Profiler)](replay-a-trace-table-sql-server-profiler.md)|  
|Содержит описание процесса воспроизведения файла трассировки.|[Воспроизведение файла трассировки (приложение SQL Server Profiler)](replay-a-trace-file-sql-server-profiler.md)|  
|Содержит описание процесса воспроизведения одиночного события за раз.|[Воспроизведение одиночного события за раз (приложение SQL Server Profiler)](replay-a-single-event-at-a-time-sql-server-profiler.md)|  
|Содержит описание процесса воспроизведения до точки останова.|[Воспроизведение нагрузки до точки останова (приложение SQL Server Profiler)](replay-to-a-breakpoint-sql-server-profiler.md)|  
|Содержит описание процесса воспроизведения до курсора.|[Воспроизвести нагрузку до курсора (приложение SQL Server Profiler)](replay-to-a-cursor-sql-server-profiler.md)|  
|Содержит описание процесса воспроизведения скрипта Transact-SQL.|[Воспроизведение скрипта на языке Transact-SQL (приложение SQL Server Profiler)](replay-a-transact-sql-script-sql-server-profiler.md)|  
|Содержит описание процесса создания шаблона трассировки.|[Создание шаблона трассировки (приложение SQL Server Profiler)](create-a-trace-template-sql-server-profiler.md)|  
|Содержит описание процесса изменения шаблона трассировки.|[Изменение шаблона трассировки (приложение SQL Server Profiler)](../../database-engine/modify-a-trace-template-sql-server-profiler.md)|  
|Содержит описание процесса настройки глобальных параметров трассировки.|[Настройка глобальных параметров трассировки (приложение SQL Server Profiler)](set-global-trace-options-sql-server-profiler.md)|  
|Содержит описание процесса поиска значения или столбца данных во время трассировки.|[Поиск значения или столбца данных во время трассировки (приложение SQL Server Profiler)](find-a-value-or-data-column-while-tracing-sql-server-profiler.md)|  
|Содержит описание процесса создания шаблона на основе выполняемой трассировки.|[Извлечение шаблона из выполняемой трассировки (приложение SQL Server Profiler)](derive-a-template-from-a-running-trace-sql-server-profiler.md)|  
|Содержит описание процесса создания шаблона на основе файла или таблицы трассировки.|[Извлечение шаблона из файла трассировки или таблицы трассировки (приложение SQL Server Profiler)](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)|  
|Содержит описание процесса создания скрипта Transact-SQL на основе выполняемой трассировки.|[Создание скрипта Transact-SQL для выполнения трассировки (приложение SQL Server Profiler)](create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)|  
|Содержит описание процесса экспорта шаблона трассировки.|[Экспорт шаблона трассировки (приложение SQL Server Profiler)](export-a-trace-template-sql-server-profiler.md)|  
|Содержит описание процесса импорта шаблона трассировки.|[Импорт шаблона трассировки (приложение SQL Server Profiler)](import-a-trace-template-sql-server-profiler.md)|  
|Содержит описание процесса извлечения скрипта из трассировки.|[Извлечение скрипта из трассировки (приложение SQL Server Profiler)](extract-a-script-from-a-trace-sql-server-profiler.md)|  
|Содержит описание процесса согласования трассировки с данными журнала производительности Windows.|[Сопоставить трассировку с данными журнала производительности Windows (приложение SQL Server Profiler)](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)|  
|Содержит описание процесса упорядочения столбцов, отображаемых в трассировке.|[Упорядочивание столбцов, отображаемых в трассировке (приложение SQL Server Profiler)](organize-columns-displayed-in-a-trace-sql-server-profiler.md)|  
|Содержит описание процесса запуска приложения SQL Server Profiler.|[Запуск приложения SQL Server Profiler](start-sql-server-profiler.md)|  
|Содержит описание процесса сохранения трассировок и шаблонов трассировок.|[Сохранение трассировок и шаблонов трассировок](save-traces-and-trace-templates.md)|  
|Содержит описание процесса изменения шаблонов трассировок.|[Изменение шаблонов трассировки](modify-trace-templates.md)|  
|Содержит описание процесса согласования трассировки с данными журнала производительности Windows.|[Сопоставление трассировки с журналом производительности Windows](correlate-a-trace-with-windows-performance-log-data.md)|  
|Содержит описание процесса просмотра и анализа трассировок с помощью приложения SQL Server Profiler.|[Просмотр и анализ трассировок с помощью приложения SQL Server Profiler](view-and-analyze-traces-with-sql-server-profiler.md)|  
|Содержит описание процесса анализа взаимоблокировок с помощью приложения SQL Server Profiler.|[Анализ взаимоблокировок в приложении SQL Server Profiler](analyze-deadlocks-with-sql-server-profiler.md)|  
|Содержит описание процесса анализа запросов с помощью результатов инструкции SHOWPLAN в приложении SQL Server Profiler.|[Анализ запросов с помощью результатов инструкции SHOWPLAN в приложении SQL Server Profiler](analyze-queries-with-showplan-results-in-sql-server-profiler.md)|  
|Содержит описание процесса фильтрации трассировок с помощью приложения SQL Server Profiler.|[Фильтрация трассировок с помощью приложения SQL Server Profiler](filter-traces-with-sql-server-profiler.md)|  
|Содержит описание процесса использования возможностей воспроизведения приложения SQL Server Profiler.|[Воспроизведение трассировок](replay-traces.md)|  
|Позволяет получить список контекстной справки по разделам приложения SQL Server Profiler.|[Справка F1 приложения SQL Server Profiler](sql-server-profiler-f1-help.md)|  
|Позволяет получить список системных хранимых процедур, используемых [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для контроля производительности и активности.|[Хранимые процедуры приложения SQL Server Profiler (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)|  
  
## <a name="see-also"></a>См. также  
 [Категория событий locks](../../relational-databases/event-classes/locks-event-category.md)   
 [Категория событий Sessions](../../relational-databases/event-classes/sessions-event-category.md)   
 [Категория событий хранимых процедур](../../relational-databases/event-classes/stored-procedures-event-category.md)   
 [Категория событий TSQL](../../relational-databases/event-classes/tsql-event-category.md)   
 [Мониторинг производительности и действий сервера](../../relational-databases/performance/server-performance-and-activity-monitoring.md)  
  
  
