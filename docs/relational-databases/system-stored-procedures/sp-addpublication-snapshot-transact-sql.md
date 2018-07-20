---
title: sp_addpublication_snapshot (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/15/2018
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
- sp_addpublication_snapshot_TSQL
- sp_addpublication_snapshot
helpviewer_keywords:
- sp_addpublication_snapshot
ms.assetid: 192b6214-df6e-44a3-bdd4-9d933a981619
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9ea774a66ea2e89eba185197d07630a6a2edc6ab
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088036"
---
# <a name="spaddpublicationsnapshot-transact-sql"></a>sp_addpublication_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

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
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@frequency_type=**] *frequency_type*  
 Частота, с которой выполняется агент моментальных снимков. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно.|  
|**4** (по умолчанию)|Ежедневно.|  
|**8**|Еженедельно.|  
|**16**|Ежемесячно.|  
|**32**|Ежемесячно относительно интервала частоты.|  
|**64**|При запуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**128**|Запускать, когда компьютер простаивает|  
  
 [  **@frequency_interval=**] *frequency_interval*  
 — Это значение, которое применяется к частоте, задаваемой аргументом *frequency_type*. *frequency_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение аргумента frequency_type|Воздействие на аргумент frequency_interval|  
|------------------------------|-----------------------------------|  
|**1**|*frequency_interval* не используется.|  
|**4** (по умолчанию)|Каждый *frequency_interval* дней, по умолчанию ежедневно.|  
|**8**|*frequency_interval* равно одному или нескольким из следующих (в сочетании с [ &#124; (побитовое или)](../../t-sql/language-elements/bitwise-or-transact-sql.md) логический оператор):<br /><br /> **1** = воскресенье&#124;<br /><br /> **2** = понедельник&#124;<br /><br /> **4** = Вторник&#124;<br /><br /> **8** = среда&#124;<br /><br /> **16** = четверг&#124;<br /><br /> **32** = Пятница&#124;<br /><br /> **64** = суббота|  
|**16**|На *frequency_interval* день месяца.|  
|**32**|*frequency_interval* является одним из следующих:<br /><br /> **1** = воскресенье&#124;<br /><br /> **2** = понедельник&#124;<br /><br /> **3** = Вторник&#124;<br /><br /> **4** = среда&#124;<br /><br /> **5** = четверг&#124;<br /><br /> **6** = Пятница&#124;<br /><br /> **7** = суббота&#124;<br /><br /> **8** = день&#124;<br /><br /> **9** = рабочий день&#124;<br /><br /> **10** = выходной день|  
|**64**|*frequency_interval* не используется.|  
|**128**|*frequency_interval* не используется.|  
  
 [  **@frequency_subday=**] *frequency_subday*  
 Единица измерения для *freq_subday_interval*. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4** (по умолчанию)|Минута|  
|**8**|Час|  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию 5, означающее каждые 5 минут.  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 Дата запуска агента моментальных снимков. *frequency_relative_interval* — **int**, значение по умолчанию 1.  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию 0.  
  
 [  **@active_start_date=**] *active_start_date*  
 Дата первого назначенного запуска агента моментальных снимков в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию 0.  
  
 [  **@active_end_date=**] *active_end_date*  
 Дата плановой остановки агента моментальных снимков в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию 99991231, что соответствует 31 декабря 9999 года.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Время первого планового запуска агента моментальных снимков в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию 0.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Время плановой остановки агента моментальных снимков в формате ЧЧММСС. *active_end_time_of_day* — **int**, значение по умолчанию 235959, означающее 23:59:59. в 24-часовом формате.  
  
 [  **@snapshot_job_name =** ] **"***snapshot_agent_name***"**  
 Имя существующего задания агента моментальных снимков, если оно используется. *snapshot_agent_name* — **nvarchar(100)** со значением по умолчанию NULL. Этот параметр предназначен для внутреннего использования и не указывается при создании новой публикации. Если *snapshot_agent_name* указан, то *job_login* и *job_password* должен иметь значение NULL.  
  
 [ **@publisher_security_mode**=] *publisher_security_mode*  
 Режим безопасности, используемый агентом при установке соединения с издателем. *publisher_security_mode* — **smallint**, значение по умолчанию 1. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, и **1** задает проверку подлинности Windows. Значение **0** должен быть указан для отличных[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [ **@publisher_login**=] **"***publisher_login***"**  
 Имя входа, используемое для соединения с издателем. *publisher_login* — **sysname**, значение по умолчанию NULL. *publisher_login* должен быть указан, если *publisher_security_mode* — **0**. Если *publisher_login* имеет значение NULL и *publisher_security_mode* — **1**, то учетная запись, указанная в *job_login* будет использоваться при соединения с издателем.  
  
 [ **@publisher_password**=] **"***publisher_password***"**  
 Пароль, используемый при соединении с издателем. *publisher_password* — **sysname**, значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. В целях повышения безопасности рекомендуется вводить имена входа и пароли во время выполнения.  
  
 [ **@job_login**=] **"***job_login***"**  
 — Это имя для учетной записи, под которой запускается агент. Azure SQL управляемом экземпляре базы данных используйте учетную запись SQL Server. *job_login* — **nvarchar(257)**, значение по умолчанию NULL. Для соединений агента с распространителем всегда используется эта учетная запись. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков.  
  
> [!NOTE]  
>  Для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, это должно быть то же имя входа, указанное в [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md).  
  
 [ **@job_password**=] **"***job_password***"**  
 Пароль для учетной записи Windows, под которой запускается агент. *job_password* — **sysname**, не имеет значения по умолчанию. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. В целях повышения безопасности рекомендуется вводить имена входа и пароли во время выполнения.  
  
 [ **@publisher**=] **"***издателя***"**  
 Задает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать при создании агента моментальных снимков в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addpublication_snapshot** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addpublication-snapsh_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addpublication_snapshot**.  
  
## <a name="see-also"></a>См. также  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Создание и применение моментального снимка](../../relational-databases/replication/create-and-apply-the-snapshot.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)   
 [sp_startpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
