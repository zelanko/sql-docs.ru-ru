---
title: sp_addsubscription (Transact-SQL) | Документация Майкрософт
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.custom: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsubscription
- sp_addsubscription_TSQL
helpviewer_keywords:
- sp_addsubscription
ms.assetid: 61ddf287-1fa0-4c1a-8657-ced50cebf0e0
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2ca3505d952e1bffa68d23fe2de5b51c050640c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096224"
---
# <a name="spaddsubscription-transact-sql"></a>sp_addsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет подписку на публикацию и устанавливает состояние подписчика. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addsubscription [ @publication = ] 'publication'  
    [ , [ @article = ] 'article']  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @destination_db = ] 'destination_db' ]  
        [ , [ @sync_type = ] 'sync_type' ]  
    [ , [ @status = ] 'status'  
        [ , [ @subscription_type = ] 'subscription_type' ]  
    [ , [ @update_mode = ] 'update_mode' ]  
    [ , [ @loopback_detection = ] 'loopback_detection' ]  
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
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
    [ , [ @reserved = ] 'reserved' ]  
    [ , [ @enabled_for_syncmgr= ] 'enabled_for_syncmgr' ]  
    [ , [ @offloadagent= ] remote_agent_activation]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
    [ , [ @distribution_job_name= ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @backupdevicetype = ] 'backupdevicetype' ]  
    [ , [ @backupdevicename = ] 'backupdevicename' ]  
    [ , [ @mediapassword = ] 'mediapassword' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @fileidhint = ] fileidhint ]  
    [ , [ @unload = ] unload ]  
    [ , [ @subscriptionlsn = ] subscriptionlsn ]  
    [ , [ @subscriptionstreams = ] subscriptionstreams ]  
    [ , [ @subscriber_type = ] subscriber_type ]  
    [ , [ @memory_optimized = ] memory_optimized ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @publication=] '*публикации*"  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ @article=] '*статье*"  
 Статья, на которую подписана публикация. *статья* — **sysname**, значение по умолчанию все. Если значение равно ALL, то подписка добавляется ко всем статьям в данной публикации. Издателями Oracle поддерживаются только значения ALL и NULL.  
  
 [ @subscriber=] '*подписчика*"  
 Имя подписчика. *подписчик* — **sysname**, значение по умолчанию NULL.  
  
 [ @destination_db=] '*destination_db*"  
 Имя целевой базы данных, в которую помещаются реплицированные данные. *destination_db* — **sysname**, значение по умолчанию NULL. Если задано значение NULL, *destination_db* присваивается имя базы данных публикации. Для издателей Oracle *destination_db* должен быть указан. Для отличных от подписчика SQL Server, укажите значение (назначение по умолчанию) для *destination_db*.  
  
 [ @sync_type=] '*sync_type*"  
 Тип синхронизации подписки. *sync_type* — **nvarchar(255)** , и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|none|Подписчик уже имеет схему и начальные данные для опубликованных таблиц.<br /><br /> Примечание. Этот параметр является устаревшим. Вместо этого используйте значение «replication support only».|  
|automatic (по умолчанию)|Схема и начальные данные для опубликованных таблиц вначале передаются подписчику.|  
|replication support only|Предоставляет автоматическое создание на подписчике статьи хранимой процедуры и триггеров, которые поддерживают обновляемые подписки, если это подходит. Предполагает, что подписчик уже имеет схему и начальные данные для опубликованных таблиц. При настройке топологии одноранговой репликации транзакций убедитесь, что данные во всех узлах топологии идентичны. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).<br /><br /> *Не поддерживается для подписок на публикации SQL Server.*|  
|initialize with backup|Схема и начальные данные для опубликованных таблиц извлекаются из резервной копии базы данных публикации. Предполагает, что подписчик имеет доступ к резервной копии базы данных публикации. Расположение резервной копии и тип носителя для резервной копии задаются *backupdevicename* и *backupdevicetype*. При использовании этого аргумента топология одноранговой репликации транзакций должна быть зафиксирована во время настройки.<br /><br /> *Не поддерживается для подписок на публикации SQL Server.*|  
|initialize from lsn|Используется при добавлении узла к топологии одноранговой репликации транзакций. Используется с @subscriptionlsn, чтобы убедиться в том, что все нужные транзакции реплецированы на новый узел. Предполагает, что подписчик уже имеет схему и начальные данные для опубликованных таблиц. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
  
> [!NOTE]  
>  Системные таблицы и данные переносятся всегда.  
  
 [ @status=] '*состояние*"  
 Состояние подписки. *состояние* — **sysname**, со значением по умолчанию NULL. Если этот параметр не задан явно, при репликации ему устанавливается одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|active|Подписка инициализирована и готова к принятию изменений. Этот параметр задается, если значение *sync_type* имеет значение none, инициализации с помощью резервной копии или только поддержка репликации.|  
|subscribed|Требуется инициализация подписки. Этот параметр задается, если значение *sync_type* выполняется автоматически.|  
  
 [ @subscription_type=] '*subscription_type*"  
 Тип подписки. *subscription_type* — **nvarchar(4)** , значение по умолчанию push. Может принимать значения push или pull. Агенты распространителя принудительных подписок находятся на распространителе, а агенты распространителя подписок по запросу на подписчике. *subscription_type* может принимать значение pull для создания именованной подписки по запросу, известной издателю. Дополнительные сведения см. в статье [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md).  
  
> [!NOTE]  
>  Анонимные подписки не нуждаются в использовании этой хранимой процедуры.  
  
 [ @update_mode=] '*update_mode*"  
 — Это тип обновления. *update_mode* — **nvarchar(30)** , и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|read only (по умолчанию)|Подписка только для чтения. Изменения у подписчика не отправляются издателю.|  
|sync tran|Включает поддержку немедленно обновляемых подписок. Не поддерживается для издателей Oracle.|  
|queued tran|Обеспечивает подписку обновляемую посредством очередей. Изменение данных можно выполнять у подписчика, сохранять в очереди и после этого передавать издателю. Не поддерживается для издателей Oracle.|  
|отработка отказа|Включает для подписки немедленное обновление с обновлением по очереди при переходе на другой ресурс в случае отработки отказа. Изменение данных можно выполнять на подписчике и немедленно передавать издателю. Если издатель и подписчик не подключены, режим обновления может быть изменен так, что изменения данных, сделанные у подписчика, будут сохраняться в очереди до тех пор, пока подписчик и издатель не будут повторно подключены. Не поддерживается для издателей Oracle.|  
|queued failover|Включает подписку с обновлением по очереди в качестве обновляемой посредством очередей подписки, при этом поддерживает возможность переключения в режим немедленного обновления. Изменение данных можно выполнять у подписчика и сохранять в очереди до установления соединения между подписчиком и издателем. При установлении постоянного соединения можно переключиться в режим немедленного обновления. Не поддерживается для издателей Oracle.|  
  
 Обратите внимание на то, что значения synctran и queued tran не допускается, если публикация, на которую выполняется подписка допускает службы DTS.  
  
 [ @loopback_detection=] '*loopback_detection*"  
 Определяет, отправляет ли агент распространителя транзакции, изначально созданные на подписчике, обратно подписчику. *loopback_detection* — **nvarchar(5)** , и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|true|Агент распространителя не отправляет транзакции, изначально созданные у подписчика, обратно. Используется с двунаправленной репликацией транзакций. Дополнительные сведения см. в статье [Bidirectional Transactional Replication](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md).|  
|False|Агент распространителя отправляет транзакции, изначально созданные у подписчика, обратно.|  
|NULL (по умолчанию)|Автоматически устанавливается значение true для подписчика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и значение false для подписчика, не относящегося к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 [ @frequency_type=] *frequency_type*  
 Частота запуска задачи распространения по расписанию. *frequency_type* имеет тип int и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|1|Однократно|  
|2|по запросу|  
|4|Ежедневно|  
|8|Еженедельно|  
|16|Ежемесячно|  
|32|Ежемесячно с относительной датой|  
|64 (по умолчанию)|Автозапуск|  
|128|Повторяющееся задание|  
  
 [ @frequency_interval=] *frequency_interval*  
 — Это значение, которое применяется к частоте, задаваемой аргументом *frequency_type*. *frequency_interval* — **int**, значение по умолчанию NULL.  
  
 [ @frequency_relative_interval=] *frequency_relative_interval*  
 Дата агента распространителя. Этот параметр используется при *frequency_type* имеет значение 32 (ежемесячное относительное расписание). *frequency_relative_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|1|Первая|  
|2|Вторая|  
|4|Третья|  
|8|Четвертая|  
|16|Последняя|  
|NULL (по умолчанию)||  
  
 [ @frequency_recurrence_factor=] *frequency_recurrence_factor*  
 Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию NULL.  
  
 [ @frequency_subday=] *frequency_subday*  
 Частота повторного планирования в течение определенного периода, в минутах. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|1|Однократно|  
|2|Вторая|  
|4|Минута|  
|8|Час|  
|NULL||  
  
 [ @frequency_subday_interval=] *frequency_subday_interval*  
 Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию NULL.  
  
 [ @active_start_time_of_day=] *active_start_time_of_day*  
 Время суток, на которое запланирован первый запуск агента распространителя, в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию NULL.  
  
 [ @active_end_time_of_day=] *active_end_time_of_day*  
 Время суток, на которое запланирован останов агента распространителя, в формате ЧЧММСС. *active_end_time_of_day* — **int**, значение по умолчанию NULL.  
  
 [ @active_start_date=] *active_start_date*  
 Дата, когда запланирован первый запуск агента распространителя, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию NULL.  
  
 [ @active_end_date=] *active_end_date*  
 Дата, когда запланирован останов агента распространителя, в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию NULL.  
  
 [ @optional_command_line=] '*optional_command_line*"  
 Необязательное приглашение к вводу команды. *optional_command_line* — **nvarchar(4000)** , значение по умолчанию NULL.  
  
 [ @reserved=] '*зарезервированные*"  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @enabled_for_syncmgr=] '*enabled_for_syncmgr*"  
 Является ли подписку можно синхронизировать через [!INCLUDE[msCoName](../../includes/msconame-md.md)] диспетчера синхронизации Windows. *enabled_for_syncmgr* — **nvarchar(5)** , значение по умолчанию FALSE. Если это значение равно FALSE, подписка не регистрируется диспетчером синхронизации Windows. Если значение равно TRUE, подписка регистрируется диспетчером синхронизации Windows и может быть синхронизирована без запуска среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Не поддерживается для издателей Oracle.  
  
 [ @offloadagent=] '*remote_agent_activation*"  
 Указывает на то, что агент может быть активирован удаленно. *remote_agent_activation* — **бит** значение по умолчанию 0.  
  
> [!NOTE]  
>  Этот аргумент является устаревшим и сохраняется только для поддержки обратной совместимости скриптов.  
  
 [ @offloadserver=] '*remote_agent_server_name*"  
 Указывает сетевое имя сервера, используемого для удаленной активации. *remote_agent_server_name*— **sysname**, значение по умолчанию NULL.  
  
 [ @dts_package_name=] '*dts_package_name*"  
 Указывает имя пакета служб DTS. *dts_package_name* — **sysname** значение по умолчанию NULL. Например, для задания пакета DTSPub_Package параметр должен быть равен `@dts_package_name = N'DTSPub_Package'`. Этот аргумент доступен для принудительных подписок. Для добавления сведений о пакете служб DTS к подписке по запросу используется процедура sp_addpullsubscription_agent.  
  
 [ @dts_package_password=] '*dts_package_password*"  
 Задает пароль для пакета, если он имеется. *dts_package_password* — **sysname** значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать пароль, если *dts_package_name* указан.  
  
 [ @dts_package_location=] '*dts_package_location*"  
 Указывает местоположение пакета. *dts_package_location* — **nvarchar(12)** , значение по умолчанию РАСПРОСТРАНИТЕЛЬ. Пакет может храниться на распространителе или на подписчике.  
  
 [ @distribution_job_name=] '*distribution_job_name*"  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @publisher=] '*издателя*"  
 Указывает, отличный от [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует указывать для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
 [ @backupdevicetype=] '*backupdevicetype*"  
 Задает тип устройства резервного копирования, используемого при инициализации подписчика из резервной копии. *backupdevicetype* — **nvarchar(20)** , и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|logical (по умолчанию)|Устройство резервного копирования является логическим устройством.|  
|disk|Устройство резервного копирования является жестким диском.|  
|tape|Устройство резервного копирования является накопителем на магнитной ленте.|  
  
 *backupdevicetype* используется, только если *sync_method*имеет значение initialize_with_backup.  
  
 [ @backupdevicename=] '*backupdevicename*"  
 Указывает имя устройства, используемого при инициализации подписчика из резервной копии. *backupdevicename* — **nvarchar(1000)** , значение по умолчанию NULL.  
  
 [ @mediapassword=] '*mediapassword*"  
 Указывает пароль для набора носителей, если при форматировании носителя был задан пароль. *MEDIAPASSWORD* — **sysname**, со значением по умолчанию NULL.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 [ @password=] '*пароль*"  
 Указывает пароль для резервной копии, если при создании резервной копии был задан пароль. *пароль*— **sysname**, со значением по умолчанию NULL.  
  
 [ @fileidhint=] *fileidhint*  
 Определяет порядковый номер восстанавливаемого резервного набора данных. *fileidhint* — **int**, со значением по умолчанию NULL.  
  
 [ @unload=] *выгрузки*  
 Определяет, должно ли быть выгружено ленточное устройство резервного копирования после завершения инициализации из резервной копии. *выгрузить* — **бит**, со значением по умолчанию 1. 1 указывает, что лента должна быть выгружена. *выгрузить* используется, только если *backupdevicetype* является ленточный накопитель.  
  
 [ @subscriptionlsn=] *subscriptionlsn*  
 Задает регистрационный номер транзакции в журнале (LSN), начиная с которого подписка должна доставлять изменения на узел в одноранговой топологии репликации транзакций. Используется с @sync_type значение initialize из номера lsn, чтобы убедиться в том, что все необходимые транзакции будут реплицированы на новый узел. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 [ @subscriptionstreams=] *subscriptionstreams*  
 Число соединений на каждого агента распространителя для параллельного применения пакетов изменений на подписчике при сохранении многих характеристик транзакций, имеющихся для однопоточного выполнения. *SubscriptionStreams* — **tinyint**, со значением по умолчанию NULL. Поддерживаются значения в диапазоне от 1 до 64. Этот параметр не поддерживается для отличных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков, издателей Oracle или peer-to-peer подписок. При каждом использовании потоков подписки в таблицу msreplication_subscriptions добавляются дополнительные строки (по одной на поток) с параметром agent_id, установленным в значение NULL.  
  
> [!NOTE]  
>  Потоки подписки не работают для статей, настроенных для доставки [!INCLUDE[tsql](../../includes/tsql-md.md)]. Для использования потоков подписки настройте в статьях доставку вызовов хранимых процедур.  
  
 [ @subscriber_type=] *subscriber_type*  
 Тип подписчика. *subscriber_type* — **tinyint**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0 (по умолчанию)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчик|  
|1|Сервер источника данных ODBC|  
|2|База данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet|  
|3|Поставщик OLE DB|  
  
 [ @memory_optimized=] *memory_optimized*  
 Указывает, что данная подписка поддерживает оптимизированные для памяти таблицы. *memory_optimized* — **бит**, где 1 соответствует true (данная подписка поддерживает оптимизированные для памяти таблицы).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_addsubscription используется в репликации моментальных снимков и репликации транзакций.  
  
 При выполнении процедуры sp_addsubscription членом предопределенной роли сервера sysadmin для создания принудительной подписки задание агента распространителя явно создается и запускается под учетной записью службы агента SQL Server. Мы рекомендуем выполнить [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) и укажите учетные данные учетной записи Windows различные, конкретного агента для @job_login и @job_password. Дополнительные сведения см. в статье [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 Процедура sp_addsubscription закрывает доступ для подписчиков ODBC и OLE DB к следующим публикациям.  
  
-   Были созданы с помощью собственного *sync_method* в вызове [sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md).  
  
-   Содержащим статьи, которые были добавлены к публикации с [sp_addarticle](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) хранимую процедуру, которая бы *pre_creation_cmd* значение параметра 3 (усечение).  
  
-   Попытка задать *update_mode* значение sync tran.  
  
-   Имеющим статью, настроенную на использование параметризованных инструкций.  
  
 Кроме того, если публикация имеет *allow_queued_tran* параметра задано значение true (что разрешает постановку в очередь изменений на подписчике, пока они могут быть применены на издателе), столбец timestamp в статье указаны в качестве **timestamp**, и изменения этого столбца отправляются подписчику. Подписчик формирует и обновляет значение столбца отметок времени. Для подписчика ODBC или OLE DB, процедура sp_addsubscription завершается неудачей, если попытка подписаться на публикацию с *allow_queued_tran* присвоено значение true и имеются статьи со столбцами отметок времени.  
  
 Если подписка не использует пакет служб DTS, она не может подписаться на публикацию, которой присваивается *allow_transformable_subscriptions*. Если таблицу из публикации нужно реплицировать как в подписку служб DTS, так и в подписку, отличную от подписки служб DTS, необходимо создать две разные публикации: одну для каждого типа подписки.  
  
 При выборе параметров **sync_type** *replication support only*, *initialize with backup*или *initialize from lsn*агент чтения журнала необходимо запустить после выполнения процедуры **sp_addsubscription**, чтобы скрипты установки были записаны в базу данных распространителя. Агент чтения журнала должен работать под учетной записью, которая является членом предопределенной роли сервера **sysadmin** . Если параметр **sync_type** установлен в значение *Automatic*, никаких специальных действий агента чтения журнала не требуется.  
  
## <a name="permissions"></a>Разрешения  
 Процедуру sp_addsubscription могут выполнять только члены предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner. Для подписок по запросу пользователи, имеющие имена входа в списке доступа к публикации, могут выполнять процедуру sp_addsubscription.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/sp-addsubscription-trans_1.sql)]  
  
## <a name="see-also"></a>См. также  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Создание подписки для подписчика, отличного от подписчика SQL Server](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)   
 [sp_changesubstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
