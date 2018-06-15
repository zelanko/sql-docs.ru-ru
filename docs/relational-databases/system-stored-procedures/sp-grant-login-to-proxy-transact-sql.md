---
title: sp_grant_login_to_proxy (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_proxy
- sp_grant_login_to_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_login_to_proxy
ms.assetid: 90e1a6d5-a692-4462-a163-4b0709d83150
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e07e03296c9264245504b65136a467e0fe7040e2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33259614"
---
# <a name="spgrantlogintoproxy-transact-sql"></a>sp_grant_login_to_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет субъекту безопасности доступ к учетной записи-посреднику.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_grant_login_to_proxy   
     { [ @login_name = ] 'login_name'   
     | [ @fixed_server_role = ] 'fixed_server_role'   
     | [ @msdb_role = ] 'msdb_role' } ,   
     { [ @proxy_id = ] id | [ @proxy_name = ] 'proxy_name' }  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@login_name** =] **"***login_name***"**  
 Имя входа, которому предоставляется доступ. *Login_name* — **nvarchar(256)**, значение по умолчанию NULL. Один из **@login_name**, **@fixed_server_role**, или **@msdb_role** должен быть указан, или хранимая процедура завершается ошибкой.  
  
 [ **@fixed_server_role**=] **"***fixed_server_role***"**  
 Предопределенная роль сервера, которой предоставляется доступ. *Fixed_server_role* — **nvarchar(256)**, значение по умолчанию NULL. Один из **@login_name**, **@fixed_server_role**, или **@msdb_role** должен быть указан, или хранимая процедура завершается ошибкой.  
  
 [ **@msdb_role**=] '*msdb_role*"  
 Роль базы данных в **msdb** базы данных для предоставления доступа к. *Msdb_role* — **nvarchar(256)**, значение по умолчанию NULL. Один из **@login_name**, **@fixed_server_role**, или **@msdb_role** должен быть указан, или хранимая процедура завершается ошибкой.  
  
 [ **@proxy_id**=] *идентификатор*  
 Идентификатор учетной записи-посредника, к которой предоставляется доступ. *Идентификатор* — **int**, значение по умолчанию NULL. Один из **@proxy_id** или **@proxy_name** должен быть указан, или хранимая процедура завершается ошибкой.  
  
 [ **@proxy_name**=] **"***proxy_name***"**  
 Имя учетной записи-посредника, к которой предоставляется доступ. *Proxy_name* — **nvarchar(256)**, значение по умолчанию NULL. Один из **@proxy_id** или **@proxy_name** должен быть указан, или хранимая процедура завершается ошибкой.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_grant_login_to_proxy** должна запускаться из **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера может выполняться **sp_grant_login_to_proxy**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере пользователь входа `adventure-works\terrid` для использования прокси-сервера `Catalog application proxy`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_login_to_proxy  
    @login_name = N'adventure-works\terrid',  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [Хранимая процедура sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
