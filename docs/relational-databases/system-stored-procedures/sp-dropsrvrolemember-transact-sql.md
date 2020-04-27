---
title: sp_dropsrvrolemember (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropsrvrolemember
- sp_dropsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropsrvrolemember
ms.assetid: 7be99181-d221-49d0-9cb2-c930d8c044a0
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 2624ed4800a247b0847adc5839346758aa50f140
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67463562"
---
# <a name="sp_dropsrvrolemember-transact-sql"></a>sp_dropsrvrolemember (Transact-SQL)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Удаляет из предопределенной роли сервера имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] либо пользователя или группу Windows.

> [!IMPORTANT]
> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте [инструкцию ALTER Server Role](../../t-sql/statements/alter-server-role-transact-sql.md) .

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Синтаксис

```
sp_dropsrvrolemember [ @loginame = ] 'login' , [ @rolename = ] 'role'  
```

## <a name="arguments"></a>Аргументы

**[ @loginame = ]** "_Login_"  
Имя входа, удаляемое из предопределенной роли сервера. Аргумент *Login* имеет тип **sysname**и не имеет значения по умолчанию. *имя для входа* должно существовать.  

**[ @rolename = ]** "_Role_"  
Имя роли сервера. Аргумент *Role* имеет тип **sysname**и значение по умолчанию NULL. значение *Role* должно быть одним из следующих:  

-   sysadmin  
  
-   securityadmin  
  
-   serveradmin  
  
-   setupadmin  
  
-   processadmin  
  
-   diskadmin  
  
-   dbcreator  
  
-   bulkadmin 
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 Для удаления имени входа из предопределенной роли сервера может использоваться только хранимая процедура sp_dropsrvrolemember. Для удаления члена из роли базы данных следует использовать хранимую процедуру sp_droprolemember.  
  
 Имя входа sa нельзя удалить ни из какой предопределенной роли сервера.  
  
 Процедуру sp_dropsrvrolemember нельзя выполнять в рамках пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в предопределенной роли сервера sysadmin либо наличия как разрешения ALTER ANY LOGIN на сервере, так и членства в роли, из которой удаляется член этой роли.  
  
## <a name="examples"></a>Примеры  
 В следующем примере имя входа Windows `JackO` удаляется из предопределенной роли сервера `sysadmin`.  
  
```sql
EXEC sp_dropsrvrolemember 'JackO', 'sysadmin';  
```  
  
## <a name="see-also"></a>См. также  
 [Создание роли сервера &#40;&#41;Transact-SQL](../../t-sql/statements/create-server-role-transact-sql.md)   
 [УДАЛИТЬ роль сервера &#40;&#41;Transact-SQL](../../t-sql/statements/drop-server-role-transact-sql.md)   
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
