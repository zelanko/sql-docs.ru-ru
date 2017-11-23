---
title: "sp_changesubscriber (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_changesubscriber
- sp_changesubscriber_TSQL
helpviewer_keywords: sp_changesubscriber
ms.assetid: d453c451-e957-490f-b968-5e03aeddaf10
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4b52c51d2e516b8d4c4f787c8e5d56d95922b2d4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spchangesubscriber-transact-sql"></a>sp_changesubscriber (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет параметры для подписчика. Обновляется любая задача распространения для подписчика для данного издателя. Эта хранимая процедура записывает **MSsubscriber_info** таблицы в базе данных распространителя. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changesubscriber [ @subscriber= ] 'subscriber'  
    [ , [ @type= ] type ]  
    [ , [ @login= ] 'login' ]  
    [ , [ @password= ] 'password' ]  
    [ , [ @commit_batch_size= ] commit_batch_size ]  
    [ , [ @status_batch_size= ] status_batch_size ]  
    [ , [ @flush_frequency= ] flush_frequency ]  
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
    [ , [ @description= ] 'description' ]  
    [ , [ @security_mode= ] security_mode ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@subscriber=**] **"***подписчика***"**  
 Имя подписчика, на котором изменяется параметр. *подписчик* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@type=**] *типа*  
 Тип подписчика. *Тип* — **tinyint**, значение по умолчанию NULL. **0** указывает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчика. **1** указывает значение, отличное от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или другой сервер источника данных ODBC подписчика.  
  
 [  **@login=**] **"***входа***"**  
 Идентификатор входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Имя входа* — **sysname**, значение по умолчанию NULL.  
  
 [  **@password=**] **"***пароль***"**  
 Пароль для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *пароль* — **sysname**, значение по умолчанию  **%** . **%**Указывает, что нет изменений пароля не было.  
  
 [  **@commit_batch_size=**] *commit_batch_size*  
 Поддерживается только для обеспечения обратной совместимости.  
  
 [  **@status_batch_size=**] *status_batch_size*  
 Поддерживается только для обеспечения обратной совместимости.  
  
 [  **@flush_frequency=**] *flush_frequency*  
 Поддерживается только для обеспечения обратной совместимости.  
  
 [  **@frequency_type=**] *frequency_type*  
 Частота запуска задачи распространения по расписанию. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
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
  
 [  **@frequency_interval=**] *frequency_interval*  
 Интервал для *frequency_type*. *frequency_interval* — **int**, значение по умолчанию NULL.  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 Дата задачи распределения. Этот параметр используется при *frequency_type* равно **32** (относительно ежемесячно). *frequency_relative_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 Является, как часто задача распространения должна выполняться за время заданного *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию NULL.  
  
 [  **@frequency_subday=**] *frequency_subday*  
 Частота повторного планирования в течение определенного периода. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4**|Минута|  
|**8**|Час|  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Интервал для *frequence_subday*. *frequency_subday_interval* — **int**, значение по умолчанию NULL.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Время суток, на которое запланирован первый запуск задачи распространения в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию NULL.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Время, когда будет прекращено выполнение задачи распространения по расписанию, в формате ЧЧММСС. *active_end_time_of_day*— **int**, значение по умолчанию NULL.  
  
 [  **@active_start_date=**] *active_start_date*  
 Дата, когда запланирован первый запуск задачи распространения, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию NULL.  
  
 [  **@active_end_date=**] *active_end_date*  
 Дата, когда запланирован останов задачи распространения в формате ГГГГММДД. *active_end_date*— **int**, значение по умолчанию NULL.  
  
 [  **@description=**] **"***описание***"**  
 Необязательное текстовое описание. *Описание* — **nvarchar(255)**, значение по умолчанию NULL.  
  
 [  **@security_mode=**] *security_mode*  
 Реализованный режим обеспечения безопасности. *security_mode* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности|  
|**1**|Проверка подлинности Windows.|  
  
 [  **@publisher** =] **"***издатель***"**  
 Задает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать при изменении свойств статьи на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_changesubscriber** используется во всех типах репликации.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_changesubscriber**.  
  
## <a name="see-also"></a>См. также:  
 [sp_addsubscriber &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributiondb (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helpsubscriberinfo (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
