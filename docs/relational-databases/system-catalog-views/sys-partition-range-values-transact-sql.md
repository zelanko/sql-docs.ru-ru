---
title: "sys.partition_range_values (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
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
- sys.partition_range_values
- partition_range_values_TSQL
- partition_range_values
- sys.partition_range_values_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.partition_range_values catalog view
ms.assetid: 9aee483e-61f3-4613-bec6-f084161f45ac
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0f1fd5ab82c373dbc08edf7a901ccfee4d6eed34
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syspartitionrangevalues-transact-sql"></a>sys.partition_range_values (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Содержит по одной строке для каждого граничного значения диапазона функции секционирования типа R.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**function_id**|**int**|Идентификатор функции секционирования для данного граничного значения диапазона.|  
|**boundary_id**|**int**|Идентификатор (порядковый номер, начиная с 1) кортежа граничных значений. Самое левое граничное значение имеет идентификатор 1.|  
|**parameter_id**|**int**|Идентификатор параметра функции, которому соответствует данное значение. В этом столбце значения соответствуют значениям **parameter_id** столбец **sys.partition_parameters** представления для какого-либо конкретного каталога **function_id**.|  
|**значение**|**sql_variant**|Фактическое граничное значение.|  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** . Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога функции секционирования &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.partition_functions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_parameters &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)  
  
  
