---
title: "sys.foreign_keys (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- foreign_keys
- sys.foreign_keys
- sys.foreign_keys_TSQL
- foreign_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.foreign_keys catalog view
ms.assetid: e960df1a-13fc-43ee-ba91-34c1b719ac2c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f2051dc726a4622f5340dc0972cf6fc38798d3f9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysforeignkeys-transact-sql"></a>sys.foreign_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит строку для каждого объекта, являющегося ограничением ВНЕШНЕГО ключа с **sys.object.type** = F.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**\<Столбцы, наследуемые из sys.objects >**||Список столбцов, наследуемых этим представлением см. в разделе [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**referenced_object_id**|**int**|Идентификатор упоминаемого объекта.|  
|**key_index_id**|**int**|Идентификатор ключевого индекса в упоминаемом объекте.|  
|**is_disabled**|**bit**|Ограничение внешнего ключа отключено.|  
|**is_not_for_replication**|**bit**|Ограничение внешнего ключа создано с помощью параметра NOT FOR REPLICATION.|  
|**is_not_trusted**|**bit**|Ограничение внешнего ключа не было проверено системой.|  
|**delete_referential_action**|**tinyint**|Ссылочное действие, объявленное для данного внешнего ключа на случай удаления.<br /><br /> 0 = нет действий.<br /><br /> 1 = каскад.<br /><br /> 2 = задать NULL.<br /><br /> 3 = задать по умолчанию.|  
|**delete_referential_action_desc**|**nvarchar(60)**|Описание ссылочного действия, объявленного для данного внешнего ключа на случай удаления.<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**update_referential_action**|**tinyint**|Ссылочное действие, объявленное для данного внешнего ключа на случай обновления.<br /><br /> 0 = нет действий.<br /><br /> 1 = каскад.<br /><br /> 2 = задать NULL.<br /><br /> 3 = задать по умолчанию.|  
|**update_referential_action_desc**|**nvarchar(60)**|Описание ссылочного действия, объявленного для данного внешнего ключа на случай обновления.<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**is_system_named**|**bit**|1 = имя создано системой.<br /><br /> 0 = имя предоставлено пользователем.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
