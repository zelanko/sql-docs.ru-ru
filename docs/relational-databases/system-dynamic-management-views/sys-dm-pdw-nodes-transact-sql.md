---
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
ms.openlocfilehash: 9ba367379795408a79b412c5b4c04097484bfd2b
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197207"
---
# <a name="sysdm_pdw_nodes-transact-sql"></a>sys. dm_pdw_nodes (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит сведения обо всех узлах в [!INCLUDE[ssAPS](../../includes/ssaps-md.md)] . В нем отображается одна строка для каждого узла в устройстве.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.<br /><br /> Ключ для этого представления.|Уникальным для устройства, независимо от типа.|  
|тип|**nvarchar(32)**|Тип узла.|"COMPUTE", "CONTROL", "MANAGEMENT"|  
|name|**nvarchar(32)**|Логическое имя узла.|Любая строка соответствующей длины.|  
|address|**nvarchar(32)**|IP-адрес этого узла.|В формате [0-255]. [0-255]. [0-255]. [0-255].|  
|is_passive|**int**|Указывает, работает ли виртуальная машина, на которой работает узел, на назначенном сервере или отработка отказа на запасной сервер.|на исходном сервере запущена виртуальная машина 0-Node.<br /><br /> на запасном сервере работает виртуальная машина с 1 узлом.|  
|region|**nvarchar(32)**|Регион, в котором работает узел.|"PDW", "HDINSIGHT"|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
