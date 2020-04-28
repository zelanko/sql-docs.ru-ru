---
title: sp_revokelogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revokelogin_TSQL
- sp_revokelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokelogin
ms.assetid: cb1ab102-1ae0-4811-9144-9a8121ef2d7e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 95598885a80b1f697f5e1287e22c1048e737ba6b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67944724"
---
# <a name="sp_revokelogin-transact-sql"></a>Хранимая процедура sp_revokelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет записи входа из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для пользователя или группы Windows, созданных с помощью инструкции CREATE login, **sp_grantlogin**или **sp_denylogin**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте [инструкцию DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_revokelogin [ @loginame= ] 'login'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @loginame = ] 'login'`Имя пользователя или группы Windows. Аргумент *Login* имеет тип **sysname**и не имеет значения по умолчанию. именем для *входа* может быть любое существующее имя пользователя или группа Windows в формате *компьютер имя*\\*пользователь или домен*\\*пользователь*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 **sp_revokelogin** отключает соединения, используя учетную запись, указанную параметром *Login* . Но пользователи Windows, которым доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] был предоставлен через членство в группе Windows, тем не менее, могут установить соединение после того, как был запрещен их индивидуальный доступ. Аналогично, если параметр *Login* указывает имя группы Windows, то члены этой группы, которым был предоставлен доступ к экземпляру по отдельности, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будут по-прежнему иметь возможность подключения.  
  
 Например, если пользователь **Адвворкс\жохн** Windows является членом группы Windows **адвворкс\админс**, а **sp_revokelogin** отменяет доступ к `ADVWORKS\john`:  
  
```  
sp_revokelogin [ADVWORKS\john]  
```  
  
 Пользователь **адвворкс\жохн** по-прежнему может подключиться, если **адвворкс\админс** предоставил доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Аналогично, если доступ к группе Windows **адвворкс\админс** был отменен, но **адвворкс\жохн** получает доступ, **адвворкс\жохн** может подключиться.  
  
 Используйте **sp_denylogin** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы явно запретить пользователям подключаться к экземпляру, независимо от членства в группе Windows.  
  
 **sp_revokelogin** не может быть выполнена в пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY LOGIN на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляются записи входа для пользователя `Corporate\MollyA`Windows.  
  
```  
EXEC sp_revokelogin 'Corporate\MollyA';  
```  
  
 либо  
  
```  
EXEC sp_revokelogin [Corporate\MollyA];  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN &#40;&#41;Transact-SQL](../../t-sql/statements/drop-login-transact-sql.md)   
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
