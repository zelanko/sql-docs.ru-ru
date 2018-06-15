---
title: DROP FULLTEXT INDEX (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
manager: craigg
ms.openlocfilehash: cfbcfee7e016d6e35dbe51e5f9b3a354cb8c7896
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33068751"
---
# <a name="drop-fulltext-index-transact-sql"></a>DROP FULLTEXT INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет полнотекстовый индекс из указанной таблицы или индексированного представления.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP FULLTEXT INDEX ON table_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *table_name*  
 Имя таблицы или индексированного представления, содержащих удаляемый полнотекстовый индекс.  
  
## <a name="remarks"></a>Remarks  
 Перед использованием команды DROP FULLTEXT INDEX необязательно удалять из полнотекстового индекса все столбцы.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER на доступ к таблице или представлению либо членство в предопределенной роли сервера **sysadmin** или предопределенных ролях базы данных **db_owner** или **db_ddladmin**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется полнотекстовый индекс в таблице `JobCandidate`.  
  
```  
USE AdventureWorks2012;  
GO  
DROP FULLTEXT INDEX ON HumanResources.JobCandidate;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.fulltext_indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)   
 [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)  
  
  
