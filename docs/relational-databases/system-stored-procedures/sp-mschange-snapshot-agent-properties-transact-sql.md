---
title: sp_MSchange_snapshot_agent_properties (Transact-SQL) | Документация Майкрософт
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
- sp_MSchange_snapshot_agent_properties_TSQL
- sp_MSchange_snapshot_agent_properties
helpviewer_keywords:
- sp_MSchange_snapshot_agent_properties
ms.assetid: 7947a788-3fd7-469f-84db-b03ba89a153c
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 67bd8a178ba3e7759257567fdb46af6ddd79daa4
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43019683"
---
# <a name="spmschangesnapshotagentproperties-transact-sql"></a>sp_MSchange_snapshot_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства задания агента моментальных снимков, которое выполняется в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии распространителя. Эта хранимая процедура используется для изменения свойств, когда издатель запущен на экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Эта хранимая процедура выполняется на распространителе в базе данных распространителя.  
  
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
 [ **@publisher** =] **"***издателя***"**  
 Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher_db=** ] **"***publisher_db***"**  
 Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publication =** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@frequency_type =** ] *frequency_type*  
 Частота, с которой выполняется агент моментальных снимков. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|по запросу|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**10**|Ежемесячно|  
|**20**|Ежемесячно, в соответствии с заданным интервалом|  
|**40**|При запуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 — Это значение, которое применяется к частоте, задаваемой аргументом *frequency_type*. *frequency_interval* — **int**, не имеет значения по умолчанию.  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 Единицы измерения для *freq_subday_interval*. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4**|Минута|  
|**8**|Час|  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, не имеет значения по умолчанию.  
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 Дата запуска агента моментальных снимков. *frequency_relative_interval* — **int**, не имеет значения по умолчанию.  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, не имеет значения по умолчанию.  
  
 [  **@active_start_date =** ] *active_start_date*  
 Дата первого назначенного запуска агента моментальных снимков в формате ГГГГММДД. *active_start_date* — **int**, не имеет значения по умолчанию.  
  
 [  **@active_end_date =** ] *active_end_date*  
 Дата плановой остановки агента моментальных снимков в формате ГГГГММДД. *active_end_date* — **int**, не имеет значения по умолчанию.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Время первого планового запуска агента моментальных снимков в формате ЧЧММСС. *active_start_time_of_day* — **int**, не имеет значения по умолчанию.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Время плановой остановки агента моментальных снимков в формате ЧЧММСС. *active_end_time_of_day* — **int**, не имеет значения по умолчанию.  
  
 [  **@snapshot_job_name =** ] **"***snapshot_agent_name***"**  
 Имя существующего задания агента моментальных снимков, если оно используется. *snapshot_agent_name* — **nvarchar(100)**, не имеет значения по умолчанию.  
  
 [ **@publisher_security_mode**=] *publisher_security_mode*  
 Режим безопасности, используемый агентом при установке соединения с издателем. *publisher_security_mode* — **int**, не имеет значения по умолчанию. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, и **1** задает проверку подлинности Windows. Значение **0** должен быть указан для отличных[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [ **@publisher_login**=] **"***publisher_login***"**  
 Имя входа, используемое для соединения с издателем. *publisher_login* — **sysname**, не имеет значения по умолчанию. *publisher_login* должен быть указан, если *publisher_security_mode* — **0**. Если *publisher_login* равно NULL, а издатель *_ ** security_mode* — **1**, то учетная запись Windows, указанных в *job_login* будет используется при соединении с издателем.  
  
 [ **@publisher_password**=] **"***publisher_password***"**  
 Пароль, используемый при соединении с издателем. *publisher_password* — **nvarchar(524)**, не имеет значения по умолчанию.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. В целях повышения безопасности рекомендуется вводить имена входа и пароли во время выполнения.  
  
 [ **@job_login**=] **"***job_login***"**  
 Имя входа для учетной записи Windows, под которой запускается агент. *job_login* — **nvarchar(257)**, не имеет значения по умолчанию. Для соединения агента с распространителем всегда используется эта учетная запись Windows. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков. *Это единственно возможный отличается от* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *издателя.*  
  
 [ **@job_password**=] **"***job_password***"**  
 Пароль для учетной записи Windows, под которой запускается агент. *job_password* — **sysname**, не имеет значения по умолчанию. Необходимо указывать этот аргумент при создании нового задания агента моментальных снимков.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. В целях повышения безопасности рекомендуется вводить имена входа и пароли во время выполнения.  
  
 [ **@publisher_type**=] **"***publisher_type***"**  
 Указывает тип издателя, если издатель не выполняется в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *publisher_type* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**|Используется издатель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Задает стандартного издателя Oracle.|  
|**ORACLE GATEWAY**|Используется издатель Oracle Gateway.|  
  
 Дополнительные сведения о различиях между издателями Oracle и издатель Oracle Gateway см. в разделе [Обзор публикации Oracle](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_MSchange_snapshot_agent_properties** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 Необходимо указать все параметры при выполнении **sp_MSchange_snapshot_agent_properties**. Выполнение [sp_helppublication_snapshot](../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md) для получения текущих свойств задания агента моментальных снимков.  
  
 Если издатель выполняется на экземпляре [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии, следует использовать [sp_changepublication_snapshot](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md) для изменения свойств задания агента моментальных снимков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера на распространителе могут выполнять процедуру **sp_MSchange_snapshot_agent_properties**.  
  
## <a name="see-also"></a>См. также  
 [sp_addpublication_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  
  
  
