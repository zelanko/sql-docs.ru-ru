---
title: sys. xml_schema_types (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_types_TSQL
- xml_schema_types_TSQL
- sys.xml_schema_types
- xml_schema_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_types catalog view
ms.assetid: 441ba49d-f778-4fa1-98c4-ced375a01a34
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 356e73e2b90d059117cadef436bcea27498c9871
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824969"
---
# <a name="sysxml_schema_types-transact-sql"></a>sys.xml_schema_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку на каждый компонент схемы XML, являющийся типом **Symbol_space** **T**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<наследуемые столбцы>**||Наследует столбцы из [sys. xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**is_abstract**|**bit**|1 = Это абстрактный тип. Все экземпляры элемента этого типа должны использовать **xsi: Type** для обозначения производного типа, который не является абстрактным.<br /><br /> 0 = Это неабстрактный тип. (по умолчанию).|  
|**allows_mixed_content**|**bit**|1 = Разрешено смешанное содержимое.<br /><br /> 0 = Смешанное содержимое не допускается (по умолчанию).|  
|**is_extension_blocked**|**bit**|1 = замена с расширением типа блокируется в экземплярах, если атрибуту Block в определении **complexType** или атрибуту **blockDefault** схемы-предка \<> элемента сведений о элементе задано значение "Extension" или "#all".<br /><br /> 0 = Замещение с расширением не блокировано.|  
|**is_restriction_blocked**|**bit**|1 = замена с ограничением типа блокируется в экземплярах, если атрибуту Block в определении **complexType** или атрибуту **blockDefault** схемы предка \<> элемент сведений об элементе задано значение "restriction" или "#all".<br /><br /> 0 = замещение с ограничением не блокировано (по умолчанию).|  
|**is_final_extension**|**bit**|1 = наследование по расширению типа блокируется, если атрибуту Final в определении **complexType** или атрибуту **finalDefault** схемы предка \<> элемент сведений о элементе задано значение "Extension" или "#all".<br /><br /> 0 = расширение разрешено (по умолчанию).|  
|**is_final_restriction**|**bit**|1 = производное ограничение типа блокируется, если атрибуту Final в определении Simple или **complexType** или атрибутом **finalDefault** схемы предка> элемент \< сведений об элементе задано значение "ограничение" или "#all".<br /><br /> 0 = ограничение разрешено (по умолчанию).|  
|**is_final_list_member**|**bit**|1 = этот простой тип не может быть использован в качестве типа элемента списка.<br /><br /> 0 = этот тип является составным, либо он может быть использован в качестве типа элемента списка (по умолчанию).|  
|**is_final_union_member**|**bit**|1 = этот простой тип не может быть использован в качестве типа члена объединения.<br /><br /> 0 = сложный тип. или он может быть использован как тип члена объединения. (по умолчанию).|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Схемы XML &#40;представления каталога системы типов XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
