---
title: sysmail_update_profileaccount_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_update_profileaccount_sp_TSQL
- sysmail_update_profileaccount_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_profileaccount_sp
ms.assetid: 92ca7488-29db-414e-8e36-08b0a8f542bb
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: c3a8e3db9e0e66f3a3e300e972ca1d2f02f1d03b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47615532"
---
# <a name="sysmailupdateprofileaccountsp-transact-sql"></a>sysmail_update_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет порядковый номер учетной записи в профиле компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_update_profileaccount_sp  { [ @profile_id = ] profile_id   
| [ @profile_name = ] 'profile_name' } ,  
    { [ @account_id = ] account_id | [ @account_name = ] 'account_name' } ,  
    [ @sequence_number = ] sequence_number  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@profile_id** =] *profile_id*  
 Идентификатор профиля для обновляемого профиля. *profile_id* — **int**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
 [ **@profile_name** =] **"***profile_name***"**  
 Имя профиля для обновляемого профиля. *profile_name* — **sysname**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
 [ **@account_id** =] *account_id*  
 Идентификатор обновляемой учетной записи. *account_id* — **int**, значение по умолчанию NULL. Либо *account_id* или *account_name* должен быть указан.  
  
 [ **@account_name** =] **"***account_name***"**  
 Имя обновляемой учетной записи. *account_name* — **sysname**, значение по умолчанию NULL. Либо *account_id* или *account_name* должен быть указан.  
  
 [ **@sequence_number** =] *sequence_number*  
 Новый порядковый номер для учетной записи в профиле. *sequence_number* — **int**, не имеет значения по умолчанию. Порядковый номер определяет порядок, в соответствии с которым учетные записи используются в профиле.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Возвращает ошибку, если указанная учетная запись не связана с указанным профилем.  
  
 Порядковый номер определяет порядок, в соответствии с которым компонент Database Mail использует учетные записи в профиле. Для нового сообщения электронной почты компонент Database Mail начинает с учетной записи, имеющей наименьший порядковый номер. Если использование этой учетной записи завершилось с ошибкой, компонент Database Mail использует учетную запись со следующим порядковым номером, и так до тех пор, пока сообщение не будет успешно отослано, либо пока не окажется безуспешным использование учетной записи с наибольшим порядковым номером. Если использование учетной записи с наибольшим порядковым номером оказывается безуспешным, создание почтового сообщения завершается ошибкой.  
  
 Если существует больше одной учетной записи с одним и тем же порядковым номером, компонент Database Mail использует только одну из них для данного почтового сообщения. В этом случае компонент Database Mail не указывает, какая учетная запись используется для этого порядкового номера, и не гарантирует того, что от сообщения к сообщению используется одна и та же учетная запись.  
  
 Хранимая процедура **sysmail_update_profileaccount_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру необходимо выполнять с трехкомпонентным именем, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию члены выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере изменяется порядковый номер учетной записи `Admin-BackupServer` в профиле `AdventureWorks Administrator` в **msdb** базы данных. После выполнения этого кода порядковым номером для этой учетной записи будет `3`, и, следовательно, эта учетная запись будет использована, если использование первых двух учетных записей завершится с ошибкой.  
  
```  
EXECUTE msdb.dbo.sysmail_update_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator'  
    ,@account_name = 'Admin-BackupServer',  
    ,@sequence_number = 3;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создайте учетную запись почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
