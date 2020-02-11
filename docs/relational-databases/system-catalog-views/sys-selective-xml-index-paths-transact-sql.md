---
title: sys. selective_xml_index_paths (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
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
ms.assetid: 07a73d71-ec3e-4894-947a-5859ca62c606
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 9ff85273a1e970b3bb891d1816a96019dd4f3ae5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135193"
---
# <a name="sysselective_xml_index_paths-transact-sql"></a>sys.selective_xml_index_paths (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Как предусмотрено, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 1 (SP1), каждая строка в представлении sys.selective_xml_index_paths содержит один развернутый путь для конкретного избирательного индекса xml.  
  
 При создании избирательного индекса xml на столбце xmlcol таблицы T с использованием следующей инструкции  
  
```  
CREATE SELECTIVE XML INDEX sxi1 ON T(xmlcol)   
FOR ( path1 = '/a/b/c' AS XQUERY 'xs:string',  
      path2 = '/a/b/d' AS XQUERY 'xs:double'  
    )  
```  
  
 Появятся две новые строки в представлении sys.selective_xml_index_paths, соответствующие индексу sxi1.  

  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор таблицы со столбцом XML.|  
|**index_id**|**int**|Уникальный идентификатор избирательного индекса xml.|  
|**path_id**|**int**|Идентификатор развернутого пути XML.|  
|**путь**|**nvarchar (4000)**|Развернутый путь. Например, /a/b/c/d/e.|  
|**name**|**имеет sysname**|Имя пути.|  
|**path_type**|**tinyint**|0 = XQUERY<br /><br /> 1 = SQL|  
|**path_type_desc**|**имеет sysname**|На основе значения **path_type** "XQuery" или "SQL".|  
|**xml_component_id**|**int**|Уникальный идентификатор компонента схемы XML в базе данных.|  
|**xquery_type_description**|**nvarchar (4000)**|Имя указанного типа xsd.|  
|**is_xquery_type_inferred**|**bit**|1 = тип является выведенным.|  
|**xquery_max_length**|**smallint**|Максимальная длина (типа xsd в символах).|  
|**is_xquery_max_length_inferred**|**bit**|1 = максимальная длина является выведенной.|  
|**is_node**|**bit**|0 = указание node() отсутствует.<br /><br /> 1 = применено указание оптимизации node().|  
|**system_type_id**|**tinyint**|Идентификатор системного типа столбца.|  
|**user_type_id**|**tinyint**|Идентификатор столбца пользовательского типа.|  
|**max_length**|**smallint**|Максимальная длина типа (в байтах).<br /><br /> -1 = типом данных столбца является varchar(max), nvarchar(max), varbinary(max) или xml.|  
|**precision**|**tinyint**|Максимальная точность типа, если это цифровой тип. В противном случае 0.|  
|**Измените**|**tinyint**|Максимальный масштаб типа, если это цифровой тип. В противном случае флагу присваивается значение 0.|  
|**collation_name**|**имеет sysname**|Имя параметров сортировки типа, если это символьный тип. В противном случае — значение NULL.|  
|**is_singleton**|**bit**|0 = указание SINGLETON отсутствует.<br /><br /> 1 = применено указание оптимизации SINGLETON.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Схемы XML &#40;представления каталога системы типов XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
