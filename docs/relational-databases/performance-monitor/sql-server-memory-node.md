---
title: Узел памяти (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ce022fb623dbd10016d09452b7ad4cb7bce7d689
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32950739"
---
# <a name="sql-server-memory-node"></a>SQL Server, память узла
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Объект **Память узла** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает счетчики для сервера мониторинга использования памяти на узлах NUMA.  
  
## <a name="memory-node-counters"></a>Счетчики памяти узла  
 В таблице описываются счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Память узла** .  
  
|SQL Server, счетчики диспетчера памяти|Description|  
|----------------------------------------|-----------------|  
|**Память узла базы данных (КБ)**|Указывает объем памяти, который используется в настоящий момент сервером на данном узле для страниц базы данных.|  
|**Свободная память узла (КБ)**|Указывает объем памяти, который не используется сервером на данном узле.|  
|**Внешняя память узла (КБ)**|Указывает объем локальной памяти, отличной от NUMA, на данном узле.|  
|**Заимствованная память узла (КБ)**|Указывает объем памяти, который используется в настоящий момент сервером на данном узле не для страниц базы данных, а для других целей.|  
|**Целевая память узла.**|Указывает идеальный объем памяти для данного узла.|  
|**Общая память узла**|Указывает общий объем памяти, выделенной серверу на данном узле.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server, объект Buffer Manager](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
  
