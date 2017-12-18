---
title: "catalog.environments (база данных SSISDB) | Документы Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 7014c0e3-65dc-4a46-842e-4decf3737748
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: edb3360d05e44131d6f30b510ed5dd120e2aeae7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="catalogenvironments-ssisdb-database"></a>catalog.environments (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает подробные сведения о среде для всех сред в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Среды содержат переменные, на которые могут ссылаться проекты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|environment_id|**bigint**|Уникальный идентификатор среды.|  
|имя|**sysname**|Имя среды.|  
|folder_id|**bigint**|Уникальный идентификатор папки, в которой хранится среда.|  
|description|**nvarchar(1024)**|Описание среды. Это значение является необязательным.|  
|created_by_sid|**varbinary(85)**|Уникальный идентификатор безопасности пользователя, создавшего среду.|  
|created_by_name|**nvarchar(128)**|Имя пользователя, создавшего среду.|  
|created_time|**datetimeoffset**|Дата и время создания среды.|  
  
## <a name="remarks"></a>Замечания  
 В этом представлении отображается строка для каждой среды в каталоге. Имена сред уникальны только в пределах папки, где они находятся. Например, среда с именем `E1` может существовать в нескольких папках в каталоге, но в каждой папке может быть только одна среда с именем `E1`.  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ для среды  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
