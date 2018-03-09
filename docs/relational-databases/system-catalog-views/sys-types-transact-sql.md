---
title: "sys.Types (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- types
- types_TSQL
- sys.types_TSQL
- sys.types
dev_langs: TSQL
helpviewer_keywords:
- sys.types catalog view
- table-valued parameters,sys.types
ms.assetid: a5dbc842-71a0-4f62-b5e0-f560a99b7f8c
caps.latest.revision: "33"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0fab5cee5706b0d8a00638f35c3b91d639efb3b6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="systypes-transact-sql"></a>sys.types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит по строке для каждого системного и определяемого пользователем типа данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя типа данных. Уникально в пределах схемы.|  
|**system_type_id**|**tinyint**|Идентификатор внутреннего системного типа, соответствующего данному типу данных.|  
|**user_type_id**|**int**|Идентификатор типа данных. Уникален в пределах базы данных. Для системных типов данных **user_type_id** = **system_type_id**.|  
|**SCHEMA_ID**|**int**|Идентификатор схемы, к которой принадлежит тип данных.|  
|**principal_id**|**int**|Идентификатор отдельного владельца, если он отличается от владельца схемы. По умолчанию содержащиеся в схеме объекты принадлежат владельцу схемы. Однако с помощью инструкции ALTER AUTHORIZATION можно изменить право собственности и указать другого владельца.<br /><br /> Имеет значение NULL, если нет другого владельца.|  
|**max_length**|**smallint**|Максимальная длина типа (в байтах):<br /><br /> -1 = тип данных столбца — **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, или **xml**.<br /><br /> Для **текст** столбцы, **max_length** значение будет равно 16.|  
|**точность**|**tinyint**|Максимальная точность значений этого типа данных, если он числовой; иначе — значение 0.|  
|**Масштаб**|**tinyint**|Максимальный масштаб значений этого типа данных, если он числовой; иначе — значение 0.|  
|**collation_name**|**sysname**|Имя параметров сортировки значений этого типа данных, если он символьный; иначе — значение NULL.|  
|**is_nullable**|**bit**|Тип данных допускает значения NULL.|  
|**is_user_defined**|**bit**|1 = определяемый пользователем тип.<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип системных данных.|  
|**is_assembly_type**|**bit**|1 = реализация этого типа данных определена в сборке среды CLR.<br /><br /> 0 = тип данных основан на системном типе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**default_object_id**|**int**|Идентификатор изолированного значения по умолчанию, привязанного к типу данных с помощью [sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md).<br /><br /> 0 = нет значения по умолчанию.|  
|**rule_object_id**|**int**|Идентификатор изолированного правила, привязанного к типу данных с помощью [sp_bindrule](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md).<br /><br /> 0 = нет правила по умолчанию.|  
|**is_table_type**|**bit**|Указывает, что тип является табличным.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Скалярные типы представлений каталога &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [OBJECTPROPERTY (Transact-SQL)](../../t-sql/functions/objectproperty-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
