---
title: catalog.environments (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 7014c0e3-65dc-4a46-842e-4decf3737748
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fceaa62ab54099181ae4d4842f40e0250d37ee6a
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="catalogenvironments-ssisdb-database"></a>catalog.environments (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает подробные сведения о среде для всех сред в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Среды содержат переменные, на которые могут ссылаться проекты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
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
  
  
