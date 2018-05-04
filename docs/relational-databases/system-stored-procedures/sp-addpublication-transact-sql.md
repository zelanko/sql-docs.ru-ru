---
title: sp_addpublication (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/17/2017
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
- sp_addpublication_TSQL
- sp_addpublication
helpviewer_keywords:
- sp_addpublication
ms.assetid: c7167ed1-2b7e-4824-b82b-65f4667c4407
caps.latest.revision: 69
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f0f667c71bd1e67b311aad2d8da93b48e605ca79
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spaddpublication-transact-sql"></a>sp_addpublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает моментальный снимок публикации транзакций. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addpublication [ @publication = ] 'publication'  
    [ , [ @taskid = ] tasked ]  
    [ , [ @restricted = ] 'restricted' ]  
    [ , [ @sync_method = ] 'sync_method' ]  
    [ , [ @repl_freq = ] 'repl_freq' ]  
    [ , [ @description = ] 'description' ]  
    [ , [ @status = ] 'status' ]  
    [ , [ @independent_agent = ] 'independent_agent' ]  
    [ , [ @immediate_sync = ] 'immediate_sync' ]  
    [ , [ @enabled_for_internet = ] 'enabled_for_internet' ]  
    [ , [ @allow_push = ] 'allow_push'  
    [ , [ @allow_pull = ] 'allow_pull' ]  
    [ , [ @allow_anonymous = ] 'allow_anonymous' ]  
    [ , [ @allow_sync_tran = ] 'allow_sync_tran' ]  
    [ , [ @autogen_sync_procs = ] 'autogen_sync_procs' ]  
    [ , [ @retention = ] retention ]  
    [ , [ @allow_queued_tran= ] 'allow_queued_updating' ]  
    [ , [ @snapshot_in_defaultfolder= ] 'snapshot_in_default_folder' ]  
    [ , [ @alt_snapshot_folder= ] 'alternate_snapshot_folder' ]  
    [ , [ @pre_snapshot_script= ] 'pre_snapshot_script' ]  
    [ , [ @post_snapshot_script= ] 'post_snapshot_script' ]  
    [ , [ @compress_snapshot= ] 'compress_snapshot' ]  
    [ , [ @ftp_address = ] 'ftp_address' ]  
    [ , [ @ftp_port= ] ftp_port ]  
    [ , [ @ftp_subdirectory = ] 'ftp_subdirectory' ]  
    [ , [ @ftp_login = ] 'ftp_login' ]  
    [ , [ @ftp_password = ] 'ftp_password' ]  
    [ , [ @allow_dts = ] 'allow_dts' ]  
    [ , [ @allow_subscription_copy = ] 'allow_subscription_copy' ]  
    [ , [ @conflict_policy = ] 'conflict_policy' ]  
    [ , [ @centralized_conflicts = ] 'centralized_conflicts' ]   
    [ , [ @conflict_retention = ] conflict_retention ]  
    [ , [ @queue_type = ] 'queue_type' ]  
    [ , [ @add_to_active_directory = ] 'add_to_active_directory' ]  
    [ , [ @logreader_job_name = ] 'logreader_agent_name' ]  
    [ , [ @qreader_job_name = ] 'queue_reader_agent_name' ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @allow_initialize_from_backup = ] 'allow_initialize_from_backup' ]  
    [ , [ @replicate_ddl = ] replicate_ddl ]  
    [ , [ @enabled_for_p2p = ] 'enabled_for_p2p' ]  
    [ , [ @publish_local_changes_only = ] 'publish_local_changes_only' ]  
    [ , [ @enabled_for_het_sub = ] 'enabled_for_het_sub' ]  
    [ , [ @p2p_conflictdetection = ] 'p2p_conflictdetection' ]  
    [ , [ @p2p_originator_id = ] p2p_originator_id  
    [ , [ @p2p_continue_onconflict = ] 'p2p_continue_onconflict'  
    [ , [ @allow_partition_switch = ] 'allow_partition_switch'  
    [ , [ @replicate_partition_switch = ]'replicate_partition_switch'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"***публикации***"**  
 Имя создаваемой публикации. *Публикация* — **sysname**, не имеет значения по умолчанию. В базе данных это имя должно быть уникальным.  
  
 [  **@taskid=**] *taskid*  
 Поддерживается только в целях обратной совместимости; Используйте [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md).  
  
 [  **@restricted=**] **"***ограниченных***"**  
 Поддерживается только в целях обратной совместимости; Используйте *default_access*.  
  
 [  **@sync_method=**] *«sync_method ***»**  
 Режим синхронизации. *значение свойства sync_method* — **nvarchar(13)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**native**|Производит выходные данные программы массового копирования всех таблиц. *Не поддерживается для издателей Oracle*.|  
|**character**|Производит выходные данные программы массового копирования всех таблиц в символьном режиме. *Для издателя Oracle* **символ** *допустимо только для репликации моментальных снимков*.|  
|**Параллельные**|Создает собственный программный вывод массового копирования всех таблиц, но не блокирует таблицы во время формирования моментальных снимков. Поддерживается только для публикаций транзакций. *Не поддерживается для издателей Oracle*.|  
|**Concurrent_c**|Создает символьный программный вывод массового копирования всех таблиц, но не блокирует таблицы во время формирования моментальных снимков. Поддерживается только для публикаций транзакций.|  
|**Моментальный снимок базы данных**|Производит выходные данные программы массового копирования всех таблиц в моментальном снимке базы данных. Моментальные снимки базы данных доступны не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).|  
|**символ моментального снимка базы данных**|Производит выходные данные программы массового копирования в символьном режиме всех таблиц в моментальном снимке базы данных. Моментальные снимки базы данных доступны не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).|  
|NULL (по умолчанию)|По умолчанию используется значение **собственного** для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей. Для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, по умолчанию используется значение **символ** при значение *repl_freq* — **моментального снимка** и **concurrent_c** для всех остальных случаях.|  
  
 [  **@repl_freq=**] **"***repl_freq***"**  
 Тип частоты репликации *repl_freq* — **nvarchar(10)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**непрерывные** (по умолчанию)|Издатель предоставляет выходные данные всех транзакций, записываемых в журнал. Для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, это необходимо, *sync_method* присвоить **concurrent_c**.|  
|**Моментальный снимок**|Издатель предоставляет только запланированные события синхронизации. Для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, это требует, *sync_method* присвоить **символ**.|  
  
 [  **@description=**] **"***описание***"**  
 Дополнительное описание публикации. *Описание* — **nvarchar(255)**, значение по умолчанию NULL.  
  
 [  **@status=**] **"***состояние***"**  
 Определяет, будут ли доступны данные публикации. *состояние* — **nvarchar(8)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Активный**|Публикация доступна подписчикам немедленно.|  
|**Неактивные** (по умолчанию)|Публикация не доступна для подписчиков при создании (они могут подписаться, но эти подписки не обрабатываются).|  
  
 *Не поддерживается для издателей Oracle*.  
  
 [  **@independent_agent=**] **"***independent_agent***"**  
 Показывает наличие изолированного агента распространителя для этой публикации. *independent_agent* — **nvarchar(5)**, значение по умолчанию FALSE. Если **true**, отсутствует для этой публикации изолированный агент распространителя. Если **false**, публикация использует общий агент распространителя, и каждой паре базы данных издателя базы данных/подписчика соответствует единственный общий агент.  
  
 [  **@immediate_sync=**] **"***immediate_synchronization***"**  
 Указывает, создаются ли для этой публикации файлы синхронизации при каждом запуске агента моментальных снимков. *immediate_synchronization* — **nvarchar(5)**, значение по умолчанию FALSE. Если **true**, файлы синхронизации создаются или повторно создаются при каждом запуске агента моментальных снимков. Подписчики могут получить файлы синхронизации немедленно, если агент моментальных снимков завершил работу до создания подписки. Новые подписки получают самые свежие файлы синхронизации, сформированные при последнем выполнении агента моментальных снимков. *independent_agent* должно быть **true** для *immediate_synchronization* быть **true**. Если **false**, файлы синхронизации создаются только в том случае, если имеются новые подписки. Необходимо вызвать [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) для каждой подписки при постепенном добавлении новой статьи к существующей публикации. Подписчики не могут получать файлы синхронизации после подписки, пока агенты моментальных снимков не будут запущены и не завершат работу.  
  
 [  **@enabled_for_internet=**] **"***enabled_for_internet***"**  
 Указывает, разрешена ли публикация через Интернет и можно ли использовать протокол FTP для передачи подписчику файлов моментальных снимков. *enabled_for_internet* — **nvarchar(5)**, значение по умолчанию FALSE. Если **true**, файлы синхронизации для публикации помещаются в каталог C:\Program Files\Microsoft SQL Server\MSSQL\MSSQL.x\Repldata\Ftp. Пользователь должен создать каталог Ftp.  
  
 [  **@allow_push=**] **"***allow_push***"**  
 Указывает, можно ли создать принудительные подписки для конкретной публикации. *allow_push* — **nvarchar(5)**, значение по умолчанию TRUE, разрешающее принудительные подписки на публикацию.  
  
 [  **@allow_pull=**] **"***allow_pull***"**  
 Указывает, можно ли создать подписки по запросу для конкретной публикации. *allow_pull* — **nvarchar(5)**, значение по умолчанию FALSE. Если **false**, подписки по запросу не разрешены для данной публикации.  
  
 [  **@allow_anonymous=**] **"***allow_anonymous***"**  
 Указывает, можно ли создать анонимные подписки для конкретной публикации. *allow_anonymous* — **nvarchar(5)**, значение по умолчанию FALSE. Если **true**, *immediate_synchronization* также должно быть присвоено **true**. Если **false**, анонимные подписки не разрешены для данной публикации.  
  
 [  **@allow_sync_tran=**] **"***allow_sync_tran***"**  
 Определяет, разрешены ли в публикации немедленно обновляемые подписки. *allow_sync_tran* — **nvarchar(5)**, значение по умолчанию FALSE. **значение true,** — *не поддерживается для издателей Oracle*.  
  
 [  **@autogen_sync_procs=**] **"***autogen_sync_procs***"**  
 Указывает, формируется ли хранимая процедура для синхронизации обновляемых подписок у издателя. *autogen_sync_procs* — **nvarchar(5)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**true**|Устанавливается автоматически, если включена обновляемая подписка.|  
|**false**|Устанавливается автоматически для издателей Oracle или если обновляемая подписка выключена.|  
|NULL (по умолчанию)|По умолчанию используется значение **true** при включении обновляемых подписок и к **false** если обновляемые подписки не включена.|  
  
> [!NOTE]  
>  Пользовательское значение для *autogen_sync_procs*будут переопределены в зависимости от значения, указанные для *allow_queued_tran* и *allow_sync_tran*.  
  
 [  **@retention=**] *хранения*  
 Срок хранения подписки в часах. *хранения* — **int**, значение по умолчанию 336 часов. Если подписка не активна в течение указанного периода, ее срок действия истекает, и она удаляется. Это значение может превышать максимальный срок хранения базы данных распространителя на издателе. Если **0**, известных подписок на публикацию никогда не истекал и удалить агент очистки подписки истек.  
  
 [  **@allow_queued_tran=** ] **"***allow_queued_updating***"**  
 Включает или отключает очередь изменений на подписчике, пока эти изменения не применятся на издателе. *allow_queued_updating* — **nvarchar(5)** значение по умолчанию FALSE. Если **false**, изменения на подписчике не помещаются в очередь. **значение true,** — *не поддерживается для издателей Oracle*.  
  
 [  **@snapshot_in_defaultfolder=** ] **"***snapshot_in_default_folder***"**  
 Указывает, хранятся ли файлы моментальных снимков в папке по умолчанию. *snapshot_in_default_folder* — **nvarchar(5)** значение по умолчанию TRUE. Если **true**, файлы моментальных снимков находятся в папке по умолчанию. Если **false**, файлы моментальных снимков хранятся в расположении, указанном в *alternate_snapshot_folder*. Другим местом может быть другой сервер, сетевой диск или съемный носитель (такой как компакт-диск или съемные диски). Файлы моментальных снимков можно также хранить на FTP-сайте, откуда подписчик позже может их получить. Обратите внимание, что этот параметр может иметь значение true и по-прежнему иметь место **@alt_snapshot_folder** параметра. Это сочетание размещает файлы моментальных снимков одновременно и в месте по умолчанию, и в альтернативном месте.  
  
 [  **@alt_snapshot_folder=** ] **"***alternate_snapshot_folder***"**  
 Указывает местоположение альтернативной папки для моментального снимка. *alternate_snapshot_folder* — **nvarchar(255)** значение по умолчанию NULL.  
  
 [  **@pre_snapshot_script=** ] **"***pre_snapshot_script***"**  
 Задает указатель **.sql** расположение файла. *pre_snapshot_script* — **nvarchar(255),** значение по умолчанию NULL. Если моментальный снимок применяется на подписчике, то агент распространителя запускает предварительный скрипт моментального снимка до выполнения скриптов реплицируемых объектов. Скрипт выполняется в контексте безопасности, использованном для агента распространителя при подключении к базе данных подписки.  
  
 [  **@post_snapshot_script=** ] **"***post_snapshot_script***"**  
 Задает указатель **.sql** расположение файла. *post_snapshot_script* — **nvarchar(255)**, значение по умолчанию NULL. Агент распространителя запускает заключительный скрипт после применения скриптов и данных всех реплицируемых объектов во время первоначальной синхронизации. Скрипт выполняется в контексте безопасности, использованном для агента распространителя при подключении к базе данных подписки.  
  
 [  **@compress_snapshot=** ] **"***compress_snapshot***"**  
 Указывает, что моментальный снимок, записываемый **@alt_snapshot_folder** сжатия в [!INCLUDE[msCoName](../../includes/msconame-md.md)] формате CAB. *compress_snapshot* — **nvarchar(5)**, значение по умолчанию FALSE. **false** указывает, что моментальный снимок не сжимается; **true** указывает, что моментальный снимок будет сжат. Нельзя сжать моментальные снимки размером более 2 гигабайт (ГБ). Сжатые файлы моментальных снимков распаковываются в расположении запуска агента распространителя. Со сжатыми моментальными снимками обычно используются подписки по запросу, чтобы сжатые файлы распаковывались на подписчике. Моментальный снимок в папке по умолчанию сжать нельзя.  
  
 [  **@ftp_address =** ] **"***ftp_address***"**  
 Сетевой адрес службы FTP распространителя. *ftp_address* — **sysname**, значение по умолчанию NULL. Указывает расположение файлов моментальных снимков публикаций для агента распространителя или агента слияния подписчика. Поскольку это свойство хранится для каждой публикации, каждая публикация может иметь разные *ftp_address*. Публикация должна поддерживать распространение моментальных снимков с помощью протокола FTP.  
  
 [  **@ftp_port=** ] *ftp_port*  
 Номер порта службы FTP распространителя. *ftp_port* — **int**, значение по умолчанию 21. Указывает расположение файлов моментальных снимков публикации для агента распространителя или агента слияния подписчика. Поскольку это свойство хранится для каждой публикации, каждая публикация может иметь свой собственный *ftp_port*.  
  
 [  **@ftp_subdirectory =** ] **"***ftp_subdirectory***"**  
 Указывает расположение файлов моментальных снимков для агента распространителя или агента слияния данного подписчика, если публикация поддерживает распространение моментальных снимков с помощью FTP. *ftp_subdirectory* — **nvarchar(255)**, значение по умолчанию NULL. Поскольку это свойство хранится для каждой публикации, каждая публикация может иметь свой собственный *ftp_subdirctory* или выбрать, чтобы не подкаталога, указав значение NULL.  
  
 [  **@ftp_login =** ] **"***ftp_login***"**  
 Имя пользователя, используемое для подключения к службе FTP. *ftp_login* — **sysname**, значение по умолчанию ANONYMOUS.  
  
 [  **@ftp_password =** ] **"***ftp_password***"**  
 Пароль пользователя, используемый для подключения к службе FTP. *ftp_password* — **sysname**, значение по умолчанию NULL.  
  
 [  **@allow_dts =** ] **"***allow_dts***"**  
 Указывает, что в публикации разрешены преобразования данных. При создании подписки можно указать пакет служб DTS. *allow_transformable_subscriptions* — **nvarchar(5)** значение по умолчанию FALSE, не разрешающее преобразования DTS. Когда *allow_dts* имеет значение true, *sync_method* должно иметь значение **символ** или **concurrent_c**.  
  
 **значение true,** — *не поддерживается для издателей Oracle*.  
  
 [  **@allow_subscription_copy =** ] **"***allow_subscription_copy***"**  
 Разрешает или запрещает возможность копирования баз данных подписки, подписанных на эту публикацию. *allow_subscription_copy* —**nvarchar(5)**, значение по умолчанию FALSE.  
  
 [  **@conflict_policy =** ] **"***conflict_policy***"**  
 Задает политику устранения конфликтов при обновлении подписчика посредством очередей. *conflict_policy* — **nvarchar(100)** значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**pub wins**|Разрешение конфликта в пользу издателя.|  
|**Sub reinit**|Повторная инициализация подписки.|  
|**Sub wins**|Разрешение конфликта в пользу подписчика.|  
|NULL (по умолчанию)|Если значение NULL и публикация является публикацией моментального снимка, политикой по умолчанию становится **sub reinit**. Если значение NULL и публикация не является публикацией моментального снимка, политикой по умолчанию становится **pub wins**.|  
  
 *Не поддерживается для издателей Oracle*.  
  
 [  **@centralized_conflicts =** ] **"***centralized_conflicts***"**  
 Определяет, хранятся ли на издателе конфликтные записи. *centralized_conflicts* — **nvarchar(5)**, значение по умолчанию TRUE. Если **true**, конфликтующие записи хранятся на издателе. Если **false**, конфликтующие записи хранятся как на издателе и на подписчике, вызвавшем конфликт. *Не поддерживается для издателей Oracle*.  
  
 [  **@conflict_retention =** ] *conflict_retention*  
 Задает срок хранения конфликтных записей в днях. Время, в течение которого метаданные конфликта хранятся для одноранговой транзакционной репликации и подписок, обновляемых посредством очереди. *conflict_retention* — **int**, значение по умолчанию 14. *Не поддерживается для издателей Oracle*.  
  
 [  **@queue_type =** ] **"***queue_type***"**  
 Задает используемый тип очереди. *queue_type* — **nvarchar(10)**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**sql**|Для хранения транзакций используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|NULL (по умолчанию)|По умолчанию используется значение **sql**, которая указывает использование [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения транзакций.|  
  
> [!NOTE]  
>  Поддержка использования [!INCLUDE[msCoName](../../includes/msconame-md.md)] очереди сообщений прекратила работу. При указании значения **msmq** вызовет предупреждение, и репликация будет автоматически присвоено значение **sql**.  
  
 *Не поддерживается для издателей Oracle*.  
  
 [  **@add_to_active_directory =** ] **"*** Добавить**_**to_active_directory ***"**  
 Этот аргумент устарел и поддерживается только для обратной совместимости скриптов. Больше нельзя добавлять данные публикации в службу [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory.  
  
 [  **@logreader_job_name =** ] **"***logreader_agent_name***"**  
 Имя существующего задания агента. *logreader_agent_name* — **sysname**, значение по умолчанию NULL. Он указывается только в том случае, если агент чтения журнала будет использовать существующее задание, а не создающееся заново.  
  
 [  **@qreader_job_name =** ] **"***queue_reader_agent_name***"**  
 Имя существующего задания агента. *queue_reader_agent_name* — **sysname**, значение по умолчанию NULL. Он указывается, только если агент чтения очереди будет использовать существующее задание, а не создающееся заново.  
  
 [  **@publisher =** ] **"***издатель***"**  
 Задает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать при добавлении публикации к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
 [  **@allow_initialize_from_backup =** ] **"***allow_initialize_from_backup***"**  
 Показывает, может ли подписчик инициализировать подписку на эту публикацию из резервной копии, а не из исходного моментального снимка. *allow_initialize_from_backup* — **nvarchar(5)**, и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**true**|Включает инициализацию из резервной копии.|  
|**false**|Отключает инициализацию из резервной копии.|  
|NULL (по умолчанию)|По умолчанию используется значение **true** для публикации в топологии репликации для одноранговых и **false** для всех публикаций.|  
  
 Дополнительные сведения см. в статье [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
> [!WARNING]  
>  Чтобы предотвратить отсутствие данных подписчика, при использовании процедуры **sp_addpublication** с `@allow_initialize_from_backup = N'true'`всегда используйте `@immediate_sync = N'true'`.  
  
 [  **@replicate_ddl =** ] *replicate_ddl*  
 Указывает, поддерживается ли для публикации репликация схемы. *replicate_ddl* — **int**, значение по умолчанию **1** для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей и **0** для отличного[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей. **1** указывает, что инструкции языка DDL для определения данных, выполняемые на издателе, реплицируются, а **0** указывает, что инструкции DDL не реплицируются. *Репликация схемы не поддерживается для издателей Oracle.* Дополнительные сведения см. в статье [Внесение изменений в схемы баз данных публикации](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
 *@replicate_ddl* Учитывается, когда инструкция DDL добавляет столбец. *@replicate_ddl* Параметр учитывается, если инструкция DDL изменяет или удаляет столбец, по следующим причинам.  
  
-   При удалении столбца sysarticlecolumns должны обновляться во избежание новые инструкции DML, в том числе удаленный столбец, что приведет к завершению работы агента распространителя. *@replicate_ddl* Параметр учитывается, поскольку репликация всегда должна реплицировать изменения схемы.  
  
-   Когда в столбец вносится изменение, исходный тип данных или возможность допустимости значения NULL может измениться, в результате чего инструкции DML будут содержать значение, которое может быть несовместимым с таблицей на подписчике. Такие инструкции DML могут привести к тому, что работа агента распространителя завершится ошибкой. *@replicate_ddl* Параметр учитывается, поскольку репликация всегда должна реплицировать изменения схемы.  
  
-   Когда инструкция DDL добавляет новый столбец, sysarticlecolumns не включает новый столбец. Инструкции DML не будут пытаться реплицировать данные для этого нового столбца. Этот параметр учитывается потому, что допустимо как выполнение, так и не выполнение репликации DDL.  
  
 [  **@enabled_for_p2p =** ] **"***enabled_for_p2p***"**  
 Разрешает использование публикации в одноранговой топологии репликации. *enabled_for_p2p* — **nvarchar(5)**, значение по умолчанию FALSE. **значение true,** указывает, что публикация поддерживает — одноранговая репликация. При задании *enabled_for_p2p* для **true**, применяются следующие ограничения:  
  
-   *allow_anonymous* должно быть **false**.  
  
-   *allow_dts* должно быть **false**.  
  
-   *allow_initialize_from_backup* должно быть **true**.  
  
-   *allow_queued_tran* должно быть **false**.  
  
-   *allow_sync_tran* должно быть **false**.  
  
-   *conflict_policy* должно быть **false**.  
  
-   *independent_agent* должно быть **true**.  
  
-   *repl_freq* должно быть **непрерывного**.  
  
-   *replicate_ddl* должно быть **1**.  
  
 Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 [  **@publish_local_changes_only =** ] **"***publish_local_changes_only***"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@enabled_for_het_sub=** ] **"***enabled_for_het_sub***"**  
 Позволяет публикации поддерживать подписчиков, не являющихся подписчиками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *enabled_for_het_sub* — **nvarchar(5)** со значением по умолчанию FALSE. Значение **true** означает, что публикация поддерживает отличных[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков. Когда *enabled_for_het_sub* — **true**, применяются следующие ограничения:  
  
-   *allow_initialize_from_backup* должно быть **false**.  
  
-   *allow_push* должно быть **true**.  
  
-   *allow_queued_tran* должно быть **false**.  
  
-   *allow_subscription_copy* должно быть **false**.  
  
-   *allow_sync_tran* должно быть **false**.  
  
-   *autogen_sync_procs* должно быть **false**.  
  
-   *conflict_policy* должен иметь значение NULL.  
  
-   *enabled_for_internet* должно быть **false**.  
  
-   *enabled_for_p2p* должно быть **false**.  
  
-   *ftp_address* должен иметь значение NULL.  
  
-   *ftp_subdirectory* должен иметь значение NULL.  
  
-   *ftp_password* должен иметь значение NULL.  
  
-   *pre_snapshot_script* должен иметь значение NULL.  
  
-   *post_snapshot_script* должен иметь значение NULL.  
  
-   *replicate_ddl* должно быть равно 0.  
  
-   *qreader_job_name* должен иметь значение NULL.  
  
-   *queue_type* должен иметь значение NULL.  
  
-   *значение свойства sync_method* не может быть **собственного** или **параллельных**.  
  
 Дополнительные сведения см. в разделе [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 [  **@p2p_conflictdetection=** ] **"***p2p_conflictdetection***"**  
 Разрешает агенту распространителя обнаруживать конфликты, если публикация поддерживает одноранговую репликацию. *p2p_conflictdetection* — **nvarchar(5)** со значением по умолчанию TRUE. Дополнительные сведения см. в разделе [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
 [  **@p2p_originator_id=** ] *p2p_originator_id*  
 Указывает идентификатор в одноранговой топологии. *p2p_originator_id* — **int**, значение по умолчанию NULL. Этот идентификатор используется для обнаружения конфликтов, если *p2p_conflictdetection* имеет значение TRUE. Укажите положительное, ненулевое значение идентификатора, которое никогда не использовалось в топологии. Список идентификаторов, которые уже были использованы, выполнение [sp_help_peerconflictdetection](../../relational-databases/system-stored-procedures/sp-help-peerconflictdetection-transact-sql.md).  
  
 [  **@p2p_continue_onconflict=** ] **"***p2p_continue_onconflict***"**  
 Определяет, продолжает ли агент распространителя обрабатывать изменения после обнаружения конфликта. *p2p_continue_onconflict* — **nvarchar(5)** со значением по умолчанию FALSE.  
  
> [!CAUTION]  
>  Рекомендуется использовать значение по умолчанию FALSE. Если присвоить этому аргументу значение TRUE, агент распространителя будет пытаться обеспечить конвергентность данных в топологии, применяя конфликтующую строку из узла с наибольшим значением идентификатора инициатора. Этот метод не гарантирует конвергенции. После обнаружения конфликта следует убедиться, что топология остается согласованной. Дополнительные сведения см. в подразделе «Обработка конфликтов» раздела [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
 [  **@allow_partition_switch=** ] **"***allow_partition_switch***"**  
 Указывает, могут ли инструкции ALTER TABLE…SWITCH выполняться по отношению к опубликованной базе данных. *allow_partition_switch* — **nvarchar(5)** со значением по умолчанию FALSE. Дополнительные сведения см. в статье [Replicate Partitioned Tables and Indexes](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md) (Репликация секционированных таблиц и индексов).  
  
 [  **@replicate_partition_switch=** ] **"***replicate_partition_switch***"**  
 Указывает, должны ли инструкции ALTER TABLE…SWITCH, которые выполняются по отношению к опубликованной базе данных, реплицироваться на подписчики. *replicate_partition_switch* — **nvarchar(5)** со значением по умолчанию FALSE. Этот параметр действителен, только если *allow_partition_switch* имеет значение TRUE.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_addpublication** используется в репликации моментальных снимков и репликации транзакций.  
  
 Если несколько существующих публикаций публикуют тот же объект базы данных, только для публикаций с *replicate_ddl* значение **1** будут реплицировать инструкции ALTER TABLE, ALTER VIEW, инструкция ALTER PROCEDURE, ALTER FUNCTION и Инструкции ALTER TRIGGER DDL. Однако инструкция ALTER TABLE DROP COLUMN DDL будет реплицирована всеми публикациями, публикующими столбец, который был удален.  
  
 С включенной репликацией DDL (*replicate_ddl* = **1**) для публикации, чтобы произвести не относящиеся к репликации изменения публикации, [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) вначале необходимо выполнить для установки *replicate_ddl* для **0**. После выполнения нереплицируемых инструкций DDL, [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) может выполняться для включения репликации DDL.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addpublication-transa_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_addpublication**. Имена входа, используемые для проверки подлинности Windows, должны иметь учетные записи пользователей в базе данных, представляющие их учетные записи пользователей Windows. Учетной записи пользователя, представляющей группу Windows, недостаточно.  
  
## <a name="see-also"></a>См. также  
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_droppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [sp_helppublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
