---
title: "DROP ENDPOINT (Transact-SQL) | Документы Microsoft"
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
- DROP_ENDPOINT_TSQL
- DROP ENDPOINT
dev_langs:
- TSQL
helpviewer_keywords:
- removing endpoints
- endpoints [SQL Server], removing
- deleting endpoints
- DROP ENDPOINT statement
- dropping endpoints
ms.assetid: 6aca7412-66a5-4fa4-86b2-061512ff2080
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c823724dbd2f273a161b103b44eb50a77d5f4462
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-endpoint-transact-sql"></a>DROP ENDPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет существующую конечную точку.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP ENDPOINT endPointName  
```  
  
## <a name="arguments"></a>Аргументы  
 *endPointName*  
 Имя конечной точки, подлежащей удалению.  
  
## <a name="remarks"></a>Замечания  
 Инструкции ENDPOINT DDL внутри пользовательской транзакции выполняться не могут.  
  
## <a name="permissions"></a>Permissions  
 Пользователь должен быть членом **sysadmin** предопределенной роли сервера, владельцем конечной точки, или было предоставлено разрешение CONTROL на конечную точку.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется созданная ранее конечная точка с именем `sql_endpoint`.  
  
```  
DROP ENDPOINT sql_endpoint;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE ENDPOINT (Transact-SQL)](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [ALTER ENDPOINT (Transact-SQL)](../../t-sql/statements/alter-endpoint-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

