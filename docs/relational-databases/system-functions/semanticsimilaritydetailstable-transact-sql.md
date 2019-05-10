---
title: semanticsimilaritydetailstable (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- semanticsimilaritydetailstable
- semanticsimilaritydetailstable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- semanticsimilaritydetailstable function
ms.assetid: 038d751a-fca5-4b4c-9129-cba741a4e173
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 680712fb2ac5b31484fc7650a8a4fab8047fc7af
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65103265"
---
# <a name="semanticsimilaritydetailstable-transact-sql"></a>semanticsimilaritydetailstable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает таблицу из нуля, одной или многих строк с ключевыми фразами, общими для двух документов (исходного документа и сопоставленного документа), содержимое которых семантически сходно.  
  
 Эта функция набора строк можно ссылаться в предложении FROM инструкции SELECT 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
SEMANTICSIMILARITYDETAILSTABLE  
    (  
    table,  
    source_column,  
    source_key,  
    matched_column,  
    matched_key  
    )  
```  
  
##  <a name="Arguments"></a> Аргументы  
 **table**  
 Имя таблицы с включенным полнотекстовым и семантическим индексированием.  
  
 Это имя может содержать от одной до четырех частей, но указать имя удаленного сервера невозможно.  
  
 **source_column**  
 Имя столбца в строке источника с содержимым, которое сравнивается на предмет подобия.  
  
 **source_key**  
 Уникальный ключ, который представляет строку исходного документа.  
  
 По возможности этот ключ неявно преобразуется к типу полнотекстового уникального ключа в исходной таблице. Ключ может быть задан в виде константы или переменной, но не может быть выражением или результатом скалярного вложенного запроса. Если указан недопустимый ключ, строки не возвращаются.  
  
 **matched_column**  
 Имя столбца в сопоставляемой строке с содержимым, которое сравнивается на предмет подобия.  
  
 **matched_key**  
 Уникальный ключ, который представляет строку сопоставляемого документа.  
  
 По возможности этот ключ неявно преобразуется к типу полнотекстового уникального ключа в исходной таблице. Ключ может быть задан в виде константы или переменной, но не может быть выражением или результатом скалярного вложенного запроса.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
 В следующей таблице приведены сведения о ключевых фразах, которые возвращает эта функция набора строк.  
  
|Column_name|Тип|Описание|  
|------------------|----------|-----------------|  
|**ключевой фразы**|**NVARCHAR**|Ключевая фраза, обуславливающая подобие между исходным документом и сопоставляемым документом.|  
|**Оценка**|**REAL**|Относительное значение для этой ключевой фразы относительно всех других ключевых фраз, которые обуславливают подобие двух документов между собой.<br /><br /> Это дробное десятичное значение в диапазоне [0.0, 1.0], где более высокие значения соответствуют большему весу, а 1.0 — показатель идеального совпадения.|  
  
## <a name="general-remarks"></a>Общие замечания  
 Дополнительные сведения см. в разделе [поиск похожих и связанных документов с помощью семантического поиска](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md).  
  
## <a name="metadata"></a>Метаданные  
 Чтобы получить сведения и состояние извлечения и заполнения данных о семантическом подобии, выполните запрос к следующим динамическим административным представлениям:  
  
-   [sys.dm_db_fts_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)  
  
-   [sys.dm_fts_semantic_similarity_population (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется разрешение SELECT на базовую таблицу, в которой были созданы индекс полнотекстового поиска и семантический индекс.  
  
## <a name="examples"></a>Примеры  
 В следующем примере извлекается 5 ключевых фраз, имеющих высший показатель подобия среди указанных кандидатов в **HumanResources.JobCandidate** таблицу образца базы данных AdventureWorks2012. @CandidateId И @MatchedID представляют значения из ключевого столбца полнотекстового индекса.  
  
```sql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROMSEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
  
```  
  
  
