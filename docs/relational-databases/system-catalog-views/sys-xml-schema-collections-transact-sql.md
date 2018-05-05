---
title: sys.xml_schema_collections (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_collections_TSQL
- sys.xml_schema_collections
- xml_schema_collections
- xml_schema_collections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_collections catalog view
ms.assetid: f3f7f3dc-029f-4942-ab3c-75fa9814e40f
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3700b31defb9095c22e82b22a58cd2c8341ff65c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysxmlschemacollections-transact-sql"></a>sys.xml_schema_collections (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждой коллекции схем XML. Коллекция схем XML представляет собой именованный набор XSD-определений. Коллекция схем XML содержится в реляционной схеме и определяется именем языка [!INCLUDE[tsql](../../includes/tsql-md.md)] в области схемы. Следующие кортежи уникальны: xml_collection_id и schema_id, так и именем.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|xml_collection_id|**int**|Идентификатор коллекции схем XML. Уникально в пределах базы данных.|  
|schema_id|**int**|Идентификатор реляционной схемы, содержащей эту коллекцию схем XML.|  
|principal_id|**int**|Идентификатор непосредственного владельца, если он отличается от владельца схемы. По умолчанию содержащиеся в схеме объекты принадлежат владельцу схемы. Однако с помощью инструкции ALTER AUTHORIZATION можно изменить право собственности и указать альтернативного владельца.<br /><br /> NULL = альтернативного владельца нет.|  
|имя|**sysname**|Имя коллекции схем XML.|  
|create_date|**datetime**|Дата создания коллекции схем XML.|  
|modify_date|**datetime**|Дата последнего изменения коллекции схем XML.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML-схем &#40;системой типов XML&#41; представления каталога &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
