---
title: sys.xml_schema_components (Transact-SQL) | Документы Microsoft
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
- xml_schema_components
- sys.xml_schema_components_TSQL
- sys.xml_schema_components
- xml_schema_components_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_components catalog view
ms.assetid: 70142d3a-f8b5-4ee2-8287-3935f0f67aa2
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7abdf05c9376d9a603003da9503669774e82341f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysxmlschemacomponents-transact-sql"></a>sys.xml_schema_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке на каждый компонент XML-схемы. Пара (**collection_id**, **namespace_id**) представляет собой составной внешний ключ для содержащего пространства имен. Для именованных компонентов значения для **symbol_space**, **имя**, **scoping_xml_component_id**, **is_qualified**,  **xml_namespace_id**, **xml_collection_id** являются уникальными.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|Уникальный идентификатор компонента схемы XML в базе данных.|  
|**xml_collection_id**|**int**|Идентификатор коллекции XML-схем, содержащей пространство имен данного компонента.|  
|**xml_namespace_id**|**int**|Идентификатор пространства имен XML в пределах коллекции.|  
|**is_qualified**|**бит**|1 = данный компонент имеет явный квалификатор пространства имен.<br /><br /> 0 = это компонент локальной области. В этом случае пара **namespace_id**, **collection_id**, ссылается на «нет пространство имен» **targetNamespace**.<br /><br /> Для компонентов с подстановкой это значение может быть равным 1.|  
|**name**|**nvarchar**<br /><br /> **(4000)**|Уникальное имя компонента XML-схемы. Если значение равно NULL, компонент является неименованным.|  
|**symbol_space**|**char(1)**|Место, в котором имя символа уникально, на основе **вид**:<br /><br /> N = нет<br /><br /> T = тип<br /><br /> E = элемент<br /><br /> M = модель-группа<br /><br /> A = атрибут<br /><br /> G = атрибут-группа|  
|**symbol_space_desc**|**nvarchar**<br /><br /> **(60)**|Описание пространства, в котором имя символа уникально, на основе **вид**:<br /><br /> None<br /><br /> TYPE<br /><br /> ELEMENT<br /><br /> MODEL_GROUP<br /><br /> ATTRIBUTE<br /><br /> ATTRIBUTE_GROUP|  
|**Тип**|**char(1)**|Разновидность компонента схемы XML.<br /><br /> N = любой тип (особый внутренний компонент)<br /><br /> Z = любой простой тип (особый внутренний компонент)<br /><br /> P = примитивный тип (внутренние типы)<br /><br /> S = простой тип<br /><br /> L = перечисляемый тип<br /><br /> U = тип объединения<br /><br /> C = составной простой тип (производный от простого)<br /><br /> K = составной тип<br /><br /> E = элемент<br /><br /> M = модель-группа<br /><br /> W = элемент-подстановка<br /><br /> A = атрибут<br /><br /> G = атрибут-группа<br /><br /> V = атрибут-подстановка|  
|**kind_desc**|**nvarchar**<br /><br /> **(60)**|Описание разновидности компонента схемы XML:<br /><br /> ANY_TYPE<br /><br /> ANY_SIMPLE_TYPE<br /><br /> PRIMITIVE_TYPE<br /><br /> SIMPLE_TYPE<br /><br /> LIST_TYPE<br /><br /> UNION_TYPE<br /><br /> COMPLEX_SIMPLE_TYPE<br /><br /> COMPLEX_TYPE<br /><br /> ELEMENT<br /><br /> MODEL_GROUP<br /><br /> ELEMENT_WILDCARD<br /><br /> ATTRIBUTE<br /><br /> ATTRIBUTE_GROUP<br /><br /> ATTRIBUTE_WILDCARD|  
|**наследование**|**char(1)**|Метод выведения производных типов:<br /><br /> N = нет (не выводится)<br /><br /> X = расширение<br /><br /> R = ограничение<br /><br /> S = замена|  
|**derivation_desc**|**nvarchar**<br /><br /> **(60)**|Описание метода выведения производных типов:<br /><br /> None<br /><br /> EXTENSION<br /><br /> RESTRICTION<br /><br /> SUBSTITUTION|  
|**base_xml_component_id**|**int**|Идентификатор компонента, от которого выводится производный компонент. NULL в случае отсутствия такового.|  
|**scoping_xml_component_id**|**int**|Уникальный идентификатор компонента области. NULL в случае отсутствия такового (глобальная область).|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML-схем &#40;системой типов XML&#41; представления каталога &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
