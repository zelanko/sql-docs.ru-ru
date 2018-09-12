---
title: Узел памяти (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ac64c1dda2e1130327c79d73637524537f744b6b
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808951"
---
# <a name="sql-server-memory-node"></a>SQL Server, память узла
  Объект **Память узла** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает счетчики для сервера мониторинга использования памяти на узлах NUMA.  
  
## <a name="memory-node-counters"></a>Счетчики памяти узла  
 В таблице описываются счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Память узла** .  
  
|SQL Server, счетчики диспетчера памяти|Описание|  
|----------------------------------------|-----------------|  
|**Память узла базы данных (КБ)**|Указывает объем памяти, который используется в настоящий момент сервером на данном узле для страниц базы данных.|  
|**Свободная память узла (КБ)**|Указывает объем памяти, который не используется сервером на данном узле.|  
|**Внешняя память узла (КБ)**|Указывает объем локальной памяти, отличной от NUMA, на данном узле.|  
|**Заимствованная память узла (КБ)**|Указывает объем памяти, который используется в настоящий момент сервером на данном узле не для страниц базы данных, а для других целей.|  
|**Целевая память узла.**|Указывает идеальный объем памяти для данного узла.|  
|**Общая память узла**|Указывает общий объем памяти, выделенной серверу на данном узле.|  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за использованием ресурсов (системный монитор)](monitor-resource-usage-system-monitor.md)   
 [SQL Server, объект Buffer Manager](sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
