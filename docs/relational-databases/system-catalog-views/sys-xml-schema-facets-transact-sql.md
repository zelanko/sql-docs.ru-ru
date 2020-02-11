---
title: sys. xml_schema_facets (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_facets
- xml_schema_facets_TSQL
- sys.xml_schema_facets_TSQL
- xml_schema_facets
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_facets catalog view
ms.assetid: 4402dde9-1877-4872-8550-140dc2a177d2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 41e00ca05205fcb1384d436de2f423c63e05ba5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103363"
---
# <a name="sysxml_schema_facets-transact-sql"></a>sys.xml_schema_facets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждого аспекта (ограничения) определения типа XML (соответствует **sys. xml_types**).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|Идентификатор компонента (типа) XML, которому принадлежит данный аспект.|  
|**facet_id**|**int**|Идентификатор (порядковый номер, начиная с 1) аспекта, уникальный в пределах компонента.|  
|**kind**|**char (2)**|Тип аспекта:<br /><br /> LG = длина<br /><br /> LN = минимальная длина<br /><br /> LX = максимальная длина<br /><br /> PT = шаблон (регулярное выражение)<br /><br /> EU = перечисление<br /><br /> IN = минимальное значение (включая)<br /><br /> IX = максимальное значение (включая)<br /><br /> EN = минимальное значение (исключая)<br /><br /> EX = максимальное значение (исключая)<br /><br /> DT = общее количество цифр<br /><br /> DF = количество цифр после запятой<br /><br /> WS = нормализация пробелов|  
|**kind_desc**|**nvarchar (60)**|Описание типа аспекта:<br /><br /> LENGTH<br /><br /> MINIMUM_LENGTH<br /><br /> MAXIMUM_LENGTH<br /><br /> PATTERN<br /><br /> ENUMERATION<br /><br /> MINIMUM_INCLUSIVE_VALUE<br /><br /> MAXIMUM_INCLUSIVE_VALUE<br /><br /> MINIMUM_EXCLUSIVE_VALUE<br /><br /> MAXIMUM_EXCLUSIVE_VALUE<br /><br /> TOTAL_DIGITS<br /><br /> FRACTION_DIGITS<br /><br /> WHITESPACE_NORMALIZATION|  
|**is_fixed**|**bit**|1 = аспект имеет фиксированное, предопределенное значение.<br /><br /> 0 = нет фиксированного значения. (по умолчанию).|  
|**значений**|**nvarchar (4000)**|Фиксированное, предопределенное значение аспекта.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Схемы XML &#40;представления каталога системы типов XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
