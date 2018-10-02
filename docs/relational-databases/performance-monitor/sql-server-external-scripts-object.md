---
title: SQL Server, объект External Scripts | Документация Майкрософт
ms.custom: ''
ms.date: 03/21/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- External Scripts object
- SQLServer:External Scripts
ms.assetid: 8a75ccce-b174-4937-bc92-8e413b55afe1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e6eb921d6ebee88ce14ad30b0d2071941ec5f007
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47665552"
---
# <a name="sql-server-external-scripts-object"></a>SQL Server, объект External Scripts
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

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
  
  
