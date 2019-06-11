---
title: sp_grant_login_to_proxy (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_proxy
- sp_grant_login_to_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_login_to_proxy
ms.assetid: 90e1a6d5-a692-4462-a163-4b0709d83150
ms.author: vanto
author: VanMSFT
manager: jrothj
ms.openlocfilehash: 81aeb41fdf7c8c17d5035347d384e7175bbd891b
ms.sourcegitcommit: 96090bb369ca8aba364c2e7f60b37165e5af28fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/10/2019
ms.locfileid: "66822668"
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
`[ @login_name = ] 'login_name'` Имя входа для предоставления доступа к. *Login_name* — **nvarchar(256)** , значение по умолчанию NULL. Один из **@login_name** , **@fixed_server_role** , или **@msdb_role** должен быть указан, или хранимая процедура завершается ошибкой.  
  
`[ @fixed_server_role = ] 'fixed_server_role'` Чтобы предоставить доступ к фиксированной серверной роли. *Fixed_server_role* — **nvarchar(256)** , значение по умолчанию NULL. Один из **@login_name** , **@fixed_server_role** , или **@msdb_role** должен быть указан, или хранимая процедура завершается ошибкой.  
  
`[ @msdb_role = ] 'msdb_role'` Роль базы данных в **msdb** базы данных для предоставления доступа к. *Msdb_role* — **nvarchar(256)** , значение по умолчанию NULL. Один из **@login_name** , **@fixed_server_role** , или **@msdb_role** должен быть указан, или хранимая процедура завершается ошибкой.  
  
`[ @proxy_id = ] id` Идентификатор для прокси-сервера, к которой предоставляется доступ. *Идентификатор* — **int**, значение по умолчанию NULL. Один из **@proxy_id** или **@proxy_name** должен быть указан, или хранимая процедура завершается ошибкой.  
  
`[ @proxy_name = ] 'proxy_name'` Имя прокси-сервера, к которой предоставляется доступ. *Proxy_name* — **nvarchar(256)** , значение по умолчанию NULL. Один из **@proxy_id** или **@proxy_name** должен быть указан, или хранимая процедура завершается ошибкой.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_grant_login_to_proxy** должна запускаться из **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера может выполняться **sp_grant_login_to_proxy**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример разрешает имени входа `adventure-works\terrid` для использования прокси-сервер `Catalog application proxy`.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_login_to_proxy  
    @login_name = N'adventure-works\terrid',  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE LOGIN (Transact-SQL)](../../t-sql/statements/create-login-transact-sql.md)   
 [Хранимая процедура sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
