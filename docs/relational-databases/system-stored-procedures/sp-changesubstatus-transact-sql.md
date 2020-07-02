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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2daa7d007783434e0994846e41300c31b3e35162
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771355"
---
# <a name="sp_changesubstatus-transact-sql"></a>sp_changesubstatus (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

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
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и значение по умолчанию **%** . Если *Публикация* не указана, затрагиваются все публикации.  
  
`[ @article = ] 'article'`Имя статьи. Оно должно быть уникальным для публикации. Аргумент *article* имеет тип **sysname**и значение по умолчанию **%** . Если *статья* не указана, затрагиваются все статьи.  
  
`[ @subscriber = ] 'subscriber'`Имя подписчика, для которого изменяется состояние. Аргумент *Subscriber* имеет тип **sysname**и значение по умолчанию **%** . Если параметр *подписчик* не указан, состояние изменяется для всех подписчиков на указанную статью.  
  
`[ @status = ] 'status'`— Это состояние подписки в таблице **syssubscriptions** . Аргумент *Status* имеет тип **sysname**, не имеет значения по умолчанию и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**active**|Подписчик синхронизирован и получает данные.|  
|**inactive**|Запись о подписчике существует, но подписка отсутствует.|  
|**subscribed**|Подписчик запрашивает данные, но еще не синхронизирован.|  
  
`[ @previous_status = ] 'previous_status'`Предыдущее состояние подписки. Аргумент *previous_status* имеет тип **sysname**и значение по умолчанию NULL. Этот параметр позволяет изменить все подписки, имеющие это состояние, таким образом разрешая групповые функции для определенного набора подписок (например, установка всех активных подписок обратно на **подписку**).  
  
`[ @destination_db = ] 'destination_db'`Имя целевой базы данных. Аргумент *destination_db* имеет тип **sysname**и значение по умолчанию **%** .  
  
`[ @frequency_type = ] frequency_type`Частота, с которой следует запланировать задачу распределения. *frequency_type* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_interval = ] frequency_interval`Значение, применяемое к частоте, установленной *frequency_type*. *frequency_interval* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Дата задачи распространения. Этот параметр используется, если *frequency_type* установлен в значение 32 (ежемесячное относительное расписание). *frequency_relative_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**1**|Первый|  
|**2**|Секунда|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последний|  
|NULL (по умолчанию)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Коэффициент повторения, используемый *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_subday = ] frequency_subday`Частота повторного планирования в течение заданного периода (в минутах). *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Секунда|  
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
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. При установке *remote_agent_server_name* любого значения, отличного от NULL, возникает ошибка.  
  
`[ @dts_package_name = ] 'dts_package_name'`Указывает имя пакета служб DTS. *dts_package_name* имеет тип **sysname**и значение по умолчанию NULL. Например, для пакета с именем **DTSPub_Package** можно указать `@dts_package_name = N'DTSPub_Package'` .  
  
`[ @dts_package_password = ] 'dts_package_password'`Указывает пароль для пакета. Аргумент *dts_package_password* имеет тип **sysname** и значение по умолчанию NULL, которое указывает, что свойство Password должно остаться без изменений.  
  
> [!NOTE]  
>  У пакета служб DTS должен быть пароль.  
  
`[ @dts_package_location = ] dts_package_location`Указывает расположение пакета. *dts_package_location* имеет **тип int**и значение по умолчанию **0**. Если значение **равно 0**, расположение пакета находится на распространителе. Если значение равно **1**, расположение пакета находится на подписчике. Расположение пакета может быть **распространителем** или **подписчиком**.  
  
`[ @skipobjectactivation = ] skipobjectactivation` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @distribution_job_name = ] 'distribution_job_name'`Имя задания распространения. Аргумент *distribution_job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @publisher = ] 'publisher'`Указывает издателя, отличного от [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  При изменении свойств статьи издателя не следует использовать *Издатель* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_changesubstatus** используется в репликации моментальных снимков и репликации транзакций.  
  
 **sp_changesubstatus** изменяет состояние подписчика в таблице **syssubscriptions** с измененным состоянием. При необходимости обновляет состояние статьи в таблице **sysarticles** , чтобы указать на активное или неактивное значение. При необходимости он устанавливает или отключает флаг репликации в таблице **sysobjects** для реплицированной таблицы.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , **db_owner** предопределенной роли базы данных или создатель подписки могут выполнять **sp_changesubstatus**.  
  
## <a name="see-also"></a>См. также  
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
