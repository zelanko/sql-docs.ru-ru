---
title: "DROP APPLICATION ROLE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_APPLICATION_ROLE_TSQL
- DROP APPLICATION ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- dropping application roles
- deleting application roles
- removing application roles
- application roles [SQL Server], removing
- DROP APPLICATION ROLE statement
ms.assetid: 44121ee7-ef40-405d-b03b-f8ddb4e3c559
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 326c0bb53e995aeacb807a91b83d69f59d034d2f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-application-role-transact-sql"></a>DROP APPLICATION ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет роль приложения из текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP APPLICATION ROLE rolename  
```  
  
## <a name="arguments"></a>Аргументы  
 *roleName*  
 Указывает имя удаляемой роли приложения.  
  
## <a name="remarks"></a>Замечания  
 Если роли приложения принадлежат какие-либо защищаемые объекты, эта роль не может быть удалена. Перед удалением роли приложения, которой принадлежат защищаемые объекты, следует сначала перенести данные о принадлежности защищаемых объектов или удалить эти объекты.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 Необходимо наличие разрешения ALTER ANY APPLICATION ROLE для этой базы данных.  
  
## <a name="examples"></a>Примеры  
 Удаление из базы данных роли приложения «weekly_ledger».  
  
```  
DROP APPLICATION ROLE weekly_ledger;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Роли приложений](../../relational-databases/security/authentication-access/application-roles.md)   
 [СОЗДАТЬ РОЛЬ приложения &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [ALTER APPLICATION ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-application-role-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

