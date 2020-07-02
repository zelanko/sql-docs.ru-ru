---
title: SEMANTICSIMILARITYTABLE (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- semanticsimilaritytable
- semanticsimilaritytable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- semanticsimilaritytable function
ms.assetid: b49d40ab-7552-438b-ad67-6237dcccb75b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 759ac2b464bbdee2a0199afe540f00c7695381a9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764280"
---
# <a name="semanticsimilaritytable-transact-sql"></a>semanticsimilaritytable (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает таблицу, состоящую из нуля, одной или более строк для документов, содержимое которых в указанных столбцах семантически сходно с содержимым указанного документа.  
  
 На эту функцию набора строк можно ссылаться в предложении FROM инструкции SELECT как на обычное имя таблицы.  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
SEMANTICSIMILARITYTABLE  
    (  
    table,  
    { column | (column_list) | * },  
    source_key  
    )  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Даваемых  
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
  
 По возможности ключ неявно преобразуется в тип полнотекстового уникального ключа в исходной таблице. Ключ может быть задан в виде константы или переменной, но не может быть выражением или результатом скалярного вложенного запроса.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
 В следующей таблице приведены сведения о сходных или связанных документах, которые возвращает эта функция набора строк.  
  
 Если результаты запрашиваются из нескольких столбцов, то совпадающие документы возвращаются для каждого столбца отдельно.  
  
|Column_name|Тип|Описание|  
|------------------|----------|-----------------|  
|**source_column_id**|**int**|Идентификатор столбца, в котором исходный документ использовался при поиске подобных документов.<br /><br /> Способы извлечения имени столбца по идентификатору столбца и идентификатора столбца по имени см. в описании функций COL_NAME и COLUMNPROPERTY.|  
|**matched_column_id**|**int**|Идентификатор столбца, в котором был найден сходный документ.<br /><br /> Способы извлечения имени столбца по идентификатору столбца и идентификатора столбца по имени см. в описании функций COL_NAME и COLUMNPROPERTY.|  
|**matched_document_key**|**\***<br /><br /> Этот ключ соответствует типу уникального ключа в исходной таблице.|Значение уникального ключа полнотекстового и семантического извлечения для документа или строки, которые оказались подобными документу, указанному в запросе.|  
|**понять**|**REAL**|Относительное значение подобия этого документа по отношению ко всем другим подобным документам.<br /><br /> Это дробное десятичное значение в диапазоне [0.0, 1.0], где чем выше показатель, тем больше соответствие, а 1.0 — идеальный показатель.|  
  
## <a name="general-remarks"></a>Общие замечания  
 Дополнительные сведения см. [в разделе Поиск схожих и связанных документов с помощью семантического поиска](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Искать схожие документы по разным столбцам невозможно. Функция **SEMANTICSIMILARITYTABLE** извлекает похожие документы только из того же столбца, что и исходный столбец, который определяется аргументом **source_key** .  
  
## <a name="metadata"></a>Метаданные  
 Чтобы получить сведения и состояние извлечения и заполнения данных о семантическом подобии, выполните запрос к следующим динамическим административным представлениям:  
  
-   [sys.dm_db_fts_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)  
  
-   [sys.dm_fts_semantic_similarity_population (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется разрешение SELECT на базовую таблицу, в которой были созданы индекс полнотекстового поиска и семантический индекс.  
  
## <a name="examples"></a>Примеры  
 В следующем примере извлекается до 10 потенциальных ключевых фраз, подобных указанному кандидату из таблицы HumanResources.JobCandidate в образце базы данных AdventureWorks2012.  
  
```scr  
SELECT TOP(10) KEY_TBL.matched_document_key AS Candidate_ID  
FROMSEMANTICSIMILARITYTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume,  
    @CandidateID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
  
```  
  
  
