---
description: sys. dm_fts_index_keywords_position_by_document (Transact-SQL)
title: sys. dm_fts_index_keywords_position_by_document (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_index_keywords_position_by_document_TSQL
- dm_fts_index_keywords_position_by_document_TSQL
- dm_fts_index_keywords_position_by_document
- sys.dm_fts_index_keywords_position_by_document
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_keywords_position_by_document dynamic management view
ms.assetid: 0d70184f-baa2-411b-a32d-a4c5af890edd
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 0b14ccbe7643ed56e18dc79b2a72e27867d63454
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474966"
---
# <a name="sysdm_fts_index_keywords_position_by_document-transact-sql"></a>sys. dm_fts_index_keywords_position_by_document (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения о положении ключевого слова в индексируемых документах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('database_name'),   
OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>Аргументы  
 db_id ("*database_name*")  
 Вызов функции [DB_ID ()](../../t-sql/functions/db-id-transact-sql.md) . Эта функция принимает имя базы данных и возвращает идентификатор базы данных, который sys. dm_fts_index_keywords_position_by_document использует для поиска указанной базы данных.  
  
 object_id ("*table_name*")  
 Вызов функции [object_id ()](../../t-sql/functions/object-id-transact-sql.md) . Эта функция принимает имя таблицы и возвращает идентификатор таблицы, содержащей полнотекстовый индекс для проверки.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Столбец|Тип данных|Описание|  
|------------|---------------|-----------------|  
|ключевое слово|**varbinary(128)**|Двоичная строка, представляющая ключевое слово.|  
|display_term|**nvarchar(4000)**|Ключевое слово в понятном формате. Этот формат является производным от внутреннего формата хранения полнотекстового индекса.|  
|column_id|**int**|Идентификатор столбца, содержащий данное ключевое слово, индексированное полнотекстовым индексом.|  
|document_id|**bigint**|Идентификатор документа или строки, содержащей текущий термин, индексированный полнотекстовым индексом. Данный идентификатор соответствует значению полнотекстового ключа этого документа или строки.|  
|position|**int**|Расположение ключевого слова в документе.|  
  
## <a name="remarks"></a>Комментарии  
 Используйте динамическое административное представление для определения расположения индексированных слов в индексированных документах. Это динамическое административное представление можно использовать для устранения проблем, когда **sys. dm_fts_index_keywords_by_document** указывает, что слова находятся в полнотекстовом индексе, но при выполнении запроса с использованием этих слов документ не возвращается.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CREATE FULLTEXT CATALOG, а также разрешение SELECT на столбцы, включенные в полнотекстовый индекс.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются ключевые слова из полнотекстового индекса `Production.Document` таблицы `AdventureWorks` образца базы данных.  
  
```  
USE AdventureWorks2012;  
GO   
  
SELECT * FROM sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('AdventureWorks2012'),  
    OBJECT_ID('AdventureWorks2012.Production.Document')   
);   
GO  
```  
  
 Можно добавить предикат к другому columns_id, как показано в следующем примере запроса, чтобы дополнительно изолировать расположения.  
  
```  
SELECT * FROM sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('AdventureWorks2012'),  
    OBJECT_ID('AdventureWorks2012.Production.Document')   
)  
WHERE document_id = 7 AND display_term = 'performance';  
```  
  
## <a name="see-also"></a>См. также:  
 [Компонент Full-text Search](../../relational-databases/search/full-text-search.md)   
 [Повышение производительности полнотекстовых индексов](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)   
 [Функции полнотекстового поиска и семантического поиска &#40;языке Transact-SQL&#41;](../../relational-databases/system-functions/full-text-search-and-semantic-search-functions-transact-sql.md)   
 [Динамические административные представления и функции полнотекстового поиска и семантического поиска &#40;языке Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Хранимые процедуры полнотекстового поиска и семантического поиска &#40;языке Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [Поиск свойств документа с помощью списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.dm_fts_index_keywords_by_document (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
