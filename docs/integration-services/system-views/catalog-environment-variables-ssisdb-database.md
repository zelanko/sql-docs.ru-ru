---
title: catalog.environment_variables (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 45f5aacd-505a-443b-8fc2-c7929e78cff8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de22e52f25658f467ed21952b1eb32356e4ff5af
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912683"
---
# <a name="catalogenvironment_variables-ssisdb-database"></a>catalog.environment_variables (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает подробные сведения о переменных среды для всех сред в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|variable_id|**bigint**|Уникальный идентификатор переменной среды.|  
|environment_id|**bigint**|Уникальный идентификатор среды, с которой связана переменная.|  
|name|**sysname**|Имя переменной среды.|  
|description|**nvarchar(1024)**|Описание переменной среды.|  
|type|**nvarchar(128)**|Тип данных переменной среды.|  
|sensitive|**bit**|Если значение равно `1`, переменная является конфиденциальной и шифруется при сохранении. Если значение равно `0`, переменная не является конфиденциальной и ее значение сохраняется в формате открытого текста.|  
|value|**sql_variant**|Значение переменной среды. Если значение sensitive равно `0`, отображается значение в виде открытого текста. Если значение sensitive равно `1`, отображается значение **NULL**.|  
  
## <a name="remarks"></a>Remarks  
 В этом представлении отображается по одной строке для каждой из переменных среды в каталоге.  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   разрешение READ на соответствующую среду  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
