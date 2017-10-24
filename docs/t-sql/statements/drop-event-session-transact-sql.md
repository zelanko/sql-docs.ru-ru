---
title: "DROP EVENT SESSION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_EVENT_SESSION_TSQL
- DROP EVENT SESSION
dev_langs:
- TSQL
helpviewer_keywords:
- event sessions [SQL Server]
- DROP EVENT SESSION statement
ms.assetid: 92eabe4b-24e2-43b1-978c-31a199964b90
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5a3f4ae4391ab174a9805b08b63d8537f00fd6e8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-event-session-transact-sql"></a>DROP EVENT SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет сеанс событий.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP EVENT SESSION event_session_name  
ON SERVER  
```  
  
## <a name="arguments"></a>Аргументы  
 *event_session_name*  
 Имя существующего сеанса событий.  
  
## <a name="remarks"></a>Замечания  
 При удалении сеанса событий полностью удаляются все сведения о конфигурации, такие как цели и параметры сеанса.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER ANY EVENT SESSION.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется, как удалить сеанс событий.  
  
```  
DROP EVENT SESSION evt_spin_lock_diagnosis  
ON SERVER;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE EVENT SESSION (Transact-SQL)](../../t-sql/statements/create-event-session-transact-sql.md)   
 [ALTER EVENT SESSION (Transact-SQL)](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [sys.server_event_sessions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)  
  
  

