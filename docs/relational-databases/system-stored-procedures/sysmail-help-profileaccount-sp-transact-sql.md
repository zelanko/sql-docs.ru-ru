---
title: "sysmail_help_profileaccount_sp (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
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
- sysmail_help_profileaccount_sp_TSQL
- sysmail_help_profileaccount_sp
dev_langs: TSQL
helpviewer_keywords: sysmail_help_profileaccount_sp
ms.assetid: 3ea68271-0a6b-4d77-991c-4757f48f747a
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 30af309db029d4d969fe39eb87e15503b590dfae
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailhelpprofileaccountsp-transact-sql"></a>sysmail_help_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Перечисляет учетные записи, связанные с одним или несколькими профилями компонента Database Mail.  
    
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_profileaccount_sp  
   {   [ @profile_id = ] profile_id   
      | [ @profile_name = ] 'profile_name' }  
   [ , {   [ @account_id = ] account_id  
         | [ @account_name = ] 'account_name' } ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@profile_id**  =] *profile_id*  
 Идентификатор перечисляемого профиля. *profile_id* — **int**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
 [  **@profile_name**  =] **"***profile_name***"**  
 Имя профиля, который следует включить в список. *profile_name* — **sysname**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
 [  **@account_id**  =] *account_id*  
 Идентификатор учетной записи, который следует включить в список. *account_id* — **int**, значение по умолчанию NULL. Когда *account_id* и *account_name* имеют значение NULL, приводится список всех учетных записей в профиле.  
  
 [  **@account_name**  =] **"***account_name***"**  
 Имя учетной записи, которую следует включить в список. *account_name* — **sysname**, значение по умолчанию NULL. Когда *account_id* и *account_name* имеют значение NULL, приводится список всех учетных записей в профиле.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор со следующими столбцами.  
  
||||  
|-|-|-|  
|Имя столбца|Тип данных|Description|  
|**profile_id**|**int**|Идентификатор профиля.|  
|**Имя_профиля**|**sysname**|Имя профиля.|  
|**account_id**|**int**|Идентификатор учетной записи.|  
|**account_name**|**sysname**|Имя учетной записи.|  
|**sequence_number**|**int**|Порядковый номер учетной записи в профиле.|  
  
## <a name="remarks"></a>Замечания  
 Если аргумент *profile_id* или *profile_name* указан, эта хранимая процедура возвращает данные для каждого профиля в экземпляре.  
  
 Хранимая процедура **sysmail_help_profileaccount_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру следует выполнять с трехкомпонентным именем, если текущая база данных не является **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Разрешения для этой процедуры по умолчанию членам выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 **А. Вывод списка учетных записей для конкретного профиля по имени**  
  
 В следующем примере выводятся данные профиля `AdventureWorks Administrator` путем указания имени профиля.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp  
   @profile_name = 'AdventureWorks Administrator';  
```  
  
 Далее приведен образец результирующего набора, отредактированного по длине строк:  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
```  
  
 **Б. Вывод списка учетных записей для конкретного профиля по Идентификатору профиля**  
  
 В следующем примере демонстрируется вывод данных профиля `AdventureWorks Administrator` путем указания идентификатора профиля.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp  
    @profile_id = 131 ;  
```  
  
 Далее приведен образец результирующего набора, отредактированного по длине строк:  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
```  
  
 **В. Список учетных записей для всех профилей**  
  
 В следующем примере демонстрируется вывод списка учетных записей для всех профилей экземпляра.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp;  
```  
  
 Далее приведен образец результирующего набора, отредактированного по длине строк:  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
106         AdventureWorks Operator      210         Operator-MainServer  1  
```  
  
## <a name="see-also"></a>См. также:  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создайте учетную запись электронной почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Компонент Database Mail хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
