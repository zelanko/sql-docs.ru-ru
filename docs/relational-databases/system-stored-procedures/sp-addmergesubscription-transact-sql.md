---
description: sp_addmergesubscription (Transact-SQL)
title: sp_addmergesubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergesubscription_TSQL
- sp_addmergesubscription
helpviewer_keywords:
- sp_addmergesubscription
ms.assetid: a191d817-0132-49ff-93ca-76f13e609b38
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 197715e613e35e71068723fe90f2643e2373817e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489592"
---
# <a name="sp_addmergesubscription-transact-sql"></a>sp_addmergesubscription (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Создает подписку на принудительную публикацию слиянием или публикацию слиянием по запросу. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmergesubscription [ @publication= ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db= ] 'subscriber_db' ]  
    [ , [ @subscription_type= ] 'subscription_type' ]  
    [ , [ @subscriber_type= ] 'subscriber_type' ]  
    [ , [ @subscription_priority= ] subscription_priority ]  
    [ , [ @sync_type= ] 'sync_type' ]  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @optional_command_line= ] 'optional_command_line' ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @enabled_for_syncmgr= ] 'enabled_for_syncmgr' ]  
    [ , [ @offloadagent= ] remote_agent_activation]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @use_interactive_resolver= ] 'use_interactive_resolver' ]  
    [ , [ @merge_job_name= ] 'merge_job_name' ]  
    [ , [ @hostname = ] 'hostname'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию. Публикация уже должна существовать.  
  
`[ @subscriber = ] 'subscriber'` Имя подписчика. Аргумент *Subscriber* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'` Имя базы данных подписки. Аргумент *subscriber_db*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @subscription_type = ] 'subscription_type'` Тип подписки. *subscription_type*имеет тип **nvarchar (15)** и значение по умолчанию Push. Если **Принудительная отправка**, добавляется принудительная подписка и агент слияния добавляется на распространителе. Если **Pull**, то подписка по запросу добавляется без добавления агент слияния на распространителе.  
  
> [!NOTE]  
>  Анонимные подписки не нуждаются в использовании этой хранимой процедуры.  
  
`[ @subscriber_type = ] 'subscriber_type'` Тип подписчика. *subscriber_type*имеет тип **nvarchar (15)** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Local** (по умолчанию)|Подписчик известен только издателю.|  
|**global**|Подписчик известен всем серверам.|  
  
 В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях локальные подписки называются клиентскими подписками, а глобальные подписки — серверными подписками.  
  
`[ @subscription_priority = ] subscription_priority` Число, указывающее приоритет подписки. *subscription_priority*является **реальным**и имеет значение по умолчанию NULL. Для локальных и анонимных подписок приоритет равен 0,0. Для глобальных подписок приоритет должен быть меньше чем 100,0.  
  
`[ @sync_type = ] 'sync_type'` Тип синхронизации подписки. *sync_type*имеет тип **nvarchar (15)** и значение по умолчанию **Automatic**. Может быть **автоматическим** или **нет**. При **автоматическом**создании схемы и начальные данные для опубликованных таблиц сначала передаются подписчику. Если **нет**, предполагается, что подписчик уже имеет схему и начальные данные для опубликованных таблиц. Системные таблицы и данные переносятся всегда.  
  
> [!NOTE]  
>  Не рекомендуется указывать значение **None**.  
  
`[ @frequency_type = ] frequency_type` Значение, указывающее, когда будет выполняться агент слияния. *frequency_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**10**|Ежемесячно|  
|**20**|Ежемесячно, в соответствии с заданным интервалом|  
|**40**|При запуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|NULL (по умолчанию)||  
  
`[ @frequency_interval = ] frequency_interval` День или дни выполнения агент слияния. *frequency_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
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
  
`[ @frequency_relative_interval = ] frequency_relative_interval` — Это запланированное слияние вхождений интервала частоты в каждом месяце. *frequency_relative_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|First|  
|**2**|Second|  
|**4**|Третье|  
|**8**|Четвертая|  
|**16**|Последний|  
|NULL (по умолчанию)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Коэффициент повторения, используемый *frequency_type*. *frequency_recurrence_factor*имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_subday = ] frequency_subday` Единица измерения для *frequency_subday_interval*. *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Second|  
|**4**|Минута|  
|**8**|Час|  
|NULL (по умолчанию)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Частота, с которой *frequency_subday* происходит между каждым слиянием. *frequency_subday_interval* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Время первого запланированного агент слияния в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Время суток, когда запланировать агент слияния прекращается в формате ЧЧММСС. *active_end_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_date = ] active_start_date` Дата первого запланированного запуска агент слияния в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_date = ] active_end_date` Дата прекращения расписания агент слияния в формате ГГГГММДД. *active_end_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'` Необязательная Командная строка для выполнения. *optional_command_line*имеет тип **nvarchar (4000)** и значение по умолчанию NULL. Этот параметр используется для добавления команды, которая захватывает выходной поток и сохраняет его в файл либо для указания файла конфигурации или атрибута.  
  
`[ @description = ] 'description'` Краткое описание этой подписки на публикацию слиянием. *Description*имеет тип **nvarchar (255)** и значение по умолчанию NULL. Это значение отображается монитором репликации в столбце **понятное имя** , который можно использовать для сортировки подписок для отслеживаемой публикации.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Указывает, можно ли синхронизировать подписку с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] диспетчера синхронизации Windows. *enabled_for_syncmgr* имеет тип **nvarchar (5)** и значение по умолчанию false. Если **значение равно false**, подписка не зарегистрирована в диспетчере синхронизации. Если **значение — true**, подписка регистрируется в диспетчере синхронизации и может быть синхронизирована без запуска [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
`[ @offloadagent = ] remote_agent_activation` Указывает, что агент может быть активирован удаленно. *remote_agent_activation* имеет **бит** с значением по умолчанию **0**.  
  
> [!NOTE]  
>  Этот аргумент является устаревшим и сохраняется только для поддержки обратной совместимости скриптов.  
  
`[ @offloadserver = ] 'remote_agent_server_name'` Указывает сетевое имя сервера, используемого для удаленной активации агента. Аргумент *remote_agent_server_name*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver'` Разрешает интерактивное разрешение конфликтов для всех статей, в которых разрешено интерактивная поддержка. *use_interactive_resolver* имеет тип **nvarchar (5)** и значение по умолчанию false.  
  
`[ @merge_job_name = ] 'merge_job_name'`Параметр * \@ merge_job_name* является устаревшим и не может быть задан. Аргумент *merge_job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @hostname = ] 'hostname'` Переопределяет значение, возвращаемое [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) , когда эта функция используется в предложении WHERE параметризованного фильтра. Аргумент *HostName* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Для обеспечения высокой производительности не рекомендуется применять функции к именам столбцов в выражениях параметризованных фильтров строк, таких как `LEFT([MyColumn]) = SUSER_SNAME()`. При использовании [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) в предложении фильтра и переопределении значения HOST_NAME может потребоваться преобразовать типы данных с помощью [Convert](../../t-sql/functions/cast-and-convert-transact-sql.md). Дополнительные сведения см. в подразделе «Переопределение значения HOST_NAME()» раздела [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_addmergesubscription** используется в репликации слиянием.  
  
 Если **sp_addmergesubscription** выполняется членом предопределенной роли сервера **sysadmin** для создания принудительной подписки, то агент слияния задание создается неявно и выполняется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы агента. Рекомендуется выполнить [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) и указать учетные данные другой учетной записи Windows, зависящей от агента, для ** \@ job_login** и ** \@ job_password**. Дополнительные сведения см. в статье [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergesubscription-_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addmergesubscription**.  
  
## <a name="see-also"></a>См. также:  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Интерактивное разрешение конфликтов](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)   
 [Subscribe to Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
