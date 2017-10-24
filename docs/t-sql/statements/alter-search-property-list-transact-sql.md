---
title: "ALTER SEARCH PROPERTY LIST (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SEARCH_PROPERTY_TSQL
- ALTER_SEARCH_PROPERTY_LIST_TSQL
- ALTER SEARCH PROPERTY LIST
- ALTER SEARCH PROPERTY
- ALTER_SEARCH_TSQL
- ALTER SEARCH
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search property lists [SQL Server], altering
- ALTER SEARCH PROPERTY LIST statement
ms.assetid: 0436e4a8-ca26-4d23-93f1-e31e2a1c8bfb
caps.latest.revision: 55
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c93a8382bec0746ae3cfb8f43485da53a06184f0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-search-property-list-transact-sql"></a>ALTER SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Добавляет или удаляет указанное свойство поиска из указанного списка свойств поиска.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER SEARCH PROPERTY LIST list_name  
{  
   ADD 'property_name'  
     WITH   
      (   
          PROPERTY_SET_GUID = 'property_set_guid'  
        , PROPERTY_INT_ID = property_int_id  
      [ , PROPERTY_DESCRIPTION = 'property_description' ]  
      )  
 | DROP 'property_name'   
}  
;  
```  
  
## <a name="arguments"></a>Аргументы  
 *Имя_списка*  
 Имя изменяемого списка свойств. *Имя_списка* является идентификатором.  
  
 Чтобы просмотреть имена существующих списков свойств, используйте [sys.registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md) представление каталога следующим образом:  
  
```  
SELECT name FROM sys.registered_search_property_lists;  
```  
  
 ADD  
 Добавляет указанное свойство поиска в список свойств, заданные *Имя_списка*. Оно регистрируется для списка свойств поиска. Прежде чем добавленные свойства можно будет использовать для поиска свойств, необходимо повторно заполнить связанные полнотекстовые индексы. Дополнительные сведения см. в статье [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md).  
  
> [!NOTE]  
>  Чтобы добавить данное свойство в список свойств поиска, необходимо указать его идентификатор GUID набора свойств (*предложения property_set_guid*) и целочисленный идентификатор свойства (*property_int_id*). Дополнительные сведения см. в разделе «Получение идентификаторов GUID набора свойств и целочисленных идентификаторов» далее в этом разделе.  
  
 *property_name*  
 Указывает имя, которое будет использоваться для обозначения свойства в полнотекстовых запросах. *property_name* должно уникально определять свойство в наборе свойств. Имя свойства может содержать внутренние пробелы. Максимальная длина *property_name* составляет 256 символов. Это имя может быть описательным, таким как автор или домашний адрес, или он может быть каноническое имя Windows свойства, такие как **System.Author** или **System.Contact.HomeAddress**.  
  
 Разработчики должны использовать значение, указываемое для *property_name* для обозначения свойства в [CONTAINS](../../t-sql/queries/contains-transact-sql.md) предиката. Таким образом, при добавлении свойства важно указать значение, которое значимо представляет свойство, определенное свойство идентификатора GUID набора (*предложения property_set_guid*) и идентификатор для свойства (*property_int _ID*). Дополнительные сведения об именах свойств см. в подразделе «Замечания» далее в этом разделе.  
  
 Чтобы просмотреть имена свойств, которые в настоящий момент находятся в списке свойств поиска для текущей базы данных, используйте [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md) представление каталога следующим образом:  
  
```  
SELECT property_name FROM sys.registered_search_properties;  
```  
  
 Предложения PROPERTY_SET_GUID = "*предложения property_set_guid*"  
 Указывает идентификатор набора свойств, к которому принадлежит свойство. Это глобальный уникальный идентификатор GUID. Дополнительные сведения о получении этого значения см. в подразделе «Замечания» далее в этом разделе.  
  
 Чтобы просмотреть свойства задать идентификатор GUID для любого свойства, существующего в списке свойств поиска для текущей базы данных, используйте [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md) представление каталога следующим образом:  
  
```  
SELECT property_set_guid FROM sys.registered_search_properties;  
```  
  
 PROPERTY_INT_ID =*property_int_id*  
 Указывает целое число, определяющее свойство в наборе свойств. Дополнительные сведения о получении этого значения см. в подразделе «Замечания».  
  
 Для просмотра целочисленного идентификатора любого свойства, которое существует в списке свойств поиска для текущей базы данных, используйте [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md) представление каталога следующим образом:  
  
```  
SELECT property_int_id FROM sys.registered_search_properties;  
```  
  
> [!NOTE]  
>  Заданное сочетание *предложения property_set_guid* и *property_int_id* должно быть уникальным в списке свойств поиска. При попытке добавить существующее сочетание операция ALTER SEARCH PROPERTY LIST завершается неудачей и выдается ошибка. Это означает, что для свойства можно определить только одно имя.  
  
 PROPERTY_DESCRIPTION = "*property_description*"  
 Указывает задаваемое пользователем описание свойства. *property_description* представляет собой строку длиной до 512 символов. Это необязательный параметр.  
  
 DROP  
 Удаляет указанное свойство из списка свойств, заданные *Имя_списка*. Удаление свойства отменяет его регистрацию, поэтому оно становится недоступным для поиска.  
  
## <a name="remarks"></a>Замечания  
 Каждый полнотекстовый индекс может иметь только один список свойств поиска.  
  
 Чтобы разрешить запросы по данному свойству поиска, необходимо добавить его в список свойств поиска полнотекстового индекса, а затем повторно заполнить индекс.  
  
 При задании свойства предложения PROPERTY_SET_GUID, PROPERTY_INT_ID и PROPERTY_DESCRIPTION можно расположить в любом порядке, разделив их запятыми и поместив в круглые скобки, например:  
  
```  
ALTER SEARCH PROPERTY LIST CVitaProperties  
ADD 'System.Author'   
WITH (   
      PROPERTY_DESCRIPTION = 'Author or authors of a given document.',  
      PROPERTY_SET_GUID   = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9',   
      PROPERTY_INT_ID = 4   
      );  
```  
  
> [!NOTE]  
>  В этом примере использовано имя свойства, `System.Author`, концептуально похожее на канонические имена свойств в Windows Vista (каноническое имя Windows).  
  
## <a name="obtaining-property-values"></a>Получение значений свойств  
 Полнотекстовый поиск сопоставляет свойство поиска с полнотекстовым индексом с помощью идентификатора GUID набора свойств и целочисленного идентификатора свойства. Сведения о способах получения этих свойств, определенных корпорацией Майкрософт см. в разделе [поиск идентификаторов GUID наборов свойств и целочисленных идентификаторов свойств для свойств поиска](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md). Дополнительные сведения о свойствах, определенных независимыми поставщиками программного обеспечения (ISV), см. в документации по этим поставщикам.  
  
## <a name="making-added-properties-searchable"></a>Наделение добавленных свойств возможностью поиска  
 Добавление свойства поиска в список свойств поиска приводит к регистрации свойства. Добавленное свойство может быть немедленно указано в [CONTAINS](../../t-sql/queries/contains-transact-sql.md) запросов. Однако запросы полнотекстового каталога, использующие вновь добавленное свойство, не будут возвращать документы, пока не будет заполнен соответствующий полнотекстовый индекс. Например, следующий запрос, основанный на вновь добавленном свойстве *new_search_property*, не вернет все документы, пока полнотекстовый индекс, связанный с целевой таблицей (*table_name*) будет заполнен повторно:  
  
```  
SELECT column_name  
FROM table_name  
WHERE CONTAINS( PROPERTY( column_name, 'new_search_property' ), 
               'contains_search_condition');  
GO   
```  
  
 Чтобы запустить полное заполнение, воспользуйтесь следующим [ALTER FULLTEXT INDEX & #40; Transact-SQL & #41; ](../../t-sql/statements/alter-fulltext-index-transact-sql.md) инструкции:  
  
```  
USE database_name;  
GO  
ALTER FULLTEXT INDEX ON table_name START FULL POPULATION;  
GO  
```  
  
> [!NOTE]  
>  Повторное заполнение не требуется после удаления свойства из списка свойств, так как только свойства, остающиеся в списке свойств поиска, доступны для полнотекстовых запросов.  
  
## <a name="related-references"></a>Связанные справочники  
 **Для создания списка свойств**  
  
-   [CREATE SEARCH PROPERTY LIST (Transact-SQL)](../../t-sql/statements/create-search-property-list-transact-sql.md)  
  
 **Чтобы удалить список свойств**  
  
-   [DROP SEARCH PROPERTY LIST (Transact-SQL)](../../t-sql/statements/drop-search-property-list-transact-sql.md)  
  
 **Чтобы добавить или удалить список свойств для полнотекстового индекса**  
  
-   [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
 **Чтобы выполнить заполнение полнотекстового индекса**  
  
-   [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
##  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение CONTROL на список свойств.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-adding-a-property"></a>A. Добавление свойства  
 В следующем примере добавляется несколько свойств — `Title`, `Author` и `Tags` — к списку свойств с именем `DocumentPropertyList`.  
  
> [!NOTE]  
>  Пример, который создает `DocumentPropertyList` список свойств см. в разделе [CREATE SEARCH PROPERTY LIST & #40; Transact-SQL & #41; ](../../t-sql/statements/create-search-property-list-transact-sql.md).  
  
```  
ALTER SEARCH PROPERTY LIST DocumentPropertyList  
   ADD 'Title'   
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 2,   
      PROPERTY_DESCRIPTION = 'System.Title - Title of the item.' );  
  
ALTER SEARCH PROPERTY LIST DocumentPropertyList   
    ADD 'Author'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 4,   
      PROPERTY_DESCRIPTION = 'System.Author - Author or authors of the item.' );  
  
ALTER SEARCH PROPERTY LIST DocumentPropertyList   
    ADD 'Tags'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 5,   
      PROPERTY_DESCRIPTION = 
          'System.Keywords - Set of keywords (also known as tags) assigned to the item.' );  
```  
  
> [!NOTE]  
>  Необходимо связать данный список свойств поиска с полнотекстовым индексом перед его использованием для запросов в области свойства. Чтобы сделать это, используйте [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) инструкцию и укажите предложение SET SEARCH PROPERTY LIST.  
  
### <a name="b-dropping-a-property"></a>Б. Удаление свойства  
 В следующем примере свойство `Comments` удаляется из списка свойств `DocumentPropertyList`.  
  
```  
ALTER SEARCH PROPERTY LIST DocumentPropertyList  
DROP 'Comments' ;  
```  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ список СВОЙСТВ поиска & #40; Transact-SQL & #41;](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [Удаление СПИСКА СВОЙСТВ поиска & #40; Transact-SQL & #41;](../../t-sql/statements/drop-search-property-list-transact-sql.md)   
 [sys.registered_search_properties & #40; Transact-SQL & #41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists & #40; Transact-SQL & #41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [sys.dm_fts_index_keywords_by_property & #40; Transact-SQL & #41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)   
 [Поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [Поиск идентификаторов GUID для наборов свойств и целочисленных идентификаторов свойств для свойств поиска](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md)  
  
  

