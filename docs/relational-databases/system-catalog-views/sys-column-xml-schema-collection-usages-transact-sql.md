---
title: sys. column_xml_schema_collection_usages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- column_xml_schema_collection_usages_TSQL
- sys.column_xml_schema_collection_usages
- column_xml_schema_collection_usages
- sys.column_xml_schema_collection_usages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_xml_schema_collection_usages catalog view
ms.assetid: 4fd1ec7f-b9dc-4ddb-ab3a-0d59ab05ad20
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 64bd9d90068d4c1dc775eef437c032dc1ba41988
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901050"
---
# <a name="syscolumn_xml_schema_collection_usages-transact-sql"></a>sys.column_xml_schema_collection_usages (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает строку для каждого столбца, проверенного XML-схемой.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, к которому относится данный столбец.|  
|**column_id**|**int**|Идентификатор столбца. Уникален в пределах объекта.|  
|**xml_collection_id**|**int**|Идентификатор коллекции, содержащей пространство имен проверяющей XML-схемы для этого столбца.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Схемы XML &#40;представления каталога системы типов XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
