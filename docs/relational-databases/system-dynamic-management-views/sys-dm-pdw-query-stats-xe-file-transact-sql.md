---
title: sys.dm_pdw_query_stats_xe_file (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.service: ''
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e0cd402f-04d0-4a5b-b725-88b31bb7862e
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 090332d413b592d80461e8ff3b3ea55795f39b79
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmpdwquerystatsxefile-transact-sql"></a>sys.dm_pdw_query_stats_xe_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Это динамическое административное Представление является устаревшим и будет удален в будущем выпуске. В этом выпуске он возвращает 0 строк.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|event|**nvarchar(60)**|Ключ для этого представления.||  
|.|**xml**|||  
|pdw_node_id|**int**|Узел, на котором выполняется данный экземпляр Xevent.||  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамических административных представлений &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
