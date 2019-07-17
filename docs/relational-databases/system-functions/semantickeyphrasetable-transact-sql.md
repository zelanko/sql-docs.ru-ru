---
title: semantickeyphrasetable (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- semantickeyphrasetable
- semantickeyphrasetable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- semantickeyphrasetable function
ms.assetid: d33b973a-2724-4d4b-aaf7-67675929c392
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bfde3ee5d26557759bd881bce34a69b6ecf98dd1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140574"
---
# <a name="semantickeyphrasetable-transact-sql"></a>semantickeyphrasetable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает таблицу с нулем, одной или несколькими строками для ключевых фраз, связанных с указанными столбцами в заданной таблице.  
  
 На эту функцию набора строк можно ссылаться из предложения FROM инструкции SELECT так же, как и на обычное имя таблицы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
SEMANTICKEYPHRASETABLE  
    (  
    table,  
    { column | (column_list) | * }  
     [ , source_key ]  
    )  
```  
  
##  <a name="Arguments"></a> Аргументы  
 **table**  
 Имя таблицы с включенным полнотекстовым и семантическим индексированием.  
  
 Это имя может содержать от одной до четырех частей, но указать имя удаленного сервера невозможно.  
  
 **column**  
 Имя индексированного столбца, для которого должны быть возвращены результаты. У столбца должно быть включено семантическое индексирование.  
  
 **column_list**  
 Задает несколько столбцов, разделенных запятыми и заключенных в круглые скобки. У всех столбцов должно быть включено семантическое индексирование.  
  
 **\***  
 Указывает на то, что используются все столбцы, у которых включено семантическое индексирование.  
  
 **source_key**  
 Уникальный ключ строки для запроса результатов по определенной строке.  
  
 По возможности ключ неявно преобразуется в тип полнотекстового уникального ключа в исходной таблице. Ключ может быть задан в виде константы или переменной, но не может быть выражением или результатом скалярного вложенного запроса. Если параметр source_key не указан, то результаты возвращаются для всех строк.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
 В следующей таблице приведены сведения о ключевых фразах, которые возвращает эта функция набора строк.  
  
|Column_name|Type|Описание|  
|------------------|----------|-----------------|  
|**column_id**|**int**|Идентификатор столбца, из которого была извлечена и проиндексирована текущая ключевая фраза.<br /><br /> Способы извлечения имени столбца по идентификатору столбца и идентификатора столбца по имени см. в описании функций COL_NAME и COLUMNPROPERTY.|  
|**document_key**|**\***<br /><br /> Этот ключ соответствует типу уникального ключа в исходной таблице.|Значение уникального ключа документа или строки, в которых была проиндексирована текущая ключевая фраза.|  
|**ключевой фразы**|**NVARCHAR**|Ключевая фраза из столбца с идентификатором column_id, связанная с документом, указанным document_key.|  
|**Оценка**|**REAL**|Относительное значение для этой ключевой фразы относительно всех других ключевых фраз того же документа в индексируемом столбце.<br /><br /> Это дробное десятичное значение в диапазоне [0.0, 1.0], где более высокие значения соответствуют большему весу, а 1.0 — показатель идеального совпадения.|  
  
## <a name="general-remarks"></a>Общие замечания  
 Дополнительные сведения см. в разделе [поиск ключевых фраз в документах с помощью семантического поиска](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md).  
  
## <a name="metadata"></a>Метаданные  
 Чтобы получить сведения об извлечении семантической ключевой фразы и о заполнении, запросите следующие динамические административные представления:  
  
-   [sys.dm_db_fts_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)  
  
-   [sys.dm_fts_index_population (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется разрешение SELECT на базовую таблицу, в которой были созданы индекс полнотекстового поиска и семантический индекс.  
  
## <a name="examples"></a>Примеры  
  
###  <a name="HowToTopPhrases"></a> Пример 1. Поиск ключевых фраз в определенном документе  
 В следующем примере извлекаются 10 первых ключевых фраз из документа, указанного в переменной @DocumentId в столбце Document таблицы Production.Document в тестовой базе данных AdventureWorks. Переменная @DocumentId представляет значение из ключевого столбца полнотекстового индекса. Функция **SEMANTICKEYPHRASETABLE** эффективно извлекает эти результаты поиском по индексу, а не путем просмотра таблицы. В этом примере предполагается, что в столбце настроено семантическое и полнотекстовое индексирование.  
  
```sql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
  
```  
  
###  <a name="HowToTopDocuments"></a> Пример 2. Поиск наиболее важных документов, содержащих определенную ключевую фразу  
 В следующем примере извлекаются 25 первых документов, содержащих ключевую фразу Bracket в столбце Document таблицы Production.Document примера базы данных AdventureWorks. В этом примере предполагается, что в столбце настроено семантическое и полнотекстовое индексирование.  
  
```sql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
  
```  
  
  
