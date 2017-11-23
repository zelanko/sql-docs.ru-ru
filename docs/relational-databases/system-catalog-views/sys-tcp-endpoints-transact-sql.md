---
title: "sys.tcp_endpoints (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.tcp_endpoints
- sys.tcp_endpoints_TSQL
- tcp_endpoints
- tcp_endpoints_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.tcp_endpoints catalog view
ms.assetid: 43cc3afa-cced-4463-8e97-fbfdaf2e4fa8
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2be15d96b5ab7274688c34303ccf1603064dce9d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="systcpendpoints-transact-sql"></a>sys.tcp_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой из конечных точек TCP, имеющихся в системе. Конечные точки, которые описаны в документах **sys.tcp_endpoints** представляют собой объекты для предоставления или отмены прав доступа на соединение. Отображаемые сведения о портах и IP-адресах не используются для настройки протоколов и могут не соответствовать фактической конфигурации протоколов. Для просмотра и настройки протоколов следует использовать диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**< унаследованные столбцы >**||Наследует столбцы из [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**port**|int|Номер порта, который прослушивается конечной точкой. Не допускает значение NULL.|  
|**is_dynamic_port**|bit|1 = Номер порта назначается динамически.<br /><br /> Не допускает значение NULL.|  
|**IP-адрес**|**nvarchar(45)**|IP-адрес средства прослушивания, указанный в предложении LISTENER_IP. Допускает значение NULL.|  
  
## <a name="remarks"></a>Замечания  
 Выполните следующий запрос для сбора сведений о конечных точках и соединениях. Конечные точки без текущих соединений или соединений TCP будут отображены со значениями NULL. Добавить **ГДЕ** предложение `WHERE des.session_id = @@SPID` для возвращения сведений о текущем соединении.  
  
```  
SELECT des.login_name, des.host_name, program_name,  dec.net_transport, des.login_time,   
e.name AS endpoint_name, e.protocol_desc, e.state_desc, e.is_admin_endpoint,   
t.port, t.is_dynamic_port, dec.local_net_address, dec.local_tcp_port   
FROM sys.endpoints AS e  
LEFT JOIN sys.tcp_endpoints AS t  
   ON e.endpoint_id = t.endpoint_id  
LEFT JOIN sys.dm_exec_sessions AS des  
   ON e.endpoint_id = des.endpoint_id  
LEFT JOIN sys.dm_exec_connections AS dec  
   ON des.session_id = dec.session_id;  
```  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога конечных точек &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
