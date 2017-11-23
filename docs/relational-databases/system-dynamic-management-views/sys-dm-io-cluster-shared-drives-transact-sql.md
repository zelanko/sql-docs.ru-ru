---
title: "sys.dm_io_cluster_shared_drives (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_io_cluster_shared_drives_TSQL
- sys.dm_io_cluster_shared_drives
- dm_io_cluster_shared_drives_TSQL
- dm_io_cluster_shared_drives
dev_langs: TSQL
helpviewer_keywords: sys.dm_io_cluster_shared_drives dynamic management view
ms.assetid: c8fcced8-c780-49dc-99bd-6beb3ca532c4
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 66e4e1de40aee22313bd8950986079e176f5278d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmioclustershareddrives-transact-sql"></a>sys.dm_io_cluster_shared_drives (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Это представление возвращает имя каждого из общих устройств, если текущий экземпляр сервера является кластерным сервером. Если текущий экземпляр сервера некластеризованный, возвращает пустой набор строк.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_io_cluster_shared_drives**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**DriveName**|**nchar(2)**|Тип устройства (буква диска), которое представляет отдельный диск, являющийся частью общего кластерного дискового массива. Столбец не может содержать значение NULL.|  
|**pdw_node_id**|**int**|**Применяется к**: ssPDW<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="remarks"></a>Замечания  
 Если включена кластеризация, экземпляру отказоустойчивого кластера требуются файлы данных и журналов, расположенные на общих дисках, к которым можно получить доступ при переходе экземпляра на другой узел. Каждая строка представления соответствует одному общему диску, который используется кластеризованным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для хранения данных или файлов журнала для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут использоваться только диски, отображаемые в этом представлении. Диски, перечисленные в данном представлении, являются дисками в группе кластерных ресурсов, связанной с этим экземпляром.  
  
> [!NOTE]  
>  В следующей версии это представление будет упразднено. Мы рекомендуем использовать [sys.dm_io_cluster_valid_path_names &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md) вместо него.  
  
## <a name="permissions"></a>Permissions  
 Пользователь должен иметь на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешение VIEW SERVER STATE.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано применение функции sys.dm_io_cluster_shared_drives для определения общих дисков на экземпляре кластеризованного сервера:  
  
```  
SELECT * FROM sys.dm_io_cluster_shared_drives;  
```  
  
 Результирующий набор:  
  
 DriveName  
  
 --------\-  
  
 m  
  
 n  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_io_cluster_valid_path_names &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)   
 [sys.dm_os_cluster_nodes &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [sys.fn_servershareddrives &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-servershareddrives-transact-sql.md)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  
