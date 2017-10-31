---
title: "DROP FULLTEXT INDEX (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_FULLTEXT_INDEX_TSQL
- DROP FULLTEXT INDEX
dev_langs:
- TSQL
helpviewer_keywords:
- deleting full-text indexes
- removing full-text indexes
- full-text indexes [SQL Server], removing
- DROP FULLTEXT INDEX statement
- dropping full-text indexes
ms.assetid: 7443a4ab-1d43-4a22-bbba-a07f620892cb
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d4636ec49342f1028a09b90c348387520e5e4355
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-fulltext-index-transact-sql"></a>DROP FULLTEXT INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет полнотекстовый индекс из указанной таблицы или индексированного представления.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP FULLTEXT INDEX ON table_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_таблицы*  
 Имя таблицы или индексированного представления, содержащих удаляемый полнотекстовый индекс.  
  
## <a name="remarks"></a>Замечания  
 Перед использованием команды DROP FULLTEXT INDEX необязательно удалять из полнотекстового индекса все столбцы.  
  
## <a name="permissions"></a>Permissions  
 Пользователь должен обладать разрешением ALTER для таблицы или индексированного представления или быть членом **sysadmin** предопределенной роли сервера или **db_owner** или **db_ddladmin** предопределенных ролей базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется полнотекстовый индекс в таблице `JobCandidate`.  
  
```  
USE AdventureWorks2012;  
GO  
DROP FULLTEXT INDEX ON HumanResources.JobCandidate;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.fulltext_indexes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)   
 [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)  
  
  

