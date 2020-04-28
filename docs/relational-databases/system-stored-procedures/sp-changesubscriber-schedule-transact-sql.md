---
title: sp_changesubscriber_schedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriber_schedule
- sp_changesubscriber_schedule_TSQL
helpviewer_keywords:
- sp_changesubscriber_schedule
ms.assetid: ff84e8e2-d496-482c-b23e-38a6626596e6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22ecb1601108562607d1fdc550daaa945fe72910
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68770726"
---
# <a name="sp_changesubscriber_schedule-transact-sql"></a>sp_changesubscriber_schedule (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Изменяет расписание агента распространителя или агента слияния для подписчика. Эта хранимая процедура выполняется на подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changesubscriber_schedule [ @subscriber = ] 'subscriber', [ @agent_type = ] type  
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
`[ @subscriber = ] 'subscriber'`Имя подписчика. Тип *подписчика* — **sysname**. Имя подписчика должно быть уникальным в базе данных, не должно использоваться до этого и не может иметь значения NULL.  
  
`[ @agent_type = ] type`Тип агента. *Type имеет тип* **smallint**и значение по умолчанию **0**. значение **0** указывает на агент распространения. **1** обозначает агент слияния.  
  
`[ @frequency_type = ] frequency_type`Частота, с которой следует запланировать задачу распределения. *frequency_type* имеет **тип int**и значение по умолчанию **64**. Существует 10 столбцов расписания.  
  
`[ @frequency_interval = ] frequency_interval`Значение, применяемое к частоте, установленной *frequency_type*. *frequency_interval* имеет **тип int**и значение по умолчанию **1**.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Дата задачи распространения. *frequency_relative_interval* имеет **тип int**и значение по умолчанию **1**.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Коэффициент повторения, используемый *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию **0**.  
  
`[ @frequency_subday = ] frequency_subday`Частота повторного планирования в течение заданного периода (в минутах). *frequency_subday* имеет **тип int**и значение по умолчанию **4**.  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Интервал для *frequency_subday*. *frequency_subday_interval* имеет **тип int**и значение по умолчанию **5**.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Время суток, когда запланировано первое выполнение задачи распространения. *active_start_time_of_day* имеет **тип int**и значение по умолчанию **0**.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Время суток, когда прекращается выполнение задачи распространения. *active_end_time_of_day* имеет **тип int**и значение по умолчанию **235959**, то есть 11:59:59 P.M. в 24-часовом формате времени.  
  
`[ @active_start_date = ] active_start_date`Дата первого запланированного выполнения задачи распределения в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию **0**.  
  
`[ @active_end_date = ] active_end_date`Дата запланированной остановки задачи распространения в формате ГГГГММДД. *active_end_date* имеет **тип int**и значение по умолчанию **99991231**, что означает 31 декабря 9999.  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  *publisher* при изменении свойств статьи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя не следует использовать издатель.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_changesubscriber_schedule** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_changesubscriber_schedule**.  
  
## <a name="see-also"></a>См. также:  
 [sp_addsubscriber_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-schedule-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
