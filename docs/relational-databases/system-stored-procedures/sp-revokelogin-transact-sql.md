---
title: "Хранимая процедура sp_revokelogin (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_revokelogin_TSQL
- sp_revokelogin
dev_langs: TSQL
helpviewer_keywords: sp_revokelogin
ms.assetid: cb1ab102-1ae0-4811-9144-9a8121ef2d7e
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1d5dd00683f92f77e9ef59a64c66a7012deb274
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sprevokelogin-transact-sql"></a>Хранимая процедура sp_revokelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет учетные записи из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для пользователя или группы, созданные с помощью CREATE LOGIN **sp_grantlogin**, или **sp_denylogin**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md) вместо него.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_revokelogin [ @loginame= ] 'login'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@loginame=**] **"***входа***"**  
 Имя пользователя или группы Windows. *Имя входа* — **sysname**, не имеет значения по умолчанию. *Имя входа* может быть любым существующим именем пользователя Windows или группы в форме *имя компьютера*\\*пользователя или домена*\\*пользователя*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_revokelogin** отключает соединения с использованием учетной записи, *входа* параметра. Но пользователи Windows, которым доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] был предоставлен через членство в группе Windows, тем не менее, могут установить соединение после того, как был запрещен их индивидуальный доступ. Аналогично Если *входа* параметр указывает имя группы Windows, члены этой группы, которым был предоставлен доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по-прежнему смогут подключиться.  
  
 Например если пользователь Windows **ADVWORKS\john** является членом группы Windows **ADVWORKS\Admins**, и **sp_revokelogin** отменяет доступ `ADVWORKS\john`:  
  
```  
sp_revokelogin [ADVWORKS\john]  
```  
  
 Пользователь **ADVWORKS\john** по-прежнему могут подключиться, если **ADVWORKS\Admins** был предоставлен доступ к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Аналогично Если группы Windows **ADVWORKS\Admins** отменен доступ, но **ADVWORKS\john** предоставляется доступ, **ADVWORKS\john** по-прежнему могут подключиться.  
  
 Используйте **sp_denylogin** к явным образом запрещает пользователям подключаться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], независимо от их членства в группах Windows.  
  
 **sp_revokelogin** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER ANY LOGIN на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляются записи имени входа для пользователя Windows `Corporate\MollyA`.  
  
```  
EXEC sp_revokelogin 'Corporate\MollyA';  
```  
  
 Или  
  
```  
EXEC sp_revokelogin [Corporate\MollyA];  
```  
  
## <a name="see-also"></a>См. также:  
 [Безопасность хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN &#40; Transact-SQL &#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [Хранимая процедура sp_denylogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_droplogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [Хранимая процедура sp_grantlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
