---
title: sys.xml_schema_wildcard_namespaces (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xml_schema_wildcard_namespaces_TSQL
- xml_schema_wildcard_namespaces
- sys.xml_schema_wildcard_namespaces_TSQL
- sys.xml_schema_wildcard_namespaces
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_wildcard_namespaces catalog view
ms.assetid: a3caa932-41c7-48a9-9b2d-ff090afbb66b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c8c51d6afa8dd3990c9ae4ba151a6fab2b0fd101
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899971"
---
# <a name="sysxml_schema_wildcard_namespaces-transact-sql"></a>sys.xml_schema_wildcard_namespaces (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает по одной строке на каждое перечисленное пространство имен в шаблоне схемы XML.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|Идентификатор компонента схемы XML (шаблона), к которому это применяется.|  
|**namespace**|**nvarchar(4000)**|Имя или URI пространства имен, используемого XML-шаблоном.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Схемы XML &#40;представления каталога системы типов XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
