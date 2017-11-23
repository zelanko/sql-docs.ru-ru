---
title: "Использование приложения SQL Server Profiler для мониторинга служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 8b77dafc-4584-4e93-8ad7-299304391bfd
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 5c25432e05a7cc2de57456fb056d7501c05bdb50
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a>Использование приложения SQL Server Profiler для мониторинга служб Analysis Services
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отслеживает события обработки ядра, например начало пакета или транзакции, и фиксирует данные об этих событиях, тем самым давая возможность осуществлять мониторинг операций серверов и баз данных (например, пользовательские операции запросов и входа в систему). Можно фиксировать данные приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или файл для дальнейшего анализа, а также можно воспроизводить зафиксированные события в том же или в другом экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , чтобы точно определить, что произошло. Можно воспроизводить события в режиме реального времени или в пошаговом режиме. Также очень полезно запускать события трассировки вместе со счетчиками приложения «Производительность» на одном и том же компьютере. Приложение SQL Profiler может определять корреляцию между ними на основе времени и отображать их совместно на одной временной шкале. События трассировки предоставят подробные сведения, в то время как счетчики приложения «Производительность» дадут общее представление. Дополнительные сведения о создании и запуске трассировок см. в разделе [Создание трассировки приложения Profiler для воспроизведения (службы Analysis Services)](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md).  
  
 В следующей таблице описаны подразделы, содержащиеся в этом разделе.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Введение в мониторинг служб Analysis Services при помощи приложения SQL Server Profiler](../../analysis-services/instances/introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|Содержит описание использования приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для мониторинга экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Создание трассировки приложения Profiler для воспроизведения (службы Analysis Services)](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md)|Содержит требования к созданию трассировки для воспроизведения с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[События трассировки служб Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)|Содержит описание классов событий служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Эти классы событий соответствуют действиям, формируемым службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , и используются для воспроизведения трассировок.|  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за экземпляром служб Analysis Services](../../analysis-services/instances/monitor-an-analysis-services-instance.md)  
  
  
