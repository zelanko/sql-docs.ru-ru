---
description: catalog.object_versions (база данных SSISDB)
title: catalog.object_versions (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 2fd8c020-1c77-4702-8e6b-efa6a348daab
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a2371508c40e60ebacbe60d656d4d9ffa3f70ce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422038"
---
# <a name="catalogobject_versions-ssisdb-database"></a>catalog.object_versions (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает версии объектов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В этом выпуске в данном представлении поддерживаются только версии проектов.  
  
|Имя столбца|Тип данных|Описание|  
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
  
## <a name="remarks"></a>Комментарии  
 В этом представлении отображается по одной строке для каждой из версий объекта в каталоге.  
  
## <a name="permissions"></a>Разрешения  
 Для просмотра строк в этом представлении необходимо иметь одно из следующих разрешений:  
  
-   разрешение READ на объект  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**.  
  
> [!NOTE]  
>  Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
