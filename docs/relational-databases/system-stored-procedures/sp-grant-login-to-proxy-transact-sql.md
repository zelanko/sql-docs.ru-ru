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
ms.openlocfilehash: bdfeab5754a2397c01ace2bb9f822fa168eeef6b
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005854"
---
# <a name="sp_grant_login_to_proxy-transact-sql"></a>sp_grant_login_to_proxy (Transact-SQL)

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
`[ @login_name = ] 'login_name'` имя входа для предоставления доступа. Аргумент *login_name* имеет тип **nvarchar (256)** и значение по умолчанию NULL. Необходимо указать один из **\@login_name**, **\@fixed_server_role**или **\@msdb_role** , иначе хранимая процедура завершится ошибкой.  
  
`[ @fixed_server_role = ] 'fixed_server_role'` предопределенной роли сервера для предоставления доступа. *Fixed_server_role* имеет тип **nvarchar (256)** и значение по умолчанию NULL. Необходимо указать один из **\@login_name**, **\@fixed_server_role**или **\@msdb_role** , иначе хранимая процедура завершится ошибкой.  
  
`[ @msdb_role = ] 'msdb_role'` роль базы данных в базе данных **msdb** , к которой предоставляется доступ. *Msdb_role* имеет тип **nvarchar (256)** и значение по умолчанию NULL. Необходимо указать один из **\@login_name**, **\@fixed_server_role**или **\@msdb_role** , иначе хранимая процедура завершится ошибкой.  
  
`[ @proxy_id = ] id` идентификатор учетной записи-посредника, для которой предоставляется доступ. *Идентификатор* имеет **тип int**и значение по умолчанию NULL. Необходимо указать один из **\@proxy_id** или **\@proxy_name** , иначе хранимая процедура завершится с ошибкой.  
  
`[ @proxy_name = ] 'proxy_name'` имя учетной записи-посредника, для которой предоставляется доступ. *Proxy_name* имеет тип **nvarchar (256)** и значение по умолчанию NULL. Необходимо указать один из **\@proxy_id** или **\@proxy_name** , иначе хранимая процедура завершится с ошибкой.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_grant_login_to_proxy** необходимо запускать из базы данных **msdb** .  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_grant_login_to_proxy**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере имя входа `adventure-works\terrid` позволяет использовать прокси-сервер `Catalog application proxy`.  
  
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
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
