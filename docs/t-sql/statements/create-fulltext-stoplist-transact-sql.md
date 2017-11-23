---
title: "Создание FULLTEXT STOPLIST (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STOPLIST_TSQL
- FULLTEXT STOPLIST
- STOPLIST
- FULLTEXT_STOPLIST_TSQL
- CREATE FULLTEXT STOPLIST
- CREATE_FULLTEXT_STOPLIST_TSQL
dev_langs: TSQL
helpviewer_keywords:
- stoplists [full-text search]
- CREATE FULLTEXT STOPLIST statement
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 0669b1d0-46cc-4fac-8df7-5f7fa7af5db4
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1836d3f750b8c1ac75fd7ed6b9626e159d16eae3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="create-fulltext-stoplist-transact-sql"></a>CREATE FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает новый полнотекстовый список стоп-слов в текущей базе данных.  
  
 Стоп-слов в базах данных управляются с помощью объектов, называемых *списки стоп-слов*. Списки стоп-слов взаимосвязаны с полнотекстовыми индексами и применяются при полнотекстовых запросах по этим индексам. Дополнительные сведения см. в разделе [Настройка стоп-слов и списков стоп-слов для полнотекстового поиска и управление ими](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
> [!IMPORTANT]  
>  Инструкции CREATE FULLTEXT STOPLIST, ALTER FULLTEXT STOPLIST и DROP FULLTEXT STOPLIST поддерживаются только в условиях применения уровня совместимости 100. При использовании уровней совместимости 80 и 90 эти инструкции не поддерживаются. Тем не менее при любом уровне совместимости системный список стоп-слов автоматически связывается с новыми полнотекстовыми индексами.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE FULLTEXT STOPLIST stoplist_name  
[ FROM { [ database_name.]source_stoplist_name } | SYSTEM STOPLIST ]  
[ AUTHORIZATION owner_name ]  
;  
```  
  
## <a name="arguments"></a>Аргументы  
 *stoplist_name*  
 Имя списка стоп-слов. *stoplist_name* не может превышать 128 символов. *stoplist_name* должно быть уникальным среди всех списков стоп-слов в текущей базе данных и соответствовать правилам для идентификаторов.  
  
 *stoplist_name* будет использоваться при создании полнотекстового индекса.  
  
 *database_name*  
 Имя базы данных, где указанный список стоп-слов *source_stoplist_name* находится. Если не указан, *имя_базы_данных* значения по умолчанию для текущей базы данных.  
  
 *source_stoplist_name*  
 Указывает, что новый список стоп-слов создается копированием существующего списка стоп-слов. Если *source_stoplist_name* не существует, или пользователь базы данных не имеет необходимых разрешений, инструкция CREATE FULLTEXT STOPLIST завершается с ошибкой. Если в текущей базе данных не зарегистрирован любой язык стоп-слов из исходного списка стоп-слов, инструкция CREATE FULLTEXT STOPLIST завершается успешно, но с предупреждениями, а соответствующие стоп-слова не добавляются.  
  
 SYSTEM STOPLIST  
 Указывает, что новый список стоп-слов создается из списка стоп-слов, что существует по умолчанию в [базы данных Resource](../../relational-databases/databases/resource-database.md).  
  
 АВТОРИЗАЦИЯ *owner_name*  
 Указывает имя участника базы данных, являющейся владельцем списка стоп-слов. *owner_name* должны быть имя участника, в которой текущий пользователь является членом, либо текущий пользователь должен иметь разрешение IMPERSONATE *owner_name*. Если атрибут не указан, владельцем становится текущий пользователь.  
  
## <a name="remarks"></a>Замечания  
 Создателем списка стоп-слов является его владелец.  
  
## <a name="permissions"></a>Permissions  
 Для создания списка стоп-слов необходимы разрешения CREATE FULLTEXT CATALOG. Владелец списка стоп-слов может явно предоставить разрешение CONTROL для списка стоп-слов, что позволит пользователям добавлять и удалять стоп-слова, а также удалять список стоп-слов.  
  
> [!NOTE]  
>  Чтобы использовать список стоп-слов с полнотекстовым индексом, необходимо разрешение REFERENCE.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-new-full-text-stoplist"></a>A. Создание полнотекстового списка стоп-слов  
 В следующем примере показано создание полнотекстового списка стоп-слов с именем `myStoplist`.  
  
```  
CREATE FULLTEXT STOPLIST myStoplist;  
GO  
```  
  
### <a name="b-copying-a-full-text-stoplist-from-an-existing-full-text-stoplist"></a>Б. Копирование полнотекстового списка стоп-слов из существующего полнотекстового списка стоп-слов  
 В следующем примере демонстрируется создание нового полнотекстового списка стоп-слов с именем `myStoplist2` путем копирования существующего списка стоп-слов базы данных AdventureWorks с именем `Customers.otherStoplist`.  
  
```  
CREATE FULLTEXT STOPLIST myStoplist2 FROM AdventureWorks.otherStoplist;  
GO  
```  
  
### <a name="c-copying-a-full-text-stoplist-from-the-system-full-text-stoplist"></a>В. Копирование списка полнотекстовых стоп-слов из системного полнотекстового списка стоп-слов  
 Следующий пример демонстрирует создание нового полнотекстового списка стоп-слов с именем `myStoplist3` путем копирования из системного списка стоп-слов.  
  
```  
CREATE FULLTEXT STOPLIST myStoplist3 FROM SYSTEM STOPLIST;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER FULLTEXT STOPLIST &#40; Transact-SQL &#41;](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [DROP FULLTEXT STOPLIST &#40; Transact-SQL &#41;](../../t-sql/statements/drop-fulltext-stoplist-transact-sql.md)   
 [Настройка и управление стоп-словами и списками стоп-слов для полнотекстового поиска](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [sys.fulltext_stoplists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [Настройка стоп-слов, списков стоп-слов и управление ими для полнотекстового поиска](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)  
  
  
