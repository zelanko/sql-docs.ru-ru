---
title: sysdatatypemappings (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysdatatypemappings
- sysdatatypemappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdatatypemappings view
ms.assetid: 5dfafb70-3e3d-4465-b293-1acff1f855b6
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6bf0df894d81eaa0688462a813578ab827c47b7f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdatatypemappings-transact-sql"></a>sysdatatypemappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysdatatypemappings** представление используется для отображения сопоставления типов данных SQL Server и типы данных системы управления базами данных (СУБД) SQL Server. Это представление хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**mapping_id**|**int**|Идентификатор сопоставления типа данных.|  
|**source_dbms**|**sysname**|Указывается имя СУБД, из которой сопоставляются типы данных. Это имя может иметь одно из следующих значений.<br /><br /> **MSSQLSERVER** = источником является база данных SQL Server.<br /><br /> **ORACLE** = источником является база данных Oracle.|  
|**source_version**|**sysname**|Указывается версия продукта СУБД источника.|  
|**source_type**|**sysname**|Указывается тип данных, представленный в СУБД источника.|  
|**source_length_min**|**bigint**|Минимальная длина типа данных в СУБД-источнике; причем значение NULL указывает, что длина не используется.|  
|**source_length_max**|**bigint**|Максимальная длина типа данных в СУБД-источнике; причем значение NULL указывает, что длина не используется.|  
|**source_precision_min**|**bigint**|Минимальная точность типа данных в СУБД-источнике; причем значение NULL указывает, что точность не используется.|  
|**source_precision_max**|**bigint**|Максимальная точность типа данных в СУБД-источнике; причем значение NULL указывает, что точность не используется.|  
|**source_scale_min**|**int**|Минимальный масштаб типа данных в СУБД-источнике; причем значение NULL указывает, что масштаб не используется.|  
|**source_scale_max**|**int**|Максимальный масштаб типа данных в СУБД-источнике; причем значение NULL указывает, что масштаб не используется.|  
|**source_nullable**|**бит**|Указывается, что тип данных назначения поддерживает значения NULL.|  
|**source_createparams**|**int**|Только для внутреннего применения.|  
|**destination_dbms**|**sysname**|Указывается имя целевой СУБД. Это имя может принимать одно из следующих значений.<br /><br /> **MSSQLSERVER** = назначением является база данных SQL Server.<br /><br /> **ORACLE** = целевой является база данных Oracle.<br /><br /> **DB2** = целевой является база данных IBM DB2.<br /><br /> **SYBASE** = назначением является база данных Sybase.|  
|**destination_version**|**sysname**|Версия продукта целевой СУБД.|  
|**destination_type**|**sysname**|Тип данных в целевой СУБД.|  
|**destination_length**|**bigint**|Длина типа данных в целевой СУБД.|  
|**destination_precision**|**bigint**|Точность типа данных в целевой СУБД.|  
|**destination_scale**|**int**|Масштаб типа данных в целевой СУБД.|  
|**destination_nullable**|**бит**|Указывает, поддерживает ли тип данных в целевой СУБД значения NULL.|  
|**destination_createparams**|**int**|Только для внутреннего применения.|  
|**dataloss**|**бит**|Указывает, возникают ли потери данных при сопоставлении типов данных СУБД источника и адресата.|  
|**is_default**|**бит**|Указывает, используется ли сопоставление типов данных по умолчанию.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpdatatypemap &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  
