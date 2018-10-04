---
title: sys.tcp_endpoints (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.tcp_endpoints
- sys.tcp_endpoints_TSQL
- tcp_endpoints
- tcp_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.tcp_endpoints catalog view
ms.assetid: 43cc3afa-cced-4463-8e97-fbfdaf2e4fa8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ad6a7f9e9c727f88015b9b815a37a5825e3b2f47
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47805512"
---
# <a name="systcpendpoints-transact-sql"></a>sys.tcp_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой из конечных точек TCP, имеющихся в системе. Конечные точки, которые описаны **sys.tcp_endpoints** представляют собой объекты для предоставления или отмены прав доступа на соединение. Отображаемые сведения о портах и IP-адресах не используются для настройки протоколов и могут не соответствовать фактической конфигурации протоколов. Для просмотра и настройки протоколов следует использовать диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**< наследуемые столбцы >**||Наследует столбцы из [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**port**|ssNoversion|Номер порта, который прослушивается конечной точкой. Не допускает значение NULL.|  
|**is_dynamic_port**|bit|1 = Номер порта назначается динамически.<br /><br /> Не допускает значение NULL.|  
|**IP-адрес**|**nvarchar(45)**|IP-адрес средства прослушивания, указанный в предложении LISTENER_IP. Допускает значение NULL.|  
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога конечных точек &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
