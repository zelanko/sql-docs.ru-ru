---
title: Хранимая процедура sp_add_proxy (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_proxy
- sp_add_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE PROXY statement
- sp_add_proxy
ms.assetid: cb59df37-f103-439b-bec1-2871fb669a8b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e9353e797f5ff84101726b0cfe7d12020f14fca3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811452"
---
# <a name="spaddproxy-transact-sql"></a>Хранимая процедура sp_add_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет указанную учетную запись-посредник агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_proxy  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description' ,  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @proxy_id = ] id OUTPUT   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@proxy_name**=] **"***proxy_name***"**  
 Имя создаваемой учетной записи-посредника. *Proxy_name* — **sysname**, значение по умолчанию NULL. При *proxy_name* имеет значение NULL или является пустой строкой, имя прокси-сервера по умолчанию используется *user_name* указано.  
  
 [ **@enabled** =] *is_enabled*  
 Указывает, включена ли учетная запись-посредник. *Is_enabled* установлен флаг **tinyint**, значение по умолчанию 1. Когда *is_enabled* — **0**, прокси-сервер не включен и не может использоваться шагом задания.  
  
 [ **@description**=] **"***описание***"**  
 Описание учетной записи-посредника. Описание **nvarchar(512)**, значение по умолчанию NULL. Описание позволяет документировать учетную запись-посредника, но оно не используется агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для других целей. Поэтому этот аргумент необязателен.  
  
 [ **@credential_name** =] **"***credential_name***"**  
 Имя учетных данных учетной записи-посредника. *Credential_name* — **sysname**, значение по умолчанию NULL. Либо *credential_name* или *credential_id* должен быть указан.  
  
 [ **@credential_id** =] *credential_id*  
 Идентификационный номер учетных данных учетной записи-посредника. *Credential_id* — **int**, значение по умолчанию NULL. Либо *credential_name* или *credential_id* должен быть указан.  
  
 [ **@proxy_id**=] *идентификатор* выходных данных  
 Идентификационный номер, присваиваемый учетной записи-посреднику после успешного создания.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Эта хранимая процедура должна выполняться в **msdb** базы данных.  
  
 Учетная запись-посредник агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] управляет безопасностью шагов задания, в которых задействованы подсистемы, отличные от подсистемы языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. Каждой учетной записи-посреднику соответствует учетная запись системы безопасности. Учетная запись-посредник может иметь доступ к любому числу подсистем.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** фиксированной роли безопасности могут выполнить эту процедуру.  
  
 Членами **sysadmin** фиксированной роли безопасности можно создавать шаги задания, использующие любой прокси-сервера. Хранимая процедура [sp_grant_login_to_proxy &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md) для предоставления другим именам входа доступа на прокси-сервер.  
  
## <a name="examples"></a>Примеры  
 В этом примере создается учетная запись-посредник для учетных данных `CatalogApplicationCredential`. Предполагается, что эти учетные данные уже существуют. Дополнительные сведения об учетных данных см. в разделе [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md).  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 1,  
    @description = 'Maintenance tasks on catalog application.',  
    @credential_name = 'CatalogApplicationCredential' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
