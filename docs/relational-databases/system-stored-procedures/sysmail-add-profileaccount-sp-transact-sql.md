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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 68d09a8149234651b4741caaeb8436f6b6cda6da
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786117"
---
# <a name="sysmail_add_profileaccount_sp-transact-sql"></a>sysmail_add_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Добавляет учетную запись Database Mail к профилю компонента Database Mail. Выполнение **sysmail_add_profileaccount_sp** после создания учетной записи базы данных с помощью [sysmail_add_account_sp &#40;transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-account-sp-transact-sql.md), а профиль базы данных создается с [sysmail_add_profile_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_add_profileaccount_sp { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    { [ @account_id = ] account_id | [ @account_name = ] 'account_name' }  
    [ , [ @sequence_number = ] sequence_number ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_id = ] profile_id`Идентификатор профиля, в который добавляется учетная запись. *profile_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *profile_id* , либо *profile_name* .  
  
`[ @profile_name = ] 'profile_name'`Имя профиля, в который добавляется учетная запись. Аргумент *profile_name* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *profile_id* , либо *profile_name* .  
  
`[ @account_id = ] account_id`Идентификатор учетной записи для добавления в профиль. *account_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *account_id* , либо *account_name* .  
  
`[ @account_name = ] 'account_name'`Имя учетной записи, добавляемой к профилю. Аргумент *account_name* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *account_id* , либо *account_name* .  
  
`[ @sequence_number = ] sequence_number`Порядковый номер учетной записи в профиле. *sequence_number* имеет **тип int**и не имеет значения по умолчанию. Порядковый номер определяет порядок, в соответствии с которым учетные записи используются в профиле.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Должны заранее существовать как профиль, так и учетная запись. В противном случае хранимая процедура возвращает ошибку.  
  
 Следует обратить внимание, что эта хранимая процедура не изменяет порядковый номер учетной записи, уже связанной с конкретным профилем.  Дополнительные сведения об обновлении порядкового номера учетной записи см. в разделе [sysmail_update_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql.md).  
  
 Порядковый номер определяет порядок, в соответствии с которым компонент Database Mail использует учетные записи в профиле. Для нового сообщения электронной почты компонент Database Mail начинает с учетной записи, имеющей наименьший порядковый номер. Если использование этой учетной записи завершилось с ошибкой, компонент Database Mail использует учетную запись со следующим порядковым номером, и так до тех пор, пока сообщение не будет успешно отослано, либо пока не окажется безуспешным использование учетной записи с наибольшим порядковым номером. Если отправка сообщения от имени учетной записи с наибольшим порядковым номером также завершилась ошибкой, то компонент Database Mail приостанавливает попытки отправки сообщения на время, заданное параметром *AccountRetryDelay* хранимой процедуры **sysmail_configure_sp**. Затем он возобновляет их отправку, начиная с учетной записи с наименьшим порядковым номером. Параметр *AccountRetryAttempts* хранимой процедуры **sysmail_configure_sp**используется для указания количества попыток отправки сообщений электронной почты, перебирающих все учетные записи указанного профиля.  
  
 Если существует несколько учетных записей с одинаковым порядковым номером, то компонент Database Mail будет использовать только одну из них для отправки данного электронного сообщения. В этом случае компонент Database Mail не указывает, какая учетная запись используется для этого порядкового номера, и не гарантирует того, что от сообщения к сообщению используется одна и та же учетная запись.  
  
 Хранимая процедура **sysmail_add_profileaccount_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
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
 [Создание учетной записи Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Database Mail объекты конфигурации](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
