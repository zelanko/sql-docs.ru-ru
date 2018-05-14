---
title: DROP QUEUE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP QUEUE
- DROP_QUEUE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dropping queues
- queues [Service Broker], removing
- deleting queues
- DROP QUEUE statement
- removing queues
ms.assetid: fd866520-ca00-477d-b2e9-0110e9610ed4
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 514946f3bb867d30f9b3f0e613203baf85f1d909
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="drop-queue-transact-sql"></a>DROP QUEUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет существующую очередь.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP QUEUE <object>  
[ ; ]  
  
<object> ::=  
{  
    [ database_name . [ schema_name ] . | schema_name . ]  
        queue_name  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных, содержащей удаляемую очередь. Если аргумент *database_name* не указан, по умолчанию используется текущая база данных.  
  
 *schema_name (object)*  
 Имя схемы, которой принадлежит удаляемая очередь. Если аргумент *schema_name* не указан, по умолчанию используется схема по умолчанию текущего пользователя.  
  
 *queue_name*  
 Имя удаляемой очереди.  
  
## <a name="remarks"></a>Remarks  
 Нельзя удалить очередь, если на нее ссылаются какие-либо службы.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения на очистку очереди предоставляются владельцу очереди, членам предопределенных ролей **db_ddladmin** или **db_owner** базы данных и членам предопределенной роли сервера **sysadmin**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется удаление очереди **ExpenseQueue** из текущей базы данных.  
  
```  
DROP QUEUE ExpenseQueue ;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE QUEUE (Transact-SQL)](../../t-sql/statements/create-queue-transact-sql.md)   
 [ALTER QUEUE (Transact-SQL)](../../t-sql/statements/alter-queue-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
