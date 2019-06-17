---
title: sys.server_triggers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_triggers
- sys.server_triggers_TSQL
- server_triggers_TSQL
- sys.server_triggers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_triggers catalog view
ms.assetid: 25926ff4-9271-45bf-bc32-d5d3344bd47a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9b13aeed62a84258fcfbf5820c17dca59f4b5852
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62660755"
---
# <a name="sysservertriggers-transact-sql"></a>sys.server_triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит набор всех триггеров DDL уровня сервера с object_type, равным TR или TA. В случае триггеров CLR сборка должна быть загружена в **master** базы данных. Все имена триггеров DDL существуют в одной, глобальной области.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя триггера.|  
|**object_id**|**int**|Идентификатор объекта.|  
|**parent_class**|**tinyint**|Класс родителя. Всегда:<br /><br /> 100 = Сервер|  
|**parent_class_desc**|**nvarchar(60)**|Описание класса родителя. Всегда:<br /><br /> SERVER.|  
|**parent_id**|**int**|Всегда равно 0 для триггеров на SERVER.|  
|**type**|**char(2)**|Тип объекта:<br /><br /> TA = триггер сборки (среда CLR)<br /><br /> TR = триггер SQL|  
|**type_desc**|**nvarchar(60)**|Описание класса объекта.<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**datetime**|Дата создания триггера.|  
|**modify_date**|**datetime**|Дата последней модификации триггера с помощью инструкции ALTER.|  
|**is_ms_shipped**|**bit**|Триггер создан от лица пользователя внутренним компонентом сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**is_disabled**|**bit**|1 = триггер отключен.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
