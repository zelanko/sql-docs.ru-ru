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
manager: craigg
ms.openlocfilehash: 2f08fa101e2a53696e58f15413ec08c301a9e890
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596952"
---
# <a name="spdropsrvrolemember-transact-sql"></a>sp_dropsrvrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет из предопределенной роли сервера имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] либо пользователя или группу Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropsrvrolemember [ @loginame = ] 'login' , [ @rolename = ] 'role'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @loginame **=** ] **"***входа***"**  
 Имя входа, удаляемое из предопределенной роли сервера. *Имя входа* — **sysname**, не имеет значения по умолчанию. *Имя входа* должен существовать.  
  
 [ @rolename **=** ] **"***роли***"**  
 Имя роли сервера. *роль* — **sysname**, значение по умолчанию NULL. *роль* должен принимать одно из следующих значений:  
  
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
  
## <a name="remarks"></a>Примечания  
 Чтобы удалить имя входа из предопределенной роли сервера можно использовать только sp_dropsrvrolemember. Используйте sp_droprolemember для удаления члена из роли базы данных.  
  
 Имя входа sa нельзя удалить из какой предопределенной роли сервера.  
  
 sp_dropsrvrolemember не может быть выполнена в пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера или обоих разрешение ALTER ANY LOGIN на сервере и членство в роли, из которой удаляется член sysadmin.  
  
## <a name="examples"></a>Примеры  
 В следующем примере имя входа Windows `JackO` удаляется из предопределенной роли сервера `sysadmin`.  
  
```  
EXEC sp_dropsrvrolemember 'JackO', 'sysadmin';  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE SERVER ROLE (Transact-SQL)](../../t-sql/statements/create-server-role-transact-sql.md)   
 [DROP SERVER ROLE (Transact-SQL)](../../t-sql/statements/drop-server-role-transact-sql.md)   
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
