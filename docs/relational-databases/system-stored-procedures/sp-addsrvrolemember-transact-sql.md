---
title: sp_addsrvrolemember (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addsrvrolemember
- sp_addsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addsrvrolemember
ms.assetid: 777f0e09-8ee5-4cb2-a3ac-939d02c3cd22
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2c927bdff462922d1846188366fbb92ce0d3663c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022424"
---
# <a name="sp_addsrvrolemember-transact-sql"></a>sp_addsrvrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет имя входа в качестве члена предопределенной роли сервера.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте [инструкцию ALTER Server Role](../../t-sql/statements/alter-server-role-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addsrvrolemember [ @loginame= ] 'login'   
    , [ @rolename = ] 'role'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @loginame **=** ] **"**_Login_**"**  
 Имя входа, добавляемое к предопределенной роли сервера. Аргумент *Login* имеет тип **sysname**и не имеет значения по умолчанию. *имя входа* может быть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] именем входа или именем входа Windows. Если имени входа Windows еще не был предоставлен доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], он предоставляется автоматически.  
  
 [ @rolename **=** ] **"**_роль_**"**  
 Имя предопределенной роли сервера, к которой добавляется имя входа. Аргумент *Role* имеет тип **sysname**, значение по умолчанию NULL и должен иметь одно из следующих значений:  
  
-   sysadmin  
  
-   securityadmin  
  
-   serveradmin  
  
-   setupadmin  
  
-   processadmin  
  
-   diskadmin  
  
-   dbcreator  
  
-   bulkadmin  

## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="remarks"></a>Remarks  
 При добавлении имени входа к предопределенной роли сервера, оно получает разрешения, связанные с этой ролью.  
  
 Нельзя изменить членство в роли имени входа sa и public.  
  
 Для добавления члена к фиксированной или пользовательской роли базы данных используется хранимая процедура sp_addrolemember.  
  
 Процедуру sp_addsrvrolemember нельзя выполнять в пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в роли, к которой добавляется новый элемент.  
  
## <a name="examples"></a>Примеры  
 В следующем примере имя входа `Corporate\HelenS` Windows добавляется к `sysadmin` предопределенной роли сервера.  
  
```  
EXEC sp_addsrvrolemember 'Corporate\HelenS', 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Функции безопасности &#40;&#41;Transact-SQL](../../t-sql/functions/security-functions-transact-sql.md)   
 [Создание роли сервера &#40;&#41;Transact-SQL](../../t-sql/statements/create-server-role-transact-sql.md)   
 [УДАЛИТЬ роль сервера &#40;&#41;Transact-SQL](../../t-sql/statements/drop-server-role-transact-sql.md)  
  
  
