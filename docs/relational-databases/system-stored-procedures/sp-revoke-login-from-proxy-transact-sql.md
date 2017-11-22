---
title: "sp_revoke_login_from_proxy (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_revoke_login_from_proxy_TSQL
- sp_revoke_login_from_proxy
dev_langs: TSQL
helpviewer_keywords: sp_revoke_login_from_proxy
ms.assetid: e4546c13-9fba-4bab-8b42-d6f18b33ec25
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: efb329d4bdbdaef250e9843ed1f4641d0a679181
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sprevokeloginfromproxy-transact-sql"></a>sp_revoke_login_from_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет доступ к учетной записи-посреднику для субъекта безопасности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_revoke_login_from_proxy   
    [ @name = ] 'name' ,  
    [ @proxy_id = ] id ,  
    [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@name=** ] **"***имя***"**  
 Имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, роли сервера или **msdb** роли базы данных, чтобы удалить права доступа. *имя* — **nvarchar(256)** без значения по умолчанию.  
  
 [  **@proxy_id=** ] *идентификатор*  
 Идентификатор учетной записи-посредника, для которой удаляется право доступа. Либо *идентификатор* или *proxy_name* должен быть указан, но не оба аргумента одновременно. *Идентификатор* — **int**, значение по умолчанию NULL.  
  
 [  **@proxy_name=** ] **"***proxy_name***"**  
 Имя учетной записи-посредника, для которой удаляется право доступа. Либо *идентификатор* или *proxy_name* должен быть указан, но не оба аргумента одновременно. *Proxy_name* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Задания, принадлежащие имени входа, которое ссылается на эту учетную запись-посредник, не смогут запуститься.  
  
## <a name="permissions"></a>Permissions  
 Для выполнения этой хранимой процедуры пользователь должен быть членом предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере для имени входа `terrid` запрещается доступ к учетной записи-посреднику `Catalog application proxy`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_revoke_login_from_proxy  
    @name = N'terrid',  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Агент SQL Server хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_grant_login_to_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_help_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-proxy-transact-sql.md)  
  
  
