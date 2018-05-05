---
title: sp_changesubscriber_schedule (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_changesubscriber_schedule
- sp_changesubscriber_schedule_TSQL
helpviewer_keywords:
- sp_changesubscriber_schedule
ms.assetid: ff84e8e2-d496-482c-b23e-38a6626596e6
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6a708393d7b442f56cf24203a609dd66dfba432a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spchangesubscriberschedule-transact-sql"></a>sp_changesubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [  **@subscriber=**] **"***подписчика***"**  
 Имя подписчика. *подписчик* — **sysname**. Имя подписчика должно быть уникальным в базе данных, не должно использоваться до этого и не может иметь значения NULL.  
  
 [  **@agent_type=**] *типа*  
 Тип агента. *Тип* — **smallint**, значение по умолчанию **0**. **0** указывает на агент распространителя. **1** указывает на агент слияния.  
  
 [  **@frequency_type=**] *frequency_type*  
 Частота запуска задачи распространения по расписанию. *frequency_type* — **int**, значение по умолчанию **64**. Существует 10 столбцов расписания.  
  
 [  **@frequency_interval=**] *frequency_interval*  
 Значение, применяемое к частоте, установленной аргументом *frequency_type*. *frequency_interval* — **int**, значение по умолчанию **1**.  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 Дата задачи распределения. *frequency_relative_interval* — **int**, значение по умолчанию **1**.  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию **0**.  
  
 [  **@frequency_subday=**] *frequency_subday*  
 Частота повторного планирования в течение определенного периода, в минутах. *frequency_subday* — **int**, значение по умолчанию **4**.  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию **5**.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Время суток, на которое запланирован первый запуск задачи распространения. *active_start_time_of_day* — **int**, значение по умолчанию **0**.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Время, когда запуск задачи распространения был удален из расписания. *active_end_time_of_day* — **int**, значение по умолчанию **235959**, означающее 23:59:59. в 24-часовом формате времени.  
  
 [  **@active_start_date=**] *active_start_date*  
 Дата, когда запланирован первый запуск задачи распространения, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию **0**.  
  
 [  **@active_end_date=**] *active_end_date*  
 Дата, когда запланирован останов задачи распространения в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию **99991231**, что соответствует 31 декабря 9999 года.  
  
 [ **@publisher**=] **"***издатель***"**  
 Указывает значение, отличное от[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать при изменении свойств статьи на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_changesubscriber_schedule** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_changesubscriber_schedule**.  
  
## <a name="see-also"></a>См. также  
 [sp_addsubscriber_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-schedule-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
