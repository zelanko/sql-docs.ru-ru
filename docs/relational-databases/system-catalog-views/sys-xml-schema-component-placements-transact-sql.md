---
description: sys.xml_schema_component_placements (Transact-SQL)
title: sys.xml_schema_component_placements (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_component_placements
- xml_schema_component_placements_TSQL
- xml_schema_component_placements
- sys.xml_schema_component_placements_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_component_placements catalog view
ms.assetid: 2d3c8828-e4b3-423d-bf11-990464c1341b
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: b4b971fe631671d193340fc3c68b8e4e235c178f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88400710"
---
# <a name="sysxml_schema_component_placements-transact-sql"></a>sys.xml_schema_component_placements (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает по одной строке на размещение для компонентов схемы XML.  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|Идентификатор компонента схемы XML, который является владельцем этого размещения.|  
|**placement_id**|**int**|Идентификатор размещения. Идентификатор уникален относительно своего владельца, компонента XML-схемы.|  
|**placed_xml_component_id**|**int**|Идентификатор размещенного компонента XML-схемы.|  
|**is_default_fixed**|**bit**|1 = значение по умолчанию зафиксировано. Это значение не может быть заменено в экземпляре XML.<br /><br /> 0 = Значение может быть переопределено (по умолчанию).|  
|**min_occurrences**|**int**|Минимальное количество экземпляров размещенного компонента.|  
|**max_occurrences**|**int**|Максимальное количество экземпляров размещенного компонента.|  
|**default_value**|**nvarchar (4000)**|Значение по умолчанию, если оно предоставляется. Если значение по умолчанию не задано, то значение равно NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Схемы XML &#40;представления каталога системы типов XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
