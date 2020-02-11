---
title: sys. plan_guides (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.planguides_TSQL
- plan_guides
- sys.planguides
- plan_guides_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.plan_guides catalog view
ms.assetid: 3dde0397-ef6f-4b3f-8250-3f25584eb62b
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 19b78ff53b5640d74b49d2e5956c39aa1df2e230
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068067"
---
# <a name="sysplan_guides-transact-sql"></a>sys.plan_guides (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой структуры плана в базе данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**plan_guide_id**|**int**|Уникальный идентификатор структуры плана в базе данных.|  
|**name**|**имеет sysname**|Имя структуры плана.|  
|**create_date**|**datetime**|Дата и время создания структуры плана.|  
|**modify_date**|**DateTime**|Дата последнего изменения структуры плана.|  
|**is_disabled**|**bit**|1 = структура плана отключена.<br /><br /> 0 = структура плана включена.|  
|**query_text**|**nvarchar(max)**|Текст запроса, по которому была создана структура плана.|  
|**scope_type**|**tinyint**|Определяет область действия структуры плана.<br /><br /> 1 = OBJECT<br /><br /> 2 = SQL<br /><br /> 3 = TEMPLATE|  
|**scope_type_desc**|**nvarchar (60)**|Описание области действия структуры плана.<br /><br /> OBJECT<br /><br /> SQL<br /><br /> TEMPLATE|  
|**scope_object_id**|**Int**|object_id объекта, определяющего область действия структуры плана, если область действия — OBJECT.<br /><br /> NULL, если структура плана имеет область действия, отличную от OBJECT.|  
|**scope_batch**|**nvarchar(max)**|Пакетный текст, если **scope_type** имеет значение SQL.<br /><br /> NULL, если тип пакета — не SQL.<br /><br /> Если значение NULL и **scope_type** равно SQL, то применяется **query_text** .|  
|**Вход**|**nvarchar(max)**|Строка, определяющая список аргументов, связанных со структурой плана.<br /><br /> NULL = со структурой плана не связан ни один список аргументов.|  
|**Советы**|**nvarchar(max)**|Указания предложения OPTION, связанные с руководством плана.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  
