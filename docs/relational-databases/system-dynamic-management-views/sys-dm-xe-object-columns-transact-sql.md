---
title: sys.dm_xe_object_columns (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_xe_object_columns
- sys.dm_xe_object_columns_TSQL
- dm_xe_object_columns_TSQL
- dm_xe_object_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_object_columns dynamic management view
- extended events [SQL Server], views
ms.assetid: d96a14f3-4284-45ff-b1fe-4858e540a013
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5810e57f4529ef417f46ab88d97b86a964e2e6f5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmxeobjectcolumns-transact-sql"></a>sys.dm_xe_object_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о схеме для всех объектов.  
  
> [!NOTE]  
>  Объекты событий предоставляют фиксированные схемы как для данных, доступных только для чтения, так и для данных, доступных для чтения и записи.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|имя|**nvarchar(60)**|Имя столбца. имя является уникальным в пределах объекта. Не допускает значение NULL.|  
|column_id|**int**|Идентификатор столбца. Идентификатор column_id является уникальным в пределах объекта, при использовании с column_type. Не допускает значение NULL.|  
|object_name|**nvarchar(60)**|Имя объекта, которому принадлежит столбец. Обеспечивает связь «многие к одному» с sys.dm_xe_objects.id. Не допускает значение NULL.|  
|object_package_guid|**uniqueidentifier**|Идентификатор GUID пакета, в котором содержится объект. Не допускает значение NULL.|  
|type_name|**nvarchar(60)**|Имя типа для этого столбца. Не допускает значение NULL.|  
|type_package_guid|**uniqueidentifier**|Идентификатор GUID пакета, в котором содержится тип данных столбца. Не допускает значение NULL.|  
|column_type|**nvarchar(60)**|Показывает, как используется этот столбец. Не допускает значение NULL. column_type может принимать одно из следующих значений:<br /><br /> readonly. Столбец содержит статическое значение, которое нельзя изменить.<br /><br /> data. Столбец содержит данные времени выполнения, представленные объектом.<br /><br /> customizable. Столбец содержит значение, которое можно изменить.<br /><br /> Примечание: Изменение этого значения можно изменить поведение объекта.|  
|column_value|**nvarchar(256)**|Отображает статические значения, связанные со столбцом объекта. Допускает значение NULL.|  
|capabilities|**int**|Битовая карта, описывающая возможности столбца. Допускает значение NULL.|  
|capabilities_desc|**nvarchar(256)**|Описание возможностей этого столбца объекта. Значение может быть одним из следующих.<br /><br /> Mandatory. Значение должно быть задано при привязывании родительского объекта к сеансу событий.<br /><br /> NULL|  
|description|**nvarchar(256)**|Описание этого столбца объекта. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
### <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|sys.dm_xe_object_columns.object_name, sys.dm_xe_object_columns.object_package_guid|sys.dm_xe_objects.name,<br /><br /> sys.dm_xe_objects.package_guid|«многие к одному»|  
|sys.dm_xe_object_columns.type_name<br /><br /> sys.dm_xe_object_columns.type_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|«многие к одному»|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

