---
title: sysmail_delete_profileaccount_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_profileaccount_sp
- sysmail_delete_profileaccount_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_profileaccount_sp
ms.assetid: b58d06f2-d6c9-4c8e-95bd-027c50f4621a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 27568d450bed5a937931164ed1c04cd09d0b7c2f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890930"
---
# <a name="sysmail_delete_profileaccount_sp-transact-sql"></a>sysmail_delete_profileaccount_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет учетную запись из профиля компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_delete_profileaccount_sp  {   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    {   [ @account_id = ] account_id | [ @account_name = ] 'account_name' }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_id = ] profile_id`Идентификатор профиля удаляемого профиля. *profile_id* имеет **тип int**и значение по умолчанию NULL. Можно указать либо *profile_id* , либо *profile_name* .  
  
`[ @profile_name = ] 'profile_name'`Имя профиля удаляемого профиля. Аргумент *profile_name* имеет тип **sysname**и значение по умолчанию NULL. Можно указать либо *profile_id* , либо *profile_name* .  
  
`[ @account_id = ] account_id`Идентификатор удаляемой учетной записи. *account_id* имеет **тип int**и значение по умолчанию NULL. Можно указать либо *account_id* , либо *account_name* .  
  
`[ @account_name = ] 'account_name'`Имя удаляемой учетной записи. Аргумент *account_name* имеет тип **sysname**и значение по умолчанию NULL. Можно указать либо *account_id* , либо *account_name* .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Возвращает ошибку, если указанная учетная запись не связана с указанным профилем.  
  
 Если указана учетная запись, но не указан профиль, хранимая процедура удаляет указанную учетную запись из всех профилей. Например, если предстоит отключить существующий SMTP-сервер, то следует удалить учетные записи, в которых используется этот SMTP-сервер, из всех профилей, вместо того чтобы удалять каждую учетную запись из каждого профиля.  
  
 Если указан профиль, но не указана учетная запись, хранимая процедура удаляет все учетные записи из указанного профиля. Например, если изменены используемые профилем SMTP-серверы, то может оказаться удобнее удалить все учетные записи из профиля, а затем добавлять новые учетные записи по мере необходимости.  
  
 Хранимая процедура **sysmail_delete_profileaccount_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано удаление учетной записи `Audit Account` из профиля `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator',  
    @account_name = 'Audit Account' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создание учетной записи Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Database Mail объекты конфигурации](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
