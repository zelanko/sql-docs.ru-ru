---
title: sys. key_constraints (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.key_constraints
- key_constraints
- sys.key_constraints_TSQL
- key_constraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.key_constraints catalog view
ms.assetid: 0f782d2f-7126-46ab-85b7-bcba44862231
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ea0dcfa0975d80ac91b7c7472046d6c1d06275d1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68104598"
---
# <a name="syskey_constraints-transact-sql"></a>sys.key_constraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит по одной строке для каждого объекта, являющегося ограничением первичного ключа или ограничение уникальности. Включает **sys. objects. Type** PK и UQ.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<Столбцы, унаследованные из sys. Objects>**||Список столбцов, наследуемых этим представлением, см. в разделе [sys. objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**unique_index_id**|**int**|Идентификатор соответствующего уникального индекса в родительском объекте, который был создан для реализации этого ограничения.|  
|**is_system_named**|**bit**|1 = имя сформировано системой.<br /><br /> 0 = имя предоставлено пользователем.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу сервера SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
