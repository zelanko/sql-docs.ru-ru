---
title: "SQL Server, объект External Scripts | Документация Майкрософт"
ms.custom: 
ms.date: 03/21/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- External Scripts object
- SQLServer:External Scripts
ms.assetid: 8a75ccce-b174-4937-bc92-8e413b55afe1
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2e5f146f5684567ec39e62d9c6d7786f3506d8d0
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-external-scripts-object"></a>SQL Server, объект External Scripts
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Объект **SQLServer:External Scripts** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет счетчики для отслеживания действий, связанных с выполнением внешних скриптов. Сведения о выполнении внешних скриптов см. в разделе [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  
  
 В следующей таблице описаны счетчики объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**External Scripts**.  
  
|Счетчики SQL Server External Scripts|Описание|  
|------------------------------------------|-----------------|  
|**Ошибки выполнения**|Количество ошибок при выполнении внешних скриптов.|  
|**Имена для входа с подразумеваемой аутентификацией**|Количество имен входа из вспомогательных процессов, проходящих неявную проверку подлинности.|  
|**Параллельное выполнение**|Количество выполненных внешних скриптов, для которых @parallel = 1.|  
|**Выполнение SQL CC**|Количество внешних скриптов, выполненных с помощью контекста вычислений SQL.|  
|**Потоковое выполнение**|Количество выполненных внешних скриптов, для которых @r_rowsPerRead = 1.|  
|**Общее время выполнения (мс)**|Общее время, потраченное на выполнение внешних скриптов.|  
|**Всего выполнений**|Количество выполненных внешних скриптов.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sys.resource_governor_external_resource_pools (Transact-SQL)](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)   
 [sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  

