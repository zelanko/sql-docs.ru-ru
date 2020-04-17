---
title: sp_addmergepullsubscription_agent (Трансакт-СЗЛ) Документы Майкрософт
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07cc514d615c86a90dcf37fbd4748c3ab1776f06
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528988"
---
# <a name="sp_addmergepullsubscription_agent-transact-sql"></a>sp_addmergepullsubscription_agent (Transact-SQL)

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
`[ @name = ] 'name'`Это имя агента. *имя* **sysname**, с дефолтом NULL.  
  
`[ @publisher = ] 'publisher'`Это имя сервера Издателя. *издатель* **sysname**, без по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Это название базы данных Издателя. *publisher_db* **sysname,** без по умолчанию.  
  
`[ @publication = ] 'publication'`Это название публикации. *публикация* **sysname,** без по умолчанию.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Используется режим безопасности при подключении к издателю при синхронизации. *publisher_security_mode* **int,** с по умолчанию 1. Если **0**, указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] аутентификация. Если **1**, определяет windows аутентификации.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'`Используется ли логин при подключении к издателю при синхронизации. *publisher_login* **sysname,** с дефолтом NULL.  
  
`[ @publisher_password = ] 'publisher_password'`Используется ли пароль при подключении к Издателю. *publisher_password* является **sysname**, с дефолтом NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] При возможности предлагать пользователю ввод учетных данных безопасности во время выполнения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @publisher_encrypted_password = ]publisher_encrypted_password`Установка *publisher_encrypted_password* больше не поддерживается. Попытка установить этот параметр **бита** до **1** приведет к ошибке.  
  
`[ @subscriber = ] 'subscriber'`Это имя абонента. *абонентs* **sysname**, с дефолтом NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'`Это название базы данных подписки. *subscriber_db* **sysname**, с дефолтом NULL.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode`Используется режим безопасности при подключении к абоненту при синхронизации. *subscriber_security_mode* **int**, с по умолчанию 1. Если **0**, указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] аутентификация. Если **1**, определяет windows аутентификации.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Агент слияния всегда подключается к локальному подписчику с использованием проверки подлинности Windows. Если для этого аргумента указано значение, оно не будет учитываться и будет возвращено предупреждающее сообщение.  
  
`[ @subscriber_login = ] 'subscriber_login'`Используется ли подписка при подключении к абоненту при синхронизации. *subscriber_login* требуется, если *subscriber_security_mode* установлен на **0**. *subscriber_login* является **sysname**, с дефолтом NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если для этого аргумента указано значение, оно не будет учитываться и будет возвращено предупреждающее сообщение.  
  
`[ @subscriber_password = ] 'subscriber_password'`Является ли пароль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] абонента для аутентификации. *subscriber_password* требуется, если *subscriber_security_mode* установлен на **0**. *subscriber_password* является **sysname**, с дефолтом NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если для этого аргумента указано значение, оно не будет учитываться и будет возвращено предупреждающее сообщение.  
  
`[ @distributor = ] 'distributor'`Это имя Дистрибьютора. *дистрибьютор* **sysname**, с по умолчанию *издателя*; то есть, Издатель также является Дистрибьютором.  
  
`[ @distributor_security_mode = ] distributor_security_mode`Используется режим безопасности при подключении к дистрибьютору при синхронизации. *distributor_security_mode* **int,** с по умолчанию 0. **0** определяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] аутентификацию. **1** определяет аутентификацию Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'`Используется ли логин Дистрибьютора при подключении к Дистрибьютору при синхронизации. *distributor_login требуется,* если *distributor_security_mode* установлен на **0**. *distributor_login* **sysname**, с дефолтом NULL.  
  
`[ @distributor_password = ] 'distributor_password'`Является паролем Дистрибьютора. *distributor_password* требуется, если *distributor_security_mode* установлен на **0**. *distributor_password* **sysname,** с дефолтом NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] При возможности предлагать пользователю ввод учетных данных безопасности во время выполнения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @encrypted_password = ] encrypted_password`Настройка *encrypted_password* больше не поддерживается. Попытка установить этот параметр **бита** до **1** приведет к ошибке.  
  
`[ @frequency_type = ] frequency_type`Частота, с которой можно запланировать агента слияния. *frequency_type* является **int,** и может быть одним из следующих значений.  
  
|Значение|Описание|  
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
>  Указание значения **64** приводит к тому, что агент слияния работает в непрерывном режиме. Это соответствует установлению **параметра непрерывного** для агента. Дополнительные сведения см. в статье [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
`[ @frequency_interval = ] frequency_interval`День или дни, которые запускает агент слияния. *frequency_interval* является **int,** и может быть одним из этих значений.  
  
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
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Является датой агента слияния. Этот параметр используется, когда *frequency_type* установлен до **32** (месячный родственник). *frequency_relative_interval* является **int,** и может быть одним из этих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Первый|  
|**2**|Секунда|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последний|  
|NULL (по умолчанию)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Является ли фактор рецидива, используемый *frequency_type*. *frequency_recurrence_factor* **int**, с дефолтом NULL.  
  
`[ @frequency_subday = ] frequency_subday`Как часто перепланировать в течение определенного периода. *frequency_subday* является **int,** и может быть одним из этих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Секунда|  
|**4**|Минута|  
|**8**|Час|  
|NULL (по умолчанию)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Является ли интервал для *frequency_subday*. *frequency_subday_interval* **int**, с дефолтом NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Это время суток, когда агент слияния впервые запланирован, отформатированный как HHMMSS. *active_start_time_of_day* **int**, с дефолтом NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Это время суток, когда агент слияния перестает быть запланированным, отформатированным как HHMMSS. *active_end_time_of_day* **int**, с дефолтом NULL.  
  
`[ @active_start_date = ] active_start_date`Является ли дата, когда агент слияния впервые запланирован, отформатирован как YYYMMD. *active_start_date* **int**, с дефолтом NULL.  
  
`[ @active_end_date = ] active_end_date`Является ли дата, когда агент слияния перестает быть запланировано, отформатированный как YYYYMMD. *active_end_date* **int**, с дефолтом NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'`Является дополнительным запросом команды, который поставляется агенту слияния. *optional_command_line* **nvarchar (255)**, с по умолчанию ' '. Может использоваться для передачи агенту слияния дополнительных параметров. Следующий пример иллюстрирует увеличение времени ожидания выполнения запроса по умолчанию до `600` секунд.  
  
```  
@optional_command_line = N'-QueryTimeOut 600'  
```  
  
`[ @merge_jobid = ] merge_jobid`Является параметром вывода для идентификатора задания. *merge_jobid* **является двоичным (16)**, с дефолтом NULL.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'`Упоняет, можно ли синхронизировать подписку через менеджер синхронизации Windows. *enabled_for_syncmgr* **nvarchar (5)**, с по умолчанию FALSE. Если **несоответствует действительности,** подписка не зарегистрирована менеджером синхронизации. Если **это правда,** подписка зарегистрирована менеджером синхронизации и может [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]быть синхронизирована без запуска.  
  
`[ @ftp_address = ] 'ftp_address'`Только для обратной совместимости.  
  
`[ @ftp_port = ] ftp_port`Только для обратной совместимости.  
  
`[ @ftp_login = ] 'ftp_login'`Только для обратной совместимости.  
  
`[ @ftp_password = ] 'ftp_password'`Только для обратной совместимости.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'`Определяет место, из которого можно забрать файлы моментального снимка. *alternate_snapshot_folder* **nvarchar (255)**, с дефолтом NULL. При значении NULL файлы моментальных снимков считываются из местонахождения по умолчанию, определяемого издателем.  
  
`[ @working_directory = ] 'working_directory'`Является ли название рабочего каталога, используемого для временного хранения данных и файлов схем для публикации, когда FTP используется для передачи файлов моментальных снимков. *working_directory* **nvarchar (255)**, с дефолтом NULL.  
  
`[ @use_ftp = ] 'use_ftp'`Определяет использование FTP вместо типичного протокола для получения снимков. *use_ftp* **nvarchar (5)**, с дефолтом FALSE.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver' ]`Использует интерактивный разрешители для разрешения конфликтов для всех статей, которые позволяют интерактивное разрешение. *use_interactive_resolver* **nvarchar (5)**, с дефолтом FALSE.  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. Установка *remote_agent_activation* на значение, не **ложное,** приведет к погрешности.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. Установка *remote_agent_server_name* к любому значению, не являющееся НУЛТ, приведет к погрешности.  
  
`[ @job_name = ] 'job_name' ]`Это имя существующей работы агента. *job_name* является **sysname,** со значением null по умолчанию. Этот аргумент указывается только тогда, когда подписка будет синхронизироваться с использованием существующего задания, а не вновь создаваемого задания (выбор по умолчанию). Если вы не являетесь участником роли сервера **sysadmin,** необходимо указать *job_login* и *job_password,* когда вы указываете *job_name.*  
  
`[ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]`Путь к папке, где будут считываться файлы моментального снимка, если будет использован отфильтрованный моментальный снимок данных. *dynamic_snapshot_location* **nvarchar (260)**, с дефолтом NULL. Дополнительные сведения см. в разделе [Параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
`[ @use_web_sync = ] use_web_sync`Означает, что синхронизация веб включена. *use_web_sync* **бит,** с по умолчанию 0. **1** указывает, что подписка на вытягивание может быть синхронизирована через Интернет с помощью HTTP.  
  
`[ @internet_url = ] 'internet_url'`Является ли расположение слушателя репликации (REPLISAPI. DLL) для синхронизации веб-страниц. *internet_url* **nvarchar (260)**, с дефолтом NULL. *internet_url* является полностью квалифицированным `http://server.domain.com/directory/replisapi.dll`URL, в формате . Если сервер настроен для прослушивания порта, отличного от 80-го, необходимо также задать номер порта в формате `http://server.domain.com:portnumber/directory/replisapi.dll`, где `portnumber` указывает номер порта.  
  
`[ @internet_login = ] 'internet_login'`Является ли логин, который агент слияния использует при подключении к веб-серверу, который размещает синхронизацию веб-страниц с помощью http Basic Authentication. *internet_login* является **sysname**, с дефолтом NULL.  
  
`[ @internet_password = ] 'internet_password'`Является ли пароль, который агент слияния использует при подключении к веб-серверу, который размещает синхронизацию веб-страниц с помощью http Basic Authentication. *internet_password* **nvarchar (524)**, со значением по умолчанию NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
`[ @internet_security_mode = ] internet_security_mode`Является ли метод проверки подлинности, используемый агентом слияния при подключении к веб-серверу во время синхронизации веб-страниц с помощью HTTPS. *internet_security_mode* является **int** и может быть одним из этих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Используется обычная проверка подлинности (проверка пароля и имени входа, входящая в протокол HTTP).|  
|**1** (по умолчанию)|Используется встроенная проверка подлинности Windows.|  
  
> [!NOTE]  
>  При веб-синхронизации рекомендуется использовать обычную проверку подлинности. Для использования синхронизации веб-страниц необходимо сделать подключение TLS к веб-серверу. Дополнительные сведения см. в разделе [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
`[ @internet_timeout = ] internet_timeout`Продолжительность времени, в секундах, до истечения срока действия запроса на синхронизацию веб-страниц. *internet_timeout* **int**, с по умолчанию **300** секунд.  
  
`[ @hostname = ] 'hostname'`Переопределяет значение HOST_NAME() при использовании этой функции в пункте WHERE параметризированного фильтра. *хост-имя* **sysname,** с дефолтом NULL.  
  
`[ @job_login = ] 'job_login'`Является ли логин для учетной записи Windows, под которой работает агент. *job_login* **nvarchar (257)**, без по умолчанию. Эта учетная запись Windows всегда используется при соединениях агента с подписчиком и соединениях с распространителем и издателем, когда применяется встроенная проверка подлинности Windows.  
  
`[ @job_password = ] 'job_password'`Является ли пароль для учетной записи Windows, под которым работает агент. *job_password* **sysname,** без по умолчанию.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. Для обеспечения лучшей защиты имена входа и пароли должны вводиться в ходе выполнения.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergepullsubscription_agent** используется в репликации слияния и использует функциональность, похожую на [sp_addpullsubscription_agent.](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)  
  
 Например, как правильно указать параметры безопасности при выполнения **sp_addmergepullsubscription_agent,** [см.](../../relational-databases/replication/create-a-pull-subscription.md)  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_1_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Выполнять **sp_addmergepullsubscription_agent**могут только члены **сисадмина** фиксированной роли сервера или **db_owner** фиксированной роли базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Создание подписки Pull](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Подписаться на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription &#40;&#41;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;&#41;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;&#41;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription&#41;&#40;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
