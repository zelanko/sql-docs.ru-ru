---
title: catalog.execution_parameter_values (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: ec93e67b-04ce-4aae-ab96-3ad20e9793ad
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 05b8024ababbe6e0c07ee72e50d844609c7a816c
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58281498"
---
# <a name="catalogexecutionparametervalues-ssisdb-database"></a>catalog.execution_parameter_values (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает фактические значения параметров, которые используются пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на экземпляре выполнения.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|execution_parameter_id|**bigint**|Уникальный идентификатор (ID) параметра исполнения.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра исполнения.|  
|object_type|**smallint**|Если значение равно `20`, то параметр принадлежит проекту. Если значение равно `30`, то параметр принадлежит пакету. Если значение равно `50`, параметр принимает одно из следующих значений:<br /><br /> **LOGGING_LEVEL**<br /><br /> **DUMP_ON_ERROR**<br /><br /> **DUMP_ON_EVENT**<br /><br /> **DUMP_EVENT_CODE**<br /><br /> **CALLER_INFO**<br /><br /> **SYNCHRONIZED**|  
|parameter_data_type|**nvarchar(128)**|Тип данных параметра.|  
|parameter_name|**sysname**|Имя параметра.|  
|parameter_value|**sql_variant**|Значение параметра. Если значение sensitive равно `0`, отображается значение в виде открытого текста. Если значение sensitive равно `1`, отображается значение **NULL**.|  
|sensitive|**bit**|Если значение равно `1`, значение параметра конфиденциально. Если значение равно `0`, то значение параметра не конфиденциально.|  
|required|**bit**|Если значение равно `1`, то значение параметра необходимо для начала выполнения. Если значение равно `0`, то значение параметра не является необходимым для начала выполнения.|  
|value_set|**bit**|Если значение равно `1`, то значение параметра было назначено. Если значение равно `0`, то значение параметра не было назначено.|  
|runtime_override|**bit**|Если значение равно `1`, это означает, что перед началом исполнения значение параметра было изменено. Если значение равно `0`, это означает, что сохранено исходное значение параметра.|  
  
## <a name="remarks"></a>Remarks  
 В этом представлении отображается одна строка для каждого параметра исполнения. Параметр исполнения имеет значение, приписанное параметру проекта или пакета в течение одного экземпляра исполнения.  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
