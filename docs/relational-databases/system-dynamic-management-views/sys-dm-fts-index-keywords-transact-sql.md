---
title: sys.dm_fts_index_keywords (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords
- sys.dm_fts_index_keywords
- sys.dm_fts_index_keywords_TSQL
- dm_fts_index_keywords_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_keywords dynamic management function
- full-text search [SQL Server], viewing keywords
- troubleshooting [SQL Server], full-text search
ms.assetid: fce7b2a1-7e74-4769-86a8-c77c7628decd
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: de956e2dffebd801205bf4ac46a7f503e1acbe8f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65944275"
---
# <a name="sysdmftsindexkeywords-transact-sql"></a>sys.dm_fts_index_keywords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о содержимом полнотекстового индекса для указанной таблицы.  
  
 **sys.dm_fts_index_keywords** является функцией динамического управления.  
  
> [!NOTE]  
>  Чтобы просмотреть данные полнотекстового индекса более низкого уровня, используйте [sys.dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md) функции динамического управления на уровне документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_fts_index_keywords( DB_ID('database_name'), OBJECT_ID('table_name') )  
```  
  
## <a name="arguments"></a>Аргументы  
 db_id('*database_name*')  
 Вызов [DB_ID()](../../t-sql/functions/db-id-transact-sql.md) функции. Эта функция принимает имя базы данных и возвращает идентификатор базы данных, который **sys.dm_fts_index_keywords** использует для поиска указанной базы данных. Если аргумент *database_name* не указан, возвращается идентификатор текущей базы данных.  
  
 object_id ("*table_name*")  
 Вызов [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md) функции. Эта функция принимает имя таблицы и возвращает идентификатор таблицы, содержащей полнотекстовый индекс для проверки.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Ключевое слово**|**nvarchar(4000)**|Шестнадцатеричное представление ключевого слова, которое хранится в полнотекстовом индексе.<br /><br /> Примечание. OxFF представляет собой специальный символ, который указывает конец файла или набора данных.|  
|**display_term**|**nvarchar(4000)**|Ключевое слово в понятном формате. Этот формат является производным от шестнадцатеричного формата.<br /><br /> Примечание. **Display_term** значение для OxFF — «Конец файла.»|  
|**column_id**|**int**|Идентификатор столбца, содержащий данное ключевое слово, индексированное полнотекстовым индексом.|  
|**document_count**|**int**|Число документов или строк, содержащих текущий термин.|  
  
## <a name="remarks"></a>Примечания  
 Сведения, возвращаемые функцией **sys.dm_fts_index_keywords** полезно для выяснения следующего, помимо прочего:  
  
-   является ли ключевое слово частью полнотекстового индекса;  
  
-   сколько документов или строк содержат данное ключевое слово;  
  
-   какое ключевое слово наиболее часто встречается в полнотекстовом индексе:  
  
    -   **document_count** каждого *keyword_value* сравнивается с общим **document_count**, числом документов для 0xFF.  
  
    -   Как правило, наиболее часто встречающиеся ключевые слова пригодны для объявления в качестве стоп-слов.  
  
> [!NOTE]  
>  **Document_count** возвращаемые **sys.dm_fts_index_keywords** может быть менее точным для определенного документа, чем число, возвращаемое функцией **sys.dm_fts_index_keywords_by_document** или **CONTAINS** запроса. Согласно проведенной оценке, эта возможная неточность не превышает 1%. Неточность может возникнуть, так как **document_id** могут быть подсчитаны дважды в том случае, когда он продолжает по более чем одной строке фрагмента индекса или при более одного раза появляется в той же строке. Чтобы получить более точное количество для определенного документа, используйте **sys.dm_fts_index_keywords_by_document** или **CONTAINS** запроса.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-high-level-full-text-index-content"></a>A. Отображение содержимого полнотекстового индекса высокого уровня  
 В следующем примере отображаются сведения о высокоуровневом содержимом полнотекстового индекса в таблице `HumanResources.JobCandidate`.  
  
```  
SELECT * FROM sys.dm_fts_index_keywords(db_id('AdventureWorks2012'), object_id('HumanResources.JobCandidate'))  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Компонент Full-text Search](../../relational-databases/search/full-text-search.md)   
 [sys.dm_fts_index_keywords_by_document (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
