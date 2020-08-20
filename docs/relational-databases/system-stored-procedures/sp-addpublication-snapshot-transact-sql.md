---
description: sp_addpublication_snapshot (Transact-SQL)
title: sp_addpublication_snapshot (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpublication_snapshot_TSQL
- sp_addpublication_snapshot
helpviewer_keywords:
- sp_addpublication_snapshot
ms.assetid: 192b6214-df6e-44a3-bdd4-9d933a981619
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 764147434455852ef09fa70768b3b71d68cc913c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489625"
---
# <a name="sp_addpublication_snapshot-transact-sql"></a>sp_addpublication_snapshot (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Создает агент моментальных снимков для указанной публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addpublication_snapshot [ @publication= ] 'publication'  
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
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @frequency_type = ] frequency_type` Частота, с которой выполняется агент моментальных снимков. *frequency_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно.|  
|**4** (по умолчанию)|Ежедневно.|  
|**8**|Еженедельно.|  
|**16**|Ежемесячно.|  
|**32**|Ежемесячно относительно интервала частоты.|  
|**64**|При запуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**128**|Запускать, когда компьютер простаивает|  
  
`[ @frequency_interval = ] frequency_interval` Значение, применяемое к частоте, установленной *frequency_type*. *frequency_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение аргумента frequency_type|Воздействие на аргумент frequency_interval|  
|------------------------------|-----------------------------------|  
|**1**|*frequency_interval* не используется.|  
|**4** (по умолчанию)|Каждые *frequency_interval* дней и по умолчанию ежедневно.|  
|**8**|*frequency_interval* является одним или несколькими следующими (в сочетании с логическим оператором [&#124; (побитовое или)](../../t-sql/language-elements/bitwise-or-transact-sql.md) ):<br /><br /> **1** = воскресенье &#124;<br /><br /> **2** = понедельник &#124;<br /><br /> **4** = вторник &#124;<br /><br /> **8** = среда &#124;<br /><br /> **16** = четверг &#124;<br /><br /> **32** = Пятница &#124;<br /><br /> **64** = Суббота|  
|**16**|В *frequency_interval* день месяца.|  
|**32**|*frequency_interval* является одним из следующих:<br /><br /> **1** = воскресенье &#124;<br /><br /> **2** = понедельник &#124;<br /><br /> **3** = вторник &#124;<br /><br /> **4** = среда &#124;<br /><br /> **5** = четверг &#124;<br /><br /> **6** = Пятница &#124;<br /><br /> **7** = Суббота &#124;<br /><br /> **8** = день &#124;<br /><br /> **9** = &#124; дня недели<br /><br /> **10** = выходной день|  
|**64**|*frequency_interval* не используется.|  
|**128**|*frequency_interval* не используется.|  
  
`[ @frequency_subday = ] frequency_subday` Единица измерения для *freq_subday_interval*. *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Second|  
|**4** (по умолчанию)|Минута|  
|**8**|Час|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Интервал для *frequency_subday*. *frequency_subday_interval* имеет **тип int**и значение по умолчанию 5, что означает каждые 5 минут.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Дата выполнения агент моментальных снимков. *frequency_relative_interval* имеет **тип int**и значение по умолчанию 1.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Коэффициент повторения, используемый *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию 0.  
  
`[ @active_start_date = ] active_start_date` Дата первого запланированного запуска агент моментальных снимков в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию 0.  
  
`[ @active_end_date = ] active_end_date` Дата прекращения расписания агент моментальных снимков в формате ГГГГММДД. *active_end_date* имеет **тип int**и значение по умолчанию 99991231, что означает 31 декабря 9999.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Время первого запланированного агент моментальных снимков в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и значение по умолчанию 0.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Время суток, когда запланировать агент моментальных снимков прекращается в формате ЧЧММСС. *active_end_time_of_day* имеет **тип int**и значение по умолчанию 235959, то есть 11:59:59 P.M. в 24-часовом формате.  
  
`[ @snapshot_job_name = ] 'snapshot_agent_name'` Имя существующего агент моментальных снимков имени задания, если используется существующее задание. *snapshot_agent_name* имеет тип **nvarchar (100)** и значение по умолчанию NULL. Этот параметр предназначен для внутреннего использования и не указывается при создании новой публикации. Если указан *snapshot_agent_name* , *job_login* и *job_password* должны иметь значение null.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Режим безопасности, используемый агентом при соединении с издателем. *publisher_security_mode* имеет значение **smallint**и значение по умолчанию 1. **0** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности, а **1** — проверка подлинности Windows. Значение **0** должно быть указано для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, отличных от. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Имя входа, используемое при соединении с издателем. Аргумент *publisher_login* имеет тип **sysname**и значение по умолчанию NULL. необходимо указать *publisher_login* , если *publisher_security_mode* равен **0**. Если *publisher_login* имеет значение null, а *publisher_security_mode* равен **1**, то при соединении с издателем будет использоваться учетная запись, указанная в *job_login* .  
  
`[ @publisher_password = ] 'publisher_password'` Пароль, используемый при соединении с издателем. Аргумент *publisher_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. В целях повышения безопасности рекомендуется вводить имена входа и пароли во время выполнения.  
  
`[ @job_login = ] 'job_login'` Имя входа для учетной записи, под которой выполняется агент. В Управляемый экземпляр Azure SQL используйте учетную запись SQL Server. *job_login* имеет тип **nvarchar (257)** и значение по умолчанию NULL. Эта учетная запись всегда используется для соединений агента с распространителем. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков.  
  
> [!NOTE]
>  Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, отличных от, это должно быть одно и то же имя входа, указанное в [Sp_adddistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md).  
  
`[ @job_password = ] 'job_password'` Пароль для учетной записи Windows, под которой запускается агент. Аргумент *job_password* имеет тип **sysname**и не имеет значения по умолчанию. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. В целях повышения безопасности рекомендуется вводить имена входа и пароли во время выполнения.  
  
`[ @publisher = ] 'publisher'` Указывает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  При создании агент моментальных снимков на издателе не следует использовать *Издатель* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_addpublication_snapshot** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addpublication-snapsh_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addpublication_snapshot**.  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Создание и применение моментального снимка](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)   
 [sp_startpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
