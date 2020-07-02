---
title: sys.xml_schema_components (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
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
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 12e0064d70c535ff3a777bfef38e85e2f7c2a724
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754340"
---
# <a name="sysxml_schema_components-transact-sql"></a>sys.xml_schema_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает по строке на каждый компонент XML-схемы. Пара (**collection_id**, **namespace_id**) является составным внешним ключом для содержащего его пространства имен. Для именованных компонентов значения **symbol_space**, **Name**, **scoping_xml_component_id**, **is_qualified**, **xml_namespace_id**, **xml_collection_id** являются уникальными.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|Уникальный идентификатор компонента схемы XML в базе данных.|  
|**xml_collection_id**|**int**|Идентификатор коллекции XML-схем, содержащей пространство имен данного компонента.|  
|**xml_namespace_id**|**int**|Идентификатор пространства имен XML в пределах коллекции.|  
|**is_qualified**|**bit**|1 = данный компонент имеет явный квалификатор пространства имен.<br /><br /> 0 = это компонент локальной области. В этом случае пара **namespace_id**, **collection_id**, относится к пространству имен **targetNamespace**.<br /><br /> Для компонентов с подстановкой это значение может быть равным 1.|  
|**name**|**nvarchar**<br /><br /> **(4000)**|Уникальное имя компонента XML-схемы. Если значение равно NULL, компонент является неименованным.|  
|**symbol_space**|**char (1)**|Пространство, в котором имя символа уникально, в зависимости от **вида**:<br /><br /> N = нет<br /><br /> T = тип<br /><br /> E = элемент<br /><br /> M = модель-группа<br /><br /> A = атрибут<br /><br /> G = атрибут-группа|  
|**symbol_space_desc**|**nvarchar**<br /><br /> **(60)**|Описание пространства, в котором имя символа уникально на основе **типа**:<br /><br /> NONE<br /><br /> TYPE<br /><br /> ELEMENT<br /><br /> MODEL_GROUP<br /><br /> ATTRIBUTE<br /><br /> ATTRIBUTE_GROUP|  
|**особого**|**char (1)**|Разновидность компонента схемы XML.<br /><br /> N = любой тип (особый внутренний компонент)<br /><br /> Z = любой простой тип (особый внутренний компонент)<br /><br /> P = примитивный тип (внутренние типы)<br /><br /> S = простой тип<br /><br /> L = перечисляемый тип<br /><br /> U = тип объединения<br /><br /> C = составной простой тип (производный от простого)<br /><br /> K = составной тип<br /><br /> E = элемент<br /><br /> M = модель-группа<br /><br /> W = элемент-подстановка<br /><br /> A = атрибут<br /><br /> G = атрибут-группа<br /><br /> V = атрибут-подстановка|  
|**kind_desc**|**nvarchar**<br /><br /> **(60)**|Описание разновидности компонента схемы XML:<br /><br /> ANY_TYPE<br /><br /> ANY_SIMPLE_TYPE<br /><br /> PRIMITIVE_TYPE<br /><br /> SIMPLE_TYPE<br /><br /> LIST_TYPE<br /><br /> UNION_TYPE<br /><br /> COMPLEX_SIMPLE_TYPE<br /><br /> COMPLEX_TYPE<br /><br /> ELEMENT<br /><br /> MODEL_GROUP<br /><br /> ELEMENT_WILDCARD<br /><br /> ATTRIBUTE<br /><br /> ATTRIBUTE_GROUP<br /><br /> ATTRIBUTE_WILDCARD|  
|**рожден**|**char (1)**|Метод выведения производных типов:<br /><br /> N = нет (не выводится)<br /><br /> X = расширение<br /><br /> R = ограничение<br /><br /> S = замена|  
|**derivation_desc**|**nvarchar**<br /><br /> **(60)**|Описание метода выведения производных типов:<br /><br /> NONE<br /><br /> EXTENSION<br /><br /> RESTRICTION<br /><br /> SUBSTITUTION|  
|**base_xml_component_id**|**int**|Идентификатор компонента, от которого выводится производный компонент. NULL в случае отсутствия такового.|  
|**scoping_xml_component_id**|**int**|Уникальный идентификатор компонента области. NULL в случае отсутствия такового (глобальная область).|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Схемы XML &#40;представления каталога системы типов XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
