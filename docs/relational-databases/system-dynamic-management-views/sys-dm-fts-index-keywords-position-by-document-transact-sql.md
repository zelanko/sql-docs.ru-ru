---
title: sys.dm_fts_index_keywords_position_by_document (Transact-SQL) | Документация Майкрософт
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7470367bd827faf4c2468ee7187a05c766256dab
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716232"
---
# <a name="sysdmftsindexkeywordspositionbydocument-transact-sql"></a>sys.dm_fts_index_keywords_position_by_document (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает информацию о позиции ключевое слово в индексированных документов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('database_name'),   
OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>Аргументы  
 DB_ID ("*имя_базы_данных*")  
 Вызов [DB_ID()](../../t-sql/functions/db-id-transact-sql.md) функции. Эта функция принимает имя базы данных и возвращает идентификатор базы данных, какие sys.dm_fts_index_keywords_position_by_document использует для поиска указанной базы данных.  
  
 object_id ("*table_name*")  
 Вызов [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md) функции. Эта функция принимает имя таблицы и возвращает идентификатор таблицы, содержащей полнотекстовый индекс для проверки.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Столбец|Data type|Описание|  
|------------|---------------|-----------------|  
|ключевое слово|**varbinary(128)**|Двоичная строка, представляющая ключевое слово.|  
|display_term|**nvarchar(4000)**|Ключевое слово в понятном формате. Этот формат является производным от внутреннего формата хранения полнотекстового индекса.|  
|column_id|**int**|Идентификатор столбца, содержащий данное ключевое слово, индексированное полнотекстовым индексом.|  
|document_id|**bigint**|Идентификатор документа или строки, содержащей текущий термин, индексированный полнотекстовым индексом. Данный идентификатор соответствует значению полнотекстового ключа этого документа или строки.|  
|position|**int**|Позиция ключевого слова в документе.|  
  
## <a name="remarks"></a>Примечания  
 Используйте динамическое административное Представление для определения расположения индексированные слова в индексированных документов. Это динамическое административное Представление можно использовать для устранения проблем при **sys.dm_fts_index_keywords_by_document** указывает слова в полнотекстовый индекс, но при выполнении запроса с помощью этих слов, документ не возвращается.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CREATE FULLTEXT CATALOG, а также разрешение SELECT на столбцы, включенные в полнотекстовый индекс.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается ключевых слов из полнотекстового индекса из `Production.Document` таблицу `AdventureWorks` образца базы данных.  
  
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
  
 Можно добавить предикат в columns_id, как в следующем примере запросе, для дальнейшей локализации для расположений.  
  
```  
SELECT * FROM sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('AdventureWorks2012'),  
    OBJECT_ID('AdventureWorks2012.Production.Document')   
)  
WHERE document_id = 7 AND display_term = 'performance';  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Full-text Search](../../relational-databases/search/full-text-search.md)   
 [Улучшения производительности полнотекстовых индексов](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)   
 [Компонент Full-Text Search и функции семантического поиска &#40;Transact-SQL&#41;](../../relational-databases/system-functions/full-text-search-and-semantic-search-functions-transact-sql.md)   
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Компонент Full-Text Search и семантический поиск хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [Поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.dm_fts_index_keywords_by_document (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
