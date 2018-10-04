---
title: sp_addmergesubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_addmergesubscription_TSQL
- sp_addmergesubscription
helpviewer_keywords:
- sp_addmergesubscription
ms.assetid: a191d817-0132-49ff-93ca-76f13e609b38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5b319f6065c31a33f30469a73286491c1d641dc3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601122"
---
# <a name="spaddmergesubscription-transact-sql"></a>sp_addmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию. Публикация уже должна существовать.  
  
 [  **@subscriber =**] **"***подписчика***"**  
 Имя подписчика. *подписчик* — **sysname**, значение по умолчанию NULL.  
  
 [  **@subscriber_db=**] **"***subscriber_db***"**  
 Имя базы данных подписки. *subscriber_db*— **sysname**, значение по умолчанию NULL.  
  
 [  **@subscription_type=**] **"***subscription_type***"**  
 Тип подписки. *subscription_type*— **nvarchar(15)**, значение по умолчанию PUSH. Если **принудительной**, добавляется принудительной подписки, и на распространителе добавляется агент слияния. Если **по запросу**, подписки по запросу добавляется без добавления агент слияния на распространителе.  
  
> [!NOTE]  
>  Анонимные подписки не нуждаются в использовании этой хранимой процедуры.  
  
 [  **@subscriber_type=**] **"***subscriber_type***"**  
 Тип подписчика. *subscriber_type*— **nvarchar(15)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**локальный** (по умолчанию)|Подписчик известен только издателю.|  
|**Глобальные**|Подписчик известен всем серверам.|  
  
 В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях локальные подписки называются клиентскими подписками, а глобальные подписки — серверными подписками.  
  
 [  **@subscription_priority=**] *subscription_priority*  
 Число, показывающее приоритет подписки. *subscription_priority*— **реальных**, значение по умолчанию NULL. Для локальных и анонимных подписок приоритет равен 0,0. Для глобальных подписок приоритет должен быть меньше чем 100,0.  
  
 [  **@sync_type=**] **"***sync_type***"**  
 Тип синхронизации подписки. *sync_type*— **nvarchar(15)**, значение по умолчанию **автоматического**. Может быть **автоматического** или **none**. Если **автоматического**, схема и начальные данные для опубликованных таблиц передаются подписчику сначала. Если **none**, он считается подписчик уже имеет схему и начальные данные для опубликованных таблиц. Системные таблицы и данные переносятся всегда.  
  
> [!NOTE]  
>  Мы рекомендуем не указав значение **none**.  
  
 [  **@frequency_type=**] *frequency_type*  
 Значение, указывающее режим работы агента слияния. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**10**|Ежемесячно|  
|**20**|Ежемесячно, в соответствии с заданным интервалом|  
|**40**|При запуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|NULL (по умолчанию)||  
  
 [  **@frequency_interval=**] *frequency_interval*  
 День или дни запуска агента слияния. *frequency_interval* — **int**, и может принимать одно из следующих значений.  
  
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
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 Запланированное выполнение слияния интервала частоты в каждом месяце. *frequency_relative_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
|NULL (по умолчанию)||  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor*— **int**, значение по умолчанию NULL.  
  
 [  **@frequency_subday=**] *frequency_subday*  
 Единица измерения для *frequency_subday_interval*. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4**|Минута|  
|**8**|Час|  
|NULL (по умолчанию)||  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Частота для *frequency_subday* между каждого слияния. *frequency_subday_interval* — **int**, значение по умолчанию NULL.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Время суток, на которое запланирован первый запуск агента слияния, в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию NULL.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Время плановой остановки агента слияния в формате ЧЧММСС. *active_end_time_of_day* — **int**, значение по умолчанию NULL.  
  
 [  **@active_start_date=**] *active_start_date*  
 Дата первого планового запуска агента слияния в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию NULL.  
  
 [  **@active_end_date=**] *active_end_date*  
 Дата плановой остановки агента слияния в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию NULL.  
  
 [  **@optional_command_line=**] **"***optional_command_line***"**  
 Необязательное приглашение к вводу команды. *optional_command_line*— **nvarchar(4000)**, значение по умолчанию NULL. Этот параметр используется для добавления команды, которая захватывает выходной поток и сохраняет его в файл либо для указания файла конфигурации или атрибута.  
  
 [  **@description=**] **"***описание***"**  
 Короткое описание данной подписки слиянием. *Описание*— **nvarchar(255)**, значение по умолчанию NULL. Это значение отображается в мониторе репликации в **понятное имя** столбец, который может использоваться для сортировки подписок для контролируемой публикации.  
  
 [  **@enabled_for_syncmgr=**] **"***enabled_for_syncmgr***"**  
 Указывает, может ли подписка быть синхронизирована с помощью диспетчера синхронизации [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. *enabled_for_syncmgr* — **nvarchar(5)**, значение по умолчанию FALSE. Если **false**, подписка не зарегистрирована диспетчером синхронизации. Если **true**, подписка регистрируется диспетчером синхронизации и может быть синхронизирована без запуска [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 [  **@offloadagent=** ] *remote_agent_activation*  
 Указывает на то, что агент может быть активирован удаленно. *remote_agent_activation* — **бит** значение по умолчанию **0**.  
  
> [!NOTE]  
>  Этот аргумент является устаревшим и сохраняется только для поддержки обратной совместимости скриптов.  
  
 [  **@offloadserver=** ] **"***remote_agent_server_name***"**  
 Указывает сетевое имя сервера, используемого для удаленной активации агента. *remote_agent_server_name*— **sysname**, значение по умолчанию NULL.  
  
 [  **@use_interactive_resolver=** ] **"***use_interactive_resolver***"**  
 Возможно разрешение конфликтов в интерактивном режиме для всех статей, которые позволяют разрешение конфликтов в интерактивном режиме. *use_interactive_resolver* — **nvarchar(5)**, значение по умолчанию FALSE.  
  
 [  **@merge_job_name=** ] **"***merge_job_name***"**  
 *@merge_job_name* Аргумент является устаревшим и не может быть задано. *merge_job_name* — **sysname**, значение по умолчанию NULL.  
  
 [ **@hostname**=] **"***hostname***"**  
 Переопределяет значение, возвращенное [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) при использовании этой функции в предложении WHERE параметризованного фильтра. *Имя узла* — **sysname**, значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Для обеспечения высокой производительности не рекомендуется применять функции к именам столбцов в выражениях параметризованных фильтров строк, таких как `LEFT([MyColumn]) = SUSER_SNAME()`. Если вы используете [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) в предложении фильтра и переопределении значения HOST_NAME, возможно, необходимо выполнить преобразование типов данных с помощью [преобразовать](../../t-sql/functions/cast-and-convert-transact-sql.md). Дополнительные сведения см. в подразделе «Переопределение значения HOST_NAME()» раздела [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergesubscription** используется в репликации слиянием.  
  
 Когда **sp_addmergesubscription** выполняется членом **sysadmin** предопределенной роли сервера для создания принудительной подписки задание агента слияния неявно создается и запускается под [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента Учетная запись службы. Мы рекомендуем выполнить [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) и укажите учетные данные учетной записи Windows различные, конкретного агента для **@job_login** и **@job_password**. Дополнительные сведения см. в статье [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergesubscription-_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addmergesubscription**.  
  
## <a name="see-also"></a>См. также  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Интерактивное разрешение конфликтов](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)   
 [Subscribe to Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
