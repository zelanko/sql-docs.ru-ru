---
title: sys.sp_rda_reconcile_indexes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sp_rda_reconcile_indexes
- sp_rda_reconcile_indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_indexes stored procedure
ms.assetid: 96b31ab9-bf84-46d6-9990-81f5c51f885a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 329446a2ca5b7719e68123b2257d32ceddcd0e8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756522"
---
# <a name="syssprdareconcileindexes-transact-sql"></a>sys.sp_rda_reconcile_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Помещает в очередь задачи схемы для сверить индексы в удаленной таблице. После успешного завершения этой задачи в удаленной таблице есть те же индексы, которые существуют в локальной таблице с включенным Stretch.  
  
 Если имеется другой задачи в очередь для сверить индексы, при вызове **sp_rda_reconcile_indexes**, эта хранимая процедура не помещает в очередь повторяющихся задач.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_reconcile_indexes [@objname = ] 'objname'  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [@objname =] *«objname»*  
 — Это полное или неполное имя таблицы с включенным Stretch, для которого вы хотите сверить индексы. Кавычки необходимы только в том случае, если указан уточненный объект.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (неуспешное завершение)  
  
## <a name="see-also"></a>См. также  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
