---
title: "Catalog.object_parameters (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: d7b04903-2d61-4159-9456-475942d1f732
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9d538e5b55ef4e8880afb2d008b11c17d9a03189
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogobjectparameters-ssisdb-database"></a>catalog.object_parameters (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает параметры для всех пакетов и проектов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|parameter_id|**bigint**|Уникальный идентификатор (ID) параметра.|  
|project_id|**bigint**|Уникальный идентификатор проекта.|  
|object_type|**smallint**|Тип параметра. Это значение равно `20` для параметра проекта и равно `30` для параметра пакета.|  
|object_name|**sysname**|Имя соответствующего проекта или пакета.|  
|parameter_name|**sysname(nvarchar(128))**|Имя параметра.|  
|Тип данных|**nvarchar(128)**|Тип данных параметра.|  
|required|**bit**|Если значение равно `1`, то значение параметра необходимо для начала выполнения. Если значение равно `0`, то значение параметра не является необходимым для начала выполнения.|  
|sensitive|**bit**|Если значение равно `1`, значение параметра конфиденциально. Если значение равно `0`, то значение параметра не конфиденциально.|  
|description|**nvarchar(1024)**|Необязательное описание пакета.|  
|design_default_value|**sql_variant**|Стандартное значение параметра, назначенное во время проектирования проекта или пакета.|  
|default_value|**sql_variant**|Значение по умолчанию, используемое сервером в настоящий момент.|  
|value_type|**char(1)**|Указывает тип значения параметра. В этом поле отображается `V` при parameter_value представляет собой литеральное значение и `R` при назначении значения с помощью ссылки на переменную среды.|  
|value_set|**bit**|Если значение равно `1`, то значение параметра было назначено. Если значение равно `0`, то значение параметра не было назначено.|  
|referenced_variable_name|**nvarchar(128)**|Имя переменной среды, назначенное значению параметра. Значение по умолчанию — **NULL**.|  
|validation_status|**char(1)**|Указано только в ознакомительных целях. Не используется в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|last_validation_time|**DateTimeOffset(7)**|Указано только в ознакомительных целях. Не используется в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
## <a name="permissions"></a>Permissions  
 Для просмотра строк в этом представлении необходимо иметь одно из следующих разрешений:  
  
-   Разрешение READ на проект  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера.  
  
 Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
