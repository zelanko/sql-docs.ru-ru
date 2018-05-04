---
title: sys.xml_schema_types (Transact-SQL) | Документы Microsoft
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
- sys.xml_schema_types_TSQL
- xml_schema_types_TSQL
- sys.xml_schema_types
- xml_schema_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_types catalog view
ms.assetid: 441ba49d-f778-4fa1-98c4-ced375a01a34
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4ccdd29bb046ca8e76f8add821884ba0af7671c8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysxmlschematypes-transact-sql"></a>sys.xml_schema_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждого компонента схемы XML, которое относится к типу **symbol_space** из **T**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<Унаследованные столбцы >**||Наследует столбцы из [sys.xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**is_abstract**|**бит**|1 = Это абстрактный тип. Все экземпляры элементов этого типа необходимо использовать **xsi: Type** для указания производного типа, который не является абстрактным.<br /><br /> 0 = Это неабстрактный тип. (по умолчанию).|  
|**allows_mixed_content**|**бит**|1 = Разрешено смешанное содержимое.<br /><br /> 0 = Смешанное содержимое не допускается (по умолчанию).|  
|**is_extension_blocked**|**бит**|1 = замещение с расширением типа в экземплярах блокировано, если атрибуту блока на **complexType** определение или **blockDefault** атрибут предка \<схемы > информационную единицу элемента имеет значение «extension» или «#all».<br /><br /> 0 = Замещение с расширением не блокировано.|  
|**is_restriction_blocked**|**бит**|1 = замещение с ограничением типа в экземплярах блокировано, если атрибуту блока на **complexType** определение или **blockDefault** атрибут предка \<схемы > информационную единицу элемента имеет значение «restriction» или «#all».<br /><br /> 0 = замещение с ограничением не блокировано (по умолчанию).|  
|**is_final_extension**|**бит**|1 = наследование с расширением типа блокировано, если атрибута final **complexType** определение или **finalDefault** атрибут предка \<схемы > сведения об элементе элемент имеет значение «extension» или «#all».<br /><br /> 0 = расширение разрешено (по умолчанию).|  
|**is_final_restriction**|**бит**|1 = наследование с ограничением типа блокировано, если атрибута final простой или **complexType** определение или **finalDefault** атрибут предка \<схемы > элемент информация имеет значение «restriction» или «#all».<br /><br /> 0 = ограничение разрешено (по умолчанию).|  
|**is_final_list_member**|**бит**|1 = этот простой тип не может быть использован в качестве типа элемента списка.<br /><br /> 0 = этот тип является составным, либо он может быть использован в качестве типа элемента списка (по умолчанию).|  
|**is_final_union_member**|**бит**|1 = этот простой тип не может быть использован в качестве типа члена объединения.<br /><br /> 0 = сложный тип. или он может быть использован как тип члена объединения. (по умолчанию).|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML-схем &#40;системой типов XML&#41; представления каталога &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
