---
title: "DROP FULLTEXT STOPLIST (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_FULLTEXT_STOPLIST_TSQL
- DROP FULLTEXT STOPLIST
dev_langs:
- TSQL
helpviewer_keywords:
- DROP FULLTEXT STOPLIST statement
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 3ee2a2bb-1dfb-4e7c-90e9-9d917cd84a15
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 86431229e26091e2fde6c3f81873523c5f09de68
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-fulltext-stoplist-transact-sql"></a>DROP FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет список полнотекстовых стоп-слов из базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
> [!IMPORTANT]  
>  Инструкция CREATE FULLTEXT STOPLIST поддерживается только для уровня совместимости 100 и выше. Для уровней совместимости 80 и 90 системный список стоп-слов всегда назначается базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP FULLTEXT STOPLIST stoplist_name  
;  
```  
  
## <a name="arguments"></a>Аргументы  
 *stoplist_name*  
 Имя полнотекстового списка стоп-слов, который нужно удалить из базы данных.  
  
## <a name="remarks"></a>Замечания  
 Инструкция DROP FULLTEXT STOPLIST закончится с ошибкой, если любой полнотекстовый индекс ссылается на удаляемый полнотекстовый список стоп-слов.  
  
## <a name="permissions"></a>Permissions  
 Чтобы удалить список стоп-слов, необходимо иметь разрешение DROP на список стоп-слов или членство в **db_owner** или **db_ddladmin** предопределенных ролей базы данных.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует удаление полнотекстового списка стоп-слов `myStoplist`.  
  
```  
DROP FULLTEXT STOPLIST myStoplist;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER FULLTEXT STOPLIST &#40; Transact-SQL &#41;](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [СОЗДАТЬ ПОЛНОТЕКСТОВЫЙ список стоп-СЛОВ &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [sys.fulltext_stoplists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)  
  
  

