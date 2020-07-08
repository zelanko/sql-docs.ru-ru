---
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
ms.openlocfilehash: e0c752f5872a6385af49753cbd24604adcb1c747
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85671931"
---
# <a name="catalogobject_versions-ssisdb-database"></a>catalog.object_versions (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
## <a name="remarks"></a>Remarks  
 В этом представлении отображается по одной строке для каждой из версий объекта в каталоге.  
  
## <a name="permissions"></a>Разрешения  
 Для просмотра строк в этом представлении необходимо иметь одно из следующих разрешений:  
  
-   разрешение READ на объект  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**.  
  
> [!NOTE]  
>  Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
