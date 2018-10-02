---
title: catalog.object_parameters (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: d7b04903-2d61-4159-9456-475942d1f732
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0afd8f494474c54eaf911f6cd7b8f74c9ec1a287
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729562"
---
# <a name="catalogobjectparameters-ssisdb-database"></a>catalog.object_parameters (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает параметры для всех пакетов и проектов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
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
|value_type|**char(1)**|Указывает тип значения параметра. Поле отображает `V`, если parameter_value имеет символьное значение, и `R`, если значение приписывается посредством ссылки на переменную среды.|  
|value_set|**bit**|Если значение равно `1`, то значение параметра было назначено. Если значение равно `0`, то значение параметра не было назначено.|  
|referenced_variable_name|**nvarchar(128)**|Имя переменной среды, назначенное значению параметра. Значение по умолчанию — **NULL**.|  
|validation_status|**char(1)**|Указано только в ознакомительных целях. Не используется в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|last_validation_time|**datetimeoffset(7)**|Указано только в ознакомительных целях. Не используется в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
## <a name="permissions"></a>Разрешения  
 Для просмотра строк в этом представлении необходимо иметь одно из следующих разрешений:  
  
-   Разрешение READ на проект  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**.  
  
 Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
