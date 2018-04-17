---
title: sys.dm_pdw_nodes (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 267eac5c7f4aa7d73827f377002f4383374d853f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwnodes-transact-sql"></a>sys.dm_pdw_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения обо всех узлов в [!INCLUDE[ssAPS](../../includes/ssaps-md.md)]. Он содержит одну строку для каждого узла в устройстве.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.<br /><br /> Ключ для этого представления.|Уникален в пределах устройства, независимо от типа.|  
|Тип|**nvarchar(32)**|Тип узла.|«ВЫЧИСЛЕНИЯ», «ДОСТУП», «УПРАВЛЕНИЕ»|  
|имя|**nvarchar(32)**|Логическое имя узла.|Любая строка соответствующей длины.|  
|address|**nvarchar(32)**|IP-адрес этого узла.|В формате [0 – 255]. [0 – 255]. [0 – 255]. [0 – 255].|  
|is_passive|**int**|Указывает, выполняется на сервере, назначенных виртуальной машины, узел или переключился на запасной сервер.|0 — узле виртуальных Машин выполняется на исходном сервере.<br /><br /> 1 — узле виртуальных Машин выполняется на сервере запасные.|  
|область|**nvarchar(32)**|Регион, где запущен узел.|«PDW», «HDINSIGHT»|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамических административных представлений &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
