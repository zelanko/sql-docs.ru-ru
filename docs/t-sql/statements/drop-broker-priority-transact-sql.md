---
title: DROP BROKER PRIORITY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_BROKER_PRIORITY_TSQL
- DROP BROKER PRIORITY
dev_langs:
- TSQL
helpviewer_keywords:
- DROP BROKER PRIORITY statement
ms.assetid: 09ee6c5b-af94-4a4b-a0e2-f9eac50e43aa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bb2601bb5fd85313fd66f58cdd0ab616bc8c13c4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893368"
---
# <a name="drop-broker-priority-transact-sql"></a>DROP BROKER PRIORITY (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет приоритет диалога из текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
DROP BROKER PRIORITY ConversationPriorityName  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *ConversationPriorityName*  
 Задает имя удаляемого приоритета диалога.  
  
## <a name="remarks"></a>Remarks  
 При удалении приоритета диалога любые существующие диалоги продолжают функционировать с уровнями приоритетов, которые были назначены им из приоритета диалога.  
  
## <a name="permissions"></a>Разрешения  
 Разрешение на создание приоритета диалога по умолчанию предоставляется членам предопределенных ролей базы данных db_ddladmin и db_owner, а также членам предопределенной роли сервера sysadmin. Необходимо разрешение ALTER на базу данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется приоритет диалога с именем `InitiatorAToTargetPriority`.  
  
```  
DROP BROKER PRIORITY InitiatorAToTargetPriority;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER BROKER PRIORITY (Transact-SQL)](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [CREATE BROKER PRIORITY (Transact-SQL)](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [sys.conversation_priorities (Transact-SQL)](../../relational-databases/system-catalog-views/sys-conversation-priorities-transact-sql.md)  
  
  
