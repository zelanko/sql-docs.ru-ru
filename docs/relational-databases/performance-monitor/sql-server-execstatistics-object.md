---
title: "Объект статистики выполнения (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 837b52d5d457a4466a46d08df918e25616d14bff
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-execstatistics-object"></a>SQL Server, объект ExecStatistics
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Объект **SQLServer:ExecStatistics** в Microsoft SQL Server предоставляет счетчики для контроля над различными выполнениями.  
  
 В этой таблице приведено описание счетчиков **Ведения статистики** SQL Server.  
  
|Счетчики ведения статистики SQL Server|Description|  
|-----------------------------------------|-----------------|  
|**Распределенный запрос**|Статистика, относящаяся к выполнению распределенных запросов.|  
|**Вызовы DTC**|Статистика, относящаяся к выполнению вызовов DTC.|  
|**Расширенные процедуры**|Статистика, относящаяся к выполнению расширенных процедур.|  
|**Вызовы OLEDB**|Статистика, относящаяся к выполнению вызовов OLEDB.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Элемент|Description|  
|----------|-----------------|  
|**Среднее время выполнения (сек)**|Среднее время выполнения выбранного типа выполнения.|  
|**Совокупное время выполнения (мс) в секунду**|Агрегированное время выполнения выбранного типа выполнения в секунду.|  
|**Текущие выполняемые задачи**|Количество совершающихся в текущий момент выполнений выбранного типа выполнения.|  
|**Выполнения, запущенные в секунду**|Количество запущенных в секунду выполнений выбранного типа выполнения.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
