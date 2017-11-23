---
title: "sysmail_help_principalprofile_sp (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/02/2016
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
- sysmail_help_principalprofile_sp_TSQL
- sysmail_help_principalprofile_sp
dev_langs: TSQL
helpviewer_keywords: sysmail_help_principalprofile_sp
ms.assetid: 0cfd6464-09c7-4f03-9d25-58001c096a9e
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 322984b88e879adb952a1168b17178b8ffe20ae2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailhelpprincipalprofilesp-transact-sql"></a>sysmail_help_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит сведения об взаимосвязях между профилями компонента Database Mail и участниками базы данных.  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_principalprofile_sp [ {   [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ]  
    [ [ , ] {   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@principal_id=** ] *principal_id*  
 Идентификатор пользователя базы данных или роли в **msdb** базы данных для добавления взаимосвязи. *principal_id* — **int**, значение по умолчанию NULL. Либо *principal_id* или *principal_name* может быть указан.  
  
 [  **@principal_name=** ] **"***principal_name***"**  
 Имя пользователя базы данных или роли в **msdb** базы данных для добавления взаимосвязи. *principal_name* — **sysname**, значение по умолчанию NULL. Либо *principal_id* или *principal_name* может быть указан.  
  
 [  **@profile_id=** ] *profile_id*  
 Идентификатор профиля для добавления взаимосвязи. *profile_id* — **int**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* может быть указан.  
  
 [  **@profile_name=** ] **"***profile_name***"**  
 Имя профиля для добавления взаимосвязи. *profile_name* — **sysname**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* может быть указан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор, содержащий столбцы, перечисленные в следующей таблице.  
  
||||  
|-|-|-|  
|Имя столбца|Тип данных|Description|  
|**principal_id**|**int**|Идентификатор пользователя базы данных.|  
|**principal_name**|**sysname**|Имя пользователя базы данных.|  
|**profile_id**|**int**|Идентификатор профиля компонента Database Mail.|  
|**Имя_профиля**|**sysname**|Имя профиля компонента Database Mail.|  
|**is_default**|**bit**|Флаг, который указывает, является ли профиль профилем по умолчанию для пользователя.|  
  
## <a name="remarks"></a>Замечания  
 Если **sysmail_help_principalprofile_sp** вызывается без параметров, возвращенный результирующий набор содержит все взаимосвязи экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В противном случае результирующий набор содержит сведения об ассоциациях, которые удовлетворяют предоставленным параметрам. Например, если представлено имя профиля, процедура приводит список всех взаимосвязей для профиля.  
  
 **sysmail_help_principalprofile_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру следует выполнять с трехкомпонентным именем, если текущая база данных не является **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-information-for-a-specific-association"></a>A. Вывод сведений об указанной ассоциации  
 В следующем примере выводятся сведения обо всех взаимосвязях между профилем `AdventureWorks Administrator` и участником `ApplicationLogin` в базе данных `msdb`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp  
    @principal_name = 'danw',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 Образец результирующего набора, отформатированного по длине строки.  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
5            danw               9           AdventureWorks Administrator   1  
```  
  
### <a name="b-listing-information-for-all-associations"></a>Б. Вывод сведений обо всех ассоциациях  
 В следующем примере выводятся сведения обо всех ассоциациях в экземпляре.  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp ;  
```  
  
 Образец результирующего набора, отформатированного по длине строки.  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
6            terrid             3           Product Update Profile         1  
5            danw               9           AdventureWorks Administrator   1  
```  
  
## <a name="see-also"></a>См. также:  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Компонент Database Mail хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
