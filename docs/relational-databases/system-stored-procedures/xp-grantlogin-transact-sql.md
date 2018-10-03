---
title: xp_grantlogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_grantlogin
- xp_grantlogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_grantlogin
ms.assetid: c851c1ab-3b29-4b99-9902-78c2665a844b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: a6b08e90fafccca3c64b13132b9cf9e248fdee7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47663781"
---
# <a name="xpgrantlogin-transact-sql"></a>xp_grantlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет группе или пользователю Windows доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_grantlogin {[@loginame = ] 'login'} [,[@logintype = ] 'logintype']  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@loginame =** ] **"***входа***"**  
 Имя добавляемого пользователя или группы Windows. Windows пользователь или группа должны быть дополнены именем домена Windows в виде *домена*\\*пользователя*. *Имя входа* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@logintype =** ] **"***logintype***"**  
 Уровень безопасности входного имени, которому предоставляется доступ. *Тип учетных данных* — **varchar(5)**, значение по умолчанию NULL. Только **администратора** можно указать. Если **администратора** указано, *входа* к предоставлен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и добавляется как член **sysadmin** предопределенной роли сервера.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **xp_grantlogin** является в настоящее время системной хранимой процедуры, а не расширенной хранимой процедуры. **xp_grantlogin** вызовы **sp_grantlogin** и **sp_addsrvrolemember**.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **securityadmin** предопределенной роли сервера. При изменении *logintype*, требуется членство в **sysadmin** предопределенной роли сервера.  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_denylogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [Хранимая процедура sp_grantlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Общие расширенные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_enumgroups &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-enumgroups-transact-sql.md)   
 [xp_loginconfig &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)   
 [Хранимая процедура sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)  
  
  
