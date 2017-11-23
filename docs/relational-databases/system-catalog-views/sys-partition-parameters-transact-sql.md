---
title: "sys.partition_parameters (Transact-SQL) | Документы Microsoft"
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
- partition_parameters_TSQL
- partition_parameters
- sys.partition_parameters_TSQL
- sys.partition_parameters
dev_langs: TSQL
helpviewer_keywords: sys.partition_parameters catalog view
ms.assetid: 2012ed9d-3ea3-4c29-9b78-dfa54a392dce
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ea75798552d0521204e063663566b08b36a5797b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syspartitionparameters-transact-sql"></a>sys.partition_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Содержит строку для каждого параметра функции секционирования.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**function_id**|**int**|Идентификатор функции секционирования, которой принадлежит данный параметр.|  
|**parameter_id**|**int**|Идентификатор параметра. Уникален внутри функции секционирования, начинается с 1.|  
|**system_type_id**|**tinyint**|Идентификатор системного типа параметра. Соответствует **system_type_id** столбец **sys.types** представления каталога.|  
|**max_length**|**smallint**|Максимальная длина аргумента в байтах.|  
|**точность**|**tinyint**|Для числового аргумента — точность; иначе 0.|  
|**Масштаб**|**tinyint**|Масштаб числового аргумента; иначе 0.|  
|**collation_name**|**sysname**|Имя параметров сортировки параметра, если он является символьным; в противном случае значение NULL.|  
|**user_type_id**|**int**|Идентификатор типа данных. Уникален в пределах базы данных. Для системных типов данных **user_type_id** = **system_type_id**.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога функции секционирования &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.partition_functions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_range_values &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)  
  
  
