---
title: sp_changepublication_snapshot (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changepublication_snapshot_TSQL
- sp_changepublication_snapshot
helpviewer_keywords:
- sp_changepublication_snapshot
ms.assetid: 518a4618-3592-4edc-8425-cbc33cdff891
author: stevestein
ms.author: sstein
ms.openlocfilehash: f17f8b8dc95d7f99a969572658ab80bb6c22c433
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124879"
---
# <a name="spchangepublicationsnapshot-transact-sql"></a>sp_changepublication_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства агента моментальных снимков для указанной публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changepublication_snapshot [ @publication= ] 'publication'  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @snapshot_job_name = ] 'snapshot_agent_name' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @frequency_type = ] frequency_type` — Это частота запуска агента по расписанию. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|по запросу|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно с относительной датой|  
|**64**|Автозапуск|  
|**128**|Повторяющееся задание|  
|NULL (по умолчанию)||  
  
`[ @frequency_interval = ] frequency_interval` Указывает дни запуска агента. *frequency_interval* — **int**, и может принимать одно из следующих значений.  
  
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
  
`[ @frequency_subday = ] frequency_subday` Единицы измерения для *freq_subday_interval*. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4**|Минута|  
|**8**|Час|  
|NULL (по умолчанию)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию NULL.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` — Дата запуска агента моментальных снимков. *frequency_relative_interval* — **int**, значение по умолчанию NULL.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию NULL.  
  
`[ @active_start_date = ] active_start_date` Дата первого запуска агента моментальных снимков планируется, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию NULL.  
  
`[ @active_end_date = ] active_end_date` Дата плановой остановки агента моментальных снимков, в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Время суток, когда агент моментальных снимков впервые запланировано, в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Время остановки агента моментальных снимков, в формате ЧЧММСС. *active_end_time_of_day* — **int**, значение по умолчанию NULL.  
  
`[ @snapshot_job_name = ] 'snapshot_agent_name'` — Это имя существующего задания агента моментальных снимков, если используется существующее задание. *snapshot_agent_name* — **nvarchar(100)** со значением по умолчанию NULL.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Режим безопасности, используемый агентом при соединении с издателем. *publisher_security_mode* — **smallint**, значение по умолчанию NULL. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, и **1** задает проверку подлинности Windows. Значение **0** должен быть указан для отличных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Имя входа, используемое при соединении с издателем. *publisher_login* — **sysname**, значение по умолчанию NULL. *publisher_login* должен быть указан, если *publisher_security_mode* — **0**. Если *publisher_login* имеет значение NULL и *publisher_security_mode* — **1**, то учетная запись Windows, указанных в *job_login* используется, если соединения с издателем.  
  
`[ @publisher_password = ] 'publisher_password'` Пароль, используемый при соединении с издателем. *publisher_password* — **sysname**, значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @job_login = ] 'job_login'` — Это имя для учетной записи Windows, под которой запускается агент. *job_login* — **nvarchar(257)** , значение по умолчанию NULL. Для соединения агента с распространителем всегда используется эта учетная запись Windows. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков. Это единственно возможный отличается от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
`[ @job_password = ] 'job_password'` — Пароль для учетной записи Windows, под которой запускается агент. *job_password* — **sysname**, значение по умолчанию NULL. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @publisher = ] 'publisher'` Указывает, отличный от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать при создании агента моментальных снимков в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_changepublication_snapshot** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_changepublication_snapshot**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
