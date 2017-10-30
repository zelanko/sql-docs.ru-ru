---
title: "Catalog.environment_references (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: efec53ef-3e5a-4b76-b71d-a0cf9e11ac00
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ee6f15af7a5384fea850aa67c7b5a95483530740
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogenvironmentreferences-ssisdb-database"></a>catalog.environment_references (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает ссылки на среду для всех проектов в **SSISDB** каталога.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|reference_id|**bigint**|Уникальный идентификатор (ID) ссылки.|  
|project_id|**bigint**|Уникальный идентификатор проекта.|  
|reference_type|**char(1)**|Указывает, может среда находиться в той же папке, что и проект (относительная ссылка), или в другой папке (абсолютная ссылка). Если значение равно `R`, для определения расположения сред используется относительная ссылка. Если значение равно `A`, то для определения расположения сред используется абсолютная ссылка.|  
|environment_folder_name|**sysname**|Имя папки в случае, если для определения местоположения среды используется абсолютная ссылка.|  
|environment_name|**sysname**|Имя среды, на которую ссылается проект.|  
|validation_status|**char(1)**|Состояние проверки.|  
|last_validation_time|**datatimeoffset(7)**|Время последней проверки.|  
  
## <a name="remarks"></a>Замечания  
 В этом представлении отображается строка для каждой ссылки на среду в каталоге.  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на соответствующий проект  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера.  
  
> [!NOTE]  
>  Наличие разрешения READ на проект влечет за собой также наличие разрешения READ на все пакеты и ссылки на среду, связанные с этим проектом. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
## <a name="remarks"></a>Замечания  
 Проект может иметь относительные или абсолютные ссылки на среду. Относительные ссылки указывают среду по имени и требуют, чтобы она находилась в той же папке, что и проект. Абсолютные ссылки указывают среду с применением имени и папки и могут указывать среды, находящиеся в иной папке, чем проект. Проект может ссылаться на несколько сред.  
  
  

