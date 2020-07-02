---
title: sys. server_trigger_events (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.server_trigger_events_TSQL
- server_trigger_events_TSQL
- sys.server_trigger_events
- server_trigger_events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_trigger_events catalog view
ms.assetid: be7d8a59-3c00-4f1b-b4b0-3dcd5572e002
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: da5fdbf9cded1ea58e3d1dc2ab29cea6df0e9693
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775226"
---
# <a name="sysserver_trigger_events-transact-sql"></a>sys.server_trigger_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Содержит по одной строке для каждого из событий, для которого срабатывает синхронный триггер уровня сервера.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Унаследованные столбцы**||Наследует все столбцы из [sys. server_events](../../relational-databases/system-catalog-views/sys-server-events-transact-sql.md).|  
|**is_first**|**bit**|Триггер помечен как первый срабатывающий триггер для этого события.|  
|**is_last**|**bit**|Триггер помечен как последний срабатывающий триггер для этого события.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
