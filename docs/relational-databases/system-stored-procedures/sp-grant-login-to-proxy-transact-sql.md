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
ms.openlocfilehash: d7ac6bfbd157a72cee716b4a5a916cf2c7069ba8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750539"
---
# <a name="sp_grant_login_to_proxy-transact-sql"></a>sp_grant_login_to_proxy (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

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
`[ @login_name = ] 'login_name'`Имя входа, к которому предоставляется доступ. *Login_name* имеет тип **nvarchar (256)** и значение по умолчанию NULL. Необходимо указать один из ** \@ login_name**, ** \@ fixed_server_role**или ** \@ msdb_role** или выполнить хранимую процедуру с ошибкой.  
  
`[ @fixed_server_role = ] 'fixed_server_role'`Предопределенная роль сервера, к которой предоставляется доступ. *Fixed_server_role* имеет тип **nvarchar (256)** и значение по умолчанию NULL. Необходимо указать один из ** \@ login_name**, ** \@ fixed_server_role**или ** \@ msdb_role** или выполнить хранимую процедуру с ошибкой.  
  
`[ @msdb_role = ] 'msdb_role'`Роль базы данных в базе данных **msdb** , к которой предоставляется доступ. *Msdb_role* имеет тип **nvarchar (256)** и значение по умолчанию NULL. Необходимо указать один из ** \@ login_name**, ** \@ fixed_server_role**или ** \@ msdb_role** или выполнить хранимую процедуру с ошибкой.  
  
`[ @proxy_id = ] id`Идентификатор учетной записи-посредника, для которой предоставляется доступ. *Идентификатор* имеет **тип int**и значение по умолчанию NULL. Необходимо указать один из ** \@ proxy_id** или ** \@ proxy_name** или выполнить хранимую процедуру с ошибкой.  
  
`[ @proxy_name = ] 'proxy_name'`Имя учетной записи-посредника, для которой предоставляется доступ. *Proxy_name* имеет тип **nvarchar (256)** и значение по умолчанию NULL. Необходимо указать один из ** \@ proxy_id** или ** \@ proxy_name** или выполнить хранимую процедуру с ошибкой.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_grant_login_to_proxy** должны запускаться из базы данных **msdb** .  
  
## <a name="permissions"></a>Разрешения  
 **Sp_grant_login_to_proxy**могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере имя входа позволяет `adventure-works\terrid` использовать прокси-сервер `Catalog application proxy` .  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_login_to_proxy  
    @login_name = N'adventure-works\terrid',  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Создание имени входа &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
