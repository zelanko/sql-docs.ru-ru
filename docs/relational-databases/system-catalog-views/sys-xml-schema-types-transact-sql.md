---
title: sys.xml_schema_types (Transact-SQL) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ce5530e160fe6473ff84fca0978b5fc467fe688
ms.sourcegitcommit: 04c031f7411aa33e2174be11dfced7feca8fbcda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "64945866"
---
# <a name="sysxmlschematypes-transact-sql"></a>sys.xml_schema_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке на каждый компонент схемы XML, имеющее тип, **symbol_space** из **T**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<наследуемые столбцы >**||Наследует столбцы из [sys.xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**is_abstract**|**bit**|1 = Это абстрактный тип. Все экземпляры элемента этого типа должны использовать **xsi: Type** для указания производного типа, не является абстрактным.<br /><br /> 0 = Это неабстрактный тип. (по умолчанию).|  
|**allows_mixed_content**|**bit**|1 = Разрешено смешанное содержимое.<br /><br /> 0 = Смешанное содержимое не допускается (по умолчанию).|  
|**is_extension_blocked**|**bit**|1 = замещение с расширением типа в экземплярах блокировано, если атрибуту block на **complexType** определение или **blockDefault** атрибут предка \<схемы > информационного элемента имеет значение «extension» или «#all».<br /><br /> 0 = Замещение с расширением не блокировано.|  
|**is_restriction_blocked**|**bit**|1 = замещение с ограничением типа в экземплярах блокировано, если атрибуту block на **complexType** определение или **blockDefault** атрибут предка \<схемы > информационного элемента имеет значение «restriction» или «#all».<br /><br /> 0 = замещение с ограничением не блокировано (по умолчанию).|  
|**is_final_extension**|**bit**|1 = наследование с расширением типа блокировано, если атрибута final **complexType** определение или **finalDefault** атрибут предка \<схемы > сведения об элементе элемент имеет значение «extension» или «#all».<br /><br /> 0 = расширение разрешено (по умолчанию).|  
|**is_final_restriction**|**bit**|1 = наследование с ограничением типа блокировано, если атрибута final простой или **complexType** определение или **finalDefault** атрибут предка \<схемы > элемент сведения элемента имеет значение «restriction» или «#all».<br /><br /> 0 = ограничение разрешено (по умолчанию).|  
|**is_final_list_member**|**bit**|1 = этот простой тип не может быть использован в качестве типа элемента списка.<br /><br /> 0 = этот тип является составным, либо он может быть использован в качестве типа элемента списка (по умолчанию).|  
|**is_final_union_member**|**bit**|1 = этот простой тип не может быть использован в качестве типа члена объединения.<br /><br /> 0 = сложный тип. или он может быть использован как тип члена объединения. (по умолчанию).|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML-схем &#40;системой типов XML&#41; представления каталога &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
