---
title: Производительность сервера и мониторинг активности | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- activity monitoring [SQL Server]
- traces [SQL Server], how-to topics
- monitoring server performance [SQL Server], activity monitoring
- stored procedures [SQL Server], traces
- performance [SQL Server], servers
- servers [SQL Server], performance
- SQL Server Profiler, how-to topics
- SQL Server Management Studio [SQL Server], monitoring system
- Profiler [SQL Server Profiler], how-to topics
ms.assetid: f9abe48d-d6e9-4c38-a355-fc5eb5a95a25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 29f18956ef1cdaa85b186e610c1c915d45602126
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047846"
---
# <a name="server-performance-and-activity-monitoring"></a>Производительность сервера и мониторинг активности
  Наблюдение за базами данных выполняется с целью оценки производительности сервера. Эффективное наблюдение подразумевает регулярное создание моментальных снимков текущей производительности для обнаружения процессов, вызывающих неполадки, и постоянный сбор данных для отслеживания тенденций роста или изменения производительности. В состав [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и операционной системы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows входят программы, позволяющие следить за текущим состоянием базы данных и измерять производительность по мере изменения состояния.  
  
 Далее приведены разделы, объясняющие использование средств наблюдения за производительностью и активностью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Windows. Занятие содержит следующие разделы:  
  
## <a name="in-this-section"></a>В этом разделе  
 **Выполнение задач наблюдения с помощью средств Windows**  
  
-   [Запуск системного монитора (Windows)](start-system-monitor-windows.md)  
  
-   [Просмотр журнала приложений Windows (Windows)](view-the-windows-application-log-windows-10.md)  
  
 **Создание предупреждений базы данных SQL Server с помощью инструментов Windows**  
  
-   [Настройка оповещения базы данных SQL Server (Windows)](set-up-a-sql-server-database-alert-windows.md)  
  
 **Выполнение задач наблюдения в среде SQL Server Management Studio**  
  
-   [Просмотр журнала ошибок SQL Server (среда SQL Server Management Studio)](../../ssms/sql-server-management-studio-ssms.md)  
  
-   [Открытие монитора активности (среда SQL Server Management Studio)](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)  
  
 **Выполнение задач наблюдения с помощью трассировки SQL с использованием хранимых процедур Transact-SQL**  
  
-   [Создание трассировки (Transact-SQL)](../sql-trace/create-a-trace-transact-sql.md)  
  
-   [Создание фильтра трассировки (Transact-SQL)](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)  
  
-   [Изменение существующей трассировки (Transact-SQL)](../sql-trace/modify-an-existing-trace-transact-sql.md)  
  
-   [Просмотр сохраненной трассировки (Transact-SQL)](../sql-trace/view-a-saved-trace-transact-sql.md)  
  
-   [Просмотр сведений фильтров (Transact-SQL)](../sql-trace/view-filter-information-transact-sql.md)  
  
-   [Удаление трассировки (Transact-SQL)](../sql-trace/delete-a-trace-transact-sql.md)  
  
 **Создание и изменения трассировок с помощью приложения SQL Server Profiler**  
  
-   [Создание трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
-   [Настройка глобальных параметров трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)  
  
-   [Указание столбцов событий и данных для файла трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
-   [Создание скрипта Transact-SQL для выполнения трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)  
  
-   [Сохранение результатов трассировки в файл (приложение SQL Server Profiler)](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
-   [Установка максимального размера для файла трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
-   [Сохранение результатов трассировки в таблицу (SQL Server Profiler)](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)  
  
-   [Установка максимального размера для таблицы трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
-   [Фильтрация событий в трассировке (приложение SQL Server Profiler)](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
-   [Просмотр сведений о фильтре (приложение SQL Server Profiler)](../../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)  
  
-   [Изменение фильтра (приложение SQL Server Profiler)](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)  
  
-   [Фильтрация событий по времени начала (SQL Server Profiler)](../../tools/sql-server-profiler/filter-events-based-on-the-event-start-time-sql-server-profiler.md)  
  
-   [Фильтрация событий по времени окончания (SQL Server Profiler)](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
-   [Фильтрация идентификаторов серверных процессов (SPID) в трассировке (приложение SQL Server Profiler)](../../tools/sql-server-profiler/filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)  
  
-   [Упорядочивание столбцов, отображаемых в трассировке (приложение SQL Server Profiler)](../../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)  
  
 **Запуск, приостановка и полная остановка трассировок с помощью приложения SQL Server Profiler**  
  
-   [Автоматический запуск трассировки после соединения с сервером (приложение SQL Server Profiler)](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)  
  
-   [Приостановка трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)  
  
-   [Остановка трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)  
  
-   [Проведение трассировки после паузы или остановки (SQL Server Profiler)](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
 **Открытие трассировок и конфигурации их отображения с помощью приложения SQL Server Profiler**  
  
-   [Открыть файл трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)  
  
-   [Открыть таблицу трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
-   [Очистка окна трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)  
  
-   [Закрытие окна трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/close-a-trace-window-sql-server-profiler.md)  
  
-   [Установка значений по умолчанию для определения трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)  
  
-   [Настройка параметров отображения трассировки по умолчанию (приложение SQL Server Profiler)](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 **Воспроизведение трассировок с помощью приложения SQL Server Profiler**  
  
-   [Воспроизведение файла трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)  
  
-   [Воспроизведение таблицы трассировки (SQL Server Profiler)](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)  
  
-   [Воспроизведение одиночного события за раз (приложение SQL Server Profiler)](../../tools/sql-server-profiler/replay-a-single-event-at-a-time-sql-server-profiler.md)  
  
-   [Воспроизведение нагрузки до точки останова (приложение SQL Server Profiler)](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)  
  
-   [Воспроизведение нагрузки до курсора (приложение SQL Server Profiler)](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)  
  
-   [Воспроизведение скрипта на языке Transact-SQL (приложение SQL Server Profiler)](../../tools/sql-server-profiler/replay-a-transact-sql-script-sql-server-profiler.md)  
  
 **Создание, изменение и использование шаблонов трассировок с помощью приложения SQL Server Profiler**  
  
-   [Создание шаблона трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)  
  
-   [Изменение шаблона трассировки (приложение SQL Server Profiler)](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
-   [Извлечь шаблон из выполняемой трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)  
  
-   [Извлечь шаблон из файла трассировки или таблицы трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)  
  
-   [Экспорт шаблона трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/export-a-trace-template-sql-server-profiler.md)  
  
-   [Импорт шаблона трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/import-a-trace-template-sql-server-profiler.md)  
  
 **Использование приложения SQL Server Profiler с целью сбора данных о производительности сервера мониторинга**  
  
-   [Поиск значения или столбца данных во время трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)  
  
-   [Сохранение графов взаимоблокировок &#40;SQL Server Profiler&#41;](save-deadlock-graphs-sql-server-profiler.md)  
  
-   [Раздельное сохранение событий Showplan XML (приложение SQL Server Profiler)](save-showplan-xml-events-separately-sql-server-profiler.md)  
  
-   [Раздельное сохранение событий Showplan XML Statistics Profile (приложение SQL Server Profiler)](save-showplan-xml-statistics-profile-events-separately-sql-server-profiler.md)  
  
-   [Извлечение скрипта из трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/extract-a-script-from-a-trace-sql-server-profiler.md)  
  
-   [Сопоставить трассировку с данными журнала производительности Windows (приложение SQL Server Profiler)](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
