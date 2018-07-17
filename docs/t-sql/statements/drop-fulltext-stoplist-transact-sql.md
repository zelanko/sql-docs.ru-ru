---
title: DROP FULLTEXT STOPLIST (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3792a7c675b8a0121908a942dc0e58e61efc074e
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37788875"
---
# <a name="drop-fulltext-stoplist-transact-sql"></a>DROP FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Примечания  
 Инструкция DROP FULLTEXT STOPLIST закончится с ошибкой, если любой полнотекстовый индекс ссылается на удаляемый полнотекстовый список стоп-слов.  
  
## <a name="permissions"></a>Разрешения  
 Чтобы удалить список стоп-слов, необходимо иметь на него разрешение DROP или быть членом предопределенных ролей базы данных **db_owner** или **db_ddladmin**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует удаление полнотекстового списка стоп-слов `myStoplist`.  
  
```  
DROP FULLTEXT STOPLIST myStoplist;  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER FULLTEXT STOPLIST (Transact-SQL)](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [CREATE FULLTEXT STOPLIST (Transact-SQL)](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [sys.fulltext_stoplists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)  
  
  
