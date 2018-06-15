---
title: sys.dm_os_cluster_nodes (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_cluster_nodes_TSQL
- dm_os_cluster_nodes_TSQL
- dm_os_cluster_nodes
- sys.dm_os_cluster_nodes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_cluster_nodes dynamic management view
ms.assetid: 92fa804e-2d08-42c6-a36f-9791544b1d42
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6fb5b957cfdaa340ec90a9bb30a5e9db6a54ca31
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34465210"
---
# <a name="sysdmosclusternodes-transact-sql"></a>sys.dm_os_cluster_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждого узла в конфигурации экземпляра отказоустойчивого кластера. Если текущий экземпляр является экземпляром отказоустойчивого кластера, то возвращается список узлов, в которых определен этот экземпляр отказоустойчивого кластера (прежде «виртуальный сервер»). Если текущий экземпляр сервера не является кластеризованным экземпляром отработки отказа, то возвращается пустой набор строк.  
  
> **Примечание:** вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_cluster_nodes**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Имя_узла**|**sysname**|Имя узла в конфигурации экземпляра отказоустойчивого кластера (виртуального сервера) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|status|**int**|Состояние узла в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра отказоустойчивого кластера: 0, 1, 2, 3, -1. Дополнительные сведения см. в разделе [функция GetClusterNodeState](http://go.microsoft.com/fwlink/?LinkId=204794).|  
|status_description|**nvarchar(20)**|Описание состояния узла отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 0 = работает<br /><br /> 1 = остановлен<br /><br /> 2 = приостановлен<br /><br /> 3 = соединение<br /><br /> -1 = неизвестно|  
|is_current_owner|bit|1 означает, что этот узел является текущим владельцем ресурса отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="remarks"></a>Примечания  
 Когда отказоустойчивый кластер включен, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может работать на любом из узлов отказоустойчивого кластера, входящих в конфигурацию экземпляра отказоустойчивого кластера (виртуального сервера) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> **Примечание:** данное представление заменит функцию fn_virtualservernodes, которая будет считаться устаревшей в следующей версии.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения VIEW SERVER STATE на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере sys. dm_os_cluster_nodes используется для возврата узлов экземпляра кластерного сервера.  
  
```  
SELECT NodeName, status, status_description, is_current_owner   
FROM sys.dm_os_cluster_nodes;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|NodeName|status|status_description|is_current_owner|  
|--------------|------------|-------------------------|------------------------|  
|node1|0|up|1|  
|node2|0|up|0|  
|Node3|1|down|0|  
  
## <a name="see-also"></a>См. также  
 [sys.dm_os_cluster_properties &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-properties-transact-sql.md)   
 [sys.dm_io_cluster_shared_drives &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md)   
 [sys.fn_virtualservernodes &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-virtualservernodes-transact-sql.md)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  



