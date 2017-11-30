---
title: "sys.xml_schema_facets (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_facets
- xml_schema_facets_TSQL
- sys.xml_schema_facets_TSQL
- xml_schema_facets
dev_langs: TSQL
helpviewer_keywords: sys.xml_schema_facets catalog view
ms.assetid: 4402dde9-1877-4872-8550-140dc2a177d2
caps.latest.revision: "33"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 782d0a0619831ade9ed4051d1f4195432f112667
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sysxmlschemafacets-transact-sql"></a>sys.xml_schema_facets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке каждого из аспектов (ограничений) определения типа xml (соответствует **sys.xml_types**).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|Идентификатор компонента (типа) XML, которому принадлежит данный аспект.|  
|**facet_id**|**int**|Идентификатор (порядковый номер, начиная с 1) аспекта, уникальный в пределах компонента.|  
|**Тип**|**char(2)**|Тип аспекта:<br /><br /> LG = длина<br /><br /> LN = минимальная длина<br /><br /> LX = максимальная длина<br /><br /> PT = шаблон (регулярное выражение)<br /><br /> EU = перечисление<br /><br /> IN = минимальное значение (включая)<br /><br /> IX = максимальное значение (включая)<br /><br /> EN = минимальное значение (исключая)<br /><br /> EX = максимальное значение (исключая)<br /><br /> DT = общее количество цифр<br /><br /> DF = количество цифр после запятой<br /><br /> WS = нормализация пробелов|  
|**kind_desc**|**nvarchar (60)**|Описание типа аспекта:<br /><br /> LENGTH<br /><br /> MINIMUM_LENGTH<br /><br /> MAXIMUM_LENGTH<br /><br /> PATTERN<br /><br /> ENUMERATION<br /><br /> MINIMUM_INCLUSIVE_VALUE<br /><br /> MAXIMUM_INCLUSIVE_VALUE<br /><br /> MINIMUM_EXCLUSIVE_VALUE<br /><br /> MAXIMUM_EXCLUSIVE_VALUE<br /><br /> TOTAL_DIGITS<br /><br /> FRACTION_DIGITS<br /><br /> WHITESPACE_NORMALIZATION|  
|**is_fixed**|**bit**|1 = аспект имеет фиксированное, предопределенное значение.<br /><br /> 0 = нет фиксированного значения. (по умолчанию).|  
|**значение**|**nvarchar (4000)**|Фиксированное, предопределенное значение аспекта.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML-схем &#40; Система типов XML &#41; Представления каталога &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
