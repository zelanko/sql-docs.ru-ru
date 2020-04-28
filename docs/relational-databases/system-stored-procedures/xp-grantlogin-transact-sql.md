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
ms.openlocfilehash: 957bbdc43c0f0adf3a545fee76e9f69df130d8f9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68116674"
---
# <a name="xp_grantlogin-transact-sql"></a>xp_grantlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет группе или пользователю Windows доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_grantlogin {[@loginame = ] 'login'} [,[@logintype = ] 'logintype']  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @loginame = ] 'login'`Имя добавляемого пользователя или группы Windows. Имя пользователя или группы Windows должно быть дополнено именем домена Windows в форме "пользователь *домена*\\*User*". Аргумент *Login* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @logintype = ] 'logintype'`Уровень безопасности имени входа, доступ к которому предоставляется. *тип учетных данных* имеет тип **varchar (5)** и значение по умолчанию NULL. Можно указать только **администратора** . Если указано значение **Admin** , то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]для *входа* предоставляется доступ к и добавляется как член предопределенной роли сервера **sysadmin** .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 **xp_grantlogin** теперь является системной хранимой процедурой, а не расширенной хранимой процедурой. **xp_grantlogin** вызывает **sp_grantlogin** и **sp_addsrvrolemember**.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера **администратора** . При изменении *тип учетных данных*требует членства в предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также:  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Общие расширенные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_enumgroups &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-enumgroups-transact-sql.md)   
 [xp_loginconfig &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)   
 [Хранимая процедура sp_revokelogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)  
  
  
