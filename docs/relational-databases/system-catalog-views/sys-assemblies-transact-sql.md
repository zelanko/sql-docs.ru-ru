---
title: sys.assemblies (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.assemblies
- assemblies_TSQL
- sys.assemblies_TSQL
- assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assemblies catalog view
ms.assetid: e321753f-293f-42ab-b225-d118713df40b
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 24bc8604b41c391d669472bc147dddd7b051a72d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysassemblies-transact-sql"></a>sys.assemblies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Возвращает по одной строке для каждой сборки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя сборки. Уникален в пределах базы данных.|  
|**principal_id**|**int**|Идентификатор участника, который является владельцем этой сборки.|  
|**assembly_id**|**int**|Идентификационный номер сборки. Уникален в базе данных.|  
|**clr_name**|**nvarchar(4000)**|Каноническая строка, кодирующая простое имя, номер версии, культуру, открытый ключ и архитектуру сборки. Данное значение однозначно идентифицирует сборку на стороне среды CLR.|  
|**permission_set**|**tinyint**|Набор разрешений/уровень безопасности для сборки.<br /><br /> 1 = безопасный доступ.<br /><br /> 2 = внешний доступ.<br /><br /> 3 = небезопасный доступ.|  
|**permission_set_desc**|**nvarchar(60)**|Описание набора разрешений/уровня безопасности для сборки.<br /><br /> SAFE_ACCESS<br /><br /> EXTERNAL_ACCESS<br /><br /> UNSAFE_ACCESS|  
|**is_visible**|**бит**|1 = сборка видна для регистрации точек входа [!INCLUDE[tsql](../../includes/tsql-md.md)].<br /><br /> 0 = сборка предназначена только для управляемых вызывающих объектов. Это означает, что сборка обеспечивает внутреннюю реализацию для других сборок в базе данных.|  
|**create_date**|**datetime**|Дата создания или регистрации сборки.|  
|**modify_date**|**datetime**|Дата изменения сборки.|  
|**is_user_defined**|**бит**|Указывает исходный файл сборки.<br /><br /> 0 = системные сборки (например Microsoft.SqlServer.Types для **hierarchyid** тип данных)<br /><br /> 1 = определяемые пользователем сборки|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога сборки среды CLR &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
