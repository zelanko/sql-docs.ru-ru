---
description: sys. dm_pdw_nodes (Transact-SQL)
title: sys. dm_pdw_nodes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b999f7e10baece4566ebe0dd87b96b92eaabac53
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474798"
---
# <a name="sysdm_pdw_nodes-transact-sql"></a>sys. dm_pdw_nodes (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит сведения обо всех узлах в [!INCLUDE[ssAPS](../../includes/ssaps-md.md)] . В нем отображается одна строка для каждого узла в устройстве.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.<br /><br /> Ключ для этого представления.|Уникальным для устройства, независимо от типа.|  
|тип|**nvarchar(32)**|Тип узла.|"COMPUTE", "CONTROL", "MANAGEMENT"|  
|name|**nvarchar(32)**|Логическое имя узла.|Любая строка соответствующей длины.|  
|address|**nvarchar(32)**|IP-адрес этого узла.|В формате [0-255]. [0-255]. [0-255]. [0-255].|  
|is_passive|**int**|Указывает, работает ли виртуальная машина, на которой работает узел, на назначенном сервере или отработка отказа на запасной сервер.|на исходном сервере запущена виртуальная машина 0-Node.<br /><br /> на запасном сервере работает виртуальная машина с 1 узлом.|  
|region|**nvarchar(32)**|Регион, в котором работает узел.|"PDW", "HDINSIGHT"|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
