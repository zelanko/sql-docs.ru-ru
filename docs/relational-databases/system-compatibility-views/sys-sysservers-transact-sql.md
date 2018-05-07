---
title: sys.sysservers (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sysservers
- sysservers_TSQL
- sysservers
- sys.sysservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysservers system table
- sys.sysservers compatibility view
ms.assetid: d02f186f-c00f-44a6-b38d-dc78a3d2145b
caps.latest.revision: 27
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a052eecd27de7767f721bc71a070eb00dad99220
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="syssysservers-transact-sql"></a>sys.sysservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждого сервера, к которому экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может обращаться как к источнику данных OLE DB.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**srvid**|**smallint**|Идентификатор (только для локального использования) удаленного сервера.|  
|**srvstatus**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SRVNAME**|**sysname**|Имя сервера.|  
|**srvproduct**|**sysname**|Название продукта для удаленного сервера.|  
|**ProviderName**|**nvarchar(128)**|Имя поставщика OLE DB для доступа к этому серверу.|  
|**Источник данных**|**nvarchar(4000)**|Значение источника данных OLE DB.|  
|**расположение**|**nvarchar(4000)**|Местоположение OLE DB.|  
|**providerstring**|**nvarchar(4000)**|Строка поставщика OLE DB.|  
|**schemadate**|**datetime**|Дата последнего обновления этой строки.|  
|**topologyx**|**int**|Не используется.|  
|**topologyy**|**int**|Не используется.|  
|**catalog**|**sysname**|Каталог, который используется при соединении с поставщиком OLE DB.|  
|**srvcollation**|**sysname**|Параметры сортировки сервера.|  
|**connecttimeout**|**int**|Время ожидания соединения с сервером.|  
|**querytimeout**|**int**|Время ожидания выполнения запросов на сервере.|  
|**srvnetname**|**char(30)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**isremote**|**бит**|1 = удаленный сервер.<br /><br /> 0 = связанный сервер.|  
|**rpc**|**бит**|1 = **sp_serveroption@rpc** значение **true** или **на**.<br /><br /> 0 = **sp_serveroption@rpc** значение **false** или **off**.|  
|**pub**|**бит**|1 = **sp_serveroption@pub** значение **true** или **на**.<br /><br /> 0 = **sp_serveroption@pub** значение **false** или **off**.|  
|**sub**|**бит**|1 = **sp_serveroption@sub** значение **true** или **на**.<br /><br /> 0 = **sp_serveroption@sub** значение **false** или **off**.|  
|**dist**|**бит**|1 = **sp_serveroption@dist** значение **true** или **на**.<br /><br /> 0 = **sp_serveroption@dist** значение **false** или **off**.|  
|**dpub**|**бит**|1 = **sp_serveroption@dpub** значение **true** или **на**.<br /><br /> 0 = **sp_serveroption@dpub** значение **false** или **off**.|  
|**rpcout**|**бит**|1 =  **sp_serveroption@rpc out** значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@rpc out** значение **false** или **off**.|  
|**DataAccess**|**бит**|1 =  **sp_serveroption@data доступа** значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@data доступа** значение **false** или **off**.|  
|**collationcompatible**|**бит**|1 =  **sp_serveroption@collation совместимых** значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@collation совместимых** значение **false** или **off**.|  
|**Системы**|**бит**|1 = **sp_serveroption@system** значение **true** или **на**.<br /><br /> 0 = **sp_serveroption@system** значение **false** или **off**.|  
|**useremotecollation**|**бит**|1 =  **sp_serveroption@remote сортировки** значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@remote сортировки** значение **false** или **off**.|  
|**lazyschemavalidation**|**бит**|1 =  **sp_serveroption@lazy проверки схемы** значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@lazy проверки схемы** значение **false** или **off**.|  
|**Параметры сортировки**|**sysname**|Параметры сортировки сервера, задаваемое при помощи  **sp_serveroption@collation имя**.|  
|**nonsqlsub**|bit|0 = сервер является экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> 1= сервер не является экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
