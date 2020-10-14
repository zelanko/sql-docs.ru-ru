---
description: sys.dm_pdw_dms_cores (Transact-SQL)
title: sys.dm_pdw_dms_cores (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b3f09b15-0863-4418-9347-a4f5fd2ab7c7
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 13a5248824387e1ba63c612b354b9b128e5ae1c0
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035427"
---
# <a name="sysdm_pdw_dms_cores-transact-sql"></a>sys.dm_pdw_dms_cores (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит сведения обо всех службах DMS, работающих на вычисленных узлах устройства. В нем отображается одна строка для каждого экземпляра службы, которая в настоящее время является одной строкой на узел.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|Уникальный числовой идентификатор, связанный с этим ядром DMS.<br /><br /> Ключ для этого представления.|Задайте для pdw_node_id узла, на котором работает этот ядро DMS.|  
|pdw_node_id|**int**|Идентификатор узла, на котором запущена эта служба DMS.|См. node_id в [sys.dm_pdw_nodes &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(32)**|Текущее состояние службы DMS.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
 Сведения о максимальном объеме строк, хранящихся в этом представлении, см. в разделе метаданные статьи [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления Azure синапсе Analytics и Параллельное хранилище данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
