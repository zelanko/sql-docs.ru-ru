---
title: sp_addsubscriber (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsubscriber
- sp_addsubscriber_TSQL
helpviewer_keywords:
- sp_addsubscriber
ms.assetid: b8a584ea-2a26-4936-965b-b84f026e39c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb21731dd02fee4ec3779affed56f85e5dbc0e9b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079228"
---
# <a name="spaddsubscriber-transact-sql"></a>sp_addsubscriber (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет нового подписчика на издатель, разрешая ему получать публикации. Эта хранимая процедура выполняется в базе данных публикации на издателе для публикаций моментальных снимков и транзакций; а для публикаций слиянием с использованием удаленного распространителя эта хранимая процедура выполняется на распространителе.  
  
> [!IMPORTANT]  
>  Данная хранимая процедура является устаревшей. Явная регистрация подписчика на издателе больше не требуется.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addsubscriber [ @subscriber = ] 'subscriber'  
    [ , [ @type = ] type ]   
    [ , [ @login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @commit_batch_size = ] commit_batch_size ]  
    [ , [ @status_batch_size = ] status_batch_size ]  
    [ , [ @flush_frequency = ] flush_frequency ]  
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
    [ , [ @description = ] 'description' ]  
    [ , [ @security_mode = ] security_mode ]  
    [ , [ @encrypted_password = ] encrypted_password ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @subscriber = ] 'subscriber'` — Имя сервера, добавляемому в качестве допустимого подписчика на публикации на этом сервере. *подписчик* — **sysname**, не имеет значения по умолчанию.  
  
`[ @type = ] type` — Это тип подписчика. *Тип* — **tinyint**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0** (по умолчанию)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчик|  
|**1**|Сервер источника данных ODBC|  
|**2**|База данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet|  
|**3**|Поставщик OLE DB|  
  
`[ @login = ] 'login'` Идентификатор имени входа для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @password = ] 'password'` Пароль для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. *пароль* — **nvarchar(524)** , значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @commit_batch_size = ] commit_batch_size` Этот параметр является устаревшим и сохраняется для обратной совместимости скриптов.  
  
> [!NOTE]  
>  Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @status_batch_size = ] status_batch_size` Этот параметр является устаревшим и сохраняется для обратной совместимости скриптов.  
  
> [!NOTE]  
>  Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @flush_frequency = ] flush_frequency` Этот параметр является устаревшим и сохраняется для обратной совместимости скриптов.  
  
> [!NOTE]  
>  Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_type = ] frequency_type` Это частота запуска агента репликации. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
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
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
 [ **@frequency_interval=** ] *frequency_interval*  
 Значение, применяемое к частоте, задаваемой аргументом *frequency_type*. *frequency_interval* — **int**, значение по умолчанию 1.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` — Дата агента репликации. Этот параметр используется при *frequency_type* присваивается **32** (относительно ежемесячно). *frequency_relative_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию **0**.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_subday = ] frequency_subday` Том, как часто следует запланировать повторное выполнение в течение определенного периода. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4** (по умолчанию)|Минута|  
|**8**|Час|  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию **5**.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Время суток, когда агент репликации впервые запланировано, в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию **0**.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Время суток, когда прекращается выполнение агента репликации, в формате ЧЧММСС. *active_end_time_of_day*— **int**, значение по умолчанию 235959, означающее 23:59:59. в 24-часовом формате.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_start_date = ] active_start_date` Дата первого запуска агента репликации запланирована, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию 0.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_end_date = ] active_end_date` Дата плановой остановки агента репликации, в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию 99991231, что соответствует 31 декабря 9999 года.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @description = ] 'description'` Представляет собой текстовое описание подписчика. *Описание* — **nvarchar(255)** , значение по умолчанию NULL.  
  
`[ @security_mode = ] security_mode` — Это Реализованный режим безопасности. *security_mode* — **int**, значение по умолчанию 1. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. **1** задает проверку подлинности Windows.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь задается на основе подписки, при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @encrypted_password = ] encrypted_password` Этот параметр является устаревшим и предоставляется для обеспечения обратной совместимости, только на *encrypted_password* любое значение, но **0** приведет к ошибке.  
  
`[ @publisher = ] 'publisher'` Указывает, отличный от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не должны использоваться при публикации из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addsubscriber** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 **sp_addsubscriber** не является обязательным, если подписчик будет иметь только анонимные подписки на публикации слиянием.  
  
 **sp_addsubscriber** записывает [MSsubscriber_info](../../relational-databases/system-tables/mssubscriber-info-transact-sql.md) в таблицу **распространения** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_addsubscriber**.  
  
## <a name="see-also"></a>См. также  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)   
 [sp_changesubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)  
  
  
