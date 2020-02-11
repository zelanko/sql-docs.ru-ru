---
title: Узел памяти (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 32a2296fdb68e640ce8ebfc8dd9cdb351666b337
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250581"
---
# <a name="sql-server-memory-node"></a>SQL Server, память узла
  Объект **Память узла** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает счетчики для сервера мониторинга использования памяти на узлах NUMA.  
  
## <a name="memory-node-counters"></a>Счетчики памяти узла  
 В таблице описываются счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Память узла** .  
  
|SQL Server, счетчики диспетчера памяти|Description|  
|----------------------------------------|-----------------|  
|**Память узла базы данных (КБ)**|Указывает объем памяти, который используется в настоящий момент сервером на данном узле для страниц базы данных.|  
|**Свободная память узла (КБ)**|Указывает объем памяти, который не используется сервером на данном узле.|  
|**Память внешнего узла (КБ)**|Указывает объем локальной памяти, отличной от NUMA, на данном узле.|  
|**Узел заимствованной памяти (КБ)**|Указывает объем памяти, который используется в настоящий момент сервером на данном узле не для страниц базы данных, а для других целей.|  
|**Память целевого узла**|Указывает идеальный объем памяти для данного узла.|  
|**Общая память узла**|Указывает общий объем памяти, выделенной серверу на данном узле.|  
  
## <a name="see-also"></a>См. также:  
 [Мониторинг использования ресурсов &#40;системном мониторе&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, объект диспетчера буферов](sql-server-buffer-manager-object.md)   
 [sys. dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
