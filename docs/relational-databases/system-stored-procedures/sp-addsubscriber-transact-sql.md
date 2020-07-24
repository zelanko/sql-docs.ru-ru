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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f83d85ab2a79a4f5f27143de655f7748fe7f0fd4
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86915306"
---
# <a name="sp_addsubscriber-transact-sql"></a>sp_addsubscriber (Transact-SQL)
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]

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
`[ @subscriber = ] 'subscriber'`Имя сервера, добавляемого в качестве допустимого подписчика на публикации на этом сервере. Аргумент *Subscriber* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @type = ] type`Тип подписчика. *Type имеет тип* **tinyint**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0** (по умолчанию)|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Подписчик|  
|**1**|Сервер источника данных ODBC|  
|**2**|База данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet|  
|**3**|Поставщик OLE DB|  
  
`[ @login = ] 'login'`Идентификатор входа для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @password = ] 'password'`Пароль для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. *Password* имеет тип **nvarchar (524)** и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @commit_batch_size = ] commit_batch_size`Этот параметр является устаревшим и поддерживается для обратной совместимости скриптов.  
  
> [!NOTE]  
>  Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @status_batch_size = ] status_batch_size`Этот параметр является устаревшим и поддерживается для обратной совместимости скриптов.  
  
> [!NOTE]  
>  Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @flush_frequency = ] flush_frequency`Этот параметр является устаревшим и поддерживается для обратной совместимости скриптов.  
  
> [!NOTE]  
>  Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_type = ] frequency_type`Частота, с которой необходимо запланировать агент репликации. *frequency_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Один раз.|  
|**2**|По запросу|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно с относительной датой|  
|**64** (по умолчанию)|Автозапуск|  
|**128**|Повторяющееся задание|  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_interval = ] frequency_interval`Значение, применяемое к частоте, установленной *frequency_type*. *frequency_interval* имеет **тип int**и значение по умолчанию 1.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Дата агента репликации. Этот параметр используется, если *frequency_type* установлен в значение **32** (ежемесячное относительное расписание). *frequency_relative_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Первое|  
|**2**|Second|  
|**4**|Третье|  
|**8**|Четвертая|  
|**16**|Последний|  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Коэффициент повторения, используемый *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию **0**.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_subday = ] frequency_subday`Частота повторного планирования в течение заданного периода. *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Second|  
|**4** (по умолчанию)|Минута|  
|**8**|Час|  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Интервал для *frequency_subday*. *frequency_subday_interval* имеет **тип int**и значение по умолчанию **5**.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Время суток, когда запланирован первый запуск агента репликации, в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и значение по умолчанию **0**.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Время суток, когда запланирована остановка агента репликации, в формате ЧЧММСС. *active_end_time_of_day*имеет **тип int**и значение по умолчанию 235959, то есть 11:59:59 P.M. в 24-часовом формате.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_start_date = ] active_start_date`Дата первого запланированного запуска агента репликации в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию 0.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @active_end_date = ] active_end_date`Дата запланированной остановки агента репликации в формате ГГГГММДД. *active_end_date* имеет **тип int**и значение по умолчанию 99991231, что означает 31 декабря 9999.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @description = ] 'description'`Текстовое описание подписчика. *Description* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  
  
`[ @security_mode = ] security_mode`Реализованный режим безопасности. *security_mode* имеет **тип int**и значение по умолчанию 1. **0** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности. **1** указывает проверку подлинности Windows.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Свойство теперь указывается для каждой подписки при выполнении [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Если значение указано, то оно используется в качестве значения по умолчанию при создании подписок на данном подписчике и при возвращении предупреждающего сообщения.  
  
`[ @encrypted_password = ] encrypted_password`Этот параметр является устаревшим и предоставляется для обеспечения обратной совместимости, если параметру *encrypted_password* любое значение, но **0** приведет к ошибке.  
  
`[ @publisher = ] 'publisher'`Указывает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  При публикации с издателя не следует использовать *Издатель* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_addsubscriber** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 **sp_addsubscriber** не требуется, если подписчик будет иметь только анонимные подписки на публикации слиянием.  
  
 **sp_addsubscriber** запись в таблицу [MSsubscriber_info](../../relational-databases/system-tables/mssubscriber-info-transact-sql.md) в базе данных **распространителя** .  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_addsubscriber**.  
  
## <a name="see-also"></a>См. также  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [sp_changesubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpsubscriberinfo (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)  
  
  
