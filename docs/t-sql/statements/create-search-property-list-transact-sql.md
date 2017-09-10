---
title: "Создание СПИСКА СВОЙСТВ поиска (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SEARCH_PROPERTY_LIST_TSQL
- CREATE SEARCH
- CREATE_SEARCH_TSQL
- CREATE_SEARCH_PROPERTY_TSQL
- CREATE SEARCH PROPERTY
- CREATE SEARCH PROPERTY LIST
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search property lists [SQL Server], creating
- CREATE SEARCH PROPERTY LIST statement
ms.assetid: 5440cbb8-3403-4d27-a2f9-8e1f5a1bc12b
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b055be4f948b62553ddbabb40613971a0e5619d8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-search-property-list-transact-sql"></a>CREATE SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Создает новый список свойств поиска. В списке свойств поиска указывается одно или несколько свойств поиска, которые необходимо включить в полнотекстовый индекс.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE SEARCH PROPERTY LIST new_list_name  
   [ FROM [ database_name. ] source_list_name ]  
   [ AUTHORIZATION owner_name ]  
;  
```  
  
## <a name="arguments"></a>Аргументы  
 *new_list_name*  
 Имя нового списка свойств поиска. *new_list_name* представляет собой идентификатор с не более 128 символов. *new_list_name* должно быть уникальным среди всех списков свойств в текущей базе данных и соответствовать правилам для идентификаторов. *new_list_name* будет использоваться при создании полнотекстового индекса.  
  
 *database_name*  
 Имя базы данных, где указанный список свойств *source_list_name* находится. Если не указан, *имя_базы_данных* значения по умолчанию для текущей базы данных.  
  
 *database_name* необходимо указать имя существующей базы данных. Имя входа для текущего соединения должны быть связаны с Идентификатором пользователя, существующего в базы данных, указанной *имя_базы_данных*. Необходимо также иметь необходимые [разрешений](#Permissions) в базе данных.  
  
 *source_list_name*  
 Указывает, что новый список свойств создается путем копирования существующего списка свойств из *имя_базы_данных*. Если *source_list_name* не существует, СОЗДАЙТЕ SEARCH PROPERTY LIST завершится с ошибкой. Свойства поиска в *source_list_name* наследуются *new_list_name*.  
  
 АВТОРИЗАЦИЯ *owner_name*  
 Указывает имя пользователя или роли-владельца списка свойств. *owner_name* должен быть именем роли, которой является текущий пользователь членом, либо текущий пользователь должен иметь разрешение IMPERSONATE *owner_name*. Если атрибут не указан, владельцем становится текущий пользователь.  
  
> [!NOTE]  
>  Владелец может быть изменен с помощью [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.  
  
## <a name="remarks"></a>Замечания  
  
> [!NOTE]  
>  Сведения о свойстве списки в целом. в разделе [поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
 По умолчанию новый список свойств, которые можно искать, пуст. В него необходимо вручную добавить одно или несколько свойств. В качестве альтернативы можно скопировать существующий список свойств поиска. В этом случае новый список наследует поисковые свойства своего источника, но его можно изменить, добавив или удалив определенные свойства. При следующем полном заполнении все свойства, приведенные в списке свойств поиска, заносятся в полнотекстовый индекс.  
  
 Инструкция CREATE SEARCH PROPERTY LIST завершится неуспехом при выполнении любого из следующих условий.  
  
-   Если база данных, указанная *имя_базы_данных* не существует.  
  
-   Если список, указанный параметром *source_list_name* не существует.  
  
-   Если отсутствуют нужные разрешения.  
  
 **Чтобы добавить или удалить свойства из списка**  
  
-   [ALTER SEARCH PROPERTY LIST (Transact-SQL)](../../t-sql/statements/alter-search-property-list-transact-sql.md)  
  
-   **Чтобы удалить список свойств**  
  
-   [DROP SEARCH PROPERTY LIST (Transact-SQL)](../../t-sql/statements/drop-search-property-list-transact-sql.md)  
  
##  <a name="Permissions"></a> Разрешения  
 Необходимы разрешения CREATE FULLTEXT CATALOG в текущей базе данных и разрешение REFERENCES для любой базы данных, из которой копируется исходный список свойств.  
  
> [!NOTE]  
>  Для связывания списка с полнотекстовым индексом требуется разрешение REFERENCES. Для добавления или удаления свойств, а также для удаления списка требуется разрешение CONTROL. Владелец списка свойств поиска может предоставить разрешения REFERENCES и CONTROL на список. Пользователи с разрешением CONTROL также могут предоставлять разрешение REFERENCES другим пользователям.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-an-empty-property-list-and-associating-it-with-an-index"></a>A. Создание пустого списка свойств и связывание его с индексом  
 В следующем примере создается новый список свойств поиска с именем `DocumentPropertyList`. Затем в примере используется [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) связывает новый список свойств с полнотекстовый индекс `Production.Document` в таблицу `AdventureWorks` базы данных, без запуска заполнения.  
  
> [!NOTE]  
>  Пример, который добавляет несколько стандартных, известных поиска свойств этого списка свойств поиска см. в разделе [ALTER SEARCH PROPERTY LIST &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-search-property-list-transact-sql.md). После добавления свойств поиска в список администратору базы данных необходимо будет использовать другую инструкцию ALTER FULLTEXT INDEX с предложением START FULL POPULATION.  
  
```  
CREATE SEARCH PROPERTY LIST DocumentPropertyList;  
GO  
USE AdventureWorks2012;  
ALTER FULLTEXT INDEX ON Production.Document   
   SET SEARCH PROPERTY LIST DocumentPropertyList  
   WITH NO POPULATION;   
GO   
```  
  
### <a name="b-creating-a-property-list-from-an-existing-one"></a>Б. Создание нового списка свойств на основе существующего  
 В следующем примере создается новый список свойств поиска, `JobCandidateProperties`, из списка, созданного в примере A, `DocumentPropertyList`, который будет связан с полнотекстовым индексом из базы данных `AdventureWorks2012`. Затем инструкция ALTER FULLTEXT INDEX связывает новый список свойств с полнотекстовым индексом таблицы `HumanResources.JobCandidate` из базы данных `AdventureWorks2012`. Эта инструкция ALTER FULLTEXT INDEX начинает полное заполнение — поведением по умолчанию для предложения SET SEARCH PROPERTY LIST.  
  
```  
CREATE SEARCH PROPERTY LIST JobCandidateProperties 
FROM AdventureWorks2012.DocumentPropertyList;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate   
   SET SEARCH PROPERTY LIST JobCandidateProperties;  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER SEARCH PROPERTY LIST &#40; Transact-SQL &#41;](../../t-sql/statements/alter-search-property-list-transact-sql.md)   
 [Удаление СПИСКА СВОЙСТВ поиска &#40; Transact-SQL &#41;](../../t-sql/statements/drop-search-property-list-transact-sql.md)   
 [sys.registered_search_properties &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [sys.dm_fts_index_keywords_by_property &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)   
 [Поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [Поиск идентификаторов GUID для наборов свойств и целочисленных идентификаторов свойств для свойств поиска](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md)  
  
  

