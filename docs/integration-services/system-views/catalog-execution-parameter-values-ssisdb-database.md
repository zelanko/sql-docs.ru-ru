---
title: "Catalog.execution_parameter_values (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: ec93e67b-04ce-4aae-ab96-3ad20e9793ad
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 60907a82f3d0bb9f273355fd6bfbd7378ce72c9f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutionparametervalues-ssisdb-database"></a>catalog.execution_parameter_values (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает фактические значения параметров, которые используются пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на экземпляре выполнения.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|execution_parameter_id|**bigint**|Уникальный идентификатор (ID) параметра исполнения.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра исполнения.|  
|object_type|**smallint**|Если значение равно `20`, то параметр принадлежит проекту. Если значение равно `30`, то параметр принадлежит пакету. Если значение равно `50`, параметр принадлежит к одному из следующих действий:<br /><br /> **LOGGING_LEVEL**<br /><br /> **DUMP_ON_ERROR**<br /><br /> **DUMP_ON_EVENT**<br /><br /> **DUMP_EVENT_CODE**<br /><br /> **CALLER_INFO**<br /><br /> **СИНХРОНИЗАЦИЯ**|  
|parameter_data_type|**nvarchar(128)**|Тип данных параметра.|  
|parameter_name|**sysname**|Имя параметра.|  
|parameter_value|**sql_variant**|Значение параметра. Если конфиденциальные является `0`, отображается значение открытого текста. Если конфиденциальные — `1`, **NULL** отображается значение.|  
|sensitive|**bit**|Если значение равно `1`, значение параметра конфиденциально. Если значение равно `0`, то значение параметра не конфиденциально.|  
|required|**bit**|Если значение равно `1`, то значение параметра необходимо для начала выполнения. Если значение равно `0`, то значение параметра не является необходимым для начала выполнения.|  
|value_set|**bit**|Если значение равно `1`, то значение параметра было назначено. Если значение равно `0`, то значение параметра не было назначено.|  
|runtime_override|**bit**|Если значение равно `1`, это означает, что перед началом исполнения значение параметра было изменено. Если значение равно `0`, это означает, что сохранено исходное значение параметра.|  
  
## <a name="remarks"></a>Замечания  
 В этом представлении отображается одна строка для каждого параметра исполнения. Параметр исполнения имеет значение, приписанное параметру проекта или пакета в течение одного экземпляра исполнения.  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
