---
title: sp_addmergepushsubscription_agent (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addmergepushsubscription_agent_TSQL
- sp_addmergepushsubscription_agent
helpviewer_keywords:
- sp_addmergepushsubscription_agent
ms.assetid: 808a1925-be46-4999-8d69-b3a83010ec81
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b22cd17a9e180a3acc7efecea36bc6df0b53557b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spaddmergepushsubscriptionagent-transact-sql"></a>sp_addmergepushsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вводит новое задание агента для подготовки расписания синхронизации принудительной подписки для публикации слиянием. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре СУБД (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmergepushsubscription_agent [ @publication =] 'publication'   
    [ , [ @subscriber = ] 'subscriber' ]   
    [ , [ @subscriber_db = ] 'subscriber_db' ]   
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]   
    [ , [ @subscriber_login = ] 'subscriber_login' ]   
    [ , [ @subscriber_password = ] 'subscriber_password' ]   
    [ , [ @publisher_security_mode = ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @job_name = ] 'job_name' ]   
    [ , [ @frequency_type = ] frequency_type ]   
    [ , [ @frequency_interval = ] frequency_interval ]   
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]   
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]   
    [ , [ @frequency_subday = ] frequency_subday ]   
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]   
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]   
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication =** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@subscriber =** ] **"***подписчика***"**  
 Имя подписчика. *подписчик* — **sysname**, значение по умолчанию NULL.  
  
 [  **@subscriber_db =** ] **"***subscriber_db***"**  
 Имя базы данных подписки. *subscriber_db* — **sysname**, значение по умолчанию NULL.  
  
 [  **@subscriber_security_mode =** ] *subscriber_security_mode*  
 Режим безопасности, используемый для подключения к подписчику при синхронизации. *subscriber_security_mode* — **int**, значение по умолчанию 1. Если **0**, указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. Если **1**, задает проверку подлинности Windows.  
  
 [  **@subscriber_login =** ] **"***subscriber_login***"**  
 Имя входа подписчика, используемое для подключения к нему при синхронизации. *subscriber_login* является обязательным, если *subscriber_security_mode* равно **0**. *subscriber_login* — **sysname**, значение по умолчанию NULL.  
  
 [  **@subscriber_password =** ] **"***subscriber_password***"**  
 Пароль подписчика для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *subscriber_password* является обязательным, если *subscriber_security_mode* равно **0**. *subscriber_password* — **sysname**, значение по умолчанию NULL. Если пароль подписчика используется, он автоматически шифруется.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
 [  **@publisher_security_mode =** ] *publisher_security_mode*  
 Режим безопасности, используемый для подключения к издателю при синхронизации. *publisher_security_mode* — **int**, значение по умолчанию 1. Если **0**, указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. Если **1**, задает проверку подлинности Windows.  
  
 [  **@publisher_login =** ] **"***publisher_login***"**  
 Имя входа, используемое для подключения к издателю при синхронизации. *publisher_login* — **sysname**, значение по умолчанию NULL.  
  
 [  **@publisher_password =** ] **"***publisher_password***"**  
 Пароль, используемый при соединении с издателем. *publisher_password* — **sysname**, значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
 [  **@job_login =** ] **"***job_login***"**  
 Имя входа для учетной записи Windows, под которой запускается агент. *job_login* — **nvarchar(257)**, значение по умолчанию NULL. Эта учетная запись Windows всегда используется для соединений агента с распространителем и соединений с подписчиком и издателем при использовании встроенной проверки подлинности Windows.  
  
 [  **@job_password =** ] **"***job_password***"**  
 Пароль для учетной записи Windows, под которой запускается агент. *job_password* — **sysname**, не имеет значения по умолчанию.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
 [  **@job_name =** ] **"***job_name***"**  
 Имя существующего задания агента. *job_name* — **sysname**, значение по умолчанию NULL. Этот аргумент указывается, только если подписка будет синхронизироваться с использованием существующего задания, а не вновь созданного (выбор по умолчанию). Если вы не являетесь членом **sysadmin** предопределенной роли сервера, необходимо указать *job_login* и *job_password* при указании *job_name*.  
  
 [  **@frequency_type =** ] *frequency_type*  
 Частота планируемого запуска агента слияния. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|по запросу|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно с относительной датой|  
|**64**|Автозапуск|  
|**128**|Повторяющееся задание|  
|NULL (по умолчанию)||  
  
> [!NOTE]  
>  При указании значения **64** агент слияния запускается в непрерывном режиме. Это соответствует параметру **-непрерывного** параметром для агента. Дополнительные сведения см. в статье [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 Даты запуска агента слияния. *frequency_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Воскресенье|  
|**2**|Понедельник|  
|**3**|Вторник|  
|**4**|Среда|  
|**5**|Четверг|  
|**6**|Пятница|  
|**7**|Суббота|  
|**8**|День|  
|**9**|По рабочим дням|  
|**10**|По выходным дням|  
|NULL (по умолчанию)||  
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 Дата агента слияния. Этот параметр используется при *frequency_type* равно **32** (относительно ежемесячно). *frequency_relative_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
|NULL (по умолчанию)||  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию NULL.  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 Частота повторного планирования в течение определенного периода. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4**|Минута|  
|**8**|Час|  
|NULL (по умолчанию)||  
  
 [  **@frequency_subday_interval =** ] *frequency_subday_interval*  
 Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию NULL.  
  
 [  **@active_start_time_of_day =** ] *active_start_time_of_day*  
 Время суток, на которое запланирован первый запуск агента слияния, в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию NULL.  
  
 [  **@active_end_time_of_day =** ] *active_end_time_of_day*  
 Время плановой остановки агента слияния в формате ЧЧММСС. *active_end_time_of_day* — **int**, значение по умолчанию NULL.  
  
 [  **@active_start_date =** ] *active_start_date*  
 Дата первого планового запуска агента слияния в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию NULL.  
  
 [  **@active_end_date =** ] *active_end_date*  
 Дата плановой остановки агента слияния в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию NULL.  
  
 [  **@enabled_for_syncmgr =** ] **"***enabled_for_syncmgr***"**  
 Указывает, может ли подписка быть синхронизирована с помощью диспетчера синхронизации Windows. *enabled_for_syncmgr* — **nvarchar(5)**, значение по умолчанию FALSE. Если **false**, подписка не зарегистрирована диспетчером синхронизации. Если **true**, подписка регистрируется диспетчером синхронизации и может быть синхронизирована без запуска [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_addmergepushsubscription_agent** используется в репликации слиянием и включает функциональность, аналогичную [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md).  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepushsubscript_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_addmergepushsubscription_agent**.  
  
## <a name="see-also"></a>См. также  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
