---
title: "Catalog.object_versions (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 2fd8c020-1c77-4702-8e6b-efa6a348daab
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3ea7c5ae054a002b9bb4f150e60f323ae03d702a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogobjectversions-ssisdb-database"></a>catalog.object_versions (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает версии объектов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В этом выпуске в данном представлении поддерживаются только версии проектов.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|object_version_lsn|**bigint**|Уникальный идентификатор версии объекта. Не гарантируется, что это число будет последовательным.|  
|object_id|**bigint**|Уникальный идентификатор объекта.|  
|object_type|**smallint**|Тип объекта. Для проектов отображается значение `20`.|  
|object_name|**sysname(nvarchar(128))**|Имя объекта.|  
|description|**nvarchar(1024)**|Описание проекта.|  
|created_by|**nvarchar(128)**|Имя пользователя, который добавил объект в каталог.|  
|created_time|**datetimeoffset**|Дата и время добавления объекта в каталог.|  
|restored_by|**nvarchar(128)**|Имя пользователя, который восстановил объект.|  
|last_restored_time|**datetimeoffset**|Дата и время последнего восстановления объекта.|  
  
## <a name="remarks"></a>Замечания  
 В этом представлении отображается по одной строке для каждой из версий объекта в каталоге.  
  
## <a name="permissions"></a>Permissions  
 Для просмотра строк в этом представлении необходимо иметь одно из следующих разрешений:  
  
-   разрешение READ на объект  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера.  
  
> [!NOTE]  
>  Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
