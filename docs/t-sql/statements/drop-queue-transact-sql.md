---
title: "DROP ОЧЕРЕДИ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP QUEUE
- DROP_QUEUE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dropping queues
- queues [Service Broker], removing
- deleting queues
- DROP QUEUE statement
- removing queues
ms.assetid: fd866520-ca00-477d-b2e9-0110e9610ed4
caps.latest.revision: "33"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3be4f36943d6e25bb520a28593d009e7a8373c48
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
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
 Имя базы данных, содержащей удаляемую очередь. Если аргумент *имя_базы_данных* предоставляется значения по умолчанию для текущей базы данных.  
  
 *schema_name (object)*  
 Имя схемы, которой принадлежит удаляемая очередь. Если аргумент *schema_name* указано, по умолчанию используется схема по умолчанию для текущего пользователя.  
  
 *queue_name*  
 Имя удаляемой очереди.  
  
## <a name="remarks"></a>Remarks  
 Нельзя удалить очередь, если на нее ссылаются какие-либо службы.  
  
## <a name="permissions"></a>Разрешения  
 Удаление очереди разрешение по умолчанию имеет владелец очереди, члены **db_ddladmin** или **db_owner** фиксированной роли базы данных и члены **sysadmin** исправлена роль сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется **ExpenseQueue** очередь из текущей базы данных.  
  
```  
DROP QUEUE ExpenseQueue ;  
  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE QUEUE (Transact-SQL)](../../t-sql/statements/create-queue-transact-sql.md)   
 [ALTER QUEUE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-queue-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
