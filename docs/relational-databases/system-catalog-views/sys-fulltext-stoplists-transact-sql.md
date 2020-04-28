---
title: sys. fulltext_stoplists (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_stoplists
- sys.fulltext_stoplists_TSQL
- fulltext_stoplists_TSQL
- fulltext_stoplists
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- sys.fulltext_stoplists catalog view
- stopwords [full-text search]
ms.assetid: eb69fb8f-f6d9-446e-83c0-67afd05dfba0
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 88f4354a343e9748e1111d26c3ce8c248431b1be
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68133774"
---
# <a name="sysfulltext_stoplists-transact-sql"></a>sys.fulltext_stoplists (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Содержит строку на каждый полнотекстовый список стоп-слов в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**stoplist_id**|**int**|Идентификатор списка стоп-слов, уникальный в пределах базы данных.|  
|**name**|**sysname**|Имя списка стоп-слов.|  
|**create_date**|**datetime**|Дата создания списка стоп-слов.|  
|**modify_date**|**datetime**|Дата последнего изменения списка стоп-слов с помощью инструкции ALTER.|  
|**Principal_id**|**int**|Идентификатор участника базы данных, который является владельцем списка стоп-слов.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys. fulltext_system_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql.md)   
 [sys. fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [Настройка стоп-слова и списков для полнотекстового поиска и управление ими](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Создание ПОЛНОТЕКСТОВОГО списка стоп-слов &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [ALTER FULLTEXT стоп-слов &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [DROP FULLTEXT STOPLIST (Transact-SQL)](../../t-sql/statements/drop-fulltext-stoplist-transact-sql.md)  
  
  
