---
description: sp_addmergepublication (Transact-SQL)
title: sp_addmergepublication (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepublication
- sp_addmergepublication_TSQL
helpviewer_keywords:
- sp_addmergepublication
ms.assetid: 28a629a1-7374-4614-9b04-279d290a942a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 346b335063238d118412e8a2951ced67ed685756
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489646"
---
# <a name="sp_addmergepublication-transact-sql"></a>sp_addmergepublication (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Создает новую публикацию слиянием. Эта хранимая процедура выполняется на издателе в публикуемой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmergepublication [ @publication = ] 'publication'   
    [ , [ @description = ] 'description'   
    [ , [ @retention = ] retention ]   
    [ , [ @sync_mode = ] 'sync_mode' ]   
    [ , [ @allow_push = ] 'allow_push' ]   
    [ , [ @allow_pull = ] 'allow_pull' ]   
    [ , [ @allow_anonymous = ] 'allow_anonymous' ]   
    [ , [ @enabled_for_internet = ] 'enabled_for_internet' ]   
    [ , [ @centralized_conflicts = ] 'centralized_conflicts' ]   
    [ , [ @dynamic_filters = ] 'dynamic_filters' ]   
    [ , [ @snapshot_in_defaultfolder = ] 'snapshot_in_default_folder' ]   
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]   
    [ , [ @pre_snapshot_script = ] 'pre_snapshot_script' ]   
    [ , [ @post_snapshot_script = ] 'post_snapshot_script' ]   
    [ , [ @compress_snapshot = ] 'compress_snapshot' ]   
    [ , [ @ftp_address = ] 'ftp_address' ]   
    [ , [ @ftp_port = ] ftp_port ]   
    [ , [ @ftp_subdirectory = ] 'ftp_subdirectory' ]   
    [ , [ @ftp_login = ] 'ftp_login' ]   
    [ , [ @ftp_password = ] 'ftp_password' ]   
    [ , [ @conflict_retention = ] conflict_retention ]   
    [ , [ @keep_partition_changes = ] 'keep_partition_changes' ]   
    [ , [ @allow_subscription_copy = ] 'allow_subscription_copy' ]   
    [ , [ @allow_synctoalternate = ] 'allow_synctoalternate' ]   
    [ , [ @validate_subscriber_info = ] 'validate_subscriber_info' ]   
    [ , [ @add_to_active_directory = ] 'add_to_active_directory' ]   
    [ , [ @max_concurrent_merge = ] maximum_concurrent_merge ]   
    [ , [ @max_concurrent_dynamic_snapshots = ] max_concurrent_dynamic_snapshots ]  
    [ , [ @use_partition_groups = ] 'use_partition_groups' ]  
    [ , [ @publication_compatibility_level = ] 'backward_comp_level' ]  
    [ , [ @replicate_ddl = ] replicate_ddl ]  
    [ , [ @allow_subscriber_initiated_snapshot = ] 'allow_subscriber_initiated_snapshot' ]   
    [ , [ @allow_web_synchronization = ] 'allow_web_synchronization' ]   
    [ , [ @web_synchronization_url = ] 'web_synchronization_url' ]  
    [ , [ @allow_partition_realignment = ] 'allow_partition_realignment' ]  
    [ , [ @retention_period_unit = ] 'retention_period_unit' ]  
    [ , [ @generation_leveling_threshold = ] generation_leveling_threshold ]  
    [ , [ @automatic_reinitialization_policy = ] automatic_reinitialization_policy ]  
    [ , [ @conflict_logging = ] 'conflict_logging' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` Имя создаваемой публикации слиянием. Аргумент *publication* имеет тип **sysname**, не имеет значения по умолчанию и не должен быть ключевым словом ALL. Имя публикации в пределах базы данных должно быть уникальным.  
  
`[ @description = ] 'description'` Описание публикации. *Description* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  
  
`[ @retention = ] retention` Срок хранения, в единицах периода хранения, для которого необходимо сохранить изменения для данной *публикации*. параметр *retention* имеет **тип int**и значение по умолчанию 14 единиц. Единицы срока хранения определяются *retention_period_unit*. Если подписка не синхронизирована в течение срока хранения, а ожидающие обработки изменения, которые были бы получены, удалены операцией очистки на стороне распространителя, срок действия подписки истекает, и подписка должна быть создана заново. Максимально допустимым сроком хранения является количество дней от 31 декабря 9999 года до текущей даты.  
  
> [!NOTE]  
>  Срок хранения для публикации слиянием предусматривает наличие 24-часового льготного срока для согласования работы подписчиков в разных часовых поясах. Например, если установить срок хранения продолжительностью в один день, то действительный срок хранения будет равен 48 часам.  
  
`[ @sync_mode = ] 'sync_mode'` Режим первоначальной синхронизации подписчиков с публикацией. *sync_mode* имеет тип **nvarchar (10)** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**native** (по умолчанию)|Производит выходные данные программы массового копирования всех таблиц.|  
|**символов**|Производит выходные данные программы массового копирования всех таблиц в символьном режиме. Требуется для поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] и подписчиков, отличных от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
  
`[ @allow_push = ] 'allow_push'` Указывает, могут ли быть созданы принудительные подписки для данной публикации. *allow_push* имеет тип **nvarchar (5)** и значение по умолчанию true, которое разрешает принудительные подписки на публикацию.  
  
`[ @allow_pull = ] 'allow_pull'` Указывает, могут ли быть созданы подписки по запросу для данной публикации. *allow_pull* имеет тип **nvarchar (5)** и значение по умолчанию true, которое разрешает подписки по запросу на публикацию. Для поддержки подписчиков необходимо указать значение true [!INCLUDE[ssEW](../../includes/ssew-md.md)] .  
  
`[ @allow_anonymous = ] 'allow_anonymous'` Указывает, могут ли быть созданы анонимные подписки для данной публикации. *allow_anonymous* имеет тип **nvarchar (5)** и значение по умолчанию true, которое разрешает анонимные подписки на публикацию. Для поддержки [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков необходимо указать **значение true**.  
  
`[ @enabled_for_internet = ] 'enabled_for_internet'` Указывает, включена ли публикация в Интернете, и определяет, может ли использоваться протокол FTP для пересылки файлов моментальных снимков на подписчик. *enabled_for_internet* имеет тип **nvarchar (5)** и значение по умолчанию false. Если задано **значение true**, файлы синхронизации для публикации помещаются в каталог C:\PROGRAM Files\Microsoft SQL сервер\мсскл\мсскл.кс\реплдата\фтп. Пользователь должен создать каталог Ftp. Если задано **значение false**, публикация не включена для доступа к Интернету.  
  
`[ @centralized_conflicts = ] 'centralized_conflicts'` Этот параметр является устаревшим и поддерживается только для обратной совместимости скриптов. Используйте *conflict_logging* , чтобы указать расположение, в котором хранятся конфликтующие записи.  
  
`[ @dynamic_filters = ] 'dynamic_filters'` Позволяет публикации слиянием использовать параметризованные фильтры строк. *dynamic_filters* имеет тип **nvarchar (5)** и значение по умолчанию false.  
  
> [!NOTE]  
>  Вместо задания этого параметра следует позволить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически определять, используются ли параметризованные фильтры строк. Если для *dynamic_filters*указано значение **true** , необходимо определить параметризованный фильтр строк для статьи. Дополнительные сведения см. в статье [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
`[ @snapshot_in_defaultfolder = ] 'snapshot_in_default_folder'` Указывает, хранятся ли файлы моментальных снимков в папке по умолчанию. *snapshot_in_default_folder* имеет тип **nvarchar (5)** и значение по умолчанию true. Если **значение — true**, файлы моментальных снимков можно найти в папке по умолчанию. Если **значение равно false**, файлы моментальных снимков будут храниться в альтернативном расположении, заданном параметром *alternate_snapshot_folder*. Это место может находиться на другом сервере, на сетевом диске или на съемном носителе (например на CD-ROM или на съемном диске). Файлы моментальных снимков могут также сохраняться с помощью протокола передачи файлов на FTP-сайте, чтобы подписчик мог извлечь эти файлы позже. Обратите внимание, что этот параметр может иметь значение true и по-прежнему иметь расположение, заданное *alt_snapshot_folder*. Это сочетание размещает файлы моментальных снимков одновременно и в месте по умолчанию, и в альтернативном месте.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'` Указывает расположение альтернативной папки для моментального снимка. *alternate_snapshot_folder* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  
  
`[ @pre_snapshot_script = ] 'pre_snapshot_script'` Задает указатель на расположение файла **SQL** . *pre_snapshot_script* имеет тип **nvarchar (255)** и значение по умолчанию NULL. При применении моментального снимка на подписчике агент слияния выполняет скрипт до моментального снимка перед выполнением скриптов объектов репликации. Скрипт выполняется в контексте безопасности, используемом агентом слияния при подключении к базе данных подписки. Скрипты, предшествующие моментальному снимку, не выполняются на [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиках.  
  
`[ @post_snapshot_script = ] 'post_snapshot_script'` Задает указатель на расположение файла **SQL** . *post_snapshot_script* имеет тип **nvarchar (255)** и значение по умолчанию NULL. Агент слияния выполняет скрипт после моментального снимка после того, как во время начальной синхронизации будут применены скрипты и данные всех других объектов репликации. Скрипт выполняется в контексте безопасности, используемом агентом слияния при подключении к базе данных подписки. Скрипты, выполняемые после моментального снимка, не выполняются на [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиках.  
  
`[ @compress_snapshot = ] 'compress_snapshot'`Указывает, что моментальный снимок, записываемый в ** \@ alt_snapshot_folder** расположение, должен быть сжат в [!INCLUDE[msCoName](../../includes/msconame-md.md)] формате CAB. *compress_snapshot* имеет тип **nvarchar (5)** и значение по умолчанию false. **значение false** указывает, что моментальный снимок не будет сжиматься. **значение true** указывает, что моментальный снимок должен быть сжат. Файлы моментальных снимков, превышающие 2 ГБ, не могут быть сжаты. Сжатые файлы моментальных снимков распаковываются в том месте, в котором выполняется агент слияния; подписки по запросу обычно используются со сжатыми моментальными снимками, так что соответствующие файлы распаковываются на подписчике. Моментальный снимок в папке по умолчанию сжать нельзя. Для поддержки [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков необходимо указать **значение false**.  
  
`[ @ftp_address = ] 'ftp_address'` Сетевой адрес службы FTP для распространителя. Аргумент *ftp_address* имеет тип **sysname**и значение по умолчанию NULL. Указывается расположение файлов моментальных снимков публикаций, откуда их выбирает агент слияния подписчика. Так как это свойство хранится для каждой публикации, каждая публикация может иметь разные *ftp_address*. Публикация должна поддерживать распространение моментальных снимков с помощью протокола FTP.  
  
`[ @ftp_port = ] ftp_port` Номер порта службы FTP для распространителя. *ftp_port* имеет **тип int**и значение по умолчанию 21. Указывается расположение файлов моментальных снимков публикаций, откуда их выбирает агент слияния подписчика. Так как это свойство хранится для каждой публикации, каждая публикация может иметь собственный *ftp_port*.  
  
`[ @ftp_subdirectory = ] 'ftp_subdirectory'` Указывает, где будут доступны файлы моментальных снимков для агент слияния подписчика, если публикация поддерживает распространение моментальных снимков с помощью FTP. *ftp_subdirectory* имеет тип **nvarchar (255)** и значение по умолчанию NULL. Так как это свойство хранится для каждой публикации, каждая публикация может иметь собственный *ftp_subdirctory* или не иметь подкаталога, обозначенного значением NULL.  
  
 При предварительном формировании моментальных снимков для публикаций при помощи параметризованных фильтров необходимо, чтобы моментальные снимки данных для каждой секции подписчика находились в своих папках. Структура каталога для предварительно формируемых при помощи FTP моментальных снимков должна иметь следующий вид:  
  
 *alternate_snapshot_folder*\фтп \\ *publisher_publicationDB_publication* \\ *PartitionID*.  
  
> [!NOTE]  
>  Указанные выше значения, выделенные курсивом, зависят от характеристик публикации и секции подписчика.  
  
`[ @ftp_login = ] 'ftp_login'` Имя пользователя, используемое для подключения к службе FTP. Аргумент *ftp_login* имеет тип **sysname**и значение по умолчанию Anonymous.  
  
`[ @ftp_password = ] 'ftp_password'` Пароль пользователя, используемый для подключения к службе FTP. Аргумент *ftp_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли.  
  
`[ @conflict_retention = ] conflict_retention` Указывает срок хранения (в днях), в течение которого сохраняются конфликты. *conflict_retention* имеет **тип int**и значение по умолчанию 14 дней, по истечении которого конфликтующая строка удаляется из таблицы конфликтов.  
  
`[ @keep_partition_changes = ] 'keep_partition_changes'` Указывает, следует ли включить оптимизацию изменения секций, если предварительно вычисленные секции использовать нельзя. *keep_partition_changes* имеет тип **nvarchar (5)** и значение по умолчанию true. **значение false** означает, что изменения секций не оптимизированы, и если предварительно вычисленные секции не используются, то при изменении данных в секции будут проверяться секции, отправленные всем подписчикам. **значение true** означает, что изменения секций оптимизированы, и затрагиваются только подписчики, имеющие строки в измененных секциях. При использовании предварительно вычисленных секций задайте для *use_partition_groups* **значение true** , а для параметра *keep_partition_changes* — **значение false**. Дополнительные сведения см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
> [!NOTE]  
>  Если для *keep_partition_changes*указано значение **true** , укажите значение **1** для параметра агент моментальных снимков параметр **-MaxNetworkOptimization значение**. Дополнительные сведения об этом параметре см. в разделе [Replication агент моментальных снимков](../../relational-databases/replication/agents/replication-snapshot-agent.md). Дополнительные сведения об указании параметров агента см. в разделе [Администрирование агента репликации](../../relational-databases/replication/agents/replication-agent-administration.md).  
  
 Для [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков *keep_partition_changes* необходимо задать значение true, чтобы гарантировать правильное распространение операций удаления. При установке значения false подписчик может получить больше строк, чем ожидается.  
  
`[ @allow_subscription_copy = ] 'allow_subscription_copy'` Включает или отключает возможность копирования баз данных подписки, подписанных на эту публикацию. *allow_subscription_copy* имеет тип **nvarchar (5)** и значение по умолчанию false. Размер копируемой базы данных подписки должен быть меньше 2 ГБ.  
  
`[ @allow_synctoalternate = ] 'allow_synctoalternate'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @validate_subscriber_info = ] 'validate_subscriber_info'` Содержит список функций, которые используются для определения секции подписчика опубликованных данных при использовании параметризованных фильтров строк. *validate_subscriber_info* имеет тип **nvarchar (500)** и значение по умолчанию NULL. Эти данные используются агентом слияния для проверки секций подписчиков. Например, если в параметризованном фильтре строк используется [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) , параметр должен иметь значение `@validate_subscriber_info=N'SUSER_SNAME()'` .  
  
> [!NOTE]  
>  Вместо задания этого параметра позвольте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически определять критерий фильтрации.  
  
`[ @add_to_active_directory = ] 'add_to_active_directory'` Этот параметр является устаревшим и поддерживается только для обратной совместимости скриптов. Больше нельзя добавлять данные публикации в службу [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory.  
  
`[ @max_concurrent_merge = ] maximum_concurrent_merge` Максимальное количество одновременных процессов слияния. *maximum_concurrent_merge* имеет **тип int** и значение по умолчанию 0. Значение **0** для этого свойства означает отсутствие ограничения на количество одновременных процессов слияния, выполняемых в данный момент времени. Это свойство устанавливает предельное значение числа процессов слияния, которые могут одновременно выполняться на публикации слиянием. Если в расписании задано одновременное выполнение большего числа процессов слияния, чем указанное значение, лишние задания будут поставлены в очередь, где они будут ожидать завершения одного из одновременно выполняющихся процессов слияния.  
  
`[ @max_concurrent_dynamic_snapshots = ] max_concurrent_dynamic_snapshots` Максимальное число сеансов агент моментальных снимков, которые могут выполняться одновременно для создания моментальных снимков отфильтрованных данных для секций подписчика. *maximum_concurrent_dynamic_snapshots* имеет **тип int** и значение по умолчанию 0. Если значение **равно 0**, количество сеансов моментальных снимков не ограничено. Если на одно и то же время назначено больше процессов моментальных снимков, чем позволяет указанное значение, лишние задачи будут помещены в очередь до завершения создания текущего моментального снимка.  
  
`[ @use_partition_groups = ] 'use_partition_groups'` Указывает, что для оптимизации процесса синхронизации должны использоваться предварительно вычисленные секции. *use_partition_groups* имеет тип **nvarchar (5)** и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**true**|Публикация использует предварительно вычисляемые секции.|  
|**false**|Публикация не использует предварительно вычисляемые секции.|  
|NULL (по умолчанию)|Стратегию секционирования выбирает система.|  
  
 По умолчанию используются предварительно вычисляемые секции. Чтобы избежать использования предварительно вычисленных секций, *use_partition_groups* необходимо задать значение **false**. При задании NULL система решает, могут ли использоваться предварительно вычисляемые секции. Если предварительно вычисленные секции не могут быть использованы, это значение будет считаться **ложным** без создания ошибок. В таких случаях *keep_partition_changes* может иметь значение **true** , чтобы обеспечить некоторую оптимизацию. Дополнительные сведения см. в разделах [параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md) и [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисленных секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
`[ @publication_compatibility_level = ] backward_comp_level` Указывает обратную совместимость публикации. *backward_comp_level* имеет тип **nvarchar (6)** и может принимать одно из следующих значений:  
  
|Значение|Версия|  
|-----------|-------------|  
|**90RTM**|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|  
|**100RTM**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
  
`[ @replicate_ddl = ] replicate_ddl` Указывает, поддерживается ли репликация схемы для публикации. *replicate_ddl* имеет **тип int**и значение по умолчанию 1. **1** указывает, что инструкции языка описания данных DDL, выполняемые на издателе, реплицируются, а **0** означает, что инструкции DDL не реплицируются. Дополнительные сведения см. в статье [Внесение изменений в схемы баз данных публикации](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
 Параметр * \@ replicate_ddl* учитывается, когда инструкция DDL добавляет столбец. Параметр * \@ replicate_ddl* игнорируется, если инструкция DDL изменяет или удаляет столбец по следующим причинам.  
  
-   При удалении столбца столбцы sysarticlecolumns должны обновляться, чтобы новые инструкции DML не включали удаленный столбец, из-за чего работа агента распространителя завершилась бы ошибкой. Параметр * \@ replicate_ddl* игнорируется, так как репликация должна всегда реплицировать изменения схемы.  
  
-   Когда в столбец вносится изменение, исходный тип данных или возможность допустимости значения NULL может измениться, в результате чего инструкции DML будут содержать значение, которое может быть несовместимым с таблицей на подписчике. Такие инструкции DML могут привести к тому, что работа агента распространителя завершится ошибкой. Параметр * \@ replicate_ddl* игнорируется, так как репликация должна всегда реплицировать изменения схемы.  
  
-   Когда инструкция DDL добавляет новый столбец, в столбцах sysarticlecolumns этого нового столбца нет. Инструкции DML не будут пытаться реплицировать данные для этого нового столбца. Этот параметр учитывается потому, что допустимо как выполнение, так и не выполнение репликации DDL.  
  
`[ @allow_subscriber_initiated_snapshot = ] 'allow_subscriber_initiated_snapshot'` Указывает, могут ли подписчики на эту публикацию инициировать процесс создания моментального снимка для создания отфильтрованного моментального снимка для их секции данных. *allow_subscriber_initiated_snapshot* имеет тип **nvarchar (5)** и значение по умолчанию false. **значение true** указывает, что подписчики могут инициировать процесс создания моментального снимка.  
  
`[ @allow_web_synchronization = ] 'allow_web_synchronization'` Указывает, включена ли публикация для веб-синхронизации. *allow_web_synchronization* имеет тип **nvarchar (5)** и значение по умолчанию false. **значение true** указывает, что подписки на эту публикацию можно СИНХРОНИЗИРОВАТЬ по протоколу HTTPS. Дополнительные сведения см. в статье [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md). Для поддержки [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков необходимо указать **значение true**.  
  
`[ @web_synchronization_url = ] 'web_synchronization_url'` Указывает значение по умолчанию для URL-адреса в Интернете, используемого для синхронизации с Интернетом. *web_synchronization_url i* **nvarchar (500)** и значение по умолчанию NULL. Определяет URL-адрес в Интернете по умолчанию, если он не задан явно при выполнении [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) .  
  
`[ @allow_partition_realignment = ] 'allow_partition_realignment'` Определяет, отправляются ли операции удаления на подписчик, когда изменение строки на издателе приводит к изменению ее секции. *allow_partition_realignment* имеет тип **nvarchar (5)** и значение по умолчанию true. **значение true** отправляет удаления на подписчика для отражения результатов изменения секции путем удаления данных, которые больше не являются частью секции подписчика. **значение false** оставляет данные из старой секции на подписчике, где изменения, вносимые в эти данные на издателе, не будут реплицироваться на подписчик, но изменения, вносимые на подписчике, будут реплицироваться на издатель. Установка *allow_partition_realignment* **false** используется для того, чтобы хранить данные в подписке из старой секции, когда данные должны быть доступны для исторических целей.  
  
> [!NOTE]  
>  Данные, остающиеся на подписчике в результате установки *allow_partition_realignment* в **значение false** , должны рассматриваться так, как если бы они были доступны только для чтения. Однако система репликации не обеспечивает этого.  
  
`[ @retention_period_unit = ] 'retention_period_unit'` Указывает единицы срока хранения, заданные в параметре *retention*. *retention_period_unit* имеет тип **nvarchar (10)** и может принимать одно из следующих значений.  
  
|Значение|Версия|  
|-----------|-------------|  
|**Day** (по умолчанию)|Срок хранения указан в днях.|  
|**week**|Срок хранения указан в неделях.|  
|**month**|Срок хранения указан в месяцах.|  
|**year**|Срок хранения указан в годах.|  
  
`[ @generation_leveling_threshold = ] generation_leveling_threshold` Указывает число изменений, содержащихся в поколении. Поколение — это набор изменений, переданных издателю или подписчику. *generation_leveling_threshold* имеет **тип int**и значение по умолчанию 1000.  
  
`[ @automatic_reinitialization_policy = ] automatic_reinitialization_policy`Указывает, передаются ли изменения с подписчика перед автоматической повторной инициализацией, необходимой для изменения публикации, где для ** \@ force_reinit_subscription**было указано значение **1** . *automatic_reinitialization_policy* имеет бит и значение по умолчанию 0. **1** означает, что изменения передаются с подписчика, прежде чем произойдет автоматическая повторная инициализация.  
  
> [!IMPORTANT]  
>  Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
`[ @conflict_logging = ] 'conflict_logging'` Указывает, где хранятся конфликтующие записи. *conflict_logging* имеет тип **nvarchar (15)** и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**publisher**|Конфликтующие записи хранятся на издателе.|  
|**абонент**|Конфликтующие записи хранятся на подписчике, вызвавшем конфликт. Не поддерживается подписчиками [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
|**как**|Конфликтующие записи хранятся одновременно на издателе и на подписчике.|  
|NULL (по умолчанию)|Репликация автоматически *conflict_logging* задает conflict_logging **, если значение** *backward_comp_level* равно **90RTM** , а в **Publisher** — во всех остальных случаях.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 **sp_addmergepublication** используется в репликации слиянием.  
  
 Чтобы вывести список объектов публикации на Active Directory с помощью параметра ** \@ add_to_active_directory** , этот [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объект уже должен быть создан в Active Directory.  
  
 Если существует несколько публикаций, которые публикуют один и тот же объект базы данных, только публикации с *replicate_ddl* значением **1** будут реплицировать инструкции ALTER TABLE, ALTER VIEW, ALTER PROCEDURE, ALTER FUNCTION и ALTER TRIGGER DDL. Однако инструкция ALTER TABLE DROP COLUMN DDL будет реплицирована всеми публикациями, публикующими столбец, который был удален.  
  
 Для [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков значение *alternate_snapshot_folder* используется только в том случае, если значение *snapshot_in_default_folder* равно **false**.  
  
 Если включена репликация DDL (_replicate_ddl_**= 1**) для публикации, чтобы не выполнять репликацию изменений DDL в публикацию, необходимо сначала выполнить [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) , чтобы установить значение *replicate_ddl* равным **0**. После выполнения нереплицируемых инструкций DDL можно снова выполнить **sp_changemergepublication** , чтобы снова включить репликацию DDL.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddMergePub](../../relational-databases/replication/codesnippet/tsql/sp-addmergepublication-t_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addmergepublication**.  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_helpmergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
