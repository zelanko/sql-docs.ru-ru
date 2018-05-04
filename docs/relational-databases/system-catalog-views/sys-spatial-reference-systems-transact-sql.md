---
title: sys.spatial_reference_systems (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- spatial_reference_systems_TSQL
- sys.spatial_reference_systems_TSQL
- sys.spatial_reference_systems
- spatial_reference_systems
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_reference_systems catalog view
- spatial_reference_systems
ms.assetid: 3c9bc120-67c3-463f-9e24-29fd623f25a0
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 46721d1a238c10d28c45e090ea3368775510e142
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysspatialreferencesystems-transact-sql"></a>sys.spatial_reference_systems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Список систем пространственной ссылки (SRID), поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|spatial_reference_id|**int**|Идентификаторы SRID, поддерживаемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|authority_name|**nvarchar(128)**|Центр сертификации SRID.|  
|authorized_spatial_reference_id|**int**|Идентификатор SRID, заданный центром сертификации в **authority_name**.|  
|well_known_text|**nvarchar(4000)**|Представление SRID в формате WKT.|  
|unit_of_measure|**nvarchar(128)**|Имя единицы измерения.|  
|unit_conversion_factor|**float**|Длина единицы измерения в метрах.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
  
