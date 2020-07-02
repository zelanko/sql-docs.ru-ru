---
title: sp_addmergepullsubscription_agent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepullsubscription_agent
- sp_addmergepullsubscription_agent_TSQL
helpviewer_keywords:
- sp_addmergepullsubscription_agent
ms.assetid: a2f4b086-078d-49b5-8971-8a1e3f6a6feb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b9af4f3564c5834b856632db70bd6b12368a22c7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786240"
---
# <a name="sp_addmergepullsubscription_agent-transact-sql"></a>sp_addmergepullsubscription_agent (Transact-SQL)

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Добавляет новое задание агента для планирования синхронизации подписки по запросу на публикацию слиянием. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmergepullsubscription_agent [ [ @name = ] 'name' ]   
        , [ @publisher = ] 'publisher'   
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication =] 'publication'   
    [ , [ @publisher_security_mod e= ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher_encrypted_password = ] publisher_encrypted_password ]   
    [ , [ @subscriber = ] 'subscriber' ]   
    [ , [ @subscriber_db = ] 'subscriber_db' ]   
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]   
    [ , [ @subscriber_login = ] 'subscriber_login' ]   
    [ , [ @subscriber_password= ] 'subscriber_password' ]   
    [ , [ @distributor = ] 'distributor' ]   
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @encrypted_password = ] encrypted_password ]   
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
    [ , [ @merge_jobid = ] merge_jobid ]   
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]   
    [ , [ @ftp_address = ] 'ftp_address' ]   
    [ , [ @ftp_port = ] ftp_port ]   
    [ , [ @ftp_login = ] 'ftp_login' ]   
    [ , [ @ftp_password = ] 'ftp_password' ]    
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]   
    [ , [ @working_directory = ] 'working_directory' ]   
    [ , [ @use_ftp = ] 'use_ftp' ]   
    [ , [ @reserved = ] 'reserved' ]   
    [ , [ @use_interactive_resolver = ] 'use_interactive_resolver' ]   
    [ , [ @offloadagent = ] 'remote_agent_activation' ]   
    [ , [ @offloadserver = ] 'remote_agent_server_name']   
    [ , [ @job_name = ] 'job_name' ]   
    [ , [ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]  
    [ , [ @use_web_sync = ] use_web_sync ]  
        [ , [ @internet_url = ] 'internet_url' ]  
    [ , [ @internet_login = ] 'internet_login' ]  
        [ , [ @internet_password = ] 'internet_password' ]  
    [ , [ @internet_security_mode = ] internet_security_mode ]  
        [ , [ @internet_timeout = ] internet_timeout ]  
    [ , [ @hostname = ] 'hostname' ]  
        [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name = ] 'name'`Имя агента. Аргумент *Name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @publisher = ] 'publisher'`Имя сервера издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных издателя. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Режим безопасности, используемый при соединении с издателем при синхронизации. *publisher_security_mode* имеет **тип int**и значение по умолчанию 1. Если значение **равно 0**, то задает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверку подлинности. Если значение равно **1**, указывает проверку подлинности Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'`Имя входа, используемое при соединении с издателем при синхронизации. Аргумент *publisher_login* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @publisher_password = ] 'publisher_password'`Пароль, используемый при соединении с издателем. Аргумент *publisher_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] При возможности предлагать пользователю ввод учетных данных безопасности во время выполнения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @publisher_encrypted_password = ]publisher_encrypted_password`Параметр *publisher_encrypted_password* больше не поддерживается. Попытка присвоить этому параметру **bit** значение **1** приведет к ошибке.  
  
`[ @subscriber = ] 'subscriber'`Имя подписчика. Аргумент *Subscriber* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'`Имя базы данных подписки. Аргумент *subscriber_db* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode`Режим безопасности, используемый при соединении с подписчиком при синхронизации. *subscriber_security_mode* имеет **тип int**и значение по умолчанию 1. Если значение **равно 0**, то задает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверку подлинности. Если значение равно **1**, указывает проверку подлинности Windows.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Агент слияния всегда подключается к локальному подписчику с использованием проверки подлинности Windows. Если для этого аргумента указано значение, оно не будет учитываться и будет возвращено предупреждающее сообщение.  
  
`[ @subscriber_login = ] 'subscriber_login'`Имя входа подписчика, используемое при соединении с подписчиком при синхронизации. *subscriber_login* является обязательным, если *subscriber_security_mode* имеет значение **0**. Аргумент *subscriber_login* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если для этого аргумента указано значение, оно не будет учитываться и будет возвращено предупреждающее сообщение.  
  
`[ @subscriber_password = ] 'subscriber_password'`Пароль подписчика для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. *subscriber_password* является обязательным, если *subscriber_security_mode* имеет значение **0**. Аргумент *subscriber_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если для этого аргумента указано значение, оно не будет учитываться и будет возвращено предупреждающее сообщение.  
  
`[ @distributor = ] 'distributor'`Имя распространителя. Аргумент *распространитель* имеет тип **sysname**и значение по умолчанию *издателя*. то есть издатель также является распространителем.  
  
`[ @distributor_security_mode = ] distributor_security_mode`Режим безопасности, используемый при соединении с распространителем при синхронизации. *distributor_security_mode* имеет **тип int**и значение по умолчанию 0. **0** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности. **1** указывает проверку подлинности Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'`Имя входа распространителя, используемое при соединении с распространителем при синхронизации. *distributor_login* является обязательным, если *distributor_security_mode* имеет значение **0**. Аргумент *distributor_login* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @distributor_password = ] 'distributor_password'`Пароль распространителя. *distributor_password* является обязательным, если *distributor_security_mode* имеет значение **0**. Аргумент *distributor_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] При возможности предлагать пользователю ввод учетных данных безопасности во время выполнения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @encrypted_password = ] encrypted_password`Параметр *encrypted_password* больше не поддерживается. Попытка присвоить этому параметру **bit** значение **1** приведет к ошибке.  
  
`[ @frequency_type = ] frequency_type`Частота, с которой следует запланировать агент слияния. *frequency_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**1**|Один раз.|  
|**2**|По запросу|  
|**4**|Ежедневно|  
|**8**|Weekly (Еженедельно);|  
|**16**|Ежемесячная|  
|**32**|Ежемесячно с относительной датой|  
|**64**|Автозапуск|  
|**128**|Повторяющееся задание|  
|NULL (по умолчанию)||  
  
> [!NOTE]  
>  Указание значения **64** приводит к запуску агент слияния в непрерывном режиме. Это соответствует установке параметра **-Continuous** для агента. Дополнительные сведения см. в статье [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
`[ @frequency_interval = ] frequency_interval`День или дни выполнения агент слияния. *frequency_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Применение|Описание|  
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
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Дата агент слияния. Этот параметр используется, если *frequency_type* установлен в значение **32** (ежемесячное относительное расписание). *frequency_relative_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**1**|Первый|  
|**2**|Секунда|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последний|  
|NULL (по умолчанию)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Коэффициент повторения, используемый *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_subday = ] frequency_subday`Частота повторного планирования в течение заданного периода. *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Секунда|  
|**4**|Минута|  
|**8**|Час|  
|NULL (по умолчанию)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Интервал для *frequency_subday*. *frequency_subday_interval* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Время первого запланированного агент слияния в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Время суток, когда запланировать агент слияния прекращается в формате ЧЧММСС. *active_end_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_date = ] active_start_date`Дата первого запланированного запуска агент слияния в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_date = ] active_end_date`Дата прекращения расписания агент слияния в формате ГГГГММДД. *active_end_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'`Необязательная Командная строка, предоставляемая агент слияния. *optional_command_line* имеет тип **nvarchar (255)** и значение по умолчанию "". Может использоваться для передачи агенту слияния дополнительных параметров. Следующий пример иллюстрирует увеличение времени ожидания выполнения запроса по умолчанию до `600` секунд.  
  
```  
@optional_command_line = N'-QueryTimeOut 600'  
```  
  
`[ @merge_jobid = ] merge_jobid`Выходной параметр для идентификатора задания. *merge_jobid* является **двоичным (16)** и ЗНАЧЕНИЕМ по умолчанию NULL.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'`Указывает, можно ли синхронизировать подписку с помощью диспетчера синхронизации Windows. *enabled_for_syncmgr* имеет тип **nvarchar (5)** и значение по умолчанию false. Если **значение равно false**, подписка не зарегистрирована в диспетчере синхронизации. Если **значение — true**, подписка регистрируется в диспетчере синхронизации и может быть синхронизирована без запуска [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
`[ @ftp_address = ] 'ftp_address'`Только для обратной совместимости.  
  
`[ @ftp_port = ] ftp_port`Только для обратной совместимости.  
  
`[ @ftp_login = ] 'ftp_login'`Только для обратной совместимости.  
  
`[ @ftp_password = ] 'ftp_password'`Только для обратной совместимости.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'`Указывает расположение, из которого следует брать файлы моментальных снимков. *alternate_snapshot_folder* имеет тип **nvarchar (255)** и значение по умолчанию NULL. При значении NULL файлы моментальных снимков считываются из местонахождения по умолчанию, определяемого издателем.  
  
`[ @working_directory = ] 'working_directory'`Имя рабочего каталога, используемого для временного хранения файлов данных и схемы публикации при использовании FTP для перемещения файлов моментальных снимков. *working_directory* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  
  
`[ @use_ftp = ] 'use_ftp'`Задает использование FTP вместо стандартного протокола для получения моментальных снимков. *use_ftp* имеет тип **nvarchar (5)** и значение по умолчанию false.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver' ]`Использует интерактивный сопоставитель для разрешения конфликтов для всех статей, допускающих интерактивное разрешение. *use_interactive_resolver* имеет тип **nvarchar (5)** и значение по умолчанию false.  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. При установке *remote_agent_activation* значение, отличное от **false** , будет выдаваться ошибка.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. При установке *remote_agent_server_name* любого значения, отличного от NULL, будет выдаваться ошибка.  
  
`[ @job_name = ] 'job_name' ]`Имя существующего задания агента. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL. Этот аргумент указывается только тогда, когда подписка будет синхронизироваться с использованием существующего задания, а не вновь создаваемого задания (выбор по умолчанию). Если вы не являетесь членом предопределенной роли сервера **sysadmin** , необходимо указать *job_login* и *job_password* при указании *job_name*.  
  
`[ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]`Путь к папке, из которой будут считываться файлы моментальных снимков, если будет использоваться моментальный снимок отфильтрованных данных. *dynamic_snapshot_location* имеет тип **nvarchar (260)** и значение по умолчанию NULL. Дополнительные сведения см. в разделе [Параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
`[ @use_web_sync = ] use_web_sync`Указывает, что веб-синхронизация включена. *use_web_sync* имеет **бит**и значение по умолчанию 0. **1** указывает, что подписка по запросу может быть синхронизирована через Интернет по протоколу HTTP.  
  
`[ @internet_url = ] 'internet_url'`Расположение прослушивателя репликации (REPLISAPI.DLL) для веб-синхронизации. *internet_url* имеет тип **nvarchar (260)** и значение по умолчанию NULL. *internet_url* является полным URL-адресом в формате `http://server.domain.com/directory/replisapi.dll` . Если сервер настроен для прослушивания порта, отличного от 80-го, необходимо также задать номер порта в формате `http://server.domain.com:portnumber/directory/replisapi.dll`, где `portnumber` указывает номер порта.  
  
`[ @internet_login = ] 'internet_login'`Имя входа, используемое агент слияния при соединении с веб-сервером, на котором размещается веб-синхронизация, с использованием обычной проверки подлинности HTTP. Аргумент *internet_login* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @internet_password = ] 'internet_password'`Пароль, используемый агент слияния при подключении к веб-серверу, на котором размещается веб-синхронизация, с использованием обычной проверки подлинности HTTP. *internet_password* имеет тип **nvarchar (524)** и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
`[ @internet_security_mode = ] internet_security_mode`Метод проверки подлинности, используемый агент слияния при подключении к веб-серверу во время веб-синхронизации по протоколу HTTPS. *internet_security_mode* имеет **тип int** и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**0**|Используется обычная проверка подлинности (проверка пароля и имени входа, входящая в протокол HTTP).|  
|**1** (по умолчанию)|Используется встроенная проверка подлинности Windows.|  
  
> [!NOTE]  
>  При веб-синхронизации рекомендуется использовать обычную проверку подлинности. Чтобы использовать веб-синхронизацию, необходимо установить TLS-соединение с этим сервером. Дополнительные сведения см. в разделе [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
`[ @internet_timeout = ] internet_timeout`Продолжительность времени в секундах до истечения срока действия запроса веб-синхронизации. *internet_timeout* имеет **тип int**и значение по умолчанию **300** секунд.  
  
`[ @hostname = ] 'hostname'`Переопределяет значение HOST_NAME (), если эта функция используется в предложении WHERE параметризованного фильтра. Аргумент *HostName* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @job_login = ] 'job_login'`Имя входа для учетной записи Windows, под которой запускается агент. *job_login* имеет тип **nvarchar (257)** и не имеет значения по умолчанию. Эта учетная запись Windows всегда используется при соединениях агента с подписчиком и соединениях с распространителем и издателем, когда применяется встроенная проверка подлинности Windows.  
  
`[ @job_password = ] 'job_password'`Пароль для учетной записи Windows, под которой запускается агент. Аргумент *job_password* имеет тип **sysname**и не имеет значения по умолчанию.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. Для обеспечения лучшей защиты имена входа и пароли должны вводиться в ходе выполнения.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergepullsubscription_agent** используется в репликации слиянием и использует функции, аналогичные [sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md).  
  
 Пример правильного указания параметров безопасности при выполнении **sp_addmergepullsubscription_agent**см. в разделе [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md).  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_1_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addmergepullsubscription_agent**.  
  
## <a name="see-also"></a>См. также:  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Subscribe to Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
