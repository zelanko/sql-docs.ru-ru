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
ms.openlocfilehash: 278af2ca1bd6abdb84cdf2371628c6b95662e46e
ms.sourcegitcommit: eae9efe2a2d3758685e85039ffb8fa698aa47f9b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73962412"
---
# <a name="sp_addsubscriber-transact-sql"></a>sp_addsubscriber (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

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
`[ @subscriber = ] 'subscriber'` — имя сервера, добавляемого в качестве допустимого подписчика на публикации на этом сервере. Аргумент *Subscriber* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @type = ] type` — это тип подписчика. *Type имеет тип* **tinyint**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0** (по умолчанию)|Подписчик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)]|  
|**1**|Сервер источника данных ODBC|  
|**2**|База данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet|  
|**3**|Поставщик OLE DB|  
  
`[ @login = ] 'login'` — это идентификатор входа для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @password = ] 'password'` — это пароль для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Password* имеет тип **nvarchar (524)** и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @commit_batch_size = ] commit_batch_size` этот параметр устарел и поддерживается для обратной совместимости скриптов.  
  
> [!NOTE]  
>  Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @status_batch_size = ] status_batch_size` этот параметр устарел и поддерживается для обратной совместимости скриптов.  
  
> [!NOTE]  
>  Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @flush_frequency = ] flush_frequency` этот параметр устарел и поддерживается для обратной совместимости скриптов.  
  
> [!NOTE]  
>  Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_type = ] frequency_type` — это частота, с которой будет планироваться агент репликации. *frequency_type* имеет **тип int**и может принимать одно из следующих значений.  
  
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
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_interval = ] frequency_interval` — это значение, применяемое к частоте, установленной *frequency_type*. *frequency_interval* имеет **тип int**и значение по умолчанию 1.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` — это Дата агента репликации. Этот параметр используется, если *frequency_type* установлен в значение **32** (ежемесячное относительное расписание). *frequency_relative_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` — фактор повторения, используемый *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию **0**.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_subday = ] frequency_subday` — Частота повторного планирования в течение заданного периода. *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4** (по умолчанию)|Минута|  
|**8**|Час|  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` — интервал для *frequency_subday*. *frequency_subday_interval* имеет **тип int**и значение по умолчанию **5**.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` — время суток, когда запланирован первый запуск агента репликации, в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и значение по умолчанию **0**.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` — время суток, когда прекращается выполнение агента репликации, в формате ЧЧММСС. *active_end_time_of_day*имеет **тип int**и значение по умолчанию 235959, то есть 11:59:59 P.M. в 24-часовом формате.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_start_date = ] active_start_date` — Дата первого запланированного запуска агента репликации в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию 0.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_end_date = ] active_end_date` — это дата, когда запланировано прекращение выполнения агента репликации в формате ГГГГММДД. *active_end_date* имеет **тип int**и значение по умолчанию 99991231, что означает 31 декабря 9999.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @description = ] 'description'` является текстовым описанием подписчика. *Description* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  
  
`[ @security_mode = ] security_mode` является реализованным режимом безопасности. *security_mode* имеет **тип int**и значение по умолчанию 1. **0** указывает проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **1** указывает проверку подлинности Windows.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @encrypted_password = ] encrypted_password` этот параметр является устаревшим и предоставляется для обеспечения обратной совместимости, при этом *encrypted_password* любое значение, но **0** приведет к ошибке.  
  
`[ @publisher = ] 'publisher'` указывает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  *Издатель* не следует использовать при публикации из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_addsubscriber** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 **sp_addsubscriber** не требуется, если подписчик будет иметь только анонимные подписки на публикации слиянием.  
  
 **sp_addsubscriber** запись в таблицу [MSsubscriber_info](../../relational-databases/system-tables/mssubscriber-info-transact-sql.md) в базе данных **распространителя** .  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_addsubscriber**.  
  
## <a name="see-also"></a>См. также статью  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [sp_changesubscriber &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)  
 [sp_dropsubscriber &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)  
 [sp_helpsubscriberinfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)  
  
  
