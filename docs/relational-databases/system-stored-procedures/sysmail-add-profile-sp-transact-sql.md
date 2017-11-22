---
title: "sysmail_add_profile_sp (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- sysmail_add_profile_sp_TSQL
- sysmail_add_profile_sp
dev_langs: TSQL
helpviewer_keywords: sysmail_add_profile_sp
ms.assetid: a828e55c-633a-41cf-9769-a0698b446e6c
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ab45b6b8af6528614a8c5e306bad2cc58eb130d9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailaddprofilesp-transact-sql"></a>sysmail_add_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает новый профиль компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_add_profile_sp [ @profile_name = ] 'profile_name'  
    [ , [ @description = ] 'description' ]  
    [ , [ @profile_id = ] new_profile_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@profile_name**  =] **"***profile_name***"**  
 Имя нового профиля. *profile_name* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@description**  =] **"***описание***"**  
 Необязательное описание нового профиля. *Описание* — **nvarchar(256)**, не имеет значения по умолчанию.  
  
 [  **@profile_id**  =] *new_profile_id***выходных данных**  
 Возвращает идентификатор нового профиля. *new_profile_id* — **int**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Профиль компонента Database Mail может хранить любое число учетных записей Database Mail. Хранимые процедуры компонента Database Mail могут ссылаться на профиль или по имени, или по идентификатору, создаваемому данной процедурой. Дополнительные сведения о добавлении учетной записи к профилю см. в разделе [sysmail_add_profileaccount_sp &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md).  
  
 Имя профиля и описание можно изменить с помощью хранимой процедуры **sysmail_update_profile_sp**, а идентификатор профиля остается неизменным в течение срока использования профиля.  
  
 Имя профиля должно быть уникальным для компонента Microsoft [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], иначе хранимая процедура вернет ошибку.  
  
 Хранимая процедура **sysmail_add_profile_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру следует выполнять с трехкомпонентным именем, если текущая база данных не является **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Разрешения для этой процедуры по умолчанию членам выполнение **sysadmin** предопределенной роли сервера.  
  
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
 [Создайте учетную запись электронной почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Компонент Database Mail хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
