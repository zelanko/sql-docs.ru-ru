---
title: sysmail_delete_account_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_account_sp
- sysmail_delete_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_account_sp
ms.assetid: 2adcac78-4a4a-407e-9666-1d9c43c73cc2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4b6adc5f6c02eae49a5f5e2598c6b02e5b00534e
ms.sourcegitcommit: 3de1fb410de2515e5a00a5dbf6dd442d888713ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2019
ms.locfileid: "70211272"
---
# <a name="sysmail_delete_account_sp-transact-sql"></a>sysmail_delete_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Удаляет почтовую учетную запись SMTP-сервера компонента Database Mail. Для удаления учетной записи также можно воспользоваться мастером настройки компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_delete_account_sp { [ @account_id = ] account_id | [ @account_name = ] 'account_name' }   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @account_id = ] account_id` ИДЕНТИФИКАЦИОНный номер удаляемой учетной записи. *account_id* имеет **тип int**и не имеет значения по умолчанию. Необходимо указать либо *account_id* , либо *account_name* .  
  
`[ @account_name = ] 'account_name'` имя учетной записи для удаления. Аргумент *account_name* имеет тип **sysname**и не имеет значения по умолчанию. Необходимо указать либо *account_id* , либо *account_name* .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Remarks  
 Эта процедура удаляет указанную учетную запись вне зависимости от того, используется ли учетная запись профилем. Не содержащий учетных записей профиль не может отправлять сообщения по электронной почте.  
  
 Хранимая процедура **sysmail_delete_account_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 Следующий пример показывает удаление учетной записи компонента Database Mail под названием `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>См. также статью  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создание учетной записи Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Database Mail объекты конфигурации](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [sysmail_add_account_sp &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sysmail-add-account-sp-transact-sql.md)  
 [sysmail_delete_profile_sp &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sysmail-delete-profile-sp-transact-sql.md)  
 [sysmail_delete_profileaccount_sp &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sysmail-delete-profileaccount-sp-transact-sql.md)  
 [sysmail_help_account_sp &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sysmail-help-account-sp-transact-sql.md)  
 [sysmail_help_profile_sp &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sysmail-help-profile-sp-transact-sql.md)  
 [sysmail_help_profileaccount_sp &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sysmail-help-profileaccount-sp-transact-sql.md)  
 [sysmail_update_profileaccount_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql.md)  
  
  
