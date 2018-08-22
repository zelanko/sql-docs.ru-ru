---
title: sp_update_proxy (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_update_proxy
- sp_update_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER PROXY statement
- sp_update_proxy
ms.assetid: 864fd0e6-9d61-4f07-92ef-145318d2f881
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 31154f48d9d13e6ebb67b25919a45ff7a1f7db8b
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393095"
---
# <a name="spupdateproxy-transact-sql"></a>sp_update_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства существующей учетной записи-посредника.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_update_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @new_name = ] 'new_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@proxy_id**=] *идентификатор*  
 Идентификационный номер изменяемой учетной записи-посредника. *Proxy_id* — **int**, значение по умолчанию NULL.  
  
 [ **@proxy_name**=] **"***proxy_name***"**  
 Имя изменяемой учетной записи-посредника. *Proxy_name* — **sysname**, значение по умолчанию NULL.  
  
 [ **@credential_name** =] **"***credential_name***"**  
 Имя новых учетных данных для учетной записи-посредника. *Credential_name* — **sysname**, значение по умолчанию NULL. Либо *credential_name* или *credential_id* может быть указан.  
  
 [ **@credential_id** =] *credential_id*  
 Идентификационный номер новых учетных данных для учетной записи-посредника. *Credential_id* — **int**, значение по умолчанию NULL. Либо *credential_name* или *credential_id* может быть указан.  
  
 [ **@new_name**=] **"***новое_имя***"**  
 Новое имя учетной записи-посредника. *Новое_имя* — **sysname**, значение по умолчанию NULL. Если указано, процедура изменяет имя прокси-сервера, *новое_имя*. Если этот аргумент равен NULL, имя учетной записи-посредника остается неизменным.  
  
 [ **@enabled** =] *is_enabled*  
 Разрешена ли учетная запись-посредник. *Is_enabled* установлен флаг **tinyint**, значение по умолчанию NULL. Когда *is_enabled* — **0**, прокси-сервер не включен и не может использоваться шагом задания. Если этот аргумент равен NULL, состояние учетной записи-посредника остается неизменным.  
  
 [ **@description**=] **"***описание***"**  
 Новое описание учетной записи-посредника. *Описание* — **nvarchar(512)**, значение по умолчанию NULL. Если этот аргумент равен NULL, описание учетной записи-посредника остается неизменным.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Либо **@proxy_name** или **@proxy_id** должен быть указан. Если указаны оба аргумента, они должны ссылаться на одну и ту же учетную запись-посредник, в противном случае хранимая процедура завершается ошибкой.  
  
 Либо **@credential_name** или **@credential_id** должен быть указан для изменения учетных данных прокси-сервер. Если указаны оба аргумента, они должны ссылаться на одни и те же учетные данные, в противном случае хранимая процедура завершается ошибкой.  
  
 Эта процедура вносит изменения в учетную запись-посредник, но не меняет порядок доступа к нему. Изменение доступа к учетной записи-посредника, использовать **sp_grant_login_to_proxy** и **sp_revoke_login_from_proxy**.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** фиксированной роли безопасности могут выполнить эту процедуру.  
  
## <a name="examples"></a>Примеры  
 В следующем примере значение «enabled» для учетной записи-посредника `Catalog application proxy` устанавливается в `0`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 0;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md)   
 [Хранимая процедура sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
