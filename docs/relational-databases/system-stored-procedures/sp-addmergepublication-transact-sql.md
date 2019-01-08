---
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 75390bbbc490046af6db4e47a7ca10cefac2546c
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591878"
---
# <a name="spaddmergepublication-transact-sql"></a>sp_addmergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [  **@publication =** ] **"**_публикации_**"**  
 Имя создаваемой публикации слиянием. *Публикация* — **sysname**, не по умолчанию, и не может быть ключевым словом все. Имя публикации в пределах базы данных должно быть уникальным.  
  
 [  **@description =** ] **"**_описание_**"**  
 Описание публикации. *Описание* — **nvarchar(255)**, значение по умолчанию NULL.  
  
 [  **@retention =** ] *хранения*  
 Срок хранения, при хранении единицы измерения срока, для которого необходимо сохранить изменения для данного *публикации*. *хранение* — **int**, значение по умолчанию 14 единиц. Единицы измерения срока хранения определяются *retention_period_unit*. Если подписка не синхронизирована в течение срока хранения, а ожидающие обработки изменения, которые были бы получены, удалены операцией очистки на стороне распространителя, срок действия подписки истекает, и подписка должна быть создана заново. Максимально допустимым сроком хранения является количество дней от 31 декабря 9999 года до текущей даты.  
  
> [!NOTE]  
>  Срок хранения для публикации слиянием предусматривает наличие 24-часового льготного срока для согласования работы подписчиков в разных часовых поясах. Например, если установить срок хранения продолжительностью в один день, то действительный срок хранения будет равен 48 часам.  
  
 [  **@sync_mode =** ] **"**_sync_mode со значением_**"**  
 Режим начальной синхронизации подписчиков на публикацию. *sync_mode со значением* — **nvarchar(10)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**собственный** (по умолчанию)|Производит выходные данные программы массового копирования всех таблиц.|  
|**character**|Производит выходные данные программы массового копирования всех таблиц в символьном режиме. Требуется для поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] и не-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.|  
  
 [  **@allow_push =** ] **"**_allow_push_**"**  
 Указывает, можно ли создать принудительные подписки для конкретной публикации. *allow_push* — **nvarchar(5)**, значение по умолчанию TRUE, разрешающее принудительные подписки на публикацию.  
  
 [  **@allow_pull =** ] **"**_allow_pull_**"**  
 Указывает, можно ли создать подписки по запросу для конкретной публикации. *allow_pull* — **nvarchar(5)**, значение по умолчанию TRUE, разрешающее подписки по запросу на публикацию. Необходимо указать значение true для поддержки [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков.  
  
 [  **@allow_anonymous =** ] **"**_allow_anonymous_**"**  
 Указывает, можно ли создать анонимные подписки для конкретной публикации. *allow_anonymous* — **nvarchar(5)**, значение по умолчанию TRUE, разрешающее анонимные подписки на публикацию. Для поддержки [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков, необходимо указать **true**.  
  
 [  **@enabled_for_internet =** ] **"**_enabled_for_internet_**"**  
 Указывает, разрешена ли публикация через Интернет и можно ли использовать протокол FTP для передачи подписчику файлов моментальных снимков. *enabled_for_internet* — **nvarchar(5)**, значение по умолчанию FALSE. Если **true**, файлы синхронизации для публикации помещаются в каталог C:\Program Files\Microsoft SQL Server\MSSQL\MSSQL.x\Repldata\Ftp. Пользователь должен создать каталог Ftp. Если **false**, данная публикация не включена для доступа к Интернету.  
  
 [  **@centralized_conflicts =**] **"**_centralized_conflicts_**"**  
 Этот аргумент устарел и поддерживается только для обратной совместимости скриптов. Используйте *conflict_logging* для указания расположения, где хранятся конфликтующие записи.  
  
 [  **@dynamic_filters =**] **"**_dynamic_filters_**"**  
 Разрешает использование параметризованных фильтров строк для публикации слиянием. *dynamic_filters* — **nvarchar(5)**, значение по умолчанию FALSE.  
  
> [!NOTE]  
>  Вместо задания этого параметра следует позволить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически определять, используются ли параметризованные фильтры строк. Если указать значение **true** для *dynamic_filters*, необходимо определить параметризованный фильтр строк для статьи. Дополнительные сведения см. в статье [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
 [  **@snapshot_in_defaultfolder =** ] **"**_snapshot_in_default_folder_**"**  
 Указывает, хранятся ли файлы моментальных снимков в папке по умолчанию. *snapshot_in_default_folder* — **nvarchar(5)**, значение по умолчанию TRUE. Если **true**, файлы моментальных снимков находятся в папке по умолчанию. Если **false**, файлы моментальных снимков, которые будут храниться в другом расположении, заданном по *alternate_snapshot_folder*. Это место может находиться на другом сервере, на сетевом диске или на съемном носителе (например на CD-ROM или на съемном диске). Файлы моментальных снимков могут также сохраняться с помощью протокола передачи файлов на FTP-сайте, чтобы подписчик мог извлечь эти файлы позже. Обратите внимание, что этот параметр может иметь значение true, по-прежнему расположении, заданном параметром *alt_snapshot_folder*. Это сочетание размещает файлы моментальных снимков одновременно и в месте по умолчанию, и в альтернативном месте.  
  
 [  **@alt_snapshot_folder =** ] **"**_alternate_snapshot_folder_**"**  
 Указывает местоположение альтернативной папки для моментального снимка. *alternate_snapshot_folder* — **nvarchar(255)**, значение по умолчанию NULL.  
  
 [  **@pre_snapshot_script =** ] **"**_pre_snapshot_script_**"**  
 Задает указатель на **.sql** расположение файла. *pre_snapshot_script* — **nvarchar(255)**, значение по умолчанию NULL. При применении моментального снимка на подписчике агент слияния выполняет скрипт до моментального снимка перед выполнением скриптов объектов репликации. Скрипт выполняется в контексте безопасности, используемом агентом слияния при подключении к базе данных подписки. Скрипты до моментального снимка не выполняются на [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков.  
  
 [  **@post_snapshot_script =** ] **"**_post_snapshot_script_**"**  
 Задает указатель на **.sql** расположение файла. *post_snapshot_script* — **nvarchar(255)**, значение по умолчанию NULL. Агент слияния выполняет скрипт после моментального снимка после того, как во время начальной синхронизации будут применены скрипты и данные всех других объектов репликации. Скрипт выполняется в контексте безопасности, используемом агентом слияния при подключении к базе данных подписки. Скрипты после моментального снимка не выполняются на [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков.  
  
 [  **@compress_snapshot =** ] **"**_compress_snapshot_**"**  
 Указывает, что моментальный снимок, записываемый **@alt_snapshot_folder** расположение — для сжатия в [!INCLUDE[msCoName](../../includes/msconame-md.md)] формате CAB. *compress_snapshot* — **nvarchar(5)**, значение по умолчанию FALSE. **false** указывает, что моментальный снимок не сжимается; **true** показывает, что моментальный снимок будет сжат. Файлы моментальных снимков, превышающие 2 ГБ, не могут быть сжаты. Сжатые файлы моментальных снимков распаковываются в том месте, в котором выполняется агент слияния; подписки по запросу обычно используются со сжатыми моментальными снимками, так что соответствующие файлы распаковываются на подписчике. Моментальный снимок в папке по умолчанию сжать нельзя. Для поддержки [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков, необходимо указать **false**.  
  
 [  **@ftp_address =** ] **"**_ftp_address_**"**  
 Сетевой адрес службы FTP распространителя. *ftp_address* — **sysname**, значение по умолчанию NULL. Указывается расположение файлов моментальных снимков публикаций, откуда их выбирает агент слияния подписчика. Поскольку это свойство хранится для каждой публикации, каждая публикация может иметь другой *ftp_address*. Публикация должна поддерживать распространение моментальных снимков с помощью протокола FTP.  
  
 [  **@ftp_port=** ] *ftp_port*  
 Номер порта службы FTP распространителя. *ftp_port* — **int**, значение по умолчанию 21. Указывается расположение файлов моментальных снимков публикаций, откуда их выбирает агент слияния подписчика. Поскольку это свойство хранится для каждой публикации, каждая публикация может иметь свой собственный *ftp_port*.  
  
 [  **@ftp_subdirectory =** ] **"**_ftp_subdirectory_**"**  
 Указывает расположение файлов моментальных снимков для агента слияния данного подписчика, если публикация поддерживает распространение моментальных снимков с помощью FTP. *ftp_subdirectory* — **nvarchar(255)**, значение по умолчанию NULL. Поскольку это свойство хранится для каждой публикации, каждая публикация может иметь свой собственный *ftp_subdirctory* или решили подкаталога, со значением NULL.  
  
 При предварительном формировании моментальных снимков для публикаций при помощи параметризованных фильтров необходимо, чтобы моментальные снимки данных для каждой секции подписчика находились в своих папках. Структура каталога для предварительно формируемых при помощи FTP моментальных снимков должна иметь следующий вид:  
  
 *alternate_snapshot_folder*\ftp\\*publisher_publicationDB_publication*\\*partitionID*.  
  
> [!NOTE]  
>  Указанные выше значения, выделенные курсивом, зависят от характеристик публикации и секции подписчика.  
  
 [  **@ftp_login =** ] **"**_ftp_login_**"**  
 Имя пользователя, используемое для подключения к службе FTP. *ftp_login* — **sysname**, значение по умолчанию «Anonymous».  
  
 [  **@ftp_password =** ] **"**_ftp_password_**"**  
 Пароль пользователя, используемый для подключения к службе FTP. *ftp_password* — **sysname**, значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли.  
  
 [  **@conflict_retention =** ] *conflict_retention*  
 Указывает срок хранения конфликтных записей (в сутках). *conflict_retention* — **int**, значение по умолчанию 14 дней до конфликт строка удаляется из конфликтной таблицы.  
  
 [  **@keep_partition_changes =** ] **"**_keep_partition_changes_**"**  
 Указывает, нужно ли включать оптимизацию изменений секций, если предварительно вычисляемые секции не могут быть использованы. *keep_partition_changes* — **nvarchar(5)**, значение по умолчанию TRUE. **false** означает, что секционирование изменений не оптимизируются, и если предварительно вычисляемые секции не используются, секции, посылаемые всем подписчикам, будут проверены при изменении данных в секции. **значение true,** означает, что секционирование изменений оптимизированы и влияет только на подписчиков, имеющих строки в изменяемых секциях. При использовании предварительно вычисляемых секций, установить *use_partition_groups* для **true** и задайте *keep_partition_changes* для **false**. Дополнительные сведения см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
> [!NOTE]  
>  Если указать значение **true** для *keep_partition_changes*, укажите значение **1** параметру агента моментальных снимков **- MaxNetworkOptimization** . Дополнительные сведения об этом параметре см. в разделе [агент моментальных снимков репликации](../../relational-databases/replication/agents/replication-snapshot-agent.md). Сведения об указании параметров агента, см. в разделе [Администрирование агента репликации](../../relational-databases/replication/agents/replication-agent-administration.md).  
  
 С помощью [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков, *keep_partition_changes* должно быть присвоено значение true, чтобы обеспечить правильное распределение удалений. При установке значения false подписчик может получить больше строк, чем ожидается.  
  
 [  **@allow_subscription_copy=** ] **"**_allow_subscription_copy_**"**  
 Разрешает или запрещает возможность копирования баз данных подписки, подписанных на эту публикацию. *allow_subscription_copy* — **nvarchar(5)**, значение по умолчанию FALSE. Размер копируемой базы данных подписки должен быть меньше 2 ГБ.  
  
 [  **@allow_synctoalternate =** ] **"**_allow_synctoalternate_**"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@validate_subscriber_info =** ] **"**_validate_subscriber_info_**"**  
 Перечисляет функции, которые применяются для определения секции подписчика опубликованных данных, при использовании параметризованных фильтров строк. *validate_subscriber_info* — **nvarchar(500)**, значение по умолчанию NULL. Эти данные используются агентом слияния для проверки секций подписчиков. Например если [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) используется в параметризованном фильтре строк, значение параметра должно быть `@validate_subscriber_info=N'SUSER_SNAME()'`.  
  
> [!NOTE]  
>  Вместо задания этого параметра позвольте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически определять критерий фильтрации.  
  
 [  **@add_to_active_directory =** ] **"**_add_to_active_directory_**"**  
 Этот аргумент устарел и поддерживается только для обратной совместимости скриптов. Больше нельзя добавлять данные публикации в службу [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory.  
  
 [  **@max_concurrent_merge =** ] *maximum_concurrent_merge*  
 Максимальное число одновременно выполняющихся процессов слияния. *maximum_concurrent_merge* — **int** значение по умолчанию 0. Значение **0** для этого свойства означает, что нет ограничений на количество параллельно выполняемых одновременно процессов слияния. Это свойство устанавливает предельное значение числа процессов слияния, которые могут одновременно выполняться на публикации слиянием. Если в расписании задано одновременное выполнение большего числа процессов слияния, чем указанное значение, лишние задания будут поставлены в очередь, где они будут ожидать завершения одного из одновременно выполняющихся процессов слияния.  
  
 [  **@max_concurrent_dynamic_snapshots =**] *max_concurrent_dynamic_snapshots*  
 Максимальное количество сеансов агента моментальных снимков, которые могут одновременно выполняться для формирования моментальных снимков отфильтрованных данных для секций подписчиков. *maximum_concurrent_dynamic_snapshots* — **int** значение по умолчанию 0. Если **0**, нет ограничений на количество сеансов моментальных снимков. Если на одно и то же время назначено больше процессов моментальных снимков, чем позволяет указанное значение, лишние задачи будут помещены в очередь до завершения создания текущего моментального снимка.  
  
 [  **@use_partition_groups =** ] **"**_use_partition_groups_**"**  
 Указывает, что для оптимизации процесса синхронизации должны использоваться предварительно вычисляемые секции. *use_partition_groups* — **nvarchar(5)**, и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**true**|Публикация использует предварительно вычисляемые секции.|  
|**false**|Публикация не использует предварительно вычисляемые секции.|  
|NULL(Default)|Стратегию секционирования выбирает система.|  
  
 По умолчанию используются предварительно вычисляемые секции. Чтобы избежать использования предварительно вычисляемых секций *use_partition_groups* должно быть присвоено **false**. При задании NULL система решает, могут ли использоваться предварительно вычисляемые секции. Если предварительно вычисляемые секции не могут быть использованы, то это значение приобретает **false** формируя ошибку. В таких случаях *keep_partition_changes* можно присвоить **true** для обеспечения некоторой оптимизации аргументу. Дополнительные сведения см. в разделе [параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md) и [оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
 [  **@publication_compatibility_level =** ] *backward_comp_level*  
 Указывает обратную совместимость публикации. *backward_comp_level* — **nvarchar(6)**, и может принимать одно из следующих значений:  
  
|Значение|Версия|  
|-----------|-------------|  
|**90RTM**|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|  
|**100RTM**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
  
 [  **@replicate_ddl =** ] *replicate_ddl*  
 Указывает, поддерживается ли для публикации репликация схемы. *replicate_ddl* — **int**, значение по умолчанию 1. **1** указывает, что инструкции языка DDL для определения данных, выполняемые на издателе, реплицируются, и **0** указывает, что инструкции DDL не реплицируются. Дополнительные сведения см. в статье [Внесение изменений в схемы баз данных публикации](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
 *@replicate_ddl* Параметр учитывается, когда инструкция DDL добавляет столбец. *@replicate_ddl* Параметр игнорируется в том случае, когда инструкция DDL изменяет или удаляет столбец по следующим причинам.  
  
-   При удалении столбца sysarticlecolumns должны обновляться во избежание новые инструкции DML из включали удаленный столбец привело к агента распространителя, завершится ошибкой. *@replicate_ddl* Параметр игнорируется, так как репликация всегда должна реплицировать изменения схемы.  
  
-   Когда в столбец вносится изменение, исходный тип данных или возможность допустимости значения NULL может измениться, в результате чего инструкции DML будут содержать значение, которое может быть несовместимым с таблицей на подписчике. Такие инструкции DML могут привести к тому, что работа агента распространителя завершится ошибкой. *@replicate_ddl* Параметр игнорируется, так как репликация всегда должна реплицировать изменения схемы.  
  
-   Когда инструкция DDL добавляет новый столбец, sysarticlecolumns не включает новый столбец. Инструкции DML не будут пытаться реплицировать данные для этого нового столбца. Этот параметр учитывается потому, что допустимо как выполнение, так и не выполнение репликации DDL.  
  
 [  **@allow_subscriber_initiated_snapshot =** ] **"**_allow_subscriber_initiated_snapshot_**"**  
 Указывает, могут ли подписчики на данную публикацию инициировать процесс моментального снимка для создания отфильтрованного моментального снимка своих секций данных. *allow_subscriber_initiated_snapshot* — **nvarchar(5)**, значение по умолчанию FALSE. **значение true,** указывает, что подписчики могут инициировать процесс создания моментального снимка.  
  
 [  **@allow_web_synchronization =** ] **"**_allow_web_synchronization_**"**  
 Указывает, включена ли для публикации веб-синхронизация. *allow_web_synchronization* — **nvarchar(5)**, значение по умолчанию FALSE. **значение true,** указывает, что подписки на эту публикацию могут синхронизироваться по протоколу HTTPS. Дополнительные сведения см. в статье [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md). Для поддержки [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков, необходимо указать **true**.  
  
 [  **@web_synchronization_url=** ] **"**_web_synchronization_url_**"**  
 Значение URL-адреса по умолчанию, применяемое для веб-синхронизации. *web_synchronization_url я*s **nvarchar(500)**, значение по умолчанию NULL. Определяет значение по умолчанию URL-адрес, если он не задан явно при [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) выполняется.  
  
 [  **@allow_partition_realignment =** ] **"**_allow_partition_realignment_**"**  
 Определяет, посылаются ли операции удаления подписчику, если в результате изменения строки на издателе изменяется его секция. *allow_partition_realignment* — **nvarchar(5)**, значение по умолчанию TRUE. **значение true,** производится пересылка операций удаления на подписчик для отражения результатов изменений секции путем удаления данных, которые больше не являются частью секции подписчика. **false** данные из старой секции остаются на подписчике, когда изменения, внесенные в эти данные на издателе не будут реплицированы на подписчик, но изменения, внесенные на подписчике будут реплицированы на издатель. Установка *allow_partition_realignment* для **false** используется для сохранения данных в подписке из старой секции, если данные должны быть доступны для статистических целей.  
  
> [!NOTE]  
>  Данные, сохраняющиеся на подписчике в результате присвоения свойству *allow_partition_realignment* для **false** должны рассматриваться как если бы это был только для чтения; Однако это не требование системы репликации.  
  
 [  **@retention_period_unit =** ] **"**_retention_period_unit_**"**  
 Указывает единицы измерения для срока хранения, установленного *хранения*. *retention_period_unit* — **nvarchar(10)**, и может принимать одно из следующих значений.  
  
|Значение|Версия|  
|-----------|-------------|  
|**день** (по умолчанию)|Срок хранения указан в днях.|  
|**week**|Срок хранения указан в неделях.|  
|**month**|Срок хранения указан в месяцах.|  
|**year**|Срок хранения указан в годах.|  
  
 [  **@generation_leveling_threshold=** ] *generation_leveling_threshold*  
 Задает число изменений, которые содержатся в поколении. Поколение — это набор изменений, переданных издателю или подписчику. *generation_leveling_threshold* — **int**, со значением по умолчанию 1000.  
  
 [  **@automatic_reinitialization_policy =** ] *automatic_reinitialization_policy*  
 Указывает, передаются ли изменения с подписчика перед автоматической повторной инициализацией, необходимой при изменении в публикации, где значение **1** был указан для **@force_reinit_subscription**. *automatic_reinitialization_policy* имеет тип bit и значение по умолчанию 0. **1** означает, что изменения передаются с подписчика перед автоматической повторной инициализацией.  
  
> [!IMPORTANT]  
>  Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
 [  **@conflict_logging =** ] **"**_conflict_logging_**"**  
 Определяет место хранения записей конфликта. *conflict_logging* — **nvarchar(15)**, и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**издатель**|Конфликтующие записи хранятся на издателе.|  
|**подписчик**|Конфликтующие записи хранятся на подписчике, вызвавшем конфликт. Не поддерживается подписчиками [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
|**оба**|Конфликтующие записи хранятся одновременно на издателе и на подписчике.|  
|NULL (по умолчанию)|Репликация автоматически устанавливает *conflict_logging* для **оба** при значение *backward_comp_level* — **90RTM** и **издателя** во всех остальных случаях.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergepublication** используется в репликации слиянием.  
  
 Для получения списка объектов публикации в Active Directory с помощью **@add_to_active_directory** параметра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объект уже должен быть создан в Active Directory.  
  
 Если несколько существующих публикаций публикуют тот же объект базы данных, только публикации с параметром *replicate_ddl* значение **1** будут реплицировать инструкции ALTER TABLE, ALTER VIEW, ALTER PROCEDURE, ALTER FUNCTION и Инструкции ALTER TRIGGER DDL. Однако инструкция ALTER TABLE DROP COLUMN DDL будет реплицирована всеми публикациями, публикующими столбец, который был удален.  
  
 Для [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков, значение *alternate_snapshot_folder* используется, только если значение *snapshot_in_default_folder* — **false**.  
  
 С включенной репликацией DDL (_replicate_ddl_**= 1**) для публикации, чтобы сделать не относящиеся к репликации в публикации изменения, [sp_changemergepublication &#40; Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) вначале необходимо выполнить для установки *replicate_ddl* для **0**. После выполнения нереплицируемых инструкций DDL, **sp_changemergepublication** может быть запущена снова включить репликацию DDL.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddMergePub](../../relational-databases/replication/codesnippet/tsql/sp-addmergepublication-t_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addmergepublication**.  
  
## <a name="see-also"></a>См. также  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [sp_changemergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_helpmergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
