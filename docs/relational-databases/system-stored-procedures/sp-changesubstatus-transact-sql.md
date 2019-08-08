---
title: sp_changesubstatus (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubstatus
- sp_changesubstatus_TSQL
helpviewer_keywords:
- sp_changesubstatus
ms.assetid: 9370e47a-d128-4f15-9224-1c3642770c39
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c10e05098a611e51583b2b1132f811d36b0f20a
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771330"
---
# <a name="sp_changesubstatus-transact-sql"></a>sp_changesubstatus (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет **%** тип **sysname**и значение по умолчанию. Если *Публикация* не указана, затрагиваются все публикации.  
  
`[ @article = ] 'article'`Имя статьи. Оно должно быть уникальным для публикации. Аргумент *article* имеет **%** тип **sysname**и значение по умолчанию. Если *статья* не указана, затрагиваются все статьи.  
  
`[ @subscriber = ] 'subscriber'`Имя подписчика, для которого изменяется состояние. Аргумент *Subscriber* имеет **%** тип **sysname**и значение по умолчанию. Если параметр *подписчик* не указан, состояние изменяется для всех подписчиков на указанную статью.  
  
`[ @status = ] 'status'`— Это состояние подписки в таблице **syssubscriptions** . Аргумент *Status* имеет тип **sysname**, не имеет значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Active**|Подписчик синхронизирован и получает данные.|  
|**Активный**|Запись о подписчике существует, но подписка отсутствует.|  
|**подписаны**|Подписчик запрашивает данные, но еще не синхронизирован.|  
  
`[ @previous_status = ] 'previous_status'`Предыдущее состояние подписки. *previous_status* имеет тип **sysname**и значение по умолчанию NULL. Этот параметр позволяет изменить все подписки, имеющие это состояние, таким образом разрешая групповые функции для определенного набора подписок (например, установка всех активных подписок обратно на подписку).  
  
`[ @destination_db = ] 'destination_db'`Имя целевой базы данных. *destination_db* имеет **тип sysname**и значение по умолчанию **%** .  
  
`[ @frequency_type = ] frequency_type`Частота, с которой следует запланировать задачу распределения. Аргумент *frequency_type* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_interval = ] frequency_interval`Значение, применяемое к частоте, заданной аргументом *frequency_type*. *frequency_interval* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Дата задачи распространения. Этот параметр используется, если аргумент *frequency_type* имеет значение 32 (ежемесячное относительное). *frequency_relative_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
|NULL (по умолчанию)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Коэффициент повторения, используемый в *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_subday = ] frequency_subday`Частота повторного планирования в течение заданного периода (в минутах). *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4**|Минута|  
|**8**|Час|  
|NULL (по умолчанию)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Интервал для *frequency_subday*. *frequency_subday_interval* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Время суток, когда запланировано первое выполнение задачи распространения, в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Время суток, когда запланировано выполнение задачи распространения, в формате ЧЧММСС. *active_end_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_date = ] active_start_date`Дата первого запланированного выполнения задачи распределения в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_date = ] active_end_date`Дата запланированной остановки задачи распространения в формате ГГГГММДД. *active_end_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'`— Необязательная Командная строка. *optional_command_line* имеет тип **nvarchar (4000)** и значение по умолчанию NULL.  
  
`[ @distribution_jobid = ] distribution_jobid`Идентификатор задания агент распространения на распространителе для подписки при изменении состояния подписки с неактивного на активное. В иных случаях он не определяется. Если в отдельный вызов этой хранимой процедуры вовлечено более одного агента распространителя, результат не определен. *distribution_jobid* является **двоичным (16)** и ЗНАЧЕНИЕМ по умолчанию NULL.  
  
`[ @from_auto_sync = ] from_auto_sync` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @ignore_distributor = ] ignore_distributor` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @offloadagent = ] remote_agent_activation`
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. Установка значения *remote_agent_activation* , отличного от **0** , приводит к ошибке.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. При установке *remote_agent_server_name* в любое значение, отличное от NULL, возникает ошибка.  
  
`[ @dts_package_name = ] 'dts_package_name'`Указывает имя пакета служб DTS. *dts_package_name* имеет тип **sysname**и значение по умолчанию NULL. Например, для пакета с именем **DTSPub_Package** можно указать `@dts_package_name = N'DTSPub_Package'`.  
  
`[ @dts_package_password = ] 'dts_package_password'`Указывает пароль для пакета. *dts_package_password* имеет тип **sysname** и значение по умолчанию NULL, которое указывает, что свойство Password должно остаться без изменений.  
  
> [!NOTE]  
>  У пакета служб DTS должен быть пароль.  
  
`[ @dts_package_location = ] dts_package_location`Указывает расположение пакета. *dts_package_location* имеет **тип int**и значение по умолчанию **0**. Если значение **равно 0**, расположение пакета находится на распространителе. Если значение равно **1**, расположение пакета находится на подписчике. Расположение пакета может быть распространителем или подписчиком.  
  
`[ @skipobjectactivation = ] skipobjectactivation` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @distribution_job_name = ] 'distribution_job_name'`Имя задания распространения. *distribution_job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  при изменении свойств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] статьи издателя не следует использовать издатель.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_changesubstatus** используется в репликации моментальных снимков и репликации транзакций.  
  
 **sp_changesubstatus** изменяет состояние подписчика в таблице **syssubscriptions** с измененным состоянием. При необходимости обновляет состояние статьи в таблице **sysarticles** , чтобы указать на активное или неактивное значение. При необходимости он устанавливает или отключает флаг репликации в таблице **sysobjects** для реплицированной таблицы.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , предопределенной роли базы данных **db_owner** или создатель подписки могут выполнять **sp_changesubstatus**.  
  
## <a name="see-also"></a>См. также  
 [sp_addsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpdistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
