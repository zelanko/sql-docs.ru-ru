---
title: Динамическая статистика запросов | Документация Майкрософт
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- query statistics [SQL Server] live query stats
- live query statistics
- debugging [SQL Server], live query stats
- statistics [SQL Server], live query statistics
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753e
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ad61ab5b110a9b2be539b486184479e6a2a9a4ea
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="live-query-statistics"></a>Динамическая статистика запросов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет просматривать динамический план выполнения активного запроса. Этот динамический план запроса позволяет анализировать процесс выполнения запроса в режиме реального времени по мере передачи управления от одного [оператора плана запроса](../../relational-databases/showplan-logical-and-physical-operators-reference.md) другому. Динамический план запроса отображает общий ход выполнения запроса и текущую статистику выполнения на уровне оператора, например число полученных строк, затраченное время, ход выполнения оператора и т. д. Так как эти данные доступны в режиме реального времени и, чтобы их увидеть, не нужно дожидаться завершения запроса, такая статистика чрезвычайно полезна для отладки проблем с производительностью запросов. Эта функция доступна начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], но она может работать и с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
> [!WARNING]  
> Эта функция предназначена в основном для диагностики. Ее использование может значительно снизить общую производительность запроса. Эта функция может использоваться с [отладчиком Transact-SQL](../../relational-databases/scripting/configure-firewall-rules-before-running-the-tsql-debugger.md).  
  
#### <a name="to-view-live-query-statistics"></a>Просмотр динамической статистики запросов  
  
1.  Чтобы просмотреть план выполнения запроса в режиме реального времени, в меню "Сервис" выберите значок **Динамическая статистика запросов** .  
  
     ![Кнопка динамической статистики запросов на панели инструментов](../../relational-databases/performance/media/livequerystatstoolbar.png "Кнопка динамической статистики запросов на панели инструментов")  
  
     Кроме того, динамический план выполнения запроса можно открыть, щелкнув правой кнопкой мыши запрос в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и выбрав пункт **Включить статистику активных запросов**.  
  
     ![Кнопка динамической статистики запросов во всплывающем меню](../../relational-databases/performance/media/livequerystatsmenu.png "Кнопка динамической статистики запросов во всплывающем меню")  
  
2.  Теперь можно выполнить запрос. В динамическом плане запроса отображается общий ход выполнения запроса и текущая статистика выполнения (например, затраченное время, ход выполнения и т. д.) по операторам плана запроса. Сведения о ходе выполнения запроса и статистика выполнения периодически обновляются во время выполнения запроса. С помощью этих сведений вы сможете в общих чертах понимать ход выполнения запроса, а также отлаживать долго выполняемые запросы, бесконечно выполняемые запросы, запросы, которые приводят к переполнению tempdb, и проблемы с временем ожидания.  
  
     ![Кнопка динамической статистики запросов в showplan](../../relational-databases/performance/media/livequerystatsplan.png "Кнопка динамической статистики запросов в showplan")  
  
 Динамический план выполнения можно открыть из **монитора активности** . Для этого правой кнопкой мыши щелкните запросы в таблице **Текущие ресурсоемкие запросы** .  
  
 ![Кнопка динамической статистики запросов в мониторе активности](../../relational-databases/performance/media/livequerystatsactmon.png "Кнопка динамической статистики запросов в мониторе активности")  
  
## <a name="remarks"></a>Remarks  
 Чтобы функция динамической статистики запросов могла собирать данные о ходе выполнения, необходимо включить инфраструктуру профиля статистики. Выбор параметра **Включить динамическую статистику запроса** в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] включает инфраструктуру статистики для текущего сеанса запроса. 
 
До версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] есть еще два способа включить инфраструктуру статистики, с помощью которой можно просматривать динамическую статистику запросов из других сеансов (например, из монитора активности).  
  
-   Выполните команды `SET STATISTICS XML ON;` или `SET STATISTICS PROFILE ON;` в нужном сеансе.  
  
 или диспетчер конфигурации служб  
  
-   Включите расширенное событие **query_post_execution_showplan** . Этот параметр применяется ко всему серверу и включает динамическую статистку запросов для всех сеансов. Сведения о включении расширенных событий см. в статье [Monitor System Activity Using Extended Events](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).  

Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1 (SP1) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеется упрощенная версия инфраструктуры профилей статистики. Есть два способа включить упрощенную инфраструктуру статистики, с помощью которой можно просматривать динамическую статистику запросов из других сеансов (например, из монитора активности).

-   Используйте глобальный флаг трассировки 7412.  
  
 или диспетчер конфигурации служб  
  
-   Включите расширенное событие **query_thread_profile** . Этот параметр применяется ко всему серверу и включает динамическую статистку запросов для всех сеансов. Сведения о включении расширенных событий см. в статье [Monitor System Activity Using Extended Events](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).
  
 > [!NOTE]
 > Хранимые процедуры, скомпилированные в собственном коде, не поддерживаются.  
  
## <a name="permissions"></a>Разрешения  
 Для заполнения страницы результатов **Динамическая статистика запросов** требуется разрешение **SHOWPLAN** уровня базы данных. Для просмотра динамической статистики нужно разрешение **VIEW SERVER STATE** уровня сервера. А для выполнения запроса требуются все разрешения, необходимые для этого.  
  
## <a name="see-also"></a>См. также:  
 [Monitor and Tune for Performance](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [Средства контроля и настройки производительности](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [Открытие монитора активности (среда SQL Server Management Studio)](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)     
 [Монитор активности](../../relational-databases/performance-monitor/activity-monitor.md)     
 [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)     
 [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)     
 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)     
 [Флаги трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)    
 [Справочник по логическим и физическим операторам Showplan](../../relational-databases/showplan-logical-and-physical-operators-reference.md)
