---
title: sys.xml_schema_elements (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sys.xml_schema_elements
- sys.xml_schema_elements_TSQL
- xml_schema_elements
- xml_schema_elements_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_elements catalog view
ms.assetid: 190ed0cd-0c5e-4607-9db4-9e77cacf17d7
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e96d6dee82b82a38c16d3d697d880416b2ea0e3f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysxmlschemaelements-transact-sql"></a>sys.xml_schema_elements (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждого компонента схемы XML, которое относится к типу **symbol_space** из **E**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<Унаследованные столбцы >**|**--**|Наследует столбцы из [sys.xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**is_default_fixed**|**бит**|1 = значение по умолчанию зафиксировано. Это значение не может быть заменено экземпляром XML.<br /><br /> 0 = значение по умолчанию не зафиксировано для элемента (по умолчанию).|  
|**is_abstract**|**бит**|1 = элемент является абстрактным, его нельзя применять в документе экземпляра. Член группы подстановки элемента должен присутствовать в документе экземпляра.<br /><br /> 0 = элемент не является абстрактным (по умолчанию).|  
|**is_nillable**|**бит**|1 = элемент можно сделать пустым.<br /><br /> 0 = элемент нельзя сделать пустым (по умолчанию).|  
|**must_be_qualified**|**бит**|1 = для элемента должно быть явно указано пространство имен.<br /><br /> 0 = пространство имен для элемента может быть указано неявно (по умолчанию).|  
|**is_extension_blocked**|**бит**|1 = замена экземпляром типа расширения блокируется.<br /><br /> 0 = замена типом расширения разрешена (по умолчанию).|  
|**is_restriction_blocked**|**бит**|1 = замена экземпляром типа ограничения блокируется.<br /><br /> 0 = Замена типом ограничения разрешена (по умолчанию).|  
|**is_substitution_blocked**|**бит**|1 = невозможно применить экземпляр группы подстановки.<br /><br /> 0 = замена группой подстановки разрешена (по умолчанию).|  
|**is_final_extension**|**бит**|1 = замена экземпляром типа расширения запрещена.<br /><br /> 0 = замена в экземпляре типа расширения разрешена (по умолчанию).|  
|**is_final_restriction**|**бит**|1 = замена экземпляром типа ограничения запрещена.<br /><br /> 0 = замена в экземпляре типа ограничения разрешена (по умолчанию).|  
|**default_value**|**nvarchar (4000)**|Значение элемента по умолчанию. Если значение по умолчанию не задано, то значение равно NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML-схем &#40;системой типов XML&#41; представления каталога &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
