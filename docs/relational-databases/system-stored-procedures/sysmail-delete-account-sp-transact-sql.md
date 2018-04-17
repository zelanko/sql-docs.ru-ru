---
title: sysmail_delete_account_sp (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sysmail_delete_account_sp
- sysmail_delete_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_account_sp
ms.assetid: 2adcac78-4a4a-407e-9666-1d9c43c73cc2
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a103d5e5c5127e65fdfd103ade26a0ce298159d0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysmaildeleteaccountsp-transact-sql"></a>sysmail_delete_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет почтовую учетную запись SMTP-сервера компонента Database Mail. Для удаления учетной записи также можно воспользоваться мастером настройки компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_delete_account_sp { [ @account_id = ] account_id | [ @account_name = ] 'account_name' }   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@account_id** =] *account_id*  
 Идентификатор удаляемой учетной записи. *account_id* — **int**, не имеет значения по умолчанию. Либо *account_id* или *account_name* должен быть указан.  
  
 [ **@account_name** =] **"***account_name***"**  
 Имя удаляемой учетной записи. *account_name* — **sysname**, не имеет значения по умолчанию. Либо *account_id* или *account_name* должен быть указан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Эта процедура удаляет указанную учетную запись вне зависимости от того, используется ли учетная запись профилем. Не содержащий учетных записей профиль не может отправлять сообщения по электронной почте.  
  
 Хранимая процедура **sysmail_delete_account_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру следует выполнять с трехкомпонентным именем, если текущая база данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию членам выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 Следующий пример показывает удаление учетной записи компонента Database Mail под названием `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создайте учетную запись электронной почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [sysmail_add_account_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-account-sp-transact-sql.md)   
 [sysmail_delete_profile_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-delete-profile-sp-transact-sql.md)   
 [sysmail_delete_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-delete-profileaccount-sp-transact-sql.md)   
 [sysmail_help_account_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-help-account-sp-transact-sql.md)   
 [sysmail_help_profile_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-help-profile-sp-transact-sql.md)   
 [sysmail_help_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-help-profileaccount-sp-transact-sql.md)   
 [sysmail_update_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql.md)  
  
  
