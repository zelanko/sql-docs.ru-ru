---
title: sp_addpushsubscription_agent (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sp_addpushsubscription_agent_TSQL
- sp_addpushsubscription_agent
helpviewer_keywords:
- sp_addpushsubscription_agent
ms.assetid: 1fdd2052-50d8-4318-8aa7-fc635d5cad18
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 3bc468a1f26c8919951420a2155c031ba2fb5a25
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spaddpushsubscriptionagent-transact-sql"></a>sp_addpushsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет новое запланированное задание агента, используемое для синхронизации принудительной подписки на публикацию транзакций. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре СУБД (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addpushsubscription_agent [ @publication= ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
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
    [ , [ @dts_package_name = ] 'dts_package_name' ]  
    [ , [ @dts_package_password = ] 'dts_package_password' ]  
    [ , [ @dts_package_location = ] 'dts_package_location' ]  
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]  
    [ , [ @distribution_job_name = ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @subscriber_provider = ] 'subscriber_provider' ]   
    [ , [ @subscriber_datasrc = ] 'subscriber_datasrc' ]   
    [ , [ @subscriber_location = ] 'subscriber_location' ]  
    [ , [ @subscriber_provider_string = ] 'subscriber_provider_string' ]   
    [ , [ @subscriber_catalog = ] 'subscriber_catalog' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication =**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@subscriber =**] **"***подписчика***"**  
 Имя подписчика. *подписчик* — **sysname**, значение по умолчанию NULL.  
  
 [  **@subscriber_db =**] **"***subscriber_db***"**  
 Имя базы данных подписки. *subscriber_db* — **sysname**, значение по умолчанию NULL. Для отличных от подписчика SQL Server, укажите значение **(назначение по умолчанию)** для *subscriber_db*.  
  
 [  **@subscriber_security_mode =**] *subscriber_security_mode*  
 Режим безопасности, используемый для подключения к подписчику при синхронизации. *subscriber_security_mode* — **int**, значение по умолчанию 1. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. **1** указывает проверку подлинности Windows.  
  
> [!IMPORTANT]  
>  Для обновляемых посредством очередей подписок при соединении с подписчиками используйте проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указывая для каждого из подписчиков различные учетные записи. Для всех других подписок используйте проверку подлинности Windows.  
  
 [  **@subscriber_login =**] **"***subscriber_login***"**  
 Имя входа подписчика, используемое для подключения к нему при синхронизации. *subscriber_login* — **sysname**, значение по умолчанию NULL.  
  
 [  **@subscriber_password =**] **"***subscriber_password***"**  
 Пароль подписчика. *subscriber_password* является обязательным, если *subscriber_security_mode* равно **0**. *subscriber_password* — **sysname**, значение по умолчанию NULL. Если пароль подписчика используется, он автоматически шифруется.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
 [  **@job_login =** ] **"***job_login***"**  
 Имя входа для учетной записи Windows, под которой запускается агент. *job_login* — **nvarchar(257)**, значение по умолчанию NULL. Эта учетная запись Windows всегда используется для подключений к распространителю средствами агентов и для подключений к подписчику в случае применения встроенных средств проверки подлинности Windows.  
  
 [  **@job_password =** ] **"***job_password***"**  
 Пароль для учетной записи Windows, под которой запускается агент. *job_password* — **sysname**, не имеет значения по умолчанию.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
 [  **@job_name =** ] **"***job_name***"**  
 Имя существующего задания агента. *job_name* — **sysname**, значение по умолчанию NULL. Этот аргумент указывается только тогда, когда подписка будет синхронизироваться с использованием существующего задания, а не вновь создаваемого задания (выбор по умолчанию). Если вы не являетесь членом **sysadmin** предопределенной роли сервера, необходимо указать *job_login* и *job_password* при указании *job_name*.  
  
 [  **@frequency_type =** ] *frequency_type*  
 Частота запуска агента распространителя по расписанию. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|по запросу|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно с относительной датой|  
|**64** (по умолчанию)|Автозапуск|  
|**128**|Повторяющееся задание|  
  
> [!NOTE]  
>  При указании значения **64** агент распространителя запускается в непрерывном режиме. Это соответствует параметру **-непрерывного** параметром для агента. Дополнительные сведения см. в статье [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 Представляет значение, которое применяется к частоте, установленной аргументом *frequency_type*. *frequency_interval* — **int**, значение по умолчанию 1.  
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 Дата агента распространителя. Этот параметр используется при *frequency_type* равно **32** (относительно ежемесячно). *frequency_relative_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию 0.  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 Частота повторного планирования в течение определенного периода. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4** (по умолчанию)|Минута|  
|**8**|Час|  
  
 [  **@frequency_subday_interval =** ] *frequency_subday_interval*  
 Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию 5.  
  
 [  **@active_start_time_of_day =** ] *active_start_time_of_day*  
 Время суток, на которое запланирован первый запуск агента распространителя, в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию 0.  
  
 [  **@active_end_time_of_day =** ] *active_end_time_of_day*  
 Время суток, на которое запланирован останов агента распространителя, в формате ЧЧММСС. *active_end_time_of_day* — **int**, значение по умолчанию 235959.  
  
 [  **@active_start_date =** ] *active_start_date*  
 Дата, когда запланирован первый запуск агента распространителя, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию 0.  
  
 [  **@active_end_date =** ] *active_end_date*  
 Дата, когда запланирован останов агента распространителя, в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию 99991231.  
  
 [  **@dts_package_name =** ] **"***dts_package_name***"**  
 Указывает имя пакета служб DTS. *dts_package_name* — **sysname** значение по умолчанию NULL. Например, для задания имени пакета `DTSPub_Package` этот параметр должен иметь значение `@dts_package_name = N'DTSPub_Package'`.  
  
 [  **@dts_package_password =** ] **"***dts_package_password***"**  
 Задает пароль для пакета, если он имеется. *dts_package_password* — **sysname** значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать пароль, если *dts_package_name* указано.  
  
 [  **@dts_package_location =** ] **"***dts_package_location***"**  
 Указывает местоположение пакета. *dts_package_location* — **nvarchar(12)**, значение по умолчанию РАСПРОСТРАНИТЕЛЬ. Расположение пакета может быть **распространителя** или **подписчика**.  
  
 [  **@enabled_for_syncmgr =** ] **"***enabled_for_syncmgr***"**  
 Является ли подписка может быть синхронизирована посредством [!INCLUDE[msCoName](../../includes/msconame-md.md)] диспетчер синхронизации. *enabled_for_syncmgr* — **nvarchar(5)**, значение по умолчанию FALSE. Если **false**, подписка не зарегистрирована диспетчером синхронизации. Если **true**, подписка регистрируется диспетчером синхронизации и может быть синхронизирована без запуска [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 [  **@distribution_job_name =** ] **"***distribution_job_name***"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@publisher =** ] **"***издатель***"**  
 Имя издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
 [  **@subscriber_provider=** ] **"***subscriber_provider***"**  
 Уникальный программный идентификатор (PROGID), с которым зарегистрирован поставщик OLE DB для источника данных, не относящихся к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *subscriber_provider* — **sysname**, и значение по умолчанию NULL. *subscriber_provider* должно быть уникальным для поставщика OLE DB, установленного на распространителе. *subscriber_provider* поддерживается только для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
 [  **@subscriber_datasrc=** ] **"***subscriber_datasrc***"**  
 Имя источника данных, понятное поставщику OLE DB. *subscriber_datasrc* — **nvarchar(4000)**, значение по умолчанию NULL. *subscriber_datasrc* передается как свойство DBPROP_INIT_DATASOURCE для инициализации поставщика OLE DB. *subscriber_datasrc* поддерживается только для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
 [  **@subscriber_location=** ] **"***subscriber_location***"**  
 Расположение базы данных, подразумевается поставщик OLE DB. *subscriber_location* — **nvarchar(4000)**, значение по умолчанию NULL. *subscriber_location* передается как свойство DBPROP_INIT_LOCATION для инициализации поставщика OLE DB. *subscriber_location* поддерживается только для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
 [  **@subscriber_provider_string=** ] **"***subscriber_provider_string***"**  
 Идентифицирующая источник данных строка соединения, зависящая от поставщика OLE DB. *subscriber_provider_string* — **nvarchar(4000)**, значение по умолчанию NULL. *subscriber_provider_string* передаваемый IDataInitialize или задается как свойство DBPROP_INIT_PROVIDERSTRING для инициализации поставщика OLE DB. *subscriber_provider_string* поддерживается только для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
 [  **@subscriber_catalog=** ] **"***subscriber_catalog***"**  
 Каталог, используемый при соединении с поставщиком OLE DB. *subscriber_catalog* — **sysname**, и значение по умолчанию NULL. *subscriber_catalog* передается как свойство DBPROP_INIT_CATALOG для инициализации поставщика OLE DB. *subscriber_catalog* поддерживается только для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_addpushsubscription_agent** используется в репликации моментальных снимков и репликации транзакций.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/sp-addpushsubscription-a_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_addpushsubscription_agent**.  
  
## <a name="see-also"></a>См. также  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Создание подписки для подписчика, отличного от подписчика SQL Server](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
