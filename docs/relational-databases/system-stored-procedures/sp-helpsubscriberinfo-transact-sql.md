---
description: sp_helpsubscriberinfo (Transact-SQL)
title: sp_helpsubscriberinfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpsubscriberinfo
- sp_helpsubscriberinfo_TSQL
helpviewer_keywords:
- sp_helpsubscriberinfo
ms.assetid: fbabe1ec-57cf-425c-bae7-af7f5d3198fd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: db23a3861e20627a829006c22d74a368acfb349f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464171"
---
# <a name="sp_helpsubscriberinfo-transact-sql"></a>sp_helpsubscriberinfo (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Отображает сведения о подписчике. Эта хранимая процедура выполняется на подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpsubscriberinfo [ [ @subscriber =] 'subscriber']  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @subscriber = ] 'subscriber'` Имя подписчика. Аргумент *Subscriber* имеет тип **sysname**и значение по умолчанию **%** , которое возвращает всю информацию.  
  
`[ @publisher = ] 'publisher'` Имя издателя. параметр *Publisher* имеет тип **sysname**, а значение по умолчанию — имя текущего сервера.  
  
> [!NOTE]  
>  нельзя указывать *Издатель* , кроме случая, когда он является издателем Oracle.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Имя издателя.|  
|**абонент**|**sysname**|Имя подписчика.|  
|**type**|**tinyint**|Тип подписчика:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] база данных **1** = источник данных ODBC|  
|**пользователей**|**sysname**|Идентификатор входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**sysname**|Пароль для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**commit_batch_size**|**int**|Не поддерживается.|  
|**status_batch_size**|**int**|Не поддерживается.|  
|**flush_frequency**|**int**|Не поддерживается.|  
|**frequency_type**|**int**|Частота запуска агента распространителя:<br /><br /> **1** = один раз<br /><br /> **2** = по запросу<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячное относительное<br /><br /> **64** = Автозапуск<br /><br /> **128** = повторяющаяся|  
|**frequency_interval**|**int**|Значение, применяемое к частоте, установленной *frequency_type*.|  
|**frequency_relative_interval**|**int**|Дата агент распространения, используемая, если *frequency_type* имеет значение **32** (ежемесячное относительное):<br /><br /> **1** = сначала<br /><br /> **2** = секунда<br /><br /> **4** = третий<br /><br /> **8** = четвертый<br /><br /> **16** = Последняя|  
|**frequency_recurrence_factor**|**int**|Коэффициент повторения, используемый *frequency_type*.|  
|**frequency_subday**|**int**|Частота изменения расписания в течение заданного периода:<br /><br /> **1** = один раз<br /><br /> **2** = секунда<br /><br /> **4** = минута<br /><br /> **8** = час|  
|**frequency_subday_interval**|**int**|Интервал для *frequency_subday*.|  
|**active_start_time_of_day**|**int**|Время суток, на которое запланирован первый запуск агента распространителя, в формате ЧЧММСС.|  
|**active_end_time_of_day**|**int**|Время суток, на которое запланирован останов агента распространителя, в формате ЧЧММСС.|  
|**active_start_date**|**int**|Дата, когда запланирован первый запуск агента распространителя, в формате ГГГГММДД.|  
|**active_end_date**|**int**|Дата, когда запланирован останов агента распространителя, в формате ГГГГММДД.|  
|**retryattempt**|**int**|Не поддерживается.|  
|**retrydelay**|**int**|Не поддерживается.|  
|**description**|**nvarchar(255)**|Текстовое описание подписчика.|  
|**security_mode**|**int**|Реализованный режим безопасности:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Проверка подлинности Windows|  
|**frequency_type2**|**int**|Частота запуска агента слияния:<br /><br /> **1** = один раз<br /><br /> **2** = по запросу<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячное относительное<br /><br /> **64** = Автозапуск<br /><br /> **128** = повторяющаяся|  
|**frequency_interval2**|**int**|Значение, применяемое к частоте, установленной *frequency_type*.|  
|**frequency_relative_interval2**|**int**|Дата агент слияния, используемая, когда *frequency_type* имеет значение 32 (ежемесячное относительное):<br /><br /> **1** = сначала<br /><br /> **2** = секунда<br /><br /> **4** = третий<br /><br /> **8** = четвертый<br /><br /> **16** = Последняя|  
|**frequency_recurrence_factor2**|**int**|Коэффициент повторения, используемый *frequency_type * *.*|  
|**frequency_subday2**|**int**|Частота изменения расписания в течение заданного периода:<br /><br /> **1** = один раз<br /><br /> **2** = секунда<br /><br /> **4** = минута<br /><br /> **8** = час|  
|**frequency_subday_interval2**|**int**|Интервал для *frequency_subday*.|  
|**active_start_time_of_day2**|**int**|Время суток, на которое запланирован первый запуск агента слияния, в формате ЧЧММСС.|  
|**active_end_time_of_day2**|**int**|Время суток, на которое запланирован останов агента слияния, в формате ЧЧММСС.|  
|**active_start_date2**|**int**|Дата, когда запланирован первый запуск агента слияния, в формате ГГГГММДД.|  
|**active_end_date2**|**int**|Дата, когда запланирован останов агента слияния, в формате ГГГГММДД.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_helpsubscriberinfo** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , предопределенной роли базы данных **db_owner** или списка доступа к публикации для публикации могут выполнять **sp_helpsubscriberinfo**.  
  
## <a name="see-also"></a>См. также  
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_changesubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
