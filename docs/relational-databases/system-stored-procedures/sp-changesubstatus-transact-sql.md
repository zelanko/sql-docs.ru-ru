---
title: sp_changesubstatus (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_changesubstatus
- sp_changesubstatus_TSQL
helpviewer_keywords:
- sp_changesubstatus
ms.assetid: 9370e47a-d128-4f15-9224-1c3642770c39
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 94c26330636d4e13fe84a2776a72315a418d3d96
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spchangesubstatus-transact-sql"></a>sp_changesubstatus (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет состояние существующего подписчика. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changesubstatus [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
        , [ @status = ] 'status'  
    [ , [ @previous_status = ] 'previous_status' ]  
    [ , [ @destination_db = ] 'destination_db' ]  
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
    [ , [ @distribution_jobid = ] distribution_jobid ]  
    [ , [ @from_auto_sync = ] from_auto_sync ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @offloadagent= ] remote_agent_activation ]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] dts_package_location ]  
    [ , [ @skipobjectactivation = ] skipobjectactivation  
  [ , [ @distribution_job_name= ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию **%**. Если *публикации* не указан, влияют на все публикации.  
  
 [  **@article=**] **"***статьи***"**  
 Имя статьи. Оно должно быть уникальным для публикации. *статья* — **sysname**, значение по умолчанию **%**. Если *статьи* не указан, влияют на все статьи.  
  
 [  **@subscriber=**] **"***подписчика***"**  
 Имя подписчика, состояние которого подлежит изменению. *подписчик* — **sysname**, значение по умолчанию **%**. Если *подписчика* не указано, состояние изменяется для всех подписчиков на указанную статью.  
  
 [  **@status =**] **"***состояние***"**  
 Состояние подписки в **syssubscriptions** таблицы. *состояние* — **sysname**, без значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Активный**|Подписчик синхронизирован и получает данные.|  
|**Неактивные**|Запись о подписчике существует, но подписка отсутствует.|  
|**Подписка**|Подписчик запрашивает данные, но еще не синхронизирован.|  
  
 [  **@previous_status=**] **"***previous_status***"**  
 Прежнее состояние подписки. *previous_status* — **sysname**, значение по умолчанию NULL. Этот параметр позволяет изменять любые подписки, для которых этот статус, тем самым возможным выполнение групповых функций в определенном наборе подписок (например возвращение всем активным подпискам **подписка**).  
  
 [  **@destination_db=**] **"***destination_db***"**  
 Имя целевой базы данных. *destination_db* — **sysname**, значение по умолчанию **%**.  
  
 [  **@frequency_type=**] *frequency_type*  
 Частота запуска задачи распространения по расписанию. *frequency_type* — **int**, значение по умолчанию NULL.  
  
 [  **@frequency_interval=**] *frequency_interval*  
 Представляет значение, которое применяется к частоте, установленной аргументом *frequency_type*. *frequency_interval* — **int**, значение по умолчанию NULL.  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 Дата задачи распределения. Этот параметр используется при *frequency_type* имеет значение 32 (ежемесячное относительное расписание). *frequency_relative_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
|NULL (по умолчанию)||  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию NULL.  
  
 [  **@frequency_subday=**] *frequency_subday*  
 Частота повторного планирования в течение определенного периода, в минутах. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4**|Минута|  
|**8**|Час|  
|NULL (по умолчанию)||  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию NULL.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Время суток, на которое запланирован первый запуск задачи распространения в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию NULL.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Время, когда будет прекращено выполнение задачи распространения по расписанию, в формате ЧЧММСС. *active_end_time_of_day* — **int**, значение по умолчанию NULL.  
  
 [  **@active_start_date=**] *active_start_date*  
 Дата, когда запланирован первый запуск задачи распространения, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию NULL.  
  
 [  **@active_end_date=**] *active_end_date*  
 Дата, когда запланирован останов задачи распространения в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию NULL.  
  
 [  **@optional_command_line=**] **"***optional_command_line***"**  
 Дополнительная командная строка. *optional_command_line* — **nvarchar(4000)**, значение по умолчанию NULL.  
  
 [  **@distribution_jobid=**] *distribution_jobid*  
 Идентификатор задания агента распространителя на распространителе для подписки при изменении состояния подписки с неактивного на активный. В иных случаях он не определяется. Если в отдельный вызов этой хранимой процедуры вовлечено более одного агента распространителя, результат не определен. *distribution_jobid* — **binary(16)**, значение по умолчанию NULL.  
  
 [  **@from_auto_sync=**] *from_auto_sync*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@ignore_distributor=**] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@offloadagent=** ] *remote_agent_activation*  
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. Установка *remote_agent_activation* для значения, отличного от **0** приводит к ошибке.  
  
 [  **@offloadserver=** ] **"***remote_agent_server_name***"**  
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. Установка *remote_agent_server_name* любое значение, отличное от NULL, приведет к ошибке.  
  
 [ **@dts_package_name**=] **"***dts_package_name***"**  
 Указывает имя пакета служб DTS. *dts_package_name* — **sysname**, значение по умолчанию NULL. Например, пакет с именем **DTSPub_Package** следует указать `@dts_package_name = N'DTSPub_Package'`.  
  
 [ **@dts_package_password**=] **"***dts_package_password***"**  
 Указывает пароль на пакет. *dts_package_password* — **sysname** значение по умолчанию NULL, при которой указывает, что свойство пароля должно быть оставлено без изменений.  
  
> [!NOTE]  
>  У пакета служб DTS должен быть пароль.  
  
 [ **@dts_package_location**=] *dts_package_location*  
 Указывает местоположение пакета. *dts_package_location* — **int**, значение по умолчанию **0**. Если **0**, что пакет находится на распространителе. Если **1**, что пакет находится на подписчике. Расположение пакета может быть **распространителя** или **подписчика**.  
  
 [ **@skipobjectactivation**=] *skipobjectactivation*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@distribution_job_name=** ] **"***distribution_job_name***"**  
 Имя задания распространения. *distribution_job_name* — **sysname**, значение по умолчанию NULL.  
  
 [ **@publisher**=] **"***издатель***"**  
 Указывает значение, отличное от[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать при изменении свойств статьи на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_changesubstatus** используется в репликации моментальных снимков и репликации транзакций.  
  
 **sp_changesubstatus** изменяет состояние подписчика в **syssubscriptions** таблицы с измененным состоянием. При необходимости, он изменяет состояние статьи в **sysarticles** таблицы для указания активности или неактивности. При необходимости устанавливает флаг репликации или отключить **sysobjects** для реплицируемой таблицы.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера **db_owner** предопределенной роли базы данных, или создатель подписки могут выполнять процедуру **sp_changesubstatus**.  
  
## <a name="see-also"></a>См. также  
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpdistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
