---
title: sys.sysservers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 03875d828940a2baa5d9f30f7beb58adb77abf07
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68018116"
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
|**isremote**|**bit**|1 = удаленный сервер.<br /><br /> 0 = связанный сервер.|  
|**rpc**|**bit**|1 = **sp_serveroption@rpc** присвоено **true** или **на**.<br /><br /> 0 = **sp_serveroption@rpc** присвоено **false** или **off**.|  
|**pub**|**bit**|1 = **sp_serveroption@pub** присвоено **true** или **на**.<br /><br /> 0 = **sp_serveroption@pub** присвоено **false** или **off**.|  
|**sub**|**bit**|1 = **sp_serveroption@sub** присвоено **true** или **на**.<br /><br /> 0 = **sp_serveroption@sub** присвоено **false** или **off**.|  
|**dist**|**bit**|1 = **sp_serveroption@dist** присвоено **true** или **на**.<br /><br /> 0 = **sp_serveroption@dist** присвоено **false** или **off**.|  
|**dpub**|**bit**|1 = **sp_serveroption@dpub** присвоено **true** или **на**.<br /><br /> 0 = **sp_serveroption@dpub** присвоено **false** или **off**.|  
|**rpcout**|**bit**|1 =  **sp_serveroption@rpc out** присвоено **true** или **на**.<br /><br /> 0 =  **sp_serveroption@rpc out** присвоено **false** или **off**.|  
|**DataAccess**|**bit**|1 =  **sp_serveroption@data доступа** присвоено **true** или **на**.<br /><br /> 0 =  **sp_serveroption@data доступа** присвоено **false** или **off**.|  
|**collationcompatible**|**bit**|1 =  **sp_serveroption@collation совместимых** присвоено **true** или **на**.<br /><br /> 0 =  **sp_serveroption@collation совместимых** присвоено **false** или **off**.|  
|**system**|**bit**|1 = **sp_serveroption@system** присвоено **true** или **на**.<br /><br /> 0 = **sp_serveroption@system** присвоено **false** или **off**.|  
|**useremotecollation**|**bit**|1 =  **sp_serveroption@remote параметры сортировки** присвоено **true** или **на**.<br /><br /> 0 =  **sp_serveroption@remote параметры сортировки** присвоено **false** или **off**.|  
|**lazyschemavalidation**|**bit**|1 =  **sp_serveroption@lazy проверка схемы** присвоено **true** или **на**.<br /><br /> 0 =  **sp_serveroption@lazy проверка схемы** присвоено **false** или **off**.|  
|**Параметры сортировки**|**sysname**|Параметры сортировки сервера, задаваемое при помощи  **sp_serveroption@collation имя**.|  
|**nonsqlsub**|bit|0 = сервер является экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> 1= сервер не является экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
