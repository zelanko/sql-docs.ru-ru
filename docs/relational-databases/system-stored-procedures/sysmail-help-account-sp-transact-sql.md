---
title: sysmail_help_account_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_account_sp_TSQL
- sysmail_help_account_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_account_sp
ms.assetid: 87c7c39c-8e05-4e68-9272-45f908809c3b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f5d5c822264682aa3fb6fd43d26f589aeb272f45
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85752745"
---
# <a name="sysmail_help_account_sp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Предоставляет сведения (за исключением паролей) об учетных записях компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @account_id = ] account_id`Идентификатор учетной записи, для которой необходимо получить список сведений. *account_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @account_name = ] 'account_name'`Имя учетной записи для вывода сведений о. Аргумент *account_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор, содержащий столбцы перечисленные ниже.  
  
||||  
|-|-|-|  
|Имя столбца|Тип данных|Описание|  
|**account_id**|**int**|Идентификатор учетной записи.|  
|**name**|**sysname**|Имя учетной записи.|  
|**nописание**|**nvarchar(256)**|Описание учетной записи.|  
|**email_address**|**nvarchar(128)**|Адрес электронной почты для отправки сообщений.|  
|**display_name**|**nvarchar(128)**|Отображаемое имя учетной записи.|  
|**replyto_address**|**nvarchar(128)**|Адрес, на который посылаются ответы на сообщения данной учетной записи.|  
|**serverType**|**sysname**|Тип почтового сервера для учетной записи.|  
|**имя**|**sysname**|Имя почтового сервера для учетной записи.|  
|**port**|**int**|Номер порта, который использует почтовый сервер.|  
|**username**|**nvarchar(128)**|Имя пользователя, используемое для входа на почтовый сервер в случае, если почтовый сервер использует проверку подлинности. Если параметр **username** имеет значение NULL, Database Mail не использует для этой учетной записи проверку подлинности.|  
|**use_default_credentials**|**bit**|Указывает, посылать ли почту серверу SMTP с помощью учетных данных компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** имеет бит и не имеет значения по умолчанию. Если этот параметр равен 1, компонент Database Mail использует учетные данные службы компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Если этот параметр равен 0, Database Mail использует ** \@ имя пользователя** и ** \@ пароль** для проверки подлинности на SMTP-сервере. Если ** \@ имя пользователя** и ** \@ пароль** имеют значение null, Database Mail использует анонимную проверку подлинности. Перед указанием этого параметра проконсультируйтесь с администратором SMTP-сервера.|  
|**enable_ssl**|**bit**|Указывает, будет ли Database Mail шифровать связь с помощью протокола TLS, который ранее назывался SSL (SSL). Используйте этот параметр, если на SMTP-сервере требуется TLS. **enable_ssl** имеет бит и не имеет значения по умолчанию. 1 указывает, Database Mail шифрует связь с помощью TLS. значение 0 указывает, Database Mail отправляет почту без шифрования TLS.|  
  
## <a name="remarks"></a>Примечания  
 Если *account_id* или *account_name* не указаны, **sysmail_help_account** выводит сведения обо всех учетных записях Database Mail в экземпляре Microsoft SQL Server.  
  
 Хранимая процедура **sysmail_help_account_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 **А. Вывод сведений обо всех учетных записях**  
  
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
  
 **Б. Вывод сведений об указанной учетной записи**  
  
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
 [Создание учетной записи Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
