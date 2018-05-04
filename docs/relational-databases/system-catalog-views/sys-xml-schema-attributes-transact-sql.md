---
title: sys.xml_schema_attributes (Transact-SQL) | Документы Microsoft
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
- xml_schema_attributes_TSQL
- xml_schema_attributes
- sys.xml_schema_attributes_TSQL
- sys.xml_schema_attributes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_attributes catalog view
ms.assetid: dd0c98aa-5e72-4df6-96d9-482786c8dbb1
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d95afebdbf6cd086f5d7908cc528929e5c26f79b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysxmlschemaattributes-transact-sql"></a>sys.xml_schema_attributes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждого компонента схемы XML, который является атрибутом, **symbol_space** из **A**.  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<Унаследованные столбцы >**|--|Наследует от [sys.xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**is_default_fixed**|**бит**|1 = значение по умолчанию зафиксировано. Это значение не может быть заменено в экземпляре XML.<br /><br /> 0 = значение по умолчанию не зафиксировано для атрибута (по умолчанию).|  
|**must_be_qualified**|**бит**|1 = для атрибута должно быть явно указано пространство имен.<br /><br /> 0 = пространство имен для атрибута может быть указано неявно (по умолчанию).|  
|**default_value**|**nvarchar**<br /><br /> **(4000)**|Значение атрибута по умолчанию. Если значение по умолчанию не задано, то значение равно NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [XML-схем &#40;системой типов XML&#41; представления каталога &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
