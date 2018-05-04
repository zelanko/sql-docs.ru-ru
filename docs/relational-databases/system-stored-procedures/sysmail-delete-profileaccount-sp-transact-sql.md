---
title: sysmail_delete_profileaccount_sp (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_delete_profileaccount_sp
- sysmail_delete_profileaccount_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_profileaccount_sp
ms.assetid: b58d06f2-d6c9-4c8e-95bd-027c50f4621a
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 84295da413d1cbd835ac4b70c2a241a03ff44410
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysmaildeleteprofileaccountsp-transact-sql"></a>sysmail_delete_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет учетную запись из профиля компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_delete_profileaccount_sp  {   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    {   [ @account_id = ] account_id | [ @account_name = ] 'account_name' }  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@profile_id** =] *profile_id*  
 Идентификатор удаляемого профиля. *profile_id* — **int**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* может быть указан.  
  
 [ **@profile_name** =] **"***profile_name***"**  
 Имя удаляемого профиля. *profile_name* — **sysname**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* может быть указан.  
  
 [ **@account_id** =] *account_id*  
 Идентификатор удаляемой учетной записи. *account_id* — **int**, значение по умолчанию NULL. Либо *account_id* или *account_name* может быть указан.  
  
 [ **@account_name** =] **"***account_name***"**  
 Имя удаляемой учетной записи. *account_name* — **sysname**, значение по умолчанию NULL. Либо *account_id* или *account_name* может быть указан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Возвращает ошибку, если указанная учетная запись не связана с указанным профилем.  
  
 Если указана учетная запись, но не указан профиль, хранимая процедура удаляет указанную учетную запись из всех профилей. Например, если предстоит отключить существующий SMTP-сервер, то следует удалить учетные записи, в которых используется этот SMTP-сервер, из всех профилей, вместо того чтобы удалять каждую учетную запись из каждого профиля.  
  
 Если указан профиль, но не указана учетная запись, хранимая процедура удаляет все учетные записи из указанного профиля. Например, если изменены используемые профилем SMTP-серверы, то может оказаться удобнее удалить все учетные записи из профиля, а затем добавлять новые учетные записи по мере необходимости.  
  
 Хранимая процедура **sysmail_delete_profileaccount_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру следует выполнять с трехкомпонентным именем, если текущая база данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию членам выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано удаление учетной записи `Audit Account` из профиля `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator',  
    @account_name = 'Audit Account' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создайте учетную запись электронной почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
