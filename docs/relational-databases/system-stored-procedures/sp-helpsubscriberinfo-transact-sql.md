---
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 14ab67bb9d69272960bbce3e1a7cfa059c609e3f
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589808"
---
# <a name="sphelpsubscriberinfo-transact-sql"></a>sp_helpsubscriberinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения о подписчике. Эта хранимая процедура выполняется на подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpsubscriberinfo [ [ @subscriber =] 'subscriber']  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@subscriber =** ] **"**_подписчика_**"**  
 Имя подписчика. *подписчик* — **sysname**, значение по умолчанию **%**, при котором возвращаются сведения.  
  
 [  **@publisher =** ] **"**_издателя_**"**  
 Имя издателя. *издатель* — **sysname**и значение по умолчанию — имя текущего сервера.  
  
> [!NOTE]  
>  *издатель* указывать не нужно, если он не является издателем Oracle.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**издатель**|**sysname**|Имя издателя.|  
|**подписчик**|**sysname**|Имя подписчика.|  
|**type**|**tinyint**|Тип подписчика:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных **1** = источник данных ODBC|  
|**Имя входа**|**sysname**|Идентификатор входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**sysname**|Пароль для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**commit_batch_size**|**int**|Не поддерживается.|  
|**status_batch_size**|**int**|Не поддерживается.|  
|**flush_frequency**|**int**|Не поддерживается.|  
|**frequency_type**|**int**|Частота запуска агента распространителя:<br /><br /> **1** = один раз<br /><br /> **2** = по запросу<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячное расписание<br /><br /> **64** = автозапуск<br /><br /> **128** = повторять|  
|**frequency_interval**|**int**|Значение, применяемое к частоте, задаваемой аргументом *frequency_type*.|  
|**frequency_relative_interval**|**int**|Дата агента распространителя, используемого при *frequency_type* присваивается **32** (по месячному расписанию):<br /><br /> **1** = первый<br /><br /> **2** = второй<br /><br /> **4** = третий<br /><br /> **8** = четвертый<br /><br /> **16** = последний|  
|**frequency_recurrence_factor**|**int**|Фактор периодически используемый аргументом *frequency_type*.|  
|**frequency_subday**|**int**|Частота изменения расписания в течение заданного периода:<br /><br /> **1** = однократно<br /><br /> **2** = второй<br /><br /> **4** = минута<br /><br /> **8** = час|  
|**frequency_subday_interval**|**int**|Интервал для *frequency_subday*.|  
|**active_start_time_of_day**|**int**|Время суток, на которое запланирован первый запуск агента распространителя, в формате ЧЧММСС.|  
|**active_end_time_of_day**|**int**|Время суток, на которое запланирован останов агента распространителя, в формате ЧЧММСС.|  
|**active_start_date**|**int**|Дата, когда запланирован первый запуск агента распространителя, в формате ГГГГММДД.|  
|**active_end_date**|**int**|Дата, когда запланирован останов агента распространителя, в формате ГГГГММДД.|  
|**retryattempt**|**int**|Не поддерживается.|  
|**значение retrydelay**|**int**|Не поддерживается.|  
|**Описание**|**nvarchar(255)**|Текстовое описание подписчика.|  
|**security_mode**|**int**|Реализованный режим безопасности:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] проверки подлинности Windows|  
|**frequency_type2**|**int**|Частота запуска агента слияния:<br /><br /> **1** = один раз<br /><br /> **2** = по запросу<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячное расписание<br /><br /> **64** = автозапуск<br /><br /> **128** = повторять|  
|**frequency_interval2**|**int**|Значение, применяемое к частоте, задаваемой аргументом *frequency_type*.|  
|**frequency_relative_interval2**|**int**|Дата агента слияния *frequency_type* имеет значение 32 (ежемесячное относительное расписание):<br /><br /> **1** = первый<br /><br /> **2** = второй<br /><br /> **4** = третий<br /><br /> **8** = четвертый<br /><br /> **16** = последний|  
|**frequency_recurrence_factor2**|**int**|Фактор периодически используемый аргументом *frequency_type **.*|  
|**frequency_subday2**|**int**|Частота изменения расписания в течение заданного периода:<br /><br /> **1** = однократно<br /><br /> **2** = второй<br /><br /> **4** = минута<br /><br /> **8** = час|  
|**frequency_subday_interval2**|**int**|Интервал для *frequency_subday*.|  
|**active_start_time_of_day2**|**int**|Время суток, на которое запланирован первый запуск агента слияния, в формате ЧЧММСС.|  
|**active_end_time_of_day2**|**int**|Время суток, на которое запланирован останов агента слияния, в формате ЧЧММСС.|  
|**active_start_date2**|**int**|Дата, когда запланирован первый запуск агента слияния, в формате ГГГГММДД.|  
|**active_end_date2**|**int**|Дата, когда запланирован останов агента слияния, в формате ГГГГММДД.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpsubscriberinfo** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных или списке доступа к публикации для публикации могут выполнять процедуру **sp_helpsubscriberinfo**.  
  
## <a name="see-also"></a>См. также  
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_changesubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
