---
title: sys.dm_pdw_nodes (Transact-SQL) | Документация Майкрософт
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
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a5df628a6b37c8d89843506c5b7f4c5050157158
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027396"
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
|is_passive|**int**|Указывает, выполняется на сервере, назначенных виртуальной машины, работающей на узел или была переключена на запасной сервер.|0 — на исходном сервере работает узел виртуальной Машины.<br /><br /> 1 - узел виртуальной Машины выполняется на запасной сервер.|  
|область|**nvarchar(32)**|Регион, где на узле выполняется.|«PDW», «HDINSIGHT»|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
