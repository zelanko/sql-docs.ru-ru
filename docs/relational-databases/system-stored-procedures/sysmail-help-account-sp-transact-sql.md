---
title: sysmail_help_account_sp (Трансакт-СЗЛ) Документы Майкрософт
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: ccb5cfd245148c97288a34b1857955f48f3efc73
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528418"
---
# <a name="sysmail_help_account_sp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет сведения (за исключением паролей) об учетных записях компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @account_id = ] account_id`Идентификатор учетной записи для пересчета информации для. *account_id* **int**, с дефолтом NULL.  
  
`[ @account_name = ] 'account_name'`Название учетной записи для списка информации для. *account_name* является **sysname**, с дефолтом NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успех) или **1** (неудача)  
  
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
|**серверный тип**|**sysname**|Тип почтового сервера для учетной записи.|  
|**Имя _сервера**|**sysname**|Имя почтового сервера для учетной записи.|  
|**Порт**|**int**|Номер порта, который использует почтовый сервер.|  
|**Пользователя**|**nvarchar(128)**|Имя пользователя, используемое для входа на почтовый сервер в случае, если почтовый сервер использует проверку подлинности. Когда **имя пользователя** NULL, Database Mail не использует аутентификацию для этой учетной записи.|  
|**use_default_credentials**|**bit**|Указывает, посылать ли почту серверу SMTP с помощью учетных данных компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** бит, без по умолчанию. Если этот параметр равен 1, компонент Database Mail использует учетные данные службы компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Когда этот параметр равен 0, Database Mail использует ** \@имя пользователя** и ** \@пароль** для проверки подлинности на сервере SMTP. Если ** \@имя пользователя** и ** \@пароль** являются NULL, то Database Mail использует анонимную аутентификацию. Перед указанием этого параметра проконсультируйтесь с администратором SMTP-сервера.|  
|**enable_ssl**|**bit**|Уточняется, шифрует ли Database Mail связь с помощью Transport Layer Security (TLS), ранее известного как Безопасный слой розеток (SSL). Используйте эту опцию, если TLS требуется на вашем сервере SMTP. **enable_ssl** бит, без по умолчанию. 1 указывает на то, что Database Mail шифрует связь с помощью TLS. 0 указывает на то, что Почта базы данных отправляет почту без шифрования TLS.|  
  
## <a name="remarks"></a>Примечания  
 При отсутствии *account_id* или *account_name* **sysmail_help_account** перечисляет информацию обо всех учетных записях базы данных Mail в экземпляре Microsoft S'L Server.  
  
 Сохраненная процедура **sysmail_help_account_sp** находится в базе данных **msdb** и принадлежит схеме **dbo.** Процедура должна быть выполнена с трехчастей имя, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Выполнение разрешений для этой процедуры по умолчанию для членов **sysadmin** фиксированной роли сервера.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Почта базы данных](../../relational-databases/database-mail/database-mail.md)   
 [Создание учетной записи почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Процедуры хранения почты базы данных &#40;&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
