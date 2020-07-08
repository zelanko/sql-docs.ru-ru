---
title: sys. sp_rda_reconcile_indexes (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be9e80c522cc68cd4438e34d96564a7e49196152
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053029"
---
# <a name="syssp_rda_reconcile_indexes-transact-sql"></a>sys. sp_rda_reconcile_indexes (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Ставит в очередь задачу схемы для согласования индексов в удаленной таблице. После успешного завершения этой задачи Удаленная таблица будет иметь те же индексы, которые существуют в локальной таблице с поддержкой растяжения.  
  
 Если имеется другая задача, поставленная в очередь для согласования индексов при вызове **sp_rda_reconcile_indexes**, эта хранимая процедура не помещает повторяющуюся задачу в очередь.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_reconcile_indexes [@objname = ] 'objname'  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @objname =] *' objname '*  
 Полное или неполное имя таблицы с поддержкой растяжения, для которой необходимо согласовать индексы. Кавычки требуются только в том случае, если указан полный объект.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (сбой)  
  
## <a name="see-also"></a>См. также  
 [База данных Stretch](../../sql-server/stretch-database/stretch-database.md)  
  
  
