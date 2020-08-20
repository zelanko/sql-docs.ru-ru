---
description: sp_changesubscriber (Transact-SQL)
title: sp_changesubscriber (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriber
- sp_changesubscriber_TSQL
helpviewer_keywords:
- sp_changesubscriber
ms.assetid: d453c451-e957-490f-b968-5e03aeddaf10
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 54e0462bc447ce1e2125ed13fbb09f64f48f5d14
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469761"
---
# <a name="sp_changesubscriber-transact-sql"></a>sp_changesubscriber (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Изменяет параметры для подписчика. Обновляется любая задача распространения для подписчика для данного издателя. Эта хранимая процедура выполняет запись в таблицу **MSsubscriber_info** в базе данных распространителя. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
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
`[ @subscriber = ] 'subscriber'` Имя подписчика, для которого необходимо изменить параметры. Аргумент *Subscriber* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @type = ] type` Тип подписчика. *Type имеет тип* **tinyint**и значение по умолчанию NULL. **0** означает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчик. **1** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] другой подписчик сервера источника данных ODBC, отличный от или другого.  
  
`[ @login = ] 'login'`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Идентификатор входа для проверки подлинности. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL.  
  
`[ @password = ] 'password'` Пароль для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. Аргумент *Password* имеет тип **sysname**и значение по умолчанию **%** . **%** Указывает, что свойство Password не изменяется.  
  
`[ @commit_batch_size = ] commit_batch_size` Поддерживается только для обратной совместимости.  
  
`[ @status_batch_size = ] status_batch_size` Поддерживается только для обратной совместимости.  
  
`[ @flush_frequency = ] flush_frequency` Поддерживается только для обратной совместимости.  
  
`[ @frequency_type = ] frequency_type` Частота, с которой следует запланировать задачу распределения. *frequency_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Один раз.|  
|**2**|По запросу|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно с относительной датой|  
|**64**|Автозапуск|  
|**128**|Повторяющееся задание|  
  
`[ @frequency_interval = ] frequency_interval` Интервал для *frequency_type*. *frequency_interval* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Дата задачи распространения. Этот параметр используется, если *frequency_type* установлен в значение **32** (ежемесячное относительное расписание). *frequency_relative_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|First|  
|**2**|Second|  
|**4**|Третье|  
|**8**|Четвертая|  
|**16**|Последний|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Частота повторения задачи распределения во время определенных *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @frequency_subday = ] frequency_subday` Частота повторного планирования в течение заданного периода. *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Second|  
|**4**|Минута|  
|**8**|Час|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Интервал для *frequence_subday*. *frequency_subday_interval* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Время суток, когда запланировано первое выполнение задачи распространения, в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Время суток, когда запланировано выполнение задачи распространения, в формате ЧЧММСС. *active_end_time_of_day*имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_date = ] active_start_date` Дата первого запланированного выполнения задачи распределения в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_date = ] active_end_date` Дата запланированной остановки задачи распространения в формате ГГГГММДД. *active_end_date*имеет **тип int**и значение по умолчанию NULL.  
  
`[ @description = ] 'description'` Необязательное текстовое описание. *Description* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  
  
`[ @security_mode = ] security_mode` Реализованный режим безопасности. *security_mode* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности|  
|**1**|Проверка подлинности Windows|  
  
`[ @publisher = ] 'publisher'` Указывает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  При изменении свойств статьи издателя не следует использовать *Издатель* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_changesubscriber** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_changesubscriber**.  
  
## <a name="see-also"></a>См. также  
 [sp_addsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributiondb (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helpsubscriberinfo (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
