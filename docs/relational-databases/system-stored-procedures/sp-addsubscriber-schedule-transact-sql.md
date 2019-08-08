---
title: sp_addsubscriber_schedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsubscriber_schedule_TSQL
- sp_addsubscriber_schedule
helpviewer_keywords:
- sp_addsubscriber_schedule
ms.assetid: a6225033-5c3b-452f-ae52-79890a3590ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7baa7419620fd25be06a731894432862bfba2b96
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769046"
---
# <a name="sp_addsubscriber_schedule-transact-sql"></a>Хранимая процедура sp_addsubscriber_schedule (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Добавляет расписание агента распространителя и агента слияния. Эта хранимая процедура выполняется на подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addsubscriber_schedule [ @subscriber = ] 'subscriber'  
    [ , [ @agent_type = ] agent_type ]  
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
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @subscriber = ] 'subscriber'`Имя подписчика. тип подписчика — **sysname**. Имя подписчика должно быть уникальным в базе данных, не должно использоваться до этого и не может иметь значения NULL.  
  
`[ @agent_type = ] agent_type`Тип агента. *agent_type* имеет значение **smallint**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0** (по умолчанию)|Агент распространителя|  
|**1**|Агент слияния.|  
  
`[ @frequency_type = ] frequency_type`Частота, с которой следует запланировать агент распространения. Аргумент *frequency_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|по запросу|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно с относительной датой|  
|**64** (по умолчанию)|Автозапуск|  
|**128**|Повторяющееся задание|  
  
`[ @frequency_interval = ] frequency_interval`Значение, применяемое к частоте, заданной аргументом *frequency_type*. *frequency_interval* имеет **тип int**и значение по умолчанию **1**.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Дата агент распространения. Этот параметр используется, если аргумент *frequency_type* имеет значение **32** (ежемесячное относительное). *frequency_relative_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Коэффициент повторения, используемый в *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию **0**.  
  
`[ @frequency_subday = ] frequency_subday`Частота повторного планирования в течение заданного периода. *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4** (по умолчанию)|Минута|  
|**8**|Час|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Интервал для *frequency_subday*. *frequency_subday_interval* имеет **тип int**и значение по умолчанию **5**.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Время первого запланированного агент распространения в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и значение по умолчанию **0**.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Время суток, когда запланировать агент распространения прекращается в формате ЧЧММСС. *active_end_time_of_day*имеет **тип int**и значение по умолчанию 235959, то есть 11:59:59 P.M. в 24-часовом формате.  
  
`[ @active_start_date = ] active_start_date`Дата первого запланированного запуска агент распространения в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию **0**.  
  
`[ @active_end_date = ] active_end_date`Дата прекращения расписания агент распространения в формате ГГГГММДД. *active_end_date* имеет **тип int**и значение по умолчанию 99991231, что означает 31 декабря 9999 г.  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  для[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя не следует указывать издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_addsubscriber_schedule** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_addsubscriber_schedule**.  
  
## <a name="see-also"></a>См. также  
 [sp_changesubscriber_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-schedule-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
