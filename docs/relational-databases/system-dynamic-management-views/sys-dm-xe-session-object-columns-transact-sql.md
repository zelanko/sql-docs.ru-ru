---
title: sys.dm_xe_session_object_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_session_object_columns_TSQL
- sys.dm_xe_session_object_columns_TSQL
- dm_xe_session_object_columns
- sys.dm_xe_session_object_columns
dev_langs:
- TSQL
helpviewer_keywords:
- xe
- sys.dm_xe_session_object_columns dynamic management view
ms.assetid: e97f3307-2da6-4c54-b818-a474faec752e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e87e0d981d2ee6f18368394329cf524da7e49a22
ms.sourcegitcommit: f46fd79fd32a894c8174a5cb246d9d34db75e5df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/26/2018
ms.locfileid: "53785845"
---
# <a name="sysdmxesessionobjectcolumns-transact-sql"></a>sys.dm_xe_session_object_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает значения конфигурации объектов, привязанных к сеансу.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Адрес сеанса событий в памяти. Обеспечивает связь «многие к одному» со столбцом sys.dm_xe_sessions.address. Не допускает значение NULL.|  
|column_name|**nvarchar(256)**|Имя значения конфигурации. Не допускает значение NULL.|  
|column_id|**int**|Идентификатор столбца. Уникален в пределах объекта. Не допускает значение NULL.|  
|column_value|**nvarchar(3072)**|Установленное значение столбца. Допускает значение NULL.|  
|object_type|**nvarchar(60)**|Тип объекта. Не допускает значение NULL. object_type является одним из:<br /><br /> event<br /><br /> target;|  
|object_name|**nvarchar(256)**|Имя объекта, которому принадлежит столбец. Не допускает значение NULL.|  
|object_package_guid|**uniqueidentifier**|Идентификатор GUID пакета, в котором содержится объект. Не допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
### <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|dm_xe_session_object_columns.object_name,<br /><br /> dm_xe_session_object_columns.object_package_guid|sys.dm_xe_objects.package_guid,<br /><br /> sys.dm_xe_objects.name|«многие к одному»|  
|dm_xe_session_object_columns.column_name,<br /><br /> dm_xe_session_object_columns.column_id|sys.dm_xe_object_columns.Name,<br /><br /> sys.dm_xe_object_columns.column_id|«многие к одному»|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

