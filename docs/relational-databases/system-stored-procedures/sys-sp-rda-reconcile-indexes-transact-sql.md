---
title: sys.sp_rda_reconcile_indexes (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_rda_reconcile_indexes
- sp_rda_reconcile_indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_indexes stored procedure
ms.assetid: 96b31ab9-bf84-46d6-9990-81f5c51f885a
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 52791b0d8c62617411bb5599542683aa34891ab0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="syssprdareconcileindexes-transact-sql"></a>sys.sp_rda_reconcile_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Помещает в очередь задачи схемы для выверки индексов в удаленной таблице. После успешного завершения этой задачи, удаленная таблица имеет те же индексы, которые существуют в локальной таблице с включенным Stretch.  
  
 Если имеется другая задача в очереди на согласовать индексы, при вызове **sp_rda_reconcile_indexes**, эта хранимая процедура не помещает в очередь повторяющихся задач.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_reconcile_indexes [@objname = ] 'objname'  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [@objname =] *«objname»*  
 — Полное или неполное имя таблицы с включенным Stretch, для которого вы хотите согласовать индексы. Они необходимы только в том случае, если указан объект с полным именем.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (неуспешное завершение)  
  
## <a name="see-also"></a>См. также  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
