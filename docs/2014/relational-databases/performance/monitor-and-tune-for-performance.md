---
title: Мониторинг и настройка производительности | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b9865d2c8c4427e72e26212417d1d11f73fc3291
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100398"
---
# <a name="monitor-and-tune-for-performance"></a>Наблюдение и настройка производительности
  Наблюдение за базами данных выполняется с целью оценки производительности сервера. Эффективное наблюдение подразумевает регулярное создание моментальных снимков текущей производительности для обнаружения процессов, вызывающих неполадки, и постоянный сбор данных для отслеживания тенденций роста или изменения производительности.  
  
 Постоянная оценка производительности базы данных помогает добиться оптимальной производительности путем минимизации времени ответа и максимального увеличения пропускной способности. Приблизительный сетевой трафик, дисковый ввод-вывод и загрузка ЦП — ключевые факторы, влияющие на производительность. Следует тщательно проанализировать требования приложения, понять логическую и физическую структуру данных, оценить использование базы данных и добиться компромисса между такими конфликтующими нагрузками, как оперативная обработка транзакций (OLTP) и поддержка решений.  
  
## <a name="benefits-of-monitoring-and-tuning-databases-for-performance"></a>Преимущества наблюдения и настройка баз данных для повышения производительности  
 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и операционной системы Microsoft Windows входят программы, позволяющие следить за текущим состоянием базы данных и измерять производительность по мере изменения условий. Существует множество средств и приемов, которые могут использоваться для наблюдения за [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поняв способы мониторинга [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно:  
  
-   Определять возможности увеличения производительности. Например, выполняя мониторинг времени ответа для часто используемых запросов, можно определить, требуется ли изменить текст запроса или индексы таблицы.  
  
-   Оценивать активность пользователей. Например, выполняя мониторинг пользователей, которые подключаются к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно определить, правильно ли настроены параметры безопасности, и проверить работу приложений и систем разработки. Контролируя выполнение SQL-запросов, можно определить, правильно ли они написаны, и проверить результаты, которые они возвращают.  
  
-   Устранять любые проблемы или отлаживать компоненты приложений, например хранимые процедуры.  
  
### <a name="monitoring-in-a-dynamic-environment"></a>Мониторинг в динамической среде  
 Важность мониторинга обусловлена динамикой среды, в которой выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Изменение этих условий приведет к изменению производительности. По результатам оценки можно заметить изменения производительности при увеличении числа пользователей, изменении методов доступа пользователей и методов соединения, при увеличении объема содержимого базы данных, изменении клиентского приложения и данных в приложении, а также при усложнении запросов и увеличении объема сетевого трафика. С помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средства для наблюдения за производительностью, можно связывать изменения отдельных показателей производительности с изменениями условий и сложных запросов. Ниже приведены примеры следующих сценариев:  
  
-   Отслеживая время отклика на часто используемые запросы, можно определить, нужно ли изменять запросы или индексы опрашиваемых таблиц.  
  
-   Отслеживая выполнение запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] можно определить правильность их написания, а также соответствие ожидаемым результатам.  
  
-   Отслеживая пользователей, пытающихся подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно проверить надежность защиты и протестировать приложения или системы разработки.  
  
 Время отклика — это время ожидания возврата пользователю первой строки результирующего набора в форме визуального подтверждения обработки запроса. Пропускная способность — это общее количество запросов, которые сервер может обработать за единицу времени.  
  
 С увеличением числа пользователей растет соперничество за ресурсы сервера, что в свою очередь увеличивает время ответа и уменьшает общую пропускную способность.  
  
## <a name="monitoring-and-tuning-performance-tasks"></a>Наблюдение за задачами производительности и их настройка  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|[Мониторинг компонентов SQL Server](monitor-sql-server-components.md)|Предоставляет шаги, необходимые для эффективного мониторинга компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Средства контроля и настройки производительности](performance-monitoring-and-tuning-tools.md)|Перечислены [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средства контроля и настройки.|  
|[Формирование базовых показателей производительности](establish-a-performance-baseline.md)|Содержит сведения о том, как создать базовый уровень производительности.|  
|[Локализация проблем производительности](isolate-performance-problems.md)|Описание способа изоляции проблем производительности базы данных.|  
|[Выявление узких мест](identify-bottlenecks.md)|Описание способов наблюдения за производительностью сервера и отслеживания его работы для выявления узких мест.|  
|[Мониторинг производительности и действий сервера](server-performance-and-activity-monitoring.md)|Описание способов использования средств наблюдения за производительностью и активностью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Windows.|  
|[Отображение и сохранение планов выполнения](display-and-save-execution-plans.md)|Описание способов отображения и сохранения планов выполнения в файле в формате XML.|  
|[Мониторинг производительности с использованием хранилища запросов](monitoring-performance-by-using-the-query-store.md)|Хранилище запросов автоматически захватывает журнал запросов, планы и статистику выполнения и сохраняет их для просмотра.|  
  
## <a name="see-also"></a>См. также  
 [Автоматизация администрирования в масштабах предприятия](../../ssms/agent/automated-administration-across-an-enterprise.md)   
 [помощник по настройке ядра СУБД](database-engine-tuning-advisor.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../performance-monitor/monitor-resource-usage-system-monitor.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  