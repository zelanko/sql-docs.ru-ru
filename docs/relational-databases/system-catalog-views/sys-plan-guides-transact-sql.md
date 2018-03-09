---
title: "sys.plan_guides (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.planguides_TSQL
- plan_guides
- sys.planguides
- plan_guides_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.plan_guides catalog view
ms.assetid: 3dde0397-ef6f-4b3f-8250-3f25584eb62b
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 591bc781d6c156320dffcb06e6e541aeb5b669a3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysplanguides-transact-sql"></a>sys.plan_guides (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой структуры плана в базе данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**plan_guide_id**|**int**|Уникальный идентификатор структуры плана в базе данных.|  
|**name**|**sysname**|Имя структуры плана.|  
|**create_date**|**datetime**|Дата и время создания структуры плана.|  
|**modify_date**|**DateTime**|Дата последнего изменения структуры плана.|  
|**is_disabled**|**bit**|1 = структура плана отключена.<br /><br /> 0 = структура плана включена.|  
|**query_text**|**nvarchar(max)**|Текст запроса, по которому была создана структура плана.|  
|**scope_type**|**tinyint**|Определяет область действия структуры плана.<br /><br /> 1 = OBJECT<br /><br /> 2 = SQL<br /><br /> 3 = TEMPLATE|  
|**scope_type_desc**|**nvarchar(60)**|Описание области действия структуры плана.<br /><br /> OBJECT<br /><br /> SQL<br /><br /> TEMPLATE|  
|**scope_object_id**|**Int**|object_id объекта, определяющего область действия структуры плана, если область действия — OBJECT.<br /><br /> NULL, если структура плана имеет область действия, отличную от OBJECT.|  
|**scope_batch**|**nvarchar(max)**|Текст пакета, если **scope_type** — SQL.<br /><br /> NULL, если тип пакета — не SQL.<br /><br /> Если значение равно NULL и **scope_type** SQL; значение **query_text** применяется.|  
|**Параметры**|**nvarchar(max)**|Строка, определяющая список аргументов, связанных со структурой плана.<br /><br /> NULL = со структурой плана не связан ни один список аргументов.|  
|**подсказки**|**nvarchar(max)**|Указания предложения OPTION, связанные с руководством плана.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_create_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  
