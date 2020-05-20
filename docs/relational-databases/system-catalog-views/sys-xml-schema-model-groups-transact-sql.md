---
title: sys. xml_schema_model_groups (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_model_groups
- xml_schema_model_groups
- sys.xml_schema_model_groups_TSQL
- xml_schema_model_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_model_groups catalog view
ms.assetid: 566556dc-a8c8-465c-9196-c7e0ae092a8a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 065d198d2de962918f74e92c9bbb038d7962d349
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833864"
---
# <a name="sysxml_schema_model_groups-transact-sql"></a>sys.xml_schema_model_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку на каждый компонент схемы XML, который является группой Model, **symbol_space** из **M**..  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<наследуемые столбцы>**||Наследует столбцы из [sys. xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**компоновщика**|**char (1)**|Способ составления группы:<br /><br /> A = XSD \< все> группа<br /><br /> C = \< группа> выбора XSD<br /><br /> S = \< группа> последовательности XSD|  
|**compositor_desc**|**nvarchar (60)**|Описание способа составления группы:<br /><br /> XSD_ALL_GROUP<br /><br /> XSD_CHOICE_GROUP<br /><br /> XSD_SEQUENCE_GROUP|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Схемы XML &#40;представления каталога системы типов XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
