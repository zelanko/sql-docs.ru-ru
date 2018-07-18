---
title: sys.dm_pdw_nodes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3f307d70f7c161743d81c33916046e88cadad9e9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37980572"
---
# <a name="sysdmpdwnodes-transact-sql"></a>sys.dm_pdw_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит информацию о всех узлов в [!INCLUDE[ssAPS](../../includes/ssaps-md.md)]. В ней перечислены одну строку для каждого узла в устройстве.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.<br /><br /> Ключ для этого представления.|UNIQUE на устройстве, независимо от типа.|  
|Тип|**nvarchar(32)**|Тип узла.|«ВЫЧИСЛЕНИЯ», «УПРАВЛЕНИЕ», «УПРАВЛЕНИЕ»|  
|name|**nvarchar(32)**|Логическое имя узла.|Любая строка соответствующей длины.|  
|address|**nvarchar(32)**|IP-адрес этого узла.|В формате [0-255]. [0-255]. [0-255]. [0-255].|  
|is_passive|**int**|Указывает, выполняется на сервере, назначенных виртуальной машины, работающей на узел или была переключена на запасной сервер.|0 — на исходном сервере работает узел виртуальной Машины.<br /><br /> 1 — узел виртуальной Машины выполняется на запасной сервер.|  
|область|**nvarchar(32)**|Регион, где на узле выполняется.|«PDW», «HDINSIGHT»|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
