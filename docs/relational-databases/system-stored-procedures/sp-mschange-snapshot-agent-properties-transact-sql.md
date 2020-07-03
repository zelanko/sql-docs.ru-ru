---
title: sp_MSchange_snapshot_agent_properties (T-SQL)
description: Описывает sp_MSchange_snapshot_agent_properties хранимую процедуру, используемую для изменения свойств агент моментальных снимков, используемых для Репликация SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_snapshot_agent_properties_TSQL
- sp_MSchange_snapshot_agent_properties
helpviewer_keywords:
- sp_MSchange_snapshot_agent_properties
ms.assetid: 7947a788-3fd7-469f-84db-b03ba89a153c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ea8b10c2cb788a8f778479487c0f39f95613f524
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893515"
---
# <a name="sp_mschange_snapshot_agent_properties-transact-sql"></a>sp_MSchange_snapshot_agent_properties (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Изменяет свойства задания агент моментальных снимков, выполняемого на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] распространителе или более поздней версии. Эта хранимая процедура используется для изменения свойств, если издатель запущен на экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Эта хранимая процедура выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_MSchange_snapshot_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @frequency_type= ] frequency_type  
        , [ @frequency_interval= ] frequency_interval  
        , [ @frequency_subday= ] frequency_subday  
        , [ @frequency_subday_interval= ] frequency_subday_interval  
        , [ @frequency_relative_interval= ] frequency_relative_interval  
        , [ @frequency_recurrence_factor= ] frequency_recurrence_factor  
        , [ @active_start_date= ] active_start_date  
        , [ @active_end_date= ] active_end_date  
        , [ @active_start_time_of_day= ] active_start_time_of_day  
        , [ @active_end_time_of_day= ] active_end_time_of_day  
        , [ @snapshot_job_name = ] 'snapshot_agent_name'  
        , [ @publisher_security_mode = ] publisher_security_mode  
        , [ @publisher_login = ] 'publisher_login'  
        , [ @publisher_password = ] 'publisher_password'   
        , [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
        , [ @publisher_type = ] 'publisher_type'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных публикации. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @frequency_type = ] frequency_type`Частота, с которой выполняется агент моментальных снимков. *frequency_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|По запросу|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**10**|Ежемесячная|  
|**20**|Ежемесячно, в соответствии с заданным интервалом|  
|**40**|При запуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
`[ @frequency_interval = ] frequency_interval`Значение, применяемое к частоте, установленной *frequency_type*. *frequency_interval* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @frequency_subday = ] frequency_subday`Единицы измерения для *freq_subday_interval*. *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Секунда|  
|**4**|Минута|  
|**8**|Час|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Интервал для *frequency_subday*. *frequency_subday_interval* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Дата выполнения агент моментальных снимков. *frequency_relative_interval* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Коэффициент повторения, используемый *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @active_start_date = ] active_start_date`Дата первого запланированного запуска агент моментальных снимков в формате ГГГГММДД. *active_start_date* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @active_end_date = ] active_end_date`Дата прекращения расписания агент моментальных снимков в формате ГГГГММДД. *active_end_date* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Время первого запланированного агент моментальных снимков в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Время суток, когда запланировать агент моментальных снимков прекращается в формате ЧЧММСС. *active_end_time_of_day* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @snapshot_job_name = ] 'snapshot_agent_name'`Имя существующего агент моментальных снимков имени задания, если используется существующее задание. *snapshot_agent_name* имеет тип **nvarchar (100)** и не имеет значения по умолчанию.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Режим безопасности, используемый агентом при соединении с издателем. *publisher_security_mode* имеет **тип int**и не имеет значения по умолчанию. **0** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности, а **1** — проверка подлинности Windows. Значение **0** должно быть указано для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, отличных от. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'`Имя входа, используемое при соединении с издателем. Аргумент *publisher_login* имеет тип **sysname**и не имеет значения по умолчанию. необходимо указать *publisher_login* , если *publisher_security_mode* равен **0**. Если *publisher_login* имеет значение NULL и издатель *_ * * security_mode* равен **1**, то при соединении с издателем будет использоваться учетная запись Windows, указанная в *job_login* .  
  
`[ @publisher_password = ] 'publisher_password'`Пароль, используемый при соединении с издателем. *publisher_password* имеет тип **nvarchar (524)** и не имеет значения по умолчанию.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. В целях повышения безопасности рекомендуется вводить имена входа и пароли во время выполнения.  
  
`[ @job_login = ] 'job_login'`Имя входа для учетной записи Windows, под которой запускается агент. *job_login* имеет тип **nvarchar (257)** и не имеет значения по умолчанию. Для соединения агента с распространителем всегда используется эта учетная запись Windows. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков. *Его нельзя изменить для не относящегося к* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Издатель.*  
  
`[ @job_password = ] 'job_password'`Пароль для учетной записи Windows, под которой запускается агент. Аргумент *job_password* имеет тип **sysname**и не имеет значения по умолчанию. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. В целях повышения безопасности рекомендуется вводить имена входа и пароли во время выполнения.  
  
`[ @publisher_type = ] 'publisher_type'`Указывает тип издателя, если издатель не выполняется в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Аргумент *publisher_type* имеет тип **sysname**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**|Используется издатель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**СУБД**|Задает стандартного издателя Oracle.|  
|**ORACLE GATEWAY.**|Используется издатель Oracle Gateway.|  
  
 Дополнительные сведения о различиях между издателем Oracle и издателем шлюза Oracle см. в разделе [Общие сведения о публикации Oracle](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_MSchange_snapshot_agent_properties** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 При выполнении **sp_MSchange_snapshot_agent_properties**необходимо указать все параметры. Выполните [sp_helppublication_snapshot](../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md) , чтобы получить текущие свойства задания агент моментальных снимков.  
  
 При запуске издателя на экземпляре [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии следует использовать [sp_changepublication_snapshot](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md) для изменения свойств задания агент моментальных снимков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** на распространителе могут выполнять **sp_MSchange_snapshot_agent_properties**.  
  
## <a name="see-also"></a>См. также  
 [sp_addpublication_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  
  
  
