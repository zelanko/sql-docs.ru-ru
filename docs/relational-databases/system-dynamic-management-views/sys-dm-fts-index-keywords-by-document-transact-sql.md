---
title: sys.dm_fts_index_keywords_by_document (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_index_keywords_by_document_TSQL
- dm_fts_index_keywords_by_document_TSQL
- sys.dm_fts_index_keywords_by_document
- dm_fts_index_keywords_by_document
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], troubleshooting
- sys.dm_fts_index_keywords_by_document dynamic management function
- full-text search [SQL Server], viewing keywords
ms.assetid: 793b978b-c8a1-428c-90c2-a3e49d81b5c9
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 51026e420e509cfe4af315dfaee767c45f04bcbb
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmftsindexkeywordsbydocument-transact-sql"></a>sys.dm_fts_index_keywords_by_document (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Возвращает сведения о содержимом полнотекстового индекса на уровне документа, связанного с указанной таблицей.  
  
 Функция sys.dm_fts_index_keywords_by_document является функцией динамического управления.  
  
 **Просмотр сведений более высокого уровня полнотекстового индекса**  
  
-   [sys.dm_fts_index_keywords (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)  
  
 **Просмотр сведений о содержимом уровня свойств, связанных со свойством документа**  
  
-   [sys.dm_fts_index_keywords_by_property (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_fts_index_keywords_by_document  
(   
    DB_ID('database_name'),     OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>Аргументы  
 DB_ID ("*имя_базы_данных*")  
 Вызов [DB_ID()](../../t-sql/functions/db-id-transact-sql.md) функции. Эта функция принимает имя базы данных и возвращает идентификатор базы данных, который затем используется функцией sys.dm_fts_index_keywords_by_document для поиска указанной базы данных. Если аргумент *database_name* не указан, возвращается идентификатор текущей базы данных.  
  
 object_id ("*table_name*")  
 Вызов [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md) функции. Эта функция принимает имя таблицы и возвращает идентификатор таблицы, содержащей полнотекстовый индекс для проверки.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Столбец|Data type|Описание|  
|------------|---------------|-----------------|  
|ключевое слово|**nvarchar(4000)**|Шестнадцатеричное представление ключевого слова, которое хранится в полнотекстовом индексе.<br /><br /> Примечание: OxFF представляет собой специальный символ, который указывает конец файла или набора данных.|  
|display_term|**nvarchar(4000)**|Ключевое слово в понятном формате. Этот формат является производным от внутреннего формата хранения полнотекстового индекса.<br /><br /> Примечание: OxFF представляет собой специальный символ, который указывает конец файла или набора данных.|  
|column_id|**int**|Идентификатор столбца, содержащий данное ключевое слово, индексированное полнотекстовым индексом.|  
|document_id|**int**|Идентификатор документа или строки, содержащей текущий термин, индексированный полнотекстовым индексом. Данный идентификатор соответствует значению полнотекстового ключа этого документа или строки.|  
|occurrence_count|**int**|Число вхождений текущего ключевого слова в документе или строку, которая обозначается **document_id**. Когда "*search_property_name*" указано, occurrence_count отображает только число вхождений текущего ключевого слова в указанном свойстве поиска в документе или строке.|  
  
## <a name="remarks"></a>Замечания  
 Данные, возвращаемые функцией sys.dm_fts_index_keywords_by_document, позволяют, в частности, выяснить следующее:  
  
-   общее число ключевых слов, содержащихся в полнотекстовом индексе;  
  
-   является ли ключевое слово частью данного документа или строки;  
  
-   сколько раз ключевое слово встречается во всем полнотекстовом индексе, а именно:  
  
     ([Сумма](../../t-sql/functions/sum-transact-sql.md)(**occurrence_count**) ГДЕ **ключевое слово**=*keyword_value* )  
  
-   сколько раз ключевое слово встречается в данном документе или строке;  
  
-   сколько ключевых слов содержит данный документ или строка.  
  
 Кроме того, с помощью данных, предоставляемых функцией sys.dm_fts_index_keywords_by_document, можно получить все ключевые слова, относящиеся к данному документу или строке.  
  
 Если полнотекстовый ключевой столбец, как и рекомендовано, имеет тип данных integer, значение document_id прямо сопоставляется со значением полнотекстового ключа базовой таблицы.  
  
 Напротив, если полнотекстовый ключевой столбец имеет тип данных, отличный от integer, значение document_id не представляет значение полнотекстового ключа базовой таблицы. В этом случае для идентификации данной строки в базовой таблице, возвращаемой функцией dm_fts_index_keywords_by_document, необходимо присоединить это представление с результатами, возвращенными процедурой [sp_fulltext_keymappings](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md). Чтобы выполнить соединение, нужно сохранить выход хранимой процедуры во временной таблице. После этого можно соединить столбец document_id, возвращенный функцией dm_fts_index_keywords_by_document, со столбцом DocId, возвращенным хранимой процедурой sp_fulltext_keymappings. Обратите внимание, что **timestamp** столбец не может принимать значения во время операции вставки, так как они создаются автоматически по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таким образом **timestamp** должен быть преобразован столбец **varbinary(8)** столбцов. Следующий пример показывает эти шаги. В этом примере *table_id* идентификатор таблицы, *имя_базы_данных* — имя базы данных, и *table_name* является именем таблицы.  
  
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
SELECT * FROM sys.dm_fts_index_keywords_by_document   
   ( @db_id, @table_id ) kbd  
   INNER JOIN #MyTempTable tt ON tt.[docid]=kbd.document_id;  
GO  
  
```  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CREATE FULLTEXT CATALOG, а также разрешение SELECT на столбцы, включенные в полнотекстовый индекс.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-full-text-index-content-at-the-document-level"></a>A. Отображение содержимого полнотекстового индекса на уровне документа  
 В следующем примере отображается содержимое полнотекстового индекса на уровне документа в таблице `HumanResources.JobCandidate` образца базы данных `AdventureWorks2012`.  
  
> [!NOTE]  
>  Этот индекс можно создать, выполнив пример, приведенный для `HumanResources.JobCandidate` в таблицу [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
```  
SELECT * FROM sys.dm_fts_index_keywords_by_document(db_id('AdventureWorks'),   
object_id('HumanResources.JobCandidate'));  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Компонент Full-Text Search](../../relational-databases/search/full-text-search.md)   
 [sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)   
 [sys.dm_fts_index_keywords_by_property (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)   
 [sp_fulltext_keymappings &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)   
 [Повышение производительности полнотекстовых индексов](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)  
  
  
