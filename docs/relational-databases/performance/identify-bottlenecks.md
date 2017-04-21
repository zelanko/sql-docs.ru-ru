---
title: "Определение узких мест | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource bottlenecks [SQL Server]
- database monitoring [SQL Server], bottlenecks
- performance [SQL Server], bottlenecks
- tuning databases [SQL Server], bottlenecks
- monitoring server performance [SQL Server], bottlenecks
- monitoring performance [SQL Server], bottlenecks
- database performance [SQL Server], bottlenecks
- server performance [SQL Server], bottlenecks
- bottlenecks [SQL Server]
- identifying bottlenecks [SQL Server]
ms.assetid: db079e65-ee80-4105-aec9-f8230d0d6635
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 20ff22698486f5537fc974a91905b9837792aa5d
ms.lasthandoff: 04/11/2017

---
# <a name="identify-bottlenecks"></a>Выявление узких мест
  Одновременный доступ к общим ресурсам может привести к появлению узких мест. Узкие места присутствуют в любой программной системе, и избежать их появления нельзя. Однако чрезмерная нагрузка на общие ресурсы повышает время отклика, и поэтому ее необходимо выявить и выполнить настройку.  
  
 Причины появления узких мест:  
  
-   недостаточность ресурсов, требуется обновление или наращивание компонентов;  
  
-   однотипные ресурсы, рабочая нагрузка на которые не распределена должным образом (например, монопольное использование диска);  
  
-   неисправность ресурса;  
  
-   ресурс неправильно настроен.  
  
## <a name="analyzing-bottlenecks"></a>Анализ узких мест  
 Чрезмерная продолжительность различных событий служит признаком узких мест, которые нуждаются в дополнительной настройке.  
  
 Например:  
  
-   какой-либо компонент препятствует завершению загрузки данного компонента, таким образом повышая общую длительность загрузки;  
  
-   запросы от клиентов могут выполняться дольше из-за загруженности сети.  
  
 Ниже приведены пять основных областей, на которые следует обратить внимание при выявлении узких мест.  
  
|Возможная область появления узких мест|Влияние на сервер|  
|------------------------------|---------------------------|  
|Использование памяти|Недостаток памяти, выделенной или доступной Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , значительно снижает производительность. Данные медленнее считываются с диска, чем непосредственно из кэша. Операционные системы Microsoft Windows выполняют чрезмерную выгрузку данных на диск и обратно в процессе обращения к различным страницам.|  
|Загрузка ЦП|Стабильно высокая загрузка ЦП может указывать на то, что следует оптимизировать запросы [!INCLUDE[tsql](../../includes/tsql-md.md)] , либо на необходимость модернизации ЦП.|  
|Дисковый ввод-вывод|[!INCLUDE[tsql](../../includes/tsql-md.md)] Чтобы снизить необходимость в операциях ввода-вывода, можно оптимизировать запросы (например, создав индексы).|  
|Соединения пользователей|Слишком много пользователей, одновременно производящих доступ к серверу, могут вызвать снижение производительности.|  
|Блокирующие блокировки|Неверно разработанные приложения могут вызвать блокировки и затруднить параллелизм, а это повышает время отклика и снижает пропускную способность системы.|  
  
## <a name="see-also"></a>См. также:  
 [Мониторинг использования ЦП](../../relational-databases/performance-monitor/monitor-cpu-usage.md)   
 [Наблюдение за использованием диска](../../relational-databases/performance-monitor/monitor-disk-usage.md)   
 [Наблюдение за использованием памяти](../../relational-databases/performance-monitor/monitor-memory-usage.md)   
 [SQL Server, объект General Statistics](../../relational-databases/performance-monitor/sql-server-general-statistics-object.md)   
 [SQL Server, объект Locks](../../relational-databases/performance-monitor/sql-server-locks-object.md)  
  
  
