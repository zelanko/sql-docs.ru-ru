---
title: sys. xml_schema_elements (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1be210ca687ff19c5e1dfaf56923a55c731807c1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831295"
---
# <a name="sysxml_schema_elements-transact-sql"></a>sys.xml_schema_elements (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку на каждый компонент схемы XML, являющийся типом, **symbol_space** из **E**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<наследуемые столбцы>**|**--**|Наследует столбцы из [sys. xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**is_default_fixed**|**bit**|1 = значение по умолчанию зафиксировано. Это значение не может быть заменено экземпляром XML.<br /><br /> 0 = значение по умолчанию не зафиксировано для элемента (по умолчанию).|  
|**is_abstract**|**bit**|1 = элемент является абстрактным, его нельзя применять в документе экземпляра. Член группы подстановки элемента должен присутствовать в документе экземпляра.<br /><br /> 0 = элемент не является абстрактным (по умолчанию).|  
|**is_nillable**|**bit**|1 = элемент можно сделать пустым.<br /><br /> 0 = элемент нельзя сделать пустым (по умолчанию).|  
|**must_be_qualified**|**bit**|1 = для элемента должно быть явно указано пространство имен.<br /><br /> 0 = пространство имен для элемента может быть указано неявно (по умолчанию).|  
|**is_extension_blocked**|**bit**|1 = замена экземпляром типа расширения блокируется.<br /><br /> 0 = замена типом расширения разрешена (по умолчанию).|  
|**is_restriction_blocked**|**bit**|1 = замена экземпляром типа ограничения блокируется.<br /><br /> 0 = Замена типом ограничения разрешена (по умолчанию).|  
|**is_substitution_blocked**|**bit**|1 = невозможно применить экземпляр группы подстановки.<br /><br /> 0 = замена группой подстановки разрешена (по умолчанию).|  
|**is_final_extension**|**bit**|1 = замена экземпляром типа расширения запрещена.<br /><br /> 0 = замена в экземпляре типа расширения разрешена (по умолчанию).|  
|**is_final_restriction**|**bit**|1 = замена экземпляром типа ограничения запрещена.<br /><br /> 0 = замена в экземпляре типа ограничения разрешена (по умолчанию).|  
|**default_value**|**nvarchar (4000)**|Значение элемента по умолчанию. Если значение по умолчанию не задано, то значение равно NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Схемы XML &#40;представления каталога системы типов XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
