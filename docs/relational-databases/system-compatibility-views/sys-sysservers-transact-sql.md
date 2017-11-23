---
title: "sys.sysservers (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysservers
- sysservers_TSQL
- sysservers
- sys.sysservers_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sysservers system table
- sys.sysservers compatibility view
ms.assetid: d02f186f-c00f-44a6-b38d-dc78a3d2145b
caps.latest.revision: "27"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e05b06dd6a37f6330f715b374e3fe46515c3f37d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syssysservers-transact-sql"></a>sys.sysservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждого сервера, к которому экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может обращаться как к источнику данных OLE DB.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**srvid**|**smallint**|Идентификатор (только для локального использования) удаленного сервера.|  
|**srvstatus**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SRVNAME**|**sysname**|Имя сервера.|  
|**srvproduct**|**sysname**|Название продукта для удаленного сервера.|  
|**ProviderName**|**nvarchar(128)**|Имя поставщика OLE DB для доступа к этому серверу.|  
|**источник данных**|**nvarchar(4000)**|Значение источника данных OLE DB.|  
|**расположение**|**nvarchar(4000)**|Местоположение OLE DB.|  
|**providerstring**|**nvarchar(4000)**|Строка поставщика OLE DB.|  
|**schemadate**|**datetime**|Дата последнего обновления этой строки.|  
|**topologyx**|**int**|Не используется.|  
|**topologyy**|**int**|Не используется.|  
|**каталог**|**sysname**|Каталог, который используется при соединении с поставщиком OLE DB.|  
|**srvcollation**|**sysname**|Параметры сортировки сервера.|  
|**connecttimeout**|**int**|Время ожидания соединения с сервером.|  
|**QueryTimeOut**|**int**|Время ожидания выполнения запросов на сервере.|  
|**srvnetname**|**char(30)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**isremote**|**bit**|1 = удаленный сервер.<br /><br /> 0 = связанный сервер.|  
|**RPC**|**bit**|1 =  **sp_serveroption@rpc**  значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@rpc**  значение **false** или **off**.|  
|**pub**|**bit**|1 =  **sp_serveroption@pub**  значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@pub**  значение **false** или **off**.|  
|**Sub**|**bit**|1 =  **sp_serveroption@sub**  значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@sub**  значение **false** или **off**.|  
|**dist**|**bit**|1 =  **sp_serveroption@dist**  значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@dist**  значение **false** или **off**.|  
|**dpub**|**bit**|1 =  **sp_serveroption@dpub**  значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@dpub**  значение **false** или **off**.|  
|**rpcout**|**bit**|1 =  **sp_serveroption@rpc out** значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@rpc out** значение **false** или **off**.|  
|**DataAccess**|**bit**|1 =  **sp_serveroption@data доступа** значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@data доступа** значение **false** или **off**.|  
|**collationcompatible**|**bit**|1 =  **sp_serveroption@collation совместимых** значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@collation совместимых** значение **false** или **off**.|  
|**системы**|**bit**|1 =  **sp_serveroption@system**  значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@system**  значение **false** или **off**.|  
|**useremotecollation**|**bit**|1 =  **sp_serveroption@remote сортировки** значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@remote сортировки** значение **false** или **off**.|  
|**lazyschemavalidation**|**bit**|1 =  **sp_serveroption@lazy проверки схемы** значение **true** или **на**.<br /><br /> 0 =  **sp_serveroption@lazy проверки схемы** значение **false** или **off**.|  
|**параметры сортировки**|**sysname**|Параметры сортировки сервера, задаваемое при помощи  **sp_serveroption@collation имя**.|  
|**nonsqlsub**|bit|0 = сервер является экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> 1= сервер не является экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление системных таблиц с системными представлениями &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
