---
title: sys.selective_xml_index_paths (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 123258c5eceebe14a8b920b7917941cd83dc7b42
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47675352"
---
# <a name="sysselectivexmlindexpaths-transact-sql"></a>sys.selective_xml_index_paths (Transact-SQL)
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

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор таблицы со столбцом XML.|  
|**index_id**|**int**|Уникальный идентификатор избирательного индекса xml.|  
|**path_id**|**int**|Идентификатор развернутого пути XML.|  
|**путь**|**nvarchar(4000)**|Развернутый путь. Например, /a/b/c/d/e.|  
|**name**|**sysname**|Имя пути.|  
|**path_type**|**tinyint**|0 = XQUERY<br /><br /> 1 = SQL|  
|**path_type_desc**|**sysname**|На основе **path_type** значение «XQUERY» или «SQL».|  
|**xml_component_id**|**int**|Уникальный идентификатор компонента схемы XML в базе данных.|  
|**xquery_type_description**|**nvarchar(4000)**|Имя указанного типа xsd.|  
|**is_xquery_type_inferred**|**bit**|1 = тип является выведенным.|  
|**xquery_max_length**|**smallint**|Максимальная длина (типа xsd в символах).|  
|**is_xquery_max_length_inferred**|**bit**|1 = максимальная длина является выведенной.|  
|**is_node**|**bit**|0 = указание node() отсутствует.<br /><br /> 1 = применено указание оптимизации node().|  
|**system_type_id**|**tinyint**|Идентификатор системного типа столбца.|  
|**user_type_id**|**tinyint**|Идентификатор столбца пользовательского типа.|  
|**max_length**|**smallint**|Максимальная длина типа (в байтах).<br /><br /> -1 = типом данных столбца является varchar(max), nvarchar(max), varbinary(max) или xml.|  
|**Точность**|**tinyint**|Максимальная точность типа, если это цифровой тип. В противном случае 0.|  
|**Масштаб**|**tinyint**|Максимальный масштаб типа, если это цифровой тип. В противном случае флагу присваивается значение 0.|  
|**collation_name**|**sysname**|Имя параметров сортировки типа, если это символьный тип. В противном случае — значение NULL.|  
|**is_singleton**|**bit**|0 = указание SINGLETON отсутствует.<br /><br /> 1 = применено указание оптимизации SINGLETON.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML-схем &#40;системой типов XML&#41; представления каталога &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
