---
title: sys.dm_xe_database_session_object_columns (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 0e6adc54-4d97-4ef0-bf4f-b4538d69f136
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 863b6d2c274c76919455a4ea68ba0e944d64f16e
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmxedatabasesessionobjectcolumns-azure-sql-database"></a>sys.dm_xe_database_session_object_columns (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Отображает значения конфигурации объектов, привязанных к сеансу.  
  
||  
|-|  
|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 и все более поздние версии.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Адрес сеанса событий в памяти. Имеет отношение "многие к одному" с sys.dm_xe_database_sessions.address. Не допускает значение NULL.|  
|column_name|**nvarchar(60)**|Имя значения конфигурации. Не допускает значение NULL.|  
|column_id|**int**|Идентификатор столбца. Уникален в пределах объекта. Не допускает значение NULL.|  
|column_value|**nvarchar(2048)**|Установленное значение столбца. Допускает значение NULL.|  
|object_type|**nvarchar(60)**|Тип объекта.  Не является nullable.object_type является одним из следующих:<br /><br /> event<br /><br /> target;|  
|object_name|**nvarchar(60)**|Имя объекта, которому принадлежит столбец. Не допускает значение NULL.|  
|object_package_guid|**uniqueidentifier**|Идентификатор GUID пакета, в котором содержится объект. Не допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|dm_xe_database_session_object_columns.object_name<br /><br /> dm_xe_database_session_object_columns.object_package_guid|sys.dm_xe_objects.package_guid<br /><br /> sys.dm_xe_objects.name|«многие к одному»|  
|dm_xe_database_session_object_columns.column_name<br /><br /> dm_xe_database_session_object_columns.column_id|sys.dm_xe_object_columns.name<br /><br /> sys.dm_xe_object_columns.column_id|«многие к одному»|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
