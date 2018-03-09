---
title: "Мониторинг и настройка производительности | Документация Майкрософт"
ms.custom: 
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instances of SQL Server, monitoring performance
- monitoring server performance [SQL Server]
- Database Engine [SQL Server], performance
- monitoring performance [SQL Server], about performance
- server performance [SQL Server]
- monitoring performance [SQL Server]
- database performance [SQL Server], about performance
- tuning databases [SQL Server], about performance
- status information [SQL Server], performance monitoring
- database monitoring [SQL Server], about performance
- monitoring [SQL Server], queries performance
- server performance [SQL Server], about performance
- tuning databases [SQL Server]
- database performance [SQL Server]
- monitoring [SQL Server], server performance
- database monitoring [SQL Server]
- monitoring server performance [SQL Server], about monitoring server performance
ms.assetid: 87f23f03-0f19-4b2e-bfae-efa378f7a0d4
caps.latest.revision: "35"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 32bb41096ecb83b0a1bd5b9cd51f406788419b4d
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="monitor-and-tune-for-performance"></a>Наблюдение и настройка производительности
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] Наблюдение за базами данных выполняется с целью оценки производительности сервера. Эффективное наблюдение подразумевает регулярное создание моментальных снимков текущей производительности для обнаружения процессов, вызывающих неполадки, и постоянный сбор данных для отслеживания тенденций роста или изменения производительности.  
  
 Постоянная оценка производительности базы данных помогает добиться оптимальной производительности путем минимизации времени ответа и максимального увеличения пропускной способности. Приблизительный сетевой трафик, дисковый ввод-вывод и загрузка ЦП — ключевые факторы, влияющие на производительность. Следует тщательно проанализировать требования приложения, понять логическую и физическую структуру данных, оценить использование базы данных и добиться компромисса между такими конфликтующими нагрузками, как оперативная обработка транзакций (OLTP) и поддержка решений.  
  
## <a name="monitoring-and-tuning-databases-for-performance"></a>Мониторинг и настройка производительности баз данных  
 В состав Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и операционной системы Microsoft Windows входят служебные программы, позволяющие следить за текущим состоянием базы данных и измерять производительность, если это состояние меняется. Для наблюдения за [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно использовать целый ряд средств и методик. Наблюдение за [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет решать следующие задачи:  
  
-   Определять возможности увеличения производительности. Например, выполняя мониторинг времени ответа для часто используемых запросов, можно определить, требуется ли изменить текст запроса или индексы таблицы.  
  
-   Оценивать активность пользователей. Например, выполняя мониторинг пользователей, которые подключаются к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно определить, правильно ли настроены параметры безопасности, и проверить работу приложений и систем разработки. Контролируя выполнение SQL-запросов, можно определить, правильно ли они написаны, и проверить результаты, которые они возвращают.  
  
-   Устранять проблемы или отлаживать компоненты приложений, например хранимые процедуры.  
  
## <a name="monitoring-in-a-dynamic-environment"></a>Мониторинг в динамической среде  
Изменение этих условий приведет к изменению производительности. По результатам оценки можно заметить изменения производительности при увеличении числа пользователей, изменении методов доступа пользователей и методов соединения, при увеличении объема содержимого базы данных, изменении клиентского приложения и данных в приложении, а также при усложнении запросов и увеличении объема сетевого трафика. С помощью средств контроля производительности можно связывать изменения отдельных показателей производительности с изменениями условий и сложных запросов. **Примеры**  
  
-   Отслеживая время отклика на часто используемые запросы, можно определить, нужно ли изменять запросы или индексы опрашиваемых таблиц.  
  
-   Отслеживая выполнение запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] можно определить правильность их написания, а также соответствие ожидаемым результатам.  
  
-   Отслеживая пользователей, пытающихся подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно проверить надежность защиты и протестировать приложения или системы разработки.  
  
 Время отклика — это время ожидания возврата пользователю первой строки результирующего набора в форме визуального подтверждения обработки запроса. Пропускная способность — это общее количество запросов, которые сервер может обработать за единицу времени.  
  
 С увеличением числа пользователей растет соперничество за ресурсы сервера, что в свою очередь увеличивает время ответа и уменьшает общую пропускную способность.  
  
## <a name="monitoring-and-performance-tuning-tasks"></a>Задачи наблюдения и настройки производительности  
  
|Раздел| Задача|  
|-----------|----------------------|  
|[Наблюдение за компонентами SQL Server](../../relational-databases/performance/monitor-sql-server-components.md)|Действия, необходимые для наблюдения за любым компонентом SQL Server.|  
|[Средства контроля и настройки производительности](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)|Список средств наблюдения и настройки, доступных в SQL Server.|  
|[Формирование базовых показателей производительности](../../relational-databases/performance/establish-a-performance-baseline.md)|Инструкции по формированию базовых показателей производительности.|  
|[Локализация проблем производительности](../../relational-databases/performance/isolate-performance-problems.md)|Локализация проблем производительности базы данных.|  
|[Выявление узких мест](../../relational-databases/performance/identify-bottlenecks.md)|Наблюдение за производительностью сервера и отслеживание его работы для выявления узких мест.|  
|[Мониторинг производительности и действий сервера](../../relational-databases/performance/server-performance-and-activity-monitoring.md)|Использование средств наблюдения за производительностью и активностью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Windows.|  
|[Отображение и сохранение планов выполнения](../../relational-databases/performance/display-and-save-execution-plans.md)|Вывод и сохранение планов выполнения в файле в формате XML.|  
|[Динамическая статистика запросов](../../relational-databases/performance/live-query-statistics.md)|Вывод статистических данных по этапам выполнения запроса в режиме реального времени.|  
|[Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)|Использование хранилища запросов для автоматической регистрации журнала запросов, планов и статистики выполнения и сохранение этих данных для просмотра.|  
|[Использование хранилища запросов с выполняющейся в памяти OLTP](../../relational-databases/performance/using-the-query-store-with-in-memory-oltp.md)|Соображения касательно оптимизированных для памяти таблиц.|  
|[Рекомендации по хранилищу запросов](../../relational-databases/performance/best-practice-with-the-query-store.md)|Рекомендации по использованию хранилища запросов.|  
  
## <a name="see-also"></a>См. также:  
 [Автоматизация администрирования в масштабах предприятия](http://msdn.microsoft.com/library/44d8365b-42bd-4955-b5b2-74a8a9f4a75f)   
 [помощник по настройке ядра СУБД](../../relational-databases/performance/database-engine-tuning-advisor.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
