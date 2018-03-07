---
title: "Удаление СПИСКА СВОЙСТВ поиска (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_SEARCH_PROPERTY_LIST_TSQL
- DROP SEARCH PROPERTY LIST
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- DROP SEARCH PROPERTY LIST statement
- search property lists [SQL Server], dropping
- search property lists [SQL Server], deleting
ms.assetid: 7c7ce52a-6b77-4a1c-9abf-d5feb664bea8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 94a86720e49809e56aefeef1b3264c511f30f6be
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="drop-search-property-list-transact-sql"></a>DROP SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Удаляет список свойств из текущей базы данных, если список свойств поиска в настоящее время не связан с каким-либо полнотекстовым индексом в базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP SEARCH PROPERTY LIST property_list_name  
;  
```  
  
## <a name="arguments"></a>Аргументы  
 *property_list_name*  
 Имя списка свойств поиска для удаления. *property_list_name* представляет собой идентификатор.  
  
 Чтобы просмотреть имена существующих списков свойств, используйте [sys.registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md) представление каталога следующим образом:  
  
```  
SELECT name FROM sys.registered_search_property_lists;  
```  
  
## <a name="remarks"></a>Замечания  
 Нельзя удалить список свойств поиска из базы данных, пока он связан с каким-либо полнотекстовым индексом, попытки сделать это приводят к ошибкам. Чтобы удалить список свойств поиска из данного полнотекстового индекса, используйте [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) инструкции и укажите предложение SET SEARCH PROPERTY LIST либо с параметром OFF или именем другого списка свойств поиска.  
  
 **Чтобы просмотреть свойства перечислены на экземпляре сервера**  
  
-   [sys.registered_search_property_lists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
 **Чтобы просмотреть свойства перечислены связанные с полнотекстовыми индексами**  
  
-   [sys.fulltext_indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)  
  
 **Чтобы удалить список свойств из полнотекстового индекса**  
  
-   [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
##  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение CONTROL для списка свойств поиска.  
  
> [!NOTE]  
>  Разрешения CONTROL для списка могут быть предоставлены владельцем списка свойств. По умолчанию владельцем списка свойств поиска является пользователь, создавший этот список. Владелец может быть изменен с помощью [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере список свойств `JobCandidateProperties` удаляется из базы данных `AdventureWorks2012`.  
  
```  
DROP SEARCH PROPERTY LIST JobCandidateProperties;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER SEARCH PROPERTY LIST &#40; Transact-SQL &#41;](../../t-sql/statements/alter-search-property-list-transact-sql.md)   
 [СОЗДАТЬ список СВОЙСТВ поиска &#40; Transact-SQL &#41;](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [Поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_properties &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [sys.registered_search_property_lists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
  
