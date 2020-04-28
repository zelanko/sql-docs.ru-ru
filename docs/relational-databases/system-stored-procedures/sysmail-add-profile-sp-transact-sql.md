---
title: sysmail_add_profile_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_profile_sp_TSQL
- sysmail_add_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_profile_sp
ms.assetid: a828e55c-633a-41cf-9769-a0698b446e6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: a4bd7f90688d61f9ecee487d553393e38bed82e3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "70211279"
---
# <a name="sysmail_add_profile_sp-transact-sql"></a>sysmail_add_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Создает новый профиль компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_add_profile_sp [ @profile_name = ] 'profile_name'  
    [ , [ @description = ] 'description' ]  
    [ , [ @profile_id = ] new_profile_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_name = ] 'profile\_name'`Имя нового профиля. Аргумент *profile_name* имеет тип **sysname**и не имеет значения по умолчанию.  
 
   > [!NOTE]
   > Имя профиля, использующего SQL Управляемый экземпляр агента SQL Azure, должно быть вызвано **AzureManagedInstance_dbmail_profile**
  
`[ @description = ] 'description'`Необязательное описание нового профиля. *Description* имеет тип **nvarchar (256)** и не имеет значения по умолчанию.  
  
`[ @profile_id = ] _new\_profile\_id OUTPUT`Возвращает идентификатор нового профиля. *new_profile_id* имеет **тип int**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Профиль компонента Database Mail может хранить любое число учетных записей Database Mail. Хранимые процедуры компонента Database Mail могут ссылаться на профиль или по имени, или по идентификатору, создаваемому данной процедурой. Дополнительные сведения о добавлении учетной записи в профиль см. в разделе [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md).  
  
 Имя и описание профиля можно изменить с помощью хранимой процедуры **sysmail_update_profile_sp**, тогда как идентификатор профиля остается постоянным в течение срока жизни профиля.  
  
 Имя профиля должно быть уникальным для компонента Microsoft [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], иначе хранимая процедура вернет ошибку.  
  
 Хранимая процедура **sysmail_add_profile_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 **А. Создание профиля**  
  
 В следующем примере показано создание профиля компонента Database Mail с именем `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.' ;  
```  
  
 **Б. Создание профиля, сохранение идентификатора профиля в переменной**  
  
 В следующем примере показано создание профиля компонента Database Mail с именем `AdventureWorks Administrator`. В примере идентификатор нового профиля сохраняется в переменной `@profileId` и возвращается в результирующем наборе.  
  
```  
DECLARE @profileId INT ;  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.',  
       @profile_id = @profileId OUTPUT ;  
  
SELECT @profileId ;  
```  
  
## <a name="see-also"></a>См. также:  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создание учетной записи Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Database Mail объекты конфигурации](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
