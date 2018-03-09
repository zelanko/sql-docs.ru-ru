---
title: "MSdbms_datatype_mapping (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSdbms_datatype_mapping_TSQL
- MSdbms_datatype_mapping
dev_langs: TSQL
helpviewer_keywords: MSdbms_datatype_mapping system table
ms.assetid: 13289a0b-dfb0-4771-ad80-4c5f83cded99
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75f042866d01baa0a74143d2698644148a100b43
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msdbmsdatatypemapping-transact-sql"></a>MSdbms_datatype_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdbms_datatype_mapping** таблица содержит допустимые сопоставления типов данных из типа данных в системы управления базами данных (СУБД) для одного или нескольких определенных типов данных в целевой СУБД. Эта таблица хранится в **msdb** базы данных и используется для разнородной репликации базы данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**datatype_mapping_id**|**int**|Идентифицирует каждое уникальное сопоставление типа данных.|  
|**map_id**|**int**|Идентифицирует исходный тип данных.|  
|**dest_datatype_id**|**int**|Идентифицирует целевой тип данных.|  
|**dest_precision**|**bigint**|Определяет точность целевого типа данных, где значение NULL обозначает, что точность не используется, а значение **-1** означает, что используется точность исходного типа данных.|  
|**dest_scale**|**int**|Определяет масштаб целевого типа данных, где значение NULL обозначает, что масштаб не используется, а значение **-1** означает, что используется масштаб исходного типа данных.|  
|**dest_length**|**bigint**|Определяет длину целевого типа данных, где значение NULL обозначает, что длина не используется, а значение **-1** означает, что используется длина исходного типа данных.|  
|**dest_nullable**|**bit**|Показывает, допускает ли целевой столбец в данном сопоставлении значения NULL; причем NULL означает, что это определение не требуется.|  
|**dest_createparams**|**int**|Битовая карта, описывающая, какое сочетание длины, точности и масштаба применимо для каждого типа данных:<br /><br /> **0x1** = точность.<br /><br /> **0x2** = масштаб.<br /><br /> **0x4** = длина.|  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Указание сопоставления типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
