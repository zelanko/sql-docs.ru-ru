---
title: sys.dm_os_hosts (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_hosts_TSQL
- dm_os_hosts
- dm_os_hosts_TSQL
- sys.dm_os_hosts
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_hosts dynamic management view
ms.assetid: a313ff3b-1fe9-421e-b94b-cea19c43b0e5
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2eb7372bb5214412d96361054fec25e5bd7b340c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmoshosts-transact-sql"></a>sys.dm_os_hosts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список всех узлов, зарегистрированных на данный момент в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это представление также возвращает ресурсы, используемые перечисляемыми узлами.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_hosts**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**host_address**|**varbinary(8)**|Внутренний адрес в памяти объекта узла.|  
|**type**|**nvarchar(60)**|Тип размещенного компонента. Например:<br /><br /> SOSHOST_CLIENTID_SERVERSNI = собственный интерфейс SQL Server;<br /><br /> SOSHOST_CLIENTID_SQLOLEDB = поставщик OLE DB для SQL Server Native Client;<br /><br /> SOSHOST_CLIENTID_MSDART = компоненты доступа к данным MDA.|  
|**name**|**nvarchar(32)**|Имя узла.|  
|**enqueued_tasks_count**|**int**|Общее количество задач, которые данный узел поместил в очереди на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**active_tasks_count**|**int**|Количество выполняющихся в данный момент задач, помещенных этим узлом в очереди.|  
|**completed_ios_count**|**int**|Количество операций ввода-вывода, инициированных и выполненных посредством этого узла.|  
|**completed_ios_in_bytes**|**bigint**|Суммарное количество байтов, обработанных в операциях ввода-вывода посредством этого узла.|  
|**active_ios_count**|**int**|Общее количество запросов ввода-вывода, относящихся к этому узлу, ожидающих завершения в настоящее время.|  
|**default_memory_clerk_address**|**varbinary(8)**|Адрес в памяти объекта клерка памяти, связанного с этим узлом. Дополнительные сведения см. в разделе [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="remarks"></a>Замечания  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешены компоненты, такие как поставщик OLE DB, которые не являются частью исполняемого файла [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для выделения памяти и участия в планировании в режиме без вытеснения. Эти компоненты размещаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а все ресурсы, выделенные им, отслеживаются. Размещение позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для лучше учитывать ресурсы, используемые для внешних компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] исполняемый файл.  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|sys.dm_os_hosts. default_memory_clerk_address|sys.dm_os_memory_clerks. memory_clerk_address|один к одному|  
|sys.dm_os_hosts. host_address|sys.dm_os_memory_clerks. host_address|один к одному|  
  
## <a name="examples"></a>Примеры  
 В следующем примере определяется общий объем памяти, задействованной размещенным компонентом.  
  
||  
|-|  
|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
```  
SELECT h.type, SUM(mc.pages_kb) AS commited_memory  
FROM sys.dm_os_memory_clerks AS mc   
INNER JOIN sys.dm_os_hosts AS h   
    ON mc.memory_clerk_address = h.default_memory_clerk_address  
GROUP BY h.type;  
```  
  
## <a name="see-also"></a>См. также  

 [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)   
 [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


