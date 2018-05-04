---
title: syscollector_collector_types (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syscollector_collector_types
- syscollector_collector_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_collector_types view
ms.assetid: d5cd30bb-89fd-4814-a7e8-9074f043f90f
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9c56b03d902a329e47496b81d4f16e7f35f4bd39
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="syscollectorcollectortypes-transact-sql"></a>syscollector_collector_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет сведения о типе сборщика для элемента сбора.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**collector_type_uid**|**uniqueidentifer**|Идентификатор GUID типа сбора. Не допускает значение NULL.|  
|**name**|**sysname**|Имя данного типа сбора. Не допускает значение NULL.|  
|**parameter_schema**|**xml**|Схема XML, описывающая конфигурацию заданного типа сборщика. Данная схема XML используется для проверки действительной XML-конфигурации, связанной с конкретным экземпляром элемента сбора. Допускает значение NULL.|  
|**parameter_formatter**|**xml**|Определяет шаблон, применяемый для преобразования XML с целью его использования на странице свойств набора сбора. Допускает значение NULL.|  
|**collection_package_id**|**uniqueidentifer**|Идентификатор GUID пакета сбора. Не допускает значение NULL.|  
|**collection_package_path**|**nvarchar(4000)**|Предоставляет путь к пакету сбора. Допускает значение NULL.|  
|**collection_package_name**|**sysname**|Имя пакета сбора. Не допускает значение NULL.|  
|**upload_package_id**|**uniqueidentifer**|Идентификатор GUID пакета передачи. Не допускает значение NULL.|  
|**upload_package_path**|**nvarchar(4000)**|Предоставляет путь к пакету передачи. Допускает значение NULL.|  
|**upload_package_name**|**sysname**|Имя пакета передачи. Не допускает значение NULL.|  
|**is_system**|**бит**|Включен (1) или off (0), чтобы указать, если тип сборщика был поставлен со сборщиком данных или если он был добавлен пользователем позже **dc_admin**. Данный тип сбора может являться пользовательским типом собственной или сторонней разработки. Не допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для **dc_operator**, **dc_proxy**.  
  
## <a name="change-history"></a>Журнал изменений  
  
|Обновленное содержимое|  
|---------------------|  
|Обновить **collection_type_uid** имя столбца, чтобы **аргумент collector_type_uid**.|  
|Исправлено описание для **parameter_schema** столбец для указания, что он допускает значения NULL.|  
|Добавлен **parameter_formatter** столбца.|  
|Исправлен тип данных для **collection_package_path** столбца, обновлено описание, чтобы указать, что он допускает значения NULL.|  
|Исправлен тип данных для **upload_package_path** столбца, обновлено описание, чтобы указать, что он допускает значения NULL.|  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Представления сборщика данных (Transact-SQL)](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
