---
title: Планы выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- query plans [SQL Server]
- execution plans [SQL Server]
- execution plan [SQL Server]
- query plan [SQL Server]
- query execution plans
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753f
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 81a9f0e52c061ec494143eb4f61158546f5e57f9
ms.sourcegitcommit: 58c25f47cfd701c61022a0adfc012e6afb9ce6e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2020
ms.locfileid: "78256952"
---
# <a name="execution-plans"></a>Планы выполнения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Чтобы иметь возможность выполнять запросы, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] должен анализировать инструкцию и определять наиболее эффективный способ доступа к необходимым данным. Этот анализ обрабатывается компонентом, который называется оптимизатором запросов. Входные данные оптимизатора запросов включают сам запрос, схему базы данных (определения таблиц и индексов) и статистику базы данных. Выходные данные оптимизатора запросов — это план выполнения запроса, который иногда называется планом запроса или выполнения.   

План выполнения запроса представляет собой определение следующего. 

- **Последовательности, в которой происходит обращение к исходным таблицам.**  
  Как правило, существует много последовательностей, в которых сервер базы данных может обращаться к базовым таблицам для построения результирующего набора. Например, если инструкция `SELECT` ссылается на три таблицы, сервер базы данных сначала может обратиться к `TableA`, использовать данные из `TableA` для извлечения соответствующих строк из `TableB`, а затем использовать данные из `TableB` для извлечения данных из `TableC`. Другие последовательности, в которых сервер базы данных может обращаться к таблицам:  
  `TableC`, `TableB`, `TableA`или  
  `TableB`, `TableA`, `TableC`или  
  `TableB`, `TableC`, `TableA`или  
  `TableC`, `TableA`, `TableB`  

- **Методы, используемые для извлечения данных из каждой таблицы.**  
  Есть различные методы для обращения к данным в каждой таблице. Если необходимы только несколько строк с определенными ключевыми значениями, то сервер базы данных может использовать индекс. Если необходимы все строки в таблице, то сервер базы данных может пропустить индексы и выполнить просмотр таблицы. Если необходимы все строки в таблице, но есть индекс, ключевые столбцы которого находятся в `ORDER BY`, то просмотр индекса вместо просмотра таблицы позволит избежать отдельный сортировки результирующего набора. Если таблица является очень маленькой, то просмотры таблицы могут быть самым эффективным методом для практически всех обращений к таблице.
  
- **Методы, используемые для вычислений, а также фильтрации, статистической обработки и сортировки данных из каждой таблицы.**  
  По мере доступа к данным из таблиц можно разными способами выполнять вычисления над данными (например, вычисления скалярных значений), а также статистическую обработку и сортировку данных, как определено в тексте запроса (например, при использовании предложения `GROUP BY` или `ORDER BY`) и их фильтрацию (например, при использовании предложения `WHERE` или `HAVING`).

> [!NOTE]
> В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] есть три способа отображения планов выполнения:        
> -  ***[Предполагаемый план выполнения](../../relational-databases/performance/display-the-estimated-execution-plan.md)***  — это скомпилированный план, созданный оптимизатором запросов на основе оценок.        
> -  ***[Действительный план выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md)***  — это скомпилированный план с [контекстом выполнения](../../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse). Сюда входят актуальные сведения времени выполнения, доступные после завершения выполнения, включая предупреждения времени выполнения, а также в более новых версиях [!INCLUDE[ssde_md](../../includes/ssde_md.md)] — время, затраченное на выполнение, и время ЦП.        
> -  ***[Статистика активных запросов](../../relational-databases/performance/live-query-statistics.md)***  — это скомпилированный план с контекстом выполнения. Сюда входят сведения о времени выполнения, которые обновляются каждую секунду. Эти сведения включают в себя, например, фактическое количество строк, передаваемых через операторы.       

> [!TIP]
> См. сведения о планах обработки и выполнения запросов в руководстве по [оптимизации инструкций SELECT](../../relational-databases/query-processing-architecture-guide.md#optimizing-select-statements) и [кэшированию и повторному использованию плана выполнения](../../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse) в документации по архитектуре обработки запросов.

## <a name="in-this-section"></a>в этом разделе  
[Инфраструктура профилирования запросов](../../relational-databases/performance/query-profiling-infrastructure.md)     
[Отображение и сохранение планов выполнения](../../relational-databases/performance/display-and-save-execution-plans.md)     
[Сравнение и анализ планов выполнения](../../relational-databases/performance/compare-and-analyze-execution-plans.md)     
[Руководства планов](../../relational-databases/performance/plan-guides.md)     

## <a name="see-also"></a>См. также:  
[Наблюдение и настройка производительности](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
[Средства контроля и настройки производительности](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
[Руководство по архитектуре обработки запросов](../../relational-databases/query-processing-architecture-guide.md)    
[Динамическая статистика запросов](../../relational-databases/performance/live-query-statistics.md)     
[Монитор активности](../../relational-databases/performance-monitor/activity-monitor.md)     
[Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)     
[sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)     
[sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)     
[Флаги трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)    
[Справочник по логическим и физическим операторам Showplan](../../relational-databases/showplan-logical-and-physical-operators-reference.md)
