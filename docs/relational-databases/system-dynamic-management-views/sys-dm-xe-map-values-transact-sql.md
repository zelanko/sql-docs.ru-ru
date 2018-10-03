---
title: sys.dm_xe_map_values (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_xe_map_values
- dm_xe_map_values
- dm_xe_map_values_TSQL
- sys.dm_xe_map_values_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_map_values dynamic management view
- xe
ms.assetid: c0c5dd7e-9cee-47e2-b65a-88194c00aa1f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0adf93355baebd7be881d46c62f649c61245af4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680342"
---
# <a name="sysdmxemapvalues-transact-sql"></a>sys.dm_xe_map_values (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сопоставление внутренних цифровых ключей с немашинным (предназначенный для человека) текстом.  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|name|**nvarchar(60)**|Имя сопоставления. имя является уникальным в локальной системе. Не допускает значение NULL.|  
|object_package_guid|**uniqueidentifier**|Идентификатор GUID пакета, в котором содержится сопоставление. Не допускает значение NULL.|  
|map_key|**int**|Значение внутреннего ключа. Не допускает значение NULL.|  
|map_value|**nvarchar(2048)**|Описание значения ключа. Не допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
### <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|dm_xe_map_values.object_package_guid<br /><br /> dm_xe_map_values.name|sys.dm_xe_objects.package_guid<br /><br /> sys.dm_xe_objects.name|«многие к одному»|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

