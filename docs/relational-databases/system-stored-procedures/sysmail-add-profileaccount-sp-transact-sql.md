---
title: sysmail_add_profileaccount_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_profileaccount_sp
- sysmail_add_profileaccount_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_profileaccount_sp
ms.assetid: 7cbf430f-1997-45ea-9707-0086184de744
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11ada827add27ae2186fdcc565b3dd2f99f76452
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017762"
---
# <a name="sysmailaddprofileaccountsp-transact-sql"></a>sysmail_add_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет учетную запись Database Mail к профилю компонента Database Mail. Выполнение **sysmail_add_profileaccount_sp** после создания учетной записи базы данных с [sysmail_add_account_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-account-sp-transact-sql.md), и при создании профиля базы данных в [sysmail_add_profile_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_add_profileaccount_sp { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    { [ @account_id = ] account_id | [ @account_name = ] 'account_name' }  
    [ , [ @sequence_number = ] sequence_number ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_id = ] profile_id` Идентификатор профиля, чтобы добавить учетную запись. *profile_id* — **int**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
`[ @profile_name = ] 'profile_name'` Имя профиля, чтобы добавить учетную запись. *profile_name* — **sysname**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
`[ @account_id = ] account_id` Идентификатор учетной записи для добавления к профилю. *account_id* — **int**, значение по умолчанию NULL. Либо *account_id* или *account_name* должен быть указан.  
  
`[ @account_name = ] 'account_name'` Имя учетной записи, добавляемой к профилю. *account_name* — **sysname**, значение по умолчанию NULL. Либо *account_id* или *account_name* должен быть указан.  
  
`[ @sequence_number = ] sequence_number` Порядковый номер учетной записи в профиле. *sequence_number* — **int**, не имеет значения по умолчанию. Порядковый номер определяет порядок, в соответствии с которым учетные записи используются в профиле.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Должны заранее существовать как профиль, так и учетная запись. В противном случае хранимая процедура возвращает ошибку.  
  
 Следует обратить внимание, что эта хранимая процедура не изменяет порядковый номер учетной записи, уже связанной с конкретным профилем. Дополнительные сведения об обновлении порядкового номера учетной записи, см. в разделе [sysmail_update_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql.md).  
  
 Порядковый номер определяет порядок, в соответствии с которым компонент Database Mail использует учетные записи в профиле. Для нового сообщения электронной почты компонент Database Mail начинает с учетной записи, имеющей наименьший порядковый номер. Если использование этой учетной записи завершилось с ошибкой, компонент Database Mail использует учетную запись со следующим порядковым номером, и так до тех пор, пока сообщение не будет успешно отослано, либо пока не окажется безуспешным использование учетной записи с наибольшим порядковым номером. Если отправка сообщения от имени учетной записи с наибольшим порядковым номером также завершилась ошибкой, то компонент Database Mail приостанавливает попытки отправки сообщения на время, заданное параметром *AccountRetryDelay* хранимой процедуры **sysmail_configure_sp**. Затем он возобновляет их отправку, начиная с учетной записи с наименьшим порядковым номером. Параметр *AccountRetryAttempts* хранимой процедуры **sysmail_configure_sp**используется для указания количества попыток отправки сообщений электронной почты, перебирающих все учетные записи указанного профиля.  
  
 Если существует несколько учетных записей с одинаковым порядковым номером, то компонент Database Mail будет использовать только одну из них для отправки данного электронного сообщения. В этом случае компонент Database Mail не указывает, какая учетная запись используется для этого порядкового номера, и не гарантирует того, что от сообщения к сообщению используется одна и та же учетная запись.  
  
 Хранимая процедура **sysmail_add_profileaccount_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру необходимо выполнять с трехкомпонентным именем, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию члены выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере профиль `AdventureWorks Administrator` ассоциируется с учетной записью `Audit Account`. Учетная запись аудита имеет порядковый номер 1.  
  
```  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator',  
    @account_name = 'Audit Account',  
    @sequence_number = 1 ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создайте учетную запись почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
