---
title: sp_addmergepushsubscription_agent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepushsubscription_agent_TSQL
- sp_addmergepushsubscription_agent
helpviewer_keywords:
- sp_addmergepushsubscription_agent
ms.assetid: 808a1925-be46-4999-8d69-b3a83010ec81
author: stevestein
ms.author: sstein
ms.openlocfilehash: fb74cc0887d68ea01fabe7f6168c0d23275d8f4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68769162"
---
# <a name="sp_addmergepushsubscription_agent-transact-sql"></a>sp_addmergepushsubscription_agent (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Вводит новое задание агента для подготовки расписания синхронизации принудительной подписки для публикации слиянием. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. [в разделе Enable encrypted connections to the ядро СУБД &#40;диспетчер конфигурации SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
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
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @subscriber = ] 'subscriber'`Имя подписчика. Аргумент *Subscriber* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'`Имя базы данных подписки. Аргумент *subscriber_db* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode`Режим безопасности, используемый при соединении с подписчиком при синхронизации. *subscriber_security_mode* имеет **тип int**и значение по умолчанию 1. Если значение **равно 0**, то задает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверку подлинности. Если значение равно **1**, указывает проверку подлинности Windows.  
  
`[ @subscriber_login = ] 'subscriber_login'`Имя входа подписчика, используемое при соединении с подписчиком при синхронизации. *subscriber_login* является обязательным, если *subscriber_security_mode* имеет значение **0**. Аргумент *subscriber_login* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @subscriber_password = ] 'subscriber_password'`Пароль подписчика для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. *subscriber_password* является обязательным, если *subscriber_security_mode* имеет значение **0**. Аргумент *subscriber_password* имеет тип **sysname**и значение по умолчанию NULL. Если пароль подписчика используется, он автоматически шифруется.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Режим безопасности, используемый при соединении с издателем при синхронизации. *publisher_security_mode* имеет **тип int**и значение по умолчанию 1. Если значение **равно 0**, то задает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверку подлинности. Если значение равно **1**, указывает проверку подлинности Windows.  
  
`[ @publisher_login = ] 'publisher_login'`Имя входа, используемое при соединении с издателем при синхронизации. Аргумент *publisher_login* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @publisher_password = ] 'publisher_password'`Пароль, используемый при соединении с издателем. Аргумент *publisher_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @job_login = ] 'job_login'`Имя входа для учетной записи Windows, под которой запускается агент. *job_login* имеет тип **nvarchar (257)** и значение по умолчанию NULL. Эта учетная запись Windows всегда используется для соединений агента с распространителем и соединений с подписчиком и издателем при использовании встроенной проверки подлинности Windows.  
  
`[ @job_password = ] 'job_password'`Пароль для учетной записи Windows, под которой запускается агент. Аргумент *job_password* имеет тип **sysname**и не имеет значения по умолчанию.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @job_name = ] 'job_name'`Имя существующего задания агента. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL. Этот аргумент указывается, только если подписка будет синхронизироваться с использованием существующего задания, а не вновь созданного (выбор по умолчанию). Если вы не являетесь членом предопределенной роли сервера **sysadmin** , необходимо указать *job_login* и *job_password* при указании *job_name*.  
  
`[ @frequency_type = ] frequency_type`Частота, с которой следует запланировать агент слияния. *frequency_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**1**|Один раз.|  
|**2**|По запросу|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**глубин**|Ежемесячная|  
|**32**|Ежемесячно с относительной датой|  
|**64**|Автозапуск|  
|**128**|Повторение|  
|NULL (по умолчанию)||  
  
> [!NOTE]  
>  Указание значения **64** приводит к запуску агент слияния в непрерывном режиме. Это соответствует установке параметра **-Continuous** для агента. Дополнительные сведения см. в статье [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
`[ @frequency_interval = ] frequency_interval`Дни, в которые выполняется агент слияния. *frequency_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**1**|Воскресенье|  
|**2**|Понедельник|  
|**3-5**|Вторник|  
|**4**|Среда|  
|**5.0**|Четверг|  
|**6**|Пятница|  
|**7**|Суббота|  
|**8**|День|  
|**8**|дни недели;|  
|**штук**|По выходным дням|  
|NULL (по умолчанию)||  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Дата агент слияния. Этот параметр используется, если *frequency_type* установлен в значение **32** (ежемесячное относительное расписание). *frequency_relative_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**1**|Первый|  
|**2**|Секунда|  
|**4**|Третья|  
|**8**|Четвертая|  
|**глубин**|Последний|  
|NULL (по умолчанию)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Коэффициент повторения, используемый *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_subday = ] frequency_subday`Частота повторного планирования в течение заданного периода. *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Секунда|  
|**4**|Минута|  
|**8**|Hour|  
|NULL (по умолчанию)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Интервал для *frequency_subday*. *frequency_subday_interval* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Время первого запланированного агент слияния в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Время суток, когда запланировать агент слияния прекращается в формате ЧЧММСС. *active_end_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_date = ] active_start_date`Дата первого запланированного запуска агент слияния в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_date = ] active_end_date`Дата прекращения расписания агент слияния в формате ГГГГММДД. *active_end_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'`Указывает, можно ли синхронизировать подписку с помощью диспетчера синхронизации Windows. *enabled_for_syncmgr* имеет тип **nvarchar (5)** и значение по умолчанию false. Если **значение равно false**, подписка не зарегистрирована в диспетчере синхронизации. Если **значение — true**, подписка регистрируется в диспетчере синхронизации и может быть синхронизирована [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]без запуска.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="remarks"></a>Remarks  
 **sp_addmergepushsubscription_agent** используется в репликации слиянием и использует функции, аналогичные [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md).  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepushsubscript_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addmergepushsubscription_agent**.  
  
## <a name="see-also"></a>См. также:  
 [Создание принудительной подписки](../../relational-databases/replication/create-a-push-subscription.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
