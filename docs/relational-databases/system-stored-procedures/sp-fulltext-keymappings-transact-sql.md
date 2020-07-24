---
title: sp_fulltext_keymappings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_keymappings_TSQL
- sp_fulltext_keymappings
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], key column
- sp_fulltext_keymappings
- full-text indexes [SQL Server], troubleshooting
ms.assetid: 2818fa42-072d-4664-a2f7-7ec363b51d81
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 000c71e284f77b5024cd45727803af55fa8d8b06
ms.sourcegitcommit: 08f331b6a5fe72d68ef1b2eccc5d16cb80c6ee39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86977746"
---
# <a name="sp_fulltext_keymappings-transact-sql"></a>sp_fulltext_keymappings (Transact-SQL)
[!INCLUDE [sql-asdbmi-pdw](../../includes/applies-to-version/sql-asdbmi-pdw.md)]

  Возвращаются сопоставления идентификаторов документов (DocIds) и значений полнотекстовых ключей. Столбец DocId содержит значения для целого числа **bigint** , которое соответствует конкретному значению полнотекстового ключа в таблице с полнотекстовым индексом. Значения DocId, удовлетворяющие условию поиска, передаются из средства полнотекстового поиска в компонент Database Engine, где они сопоставляются со значениями полнотекстового ключа из базовой таблицы, к которой был сделан запрос. Столбец полнотекстового ключа — это уникальный индекс, который необходим для одного столбца таблицы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_fulltext_keymappings { table_id | table_id, docid | table_id, NULL, key }  
```  
  
#### <a name="parameters"></a>Параметры  
 *table_id*  
 Идентификатор объекта полнотекстовой индексированной таблицы. При указании недопустимого *table_id*возвращается ошибка. Сведения о получении идентификатора объекта таблицы см. в разделе [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md).  
  
 *DocId*  
 Внутренний идентификатор документа (DocId), который соответствует значению ключа. При использовании недопустимого значения *docid* не происходит возврата значений.  
  
 *key*  
 Значение полнотекстового ключа из указанной таблицы. При использовании недопустимого значения *key* не происходит возврата значений. Дополнительные сведения о значениях полнотекстовых ключей см. в разделе [Управление полнотекстовыми индексами](https://msdn.microsoft.com/library/28ff17dc-172b-4ac4-853f-990b5dc02fd1).  
  
> [!IMPORTANT]  
>  Дополнительные сведения об использовании одного, двух или трех параметров см. в подразделе «Примечания» далее в этом разделе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|DocId|**bigint**|Столбец внутреннего идентификатора документа (DocId), который соответствует значению ключа.|  
|Ключ|*|Значение полнотекстового ключа из указанной таблицы.<br /><br /> Если в таблице сопоставлений отсутствуют полнотекстовые ключи, то возвращается пустой набор строк.|  
  
 <sup>*</sup>Тип данных для ключа совпадает с типом данных полнотекстового ключевого столбца в базовой таблице.  
  
## <a name="permissions"></a>Разрешения  
 Эта функция является открытой, поэтому не требует специальных разрешений.  
  
## <a name="remarks"></a>Комментарии  
 В следующей таблице описывается эффект от использования одного, двух или трех параметров.  
  
|Этот список параметров...|Имеет этот результат...|  
|--------------------------|----------------------|  
|*table_id*|При вызове только с параметром *table_id* sp_fulltext_keymappings возвращает все значения полнотекстового ключа (Key) из указанной базовой таблицы вместе с DocId, соответствующим каждому ключу. В это число входят ключи, которые должны быть удалены.<br /><br /> Эта функция используется для диагностики и устранения неисправностей при возникновении различных проблем. Эту функцию рекомендуется использовать для просмотра содержимого полнотекстовых индексов, если выбранный полнотекстовый ключ не имеет типа данных integer. Это подразумевает объединение результатов sp_fulltext_keymappings с результатами **sys. dm_fts_index_keywords_by_document**. Дополнительные сведения см. в разделе [sys. dm_fts_index_keywords_by_document &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md).<br /><br /> Однако, как правило, рекомендуется при возможности выполнять sp_fulltext_keymappings с параметрами, которые указывают полнотекстовый ключ или DocId. Это более эффективный способ, чем возврат всей карты ключей, особенно для очень большой таблицы, при работе с которой может возникнуть значительное снижение производительности при возврате всей карты ключей.|  
|*table_id*, *DocId*|Если указаны только *table_id* и *DocId* , *DocId* должен иметь значение, не равное NULL, и указать допустимый DocId в указанной таблице. Эта функция используется для изоляции настраиваемых полнотекстовых ключей из базовой таблицы, которая соответствует DocId определенного полнотекстового индекса.|  
|*table_id*, null, *Key*|Если имеются три параметра, второй параметр должен иметь значение NULL, а *ключ* должен быть не NULL и указывать допустимое значение полнотекстового ключа из указанной таблицы. Эта функция используется для изоляции настраиваемых DocId, которые соответствуют определенным полнотекстовым ключам в базовой таблице.|  
  
 Возвращается ошибка, если выполняется любое из следующих условий.  
  
-   Укажите недопустимый *table_id*.  
  
-   Таблица не имеет полнотекстового индекса.  
  
-   Задано значение NULL для параметра, который должен иметь значения, отличные от NULL.  
  
## <a name="examples"></a>Примеры  
  
> [!NOTE]  
>  В примерах этого раздела используется таблица `Production.ProductReview` образца базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] . Этот индекс можно создать, выполнив пример, приведенный для `ProductReview` таблицы в [инструкции CREATE FULLTEXT INDEX &#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
### <a name="a-obtaining-all-the-key-and-docid-values"></a>A. Получение значений Key и DocId  
 В следующем примере с помощью инструкции [Declare](../../t-sql/language-elements/declare-local-variable-transact-sql.md) создается локальная переменная, `@table_id` а в качестве ее значения присваивается идентификатор `ProductReview` таблицы. В примере выполняется **sp_fulltext_keymappings** указания `@table_id` параметра *table_id* .  
  
> [!NOTE]  
>  Использование **sp_fulltext_keymappings** только с параметром *table_id* подходит для небольших таблиц.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @table_id int = OBJECT_ID(N'Production.ProductReview');  
EXEC sp_fulltext_keymappings @table_id;  
GO  
  
```  
  
 Этот пример возвращает из таблицы идентификаторы DocId и полнотекстовые ключи:  
  
| TABLE | DocId | ключ |
| ----- | ----- | --- |
|`1`|`1`|`1`|  
|`2`|`2`|`2`|  
|`3`|`3`|`3`|  
|`4`|`4`|`4`|  
  
### <a name="b-obtaining-the-docid-value-for-a-specific-key-value"></a>Б. Получение значения DocId для конкретного значения Key  
 В следующем примере используется инструкция DECLARE, которая создает локальную переменную `@table_id`и присваивает ей в качестве значения идентификатор таблицы `ProductReview` . В примере выполняется **sp_fulltext_keymappings** указания `@table_id` параметра *table_id* , NULL для параметра *DocId* и 4 для параметра *ключа* .  
  
> [!NOTE]  
>  Использование **sp_fulltext_keymappings** только с параметром *table_id* , подходящим для небольших таблиц.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @table_id int = OBJECT_ID(N'Production.ProductReview');  
EXEC sp_fulltext_keymappings @table_id, NULL, 4;  
GO  
  
```  
  
 В результате выполнения данного примера возвращаются следующие результаты:  
  
| TABLE | DocId | ключ |
| ----- | ----- | --- |
|`4`|`4`|`4`|  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры полнотекстового поиска и семантического поиска &#40;языке Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
