---
title: Хранимая процедура sp_revokelogin (Transact-SQL) | Документация Майкрософт
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
- sp_revokelogin_TSQL
- sp_revokelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokelogin
ms.assetid: cb1ab102-1ae0-4811-9144-9a8121ef2d7e
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 0d59e993563b340b7016887720fb8f3638dca247
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38005467"
---
# <a name="sprevokelogin-transact-sql"></a>Хранимая процедура sp_revokelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет записи имени входа из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для пользователя Windows или группы, созданные с помощью CREATE LOGIN, **sp_grantlogin**, или **sp_denylogin**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_revokelogin [ @loginame= ] 'login'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@loginame=**] **"***входа***"**  
 Имя пользователя или группы Windows. *Имя входа* — **sysname**, не имеет значения по умолчанию. *Имя входа* может быть любым существующим именем пользователя Windows или группы в форме *имя_компьютера*\\*пользователя или домена*\\*пользователя*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **Хранимая процедура sp_revokelogin** блокирует соединения, используя учетную запись, заданную аргументом *входа* параметра. Но пользователи Windows, которым доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] был предоставлен через членство в группе Windows, тем не менее, могут установить соединение после того, как был запрещен их индивидуальный доступ. Аналогично Если *входа* параметр задает имя группы Windows, члены этой группы, которые были отдельно предоставлен доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по-прежнему будут иметь возможность подключения.  
  
 Например если пользователь Windows **ADVWORKS\john** является членом группы Windows **ADVWORKS\Admins**, и **sp_revokelogin** отменяет доступ `ADVWORKS\john`:  
  
```  
sp_revokelogin [ADVWORKS\john]  
```  
  
 Пользователь **ADVWORKS\john** по-прежнему могут подключаться, если **ADVWORKS\Admins** был предоставлен доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Аналогично Если группы Windows **ADVWORKS\Admins** отменен доступ, но **ADVWORKS\john** предоставляется доступ, **ADVWORKS\john** по-прежнему можно подключиться.  
  
 Используйте **sp_denylogin** к явно запрещает пользователям подключаться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], независимо от их членства в группах Windows.  
  
 **Хранимая процедура sp_revokelogin** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY LOGIN на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляются записи имени входа для пользователя Windows `Corporate\MollyA`.  
  
```  
EXEC sp_revokelogin 'Corporate\MollyA';  
```  
  
 либо  
  
```  
EXEC sp_revokelogin [Corporate\MollyA];  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN (Transact-SQL)](../../t-sql/statements/drop-login-transact-sql.md)   
 [Хранимая процедура sp_denylogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_droplogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [Хранимая процедура sp_grantlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
