---
title: sp_addpushsubscription_agent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpushsubscription_agent_TSQL
- sp_addpushsubscription_agent
helpviewer_keywords:
- sp_addpushsubscription_agent
ms.assetid: 1fdd2052-50d8-4318-8aa7-fc635d5cad18
author: stevestein
ms.author: sstein
ms.openlocfilehash: b0d17e4bc16340e0e913f48549f697eaabc8ec1c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031055"
---
# <a name="spaddpushsubscriptionagent-transact-sql"></a>sp_addpushsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Добавляет новое запланированное задание агента, используемое для синхронизации принудительной подписки на публикацию транзакций. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
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
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @subscriber = ] 'subscriber'` — Имя подписчика. *подписчик* — **sysname**, значение по умолчанию NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'` — Имя базы данных подписки. *subscriber_db* — **sysname**, значение по умолчанию NULL. Для отличных от подписчика SQL Server, укажите значение **(назначение по умолчанию)** для *subscriber_db*.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode` — Режим безопасности для использования при подключении к подписчику при синхронизации. *subscriber_security_mode* — **int**, значение по умолчанию 1. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. **1** задает проверку подлинности Windows.  
  
> [!IMPORTANT]  
>  Для обновляемых посредством очередей подписок при соединении с подписчиками используйте проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указывая для каждого из подписчиков различные учетные записи. Для всех других подписок используйте проверку подлинности Windows.  
  
`[ @subscriber_login = ] 'subscriber_login'` — Это имя входа подписчика, используемое при подключении к подписчику при синхронизации. *subscriber_login* — **sysname**, значение по умолчанию NULL.  
  
`[ @subscriber_password = ] 'subscriber_password'` — Пароль подписчика. *subscriber_password* является обязательным, если *subscriber_security_mode* присваивается **0**. *subscriber_password* — **sysname**, значение по умолчанию NULL. Если пароль подписчика используется, он автоматически шифруется.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @job_login = ] 'job_login'` — Это имя для учетной записи, под которой запускается агент. Azure SQL управляемом экземпляре базы данных используйте учетную запись SQL Server. *job_login* — **nvarchar(257)** , со значением по умолчанию NULL. Эта учетная запись Windows всегда используется для подключений к распространителю средствами агентов и для подключений к подписчику в случае применения встроенных средств проверки подлинности Windows.  
  
`[ @job_password = ] 'job_password'` — Пароль для учетной записи, под которой запускается агент. *job_password* — **sysname**, не имеет значения по умолчанию.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @job_name = ] 'job_name'` — Имя существующего задания агента. *имя_задания* — **sysname**, со значением по умолчанию NULL. Этот аргумент указывается только тогда, когда подписка будет синхронизироваться с использованием существующего задания, а не вновь создаваемого задания (выбор по умолчанию). Если вы не являетесь членом **sysadmin** предопределенной роли сервера, необходимо указать *job_login* и *job_password* при указании *имя_задания*.  
  
`[ @frequency_type = ] frequency_type` Это частота запуска агента распространителя. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
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
>  Указав значение **64** агент распространителя запускается в непрерывном режиме. Это соответствует вводу параметра **-непрерывной** параметром для агента. Дополнительные сведения см. в статье [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
`[ @frequency_interval = ] frequency_interval` — Это значение, которое применяется к частоте, задаваемой аргументом *frequency_type*. *frequency_interval* — **int**, значение по умолчанию 1.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` — Дата агента распространителя. Этот параметр используется при *frequency_type* присваивается **32** (относительно ежемесячно). *frequency_relative_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию 0.  
  
`[ @frequency_subday = ] frequency_subday` Том, как часто следует запланировать повторное выполнение в течение определенного периода. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4** (по умолчанию)|Минута|  
|**8**|Час|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию 5.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Время суток, когда агент распространителя впервые запланировано, в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию 0.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Время суток, когда прекращается выполнение агента распространителя, в формате ЧЧММСС. *active_end_time_of_day* — **int**, значение по умолчанию 235959.  
  
`[ @active_start_date = ] active_start_date` Дата первого запуска агента распространителя запланирована, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию 0.  
  
`[ @active_end_date = ] active_end_date` Дата плановой остановки агента распространителя, в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию 99991231.  
  
`[ @dts_package_name = ] 'dts_package_name'` Указывает имя пакета служб DTS. *dts_package_name* — **sysname** значение по умолчанию NULL. Например, для задания имени пакета `DTSPub_Package` этот параметр должен иметь значение `@dts_package_name = N'DTSPub_Package'`.  
  
`[ @dts_package_password = ] 'dts_package_password'` Указывает пароль, необходимый для запуска пакета. *dts_package_password* — **sysname** значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать пароль, если *dts_package_name* указан.  
  
`[ @dts_package_location = ] 'dts_package_location'` Указывает местоположение пакета. *dts_package_location* — **nvarchar(12)** , значение по умолчанию РАСПРОСТРАНИТЕЛЬ. Расположение пакета может быть **распространителя** или **подписчика**.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Является ли подписку можно синхронизировать через [!INCLUDE[msCoName](../../includes/msconame-md.md)] диспетчер синхронизации. *enabled_for_syncmgr* — **nvarchar(5)** , значение по умолчанию FALSE. Если **false**, подписка не зарегистрирована диспетчером синхронизации. Если **true**, подписка регистрируется диспетчером синхронизации и может быть синхронизирована без запуска [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
`[ @distribution_job_name = ] 'distribution_job_name'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @publisher = ] 'publisher'` — Имя издателя. *издатель* — **sysname**, со значением по умолчанию NULL.  
  
`[ @subscriber_provider = ] 'subscriber_provider'` Уникальный программный идентификатор (PROGID) с помощью которого поставщик OLE DB, являющихся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] зарегистрировать источник данных. *subscriber_provider* — **sysname**, значение по умолчанию NULL. *subscriber_provider* должно быть уникальным для поставщика OLE DB, установленного на распространителе. *subscriber_provider* поддерживается только для не - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
`[ @subscriber_datasrc = ] 'subscriber_datasrc'` — Имя источника данных, понятное поставщику OLE DB. *subscriber_datasrc* — **nvarchar(4000)** , со значением по умолчанию NULL. *subscriber_datasrc* передается как свойство DBPROP_INIT_DATASOURCE для инициализации поставщика OLE DB. *subscriber_datasrc* поддерживается только для не - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
`[ @subscriber_location = ] 'subscriber_location'` — Расположение базы данных, понятное поставщику OLE DB. *subscriber_location* — **nvarchar(4000)** , со значением по умолчанию NULL. *subscriber_location* передается как свойство DBPROP_INIT_LOCATION для инициализации поставщика OLE DB. *subscriber_location* поддерживается только для не - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
`[ @subscriber_provider_string = ] 'subscriber_provider_string'` — Строка подключения для поставщика OLE DB, определяющее источник данных. *subscriber_provider_string* — **nvarchar(4000)** , со значением по умолчанию NULL. *subscriber_provider_string* передается IDataInitialize или задается как свойство DBPROP_INIT_PROVIDERSTRING для инициализации поставщика OLE DB. *subscriber_provider_string* поддерживается только для не - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
`[ @subscriber_catalog = ] 'subscriber_catalog'` — Каталог, используемый при соединении с поставщиком OLE DB. *subscriber_catalog* — **sysname**, значение по умолчанию NULL. *subscriber_catalog* передается как свойство DBPROP_INIT_CATALOG для инициализации поставщика OLE DB. *subscriber_catalog* поддерживается только для не - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addpushsubscription_agent** используется в репликации моментальных снимков и репликации транзакций.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/sp-addpushsubscription-a_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addpushsubscription_agent**.  
  
## <a name="see-also"></a>См. также  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Создание подписки для подписчика, отличного от подписчика SQL Server](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
