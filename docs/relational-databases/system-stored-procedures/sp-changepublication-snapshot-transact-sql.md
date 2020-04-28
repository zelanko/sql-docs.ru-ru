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
ms.openlocfilehash: 8d7252f0335e2fc83c5b8e5e27f5e41535fdc7bc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68762258"
---
# <a name="sp_changepublication_snapshot-transact-sql"></a>sp_changepublication_snapshot (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @frequency_type = ] frequency_type`Частота, с которой будет планироваться агент. *frequency_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Один раз.|  
|**2**|По запросу|  
|**4**|Ежедневно|  
|**8**|Weekly (Еженедельно);|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно с относительной датой|  
|**64**|Автозапуск|  
|**128**|Повторяющееся задание|  
|NULL (по умолчанию)||  
  
`[ @frequency_interval = ] frequency_interval`Указывает дни, в которые запускается агент. *frequency_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
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
  
`[ @frequency_subday = ] frequency_subday`Единицы измерения для *freq_subday_interval*. *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Секунда|  
|**4**|Минута|  
|**8**|Час|  
|NULL (по умолчанию)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Интервал для *frequency_subday*. *frequency_subday_interval* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Дата выполнения агент моментальных снимков. *frequency_relative_interval* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Коэффициент повторения, используемый *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_date = ] active_start_date`Дата первого запланированного запуска агент моментальных снимков в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_date = ] active_end_date`Дата прекращения расписания агент моментальных снимков в формате ГГГГММДД. *active_end_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Время первого запланированного агент моментальных снимков в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Время суток, когда запланировать агент моментальных снимков прекращается в формате ЧЧММСС. *active_end_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @snapshot_job_name = ] 'snapshot_agent_name'`Имя существующего агент моментальных снимков имени задания, если используется существующее задание. *snapshot_agent_name* имеет тип **nvarchar (100)** и значение по умолчанию NULL.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Режим безопасности, используемый агентом при соединении с издателем. *publisher_security_mode* является **smallint**и ЗНАЧЕНИЕМ по умолчанию NULL. **0** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности, а **1** — проверка подлинности Windows. Значение **0** должно быть указано для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, отличных от.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'`Имя входа, используемое при соединении с издателем. Аргумент *publisher_login* имеет тип **sysname**и значение по умолчанию NULL. необходимо указать *publisher_login* , если *publisher_security_mode* равен **0**. Если *publisher_login* имеет значение null, а *publisher_security_mode* равен **1**, то при соединении с издателем используется учетная запись Windows, указанная в *job_login* .  
  
`[ @publisher_password = ] 'publisher_password'`Пароль, используемый при соединении с издателем. Аргумент *publisher_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @job_login = ] 'job_login'`Имя входа для учетной записи Windows, под которой запускается агент. *job_login* имеет тип **nvarchar (257)** и значение по умолчанию NULL. Для соединения агента с распространителем всегда используется эта учетная запись Windows. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков. Его нельзя изменить для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от.  
  
`[ @job_password = ] 'job_password'`Пароль для учетной записи Windows, под которой запускается агент. Аргумент *job_password* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  *publisher* при создании агент моментальных снимков на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателе не следует использовать издатель.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_changepublication_snapshot** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_changepublication_snapshot**.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
