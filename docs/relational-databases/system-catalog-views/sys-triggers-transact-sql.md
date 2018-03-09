---
title: "sys.triggers (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- triggers
- triggers_TSQL
- sys.triggers
- sys.triggers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.triggers catalog view
ms.assetid: cefa4fc4-b8b9-4cd7-b124-eed5283acbfc
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ab5788614af71fe9fa4cab1a4f22e81d5a19a6d8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="systriggers-transact-sql"></a>sys.triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого объекта, являющегося триггером типа TR или TA. Имена триггеров DML ограничены областью схемы и, следовательно, видимы в **sys.objects**. Область существования имен триггеров DDL определяется родительской сущностью, поэтому эти имена видимы только в этом представлении.  
  
 **Parent_class** и **имя** столбцы однозначно идентифицируют триггер в базе данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя триггера. Имена триггеров DML ограничены областью схемы. Область имен триггеров DDL определяется в соответствии с родительской сущностью.|  
|**object_id**|**int**|Идентификационный номер объекта. Уникален в базе данных.|  
|**parent_class**|**tinyint**|Класс родителя триггера.<br /><br /> 0 = база данных (для триггеров DDL).<br /><br /> 1 = объект или столбец (для триггеров DML).|  
|**parent_class_desc**|**nvarchar(60)**|Описание родительского класса триггера.<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN|  
|**parent_ID**|**int**|Идентификатор родителя триггера, определяющийся следующим образом:<br /><br /> 0 = триггеры, родителями которых являются базы данных.<br /><br /> Для триггеров DML это **object_id** таблицы или представления, на котором определен триггер DML.|  
|**type**|**char(2)**|Тип объекта:<br /><br /> TA = триггер сборки (среда CLR)<br /><br /> TR = триггер SQL|  
|**type_desc**|**nvarchar(60)**|Описание типа объекта.<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**datetime**|Дата создания триггера.|  
|**modify_date**|**datetime**|Дата последнего изменения объекта с помощью инструкции ALTER.|  
|**is_ms_shipped**|**bit**|Триггер создан от лица пользователя внутренним компонентом сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**is_disabled**|**bit**|Триггер выключен.|  
|**is_not_for_replication**|**bit**|Триггер создан с аргументом NOT FOR REPLICATION.|  
|**is_instead_of_trigger**|**bit**|1 = триггеры INSTEAD OF<br /><br /> 0 = триггеры AFTER|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
