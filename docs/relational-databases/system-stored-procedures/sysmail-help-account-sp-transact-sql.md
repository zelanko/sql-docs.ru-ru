---
title: sysmail_help_account_sp (Transact-SQL) | Документы Microsoft
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
- sysmail_help_account_sp_TSQL
- sysmail_help_account_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_account_sp
ms.assetid: 87c7c39c-8e05-4e68-9272-45f908809c3b
caps.latest.revision: 48
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 031dc769153549a8002525b184f4261ee9fe83bb
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysmailhelpaccountsp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет сведения (за исключением паролей) об учетных записях компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@account_id** =] *account_id*  
 Идентификатор учетной записи, о которой предоставляются сведения. *account_id* — **int**, значение по умолчанию NULL.  
  
 [ **@account_name** =] **"***account_name***"**  
 Имя учетной записи, о которой предоставляются сведения. *account_name* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор, содержащий столбцы перечисленные ниже.  
  
||||  
|-|-|-|  
|Имя столбца|Тип данных|Описание|  
|**account_id**|**int**|Идентификатор учетной записи.|  
|**name**|**sysname**|Имя учетной записи.|  
|**Описание**|**nvarchar(256)**|Описание учетной записи.|  
|**email_address**|**nvarchar(128)**|Адрес электронной почты для отправки сообщений.|  
|**display_name**|**nvarchar(128)**|Отображаемое имя учетной записи.|  
|**replyto_address**|**nvarchar(128)**|Адрес, на который посылаются ответы на сообщения данной учетной записи.|  
|**serverType**|**sysname**|Тип почтового сервера для учетной записи.|  
|**Имя сервера**|**sysname**|Имя почтового сервера для учетной записи.|  
|**port**|**int**|Номер порта, который использует почтовый сервер.|  
|**Имя пользователя**|**nvarchar(128)**|Имя пользователя, используемое для входа на почтовый сервер в случае, если почтовый сервер использует проверку подлинности. Когда **username** имеет значение NULL, компонент Database Mail не использует проверку подлинности для этой учетной записи.|  
|**use_default_credentials**|**бит**|Указывает, посылать ли почту серверу SMTP с помощью учетных данных компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** имеет тип bit и значение по умолчанию отсутствует. Если этот параметр равен 1, компонент Database Mail использует учетные данные службы компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Если этот параметр равен 0, компонент Database Mail использует **@username** и **@password** для проверки подлинности на SMTP-сервере. Если **@username** и **@password** имеют значение NULL, то компонент Database Mail использует анонимную проверку подлинности. Перед указанием этого параметра проконсультируйтесь с администратором SMTP-сервера.|  
|**enable_ssl**|**бит**|Указывает, шифрует ли компонент Database Mail соединение с помощью протокола SSL. Используйте этот аргумент, если требуется поддержка протокола SSL для SMTP-сервера. **enable_ssl** имеет тип bit и значение по умолчанию отсутствует. Значение 1 означает, что компонент Database Mail шифрует соединение при помощи протокола SSL. Значение 0 означает, что компонент Database Mail посылает электронную почту без шифрования при помощи протокола SSL.|  
  
## <a name="remarks"></a>Замечания  
 Если аргумент *account_id* или *account_name* предоставляется, **sysmail_help_account** выводит сведения для всех учетных записей компонента Database Mail в экземпляре Microsoft SQL Server.  
  
 Хранимая процедура **sysmail_help_account_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру следует выполнять с трехкомпонентным именем, если текущая база данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию членам выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 **А. Вывод сведений обо всех учетных записей**  
  
 На следующем примере показано, как выводятся сведения обо всех учетных записях в экземпляре.  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp ;  
```  
  
 Далее приведен образец результирующего набора, отредактированного по длине строк:  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- --------------------------------------- ------------------------- -------------------------------- --------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
149         Audit Account                Account for audit e-mail.               audit@Adventure-Works.com Automated Mailer (Audit)         NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
```  
  
 **Б. Вывод сведений об определенной учетной записи**  
  
 На следующем примере показано, как выводятся сведения об учетной записи с именем `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
 Далее приведен образец результирующего набора, отредактированного по длине строк:  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- ------------------------------------------------------ ------------------------- ---------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL     0                       0       
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создайте учетную запись электронной почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
