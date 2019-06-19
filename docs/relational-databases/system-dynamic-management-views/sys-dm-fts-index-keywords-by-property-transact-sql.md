---
title: sys.dm_fts_index_keywords_by_property (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords_by_property
- dm_fts_index_keywords_by_property_TSQL
- sys.dm_fts_index_keywords_by_property
- sys.dm_fts_index_keywords_by_property_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], troubleshooting
- search property lists [SQL Server], viewing keywords by property
- full-text search [SQL Server], viewing keywords
- sys.dm_fts_index_keywords_by_property dynamic management view
ms.assetid: fa41e052-a79a-4194-9b1a-2885f7828500
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: ed8d04f571deb231f3dbea4d840ee69e3ea1b140
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65944342"
---
# <a name="sysdmftsindexkeywordsbyproperty-transact-sql"></a>sys.dm_fts_index_keywords_by_property (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает данные, связанные со свойством, в полнотекстовом индексе данной таблицы. Сюда включаются все данные, принадлежащие любому свойству, зарегистрированному списком свойств поиска, связанным с этим полнотекстовым индексом.  
  
 sys.dm_fts_index_keywords_by_property является функцией динамического управления, который позволяет увидеть, какие зарегистрированные свойства были устранены фильтрами IFilters при индексировании, а также конкретное содержание каждого свойства каждого проиндексированного документа.  
  
 **Чтобы просмотреть все содержимое уровня документа (включая содержимое, связанное свойство)**  
  
-   [sys.dm_fts_index_keywords_by_document (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
 **Просмотр сведений более высокого уровня полнотекстового индекса**  
  
-   [sys.dm_fts_index_keywords (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)  
  
> [!NOTE]  
>  Сведения о списках свойств поиска, см. в разделе [поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_fts_index_keywords_by_property  
(   
    DB_ID('database_name'),   
OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>Аргументы  
 db_id('*database_name*')  
 Вызов [DB_ID()](../../t-sql/functions/db-id-transact-sql.md) функции. Эта функция принимает имя базы данных и возвращает идентификатор базы данных, какие sys.dm_fts_index_keywords_by_property использует для поиска указанной базы данных. Если аргумент *database_name* не указан, возвращается идентификатор текущей базы данных.  
  
 object_id ("*table_name*")  
 Вызов [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md) функции. Эта функция принимает имя таблицы и возвращает идентификатор таблицы, содержащей полнотекстовый индекс для проверки.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Столбец|Data type|Описание|  
|------------|---------------|-----------------|  
|ключевое слово|**nvarchar(4000)**|Шестнадцатеричное представление ключевого слова, которое хранится в полнотекстовом индексе.<br /><br /> Примечание. OxFF представляет собой специальный символ, который указывает конец файла или набора данных.|  
|display_term|**nvarchar(4000)**|Ключевое слово в понятном формате. Этот формат является производным от внутреннего формата хранения полнотекстового индекса.<br /><br /> Примечание. OxFF представляет собой специальный символ, который указывает конец файла или набора данных.|  
|column_id|**int**|Идентификатор столбца, содержащий данное ключевое слово, индексированное полнотекстовым индексом.|  
|document_id|**int**|Идентификатор документа или строки, содержащей текущий термин, индексированный полнотекстовым индексом. Данный идентификатор соответствует значению полнотекстового ключа этого документа или строки.|  
|property_id|**int**|Внутренний идентификатор свойства поиска в полнотекстовый индекс таблицы, указанной в параметре OBJECT_ID ("*table_name*") параметра.<br /><br /> После добавления свойства к списку свойств поиска механизм полнотекстового поиска регистрирует это свойство и назначает ему внутренний идентификатор свойства, относящийся к указанному списку свойств. Внутренний идентификатор свойства, являющийся целым числом, не повторяется в заданном списке свойств поиска. Если данное свойство зарегистрировано в нескольких списках свойств поиска, каждому списку свойств поиска может быть назначен отдельный внутренний идентификатор свойств.<br /><br /> Примечание. Внутренний идентификатор свойства отличается от целочисленного идентификатора свойства, указываемого при добавлении свойства в список свойств поиска. Дополнительные сведения см. в статье [Поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md).<br /><br /> Просмотр взаимосвязей между идентификатором и именем свойства.<br />                    [sys.registered_search_properties (Transact-SQL)](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)|  
  
## <a name="remarks"></a>Примечания  
 Динамическое административное представление может давать ответы на вопросы. Например:  
  
-   Какое содержимое хранится в данном свойстве данного DocID?  
  
-   Насколько распространено это свойство среди индексированных документов?  
  
-   В каких документах данное свойство содержится на самом деле? Это полезно тогда, если запрос о данном свойстве поиска не возвращает ожидаемого документа.  
  
 Если полнотекстовый ключевой столбец, как и рекомендовано, имеет тип данных integer, значение document_id прямо сопоставляется со значением полнотекстового ключа базовой таблицы.  
  
 Напротив, если полнотекстовый ключевой столбец имеет тип данных, отличный от integer, значение document_id не представляет значение полнотекстового ключа базовой таблицы. Таким образом, чтобы идентифицировать строку базовой таблицы, возвращаемые dm_fts_index_keywords_by_property, вам потребуется присоединить это представление с результатами, возвращенными процедурой [sp_fulltext_keymappings](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md). Чтобы выполнить соединение, нужно сохранить выход хранимой процедуры во временной таблице. После этого можно соединить столбец document_id, dm_fts_index_keywords_by_property со столбцом DocId, возвращаемые этой хранимой процедуры. Обратите внимание, что **timestamp** столбец не может принимать значения во время операции вставки, так как они автоматически формируются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таким образом **timestamp** должен быть преобразован столбец **varbinary(8)** столбцов. Следующий пример показывает эти шаги. В этом примере *table_id* идентификатор таблицы, *имя_базы_данных* — имя базы данных, и *table_name* имя таблицы.  
  
```  
USE database_name;  
GO  
CREATE TABLE #MyTempTable   
   (  
      docid INT PRIMARY KEY ,  
      [key] INT NOT NULL  
   );  
DECLARE @db_id int = db_id(N'database_name');  
DECLARE @table_id int = OBJECT_ID(N'table_name');  
INSERT INTO #MyTempTable EXEC sp_fulltext_keymappings @table_id;  
SELECT * FROM sys.dm_fts_index_keywords_by_property   
   ( @db_id, @table_id ) kbd  
   INNER JOIN #MyTempTable tt ON tt.[docid]=kbd.document_id;  
GO  
  
```  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CREATE FULLTEXT CATALOG, а также разрешение SELECT на столбцы, включенные в полнотекстовый индекс.  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится возвращение ключевых слов из свойства `Author` полнотекстового индекса для таблицы `Production.Document` в образце базы данных `AdventureWorks`. В примере используется псевдоним `KWBPOP` для таблицы, возвращаемой функцией **sys.dm_fts_index_keywords_by_property**. В примере используется внутренние соединения для объединения столбцов из [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md) и [sys.fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
```  
-- Once the full-text index is configured to support property searching  
-- on the Author property, return any keywords indexed for this property.  
USE AdventureWorks2012;  
GO   
SELECT KWBPOP.* FROM   
   sys.dm_fts_index_keywords_by_property( DB_ID(),   
   object_id('Production.Document') ) AS KWBPOP  
   INNER JOIN  
      sys.registered_search_properties AS RSP ON(   
         (KWBPOP.property_id = RSP.property_id)   
         AND (RSP.property_name = 'Author') )  
   INNER JOIN  
      sys.fulltext_indexes AS FTI ON(   
         (FTI.[object_id] = object_id('Production.Document'))   
         AND (RSP.property_list_id = FTI.property_list_id) );  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Full-text Search](../../relational-databases/search/full-text-search.md)   
 [Улучшения производительности полнотекстовых индексов](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)   
 [sp_fulltext_keymappings &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)   
 [sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)   
 [sys.registered_search_properties (Transact-SQL)](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [Поиск свойств документа с помощью списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
