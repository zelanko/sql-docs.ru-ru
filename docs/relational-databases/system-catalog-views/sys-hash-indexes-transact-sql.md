---
title: sys. hash_indexes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.hash_indexes_TSQL
- hash_indexes
- sys.hash_indexes
- hash_indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.hash_indexes catalog view
ms.assetid: d9e230fb-d3ff-486f-86ef-44898f0a703e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 99e3a647c55380e1731b97c267eb754a1f3c6a32
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68122741"
---
# <a name="syshash_indexes-transact-sql"></a>sys.hash_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает текущие хэш-индексы и свойства хэш-индекса. Хэш-индексы поддерживаются только в выполняющейся [в памяти OLTP &#40;оптимизации в памяти&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
 Представление sys. hash_indexes содержит те же столбцы, что и представление sys. indexes, и дополнительный столбец с именем **bucket_count**. Дополнительные сведения о других столбцах в представлении sys. hash_indexes см. в разделе [sys. indexes &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<наследуемые столбцы>**||Наследует столбцы из [sys. indexes &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).|  
|**bucket_count**|**int**|Число контейнеров хэша для хэш-индексов.<br /><br /> Дополнительные сведения о bucket_count значении, включая рекомендации по заданию значения, см. в разделе [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)].  Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
  
```  
SELECT object_name([object_id]) AS 'table_name', [object_id],  
     [name] AS 'index_name', [type_desc], [bucket_count]   
FROM sys.hash_indexes   
WHERE OBJECT_NAME([object_id]) = 'T1';  
```  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
