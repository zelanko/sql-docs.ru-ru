---
title: syscollector_collector_types (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fbfbf38e084d147e13705ae76ac5367b697c5fe6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730144"
---
# <a name="syscollector_collector_types-transact-sql"></a>syscollector_collector_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

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
|**is_system**|**bit**|Включено (1) или OFF (0), чтобы указать, был ли тип сборщика передан сборщиком данных или добавлен позже **dc_admin**. Данный тип сбора может являться пользовательским типом собственной или сторонней разработки. Не допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется SELECT для **dc_operator**, **dc_proxy**.  
  
## <a name="change-history"></a>Журнал изменений  
  
|Обновленное содержимое|  
|---------------------|  
|Имя столбца **collection_type_uid** изменено на **collector_type_uid**.|  
|Исправлено описание столбца **parameter_schema** , чтобы указать, что значение допускает значения NULL.|  
|Добавлен столбец **parameter_formatter** .|  
|Исправлен тип данных для столбца **collection_package_path** и Обновлено описание, указывающее, что значение допускает значения NULL.|  
|Исправлен тип данных для столбца **upload_package_path** и Обновлено описание, указывающее, что значение допускает значения NULL.|  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры сборщика данных &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Представления сборщика данных &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
