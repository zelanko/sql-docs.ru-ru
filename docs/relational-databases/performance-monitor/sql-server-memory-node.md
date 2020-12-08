---
title: Узел памяти (SQL Server) | Документация Майкрософт
description: Сведения об объекте "Память узла", который предоставляет счетчики для контроля использования памяти на сервере на узлах NUMA в SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 7f1c3f161d59e3bbf08036cc4c15d3380f2484dd
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505633"
---
# <a name="sql-server-memory-node"></a>SQL Server, память узла
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Объект **Память узла** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает счетчики для сервера мониторинга использования памяти на узлах NUMA.  
  
## <a name="memory-node-counters"></a>Счетчики памяти узла  
 В этой таблице описываются счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Память узла**.  
  
|SQL Server, счетчики диспетчера памяти|Описание|  
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
  
  
