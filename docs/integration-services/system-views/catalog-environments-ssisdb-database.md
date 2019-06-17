---
title: catalog.environments (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 7014c0e3-65dc-4a46-842e-4decf3737748
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9c3660f7314ce9514b4dc03ee2d6fb1490a4eab7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65715259"
---
# <a name="catalogenvironments-ssisdb-database"></a>catalog.environments (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает подробные сведения о среде для всех сред в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Среды содержат переменные, на которые могут ссылаться проекты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|environment_id|**bigint**|Уникальный идентификатор среды.|  
|name|**sysname**|Имя среды.|  
|folder_id|**bigint**|Уникальный идентификатор папки, в которой хранится среда.|  
|description|**nvarchar(1024)**|Описание среды. Это значение является необязательным.|  
|created_by_sid|**varbinary(85)**|Уникальный идентификатор безопасности пользователя, создавшего среду.|  
|created_by_name|**nvarchar(128)**|Имя пользователя, создавшего среду.|  
|created_time|**datetimeoffset**|Дата и время создания среды.|  
  
## <a name="remarks"></a>Remarks  
 В этом представлении отображается строка для каждой среды в каталоге. Имена сред уникальны только в пределах папки, где они находятся. Например, среда с именем `E1` может существовать в нескольких папках в каталоге, но в каждой папке может быть только одна среда с именем `E1`.  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ для среды  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
