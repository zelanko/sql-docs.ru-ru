---
title: sp_helpmergesubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergesubscription
- sp_helpmergesubscription_TSQL
helpviewer_keywords:
- sp_helpmergesubscription
ms.assetid: da564112-f769-4e67-9251-5699823e8c86
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0e5f044482d3e46e4e20279a437b8d9459d1d3bd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002640"
---
# <a name="sphelpmergesubscription-transact-sql"></a>sp_helpmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о подписке на публикацию слиянием (как принудительной, так и по запросу). Эта хранимая процедура выполняется на издателе в базе данных публикации или на переиздаваемом подписчике для базы данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergesubscription [ [ @publication=] 'publication']  
    [ , [ @subscriber=] 'subscriber']  
    [ , [ @subscriber_db=] 'subscriber_db']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
    [ , [ @found=] 'found' OUTPUT]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, значение по умолчанию **%** . Публикация уже должна существовать и соответствовать правилам идентификаторов. Если значение равно NULL или **%** , возвращаются сведения обо всех публикациях слиянием и подписках текущей базы данных.  
  
`[ @subscriber = ] 'subscriber'` — Имя подписчика. *подписчик* — **sysname**, значение по умолчанию **%** . Если этот аргумент равен NULL или %, возвращаются сведения обо всех подписках данной публикации.  
  
`[ @subscriber_db = ] 'subscriber_db'` — Имя базы данных подписки. *subscriber_db*— **sysname**, значение по умолчанию **%** , которое возвращает сведения обо всех базах данных подписки.  
  
`[ @publisher = ] 'publisher'` — Имя издателя. Издатель должен быть действительным сервером. *издатель*— **sysname**, значение по умолчанию **%** , который возвращает сведения обо всех издателях.  
  
`[ @publisher_db = ] 'publisher_db'` — Имя базы данных издателя. *publisher_db*— **sysname**, значение по умолчанию **%** , которое возвращает сведения обо всех базах данных издателя.  
  
`[ @subscription_type = ] 'subscription_type'` — Тип подписки. *subscription_type*— **nvarchar(15)** , и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Push-уведомлений** (по умолчанию)|Принудительная подписка|  
|**По запросу**|Подписка по запросу|  
|**оба**|Обе подписки: по запросу и принудительная подписка|  
  
`[ @found = ] 'found'OUTPUT` — Это флаг для указания возвращаемых строк. *найти*— **int** и ВЫХОДНОЙ параметр, значение по умолчанию NULL. **1** указывает, что публикация найдена. **0** указывает, что публикация не найдена.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**sysname**|Имя подписки.|  
|**публикации**|**sysname**|Имя публикации.|  
|**издатель**|**sysname**|Имя издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**подписчик**|**sysname**|Имя подписчика.|  
|**subscriber_db**|**sysname**|Имя базы данных подписки.|  
|**status**|**int**|Состояние подписки.<br /><br /> **0** = все задания ожидают запуска<br /><br /> **1** = одно или более заданий запускаются<br /><br /> **2** = все задания выполнены успешно<br /><br /> **3** = по крайней мере одно задание выполняется<br /><br /> **4** = все задания запланированы и простоя<br /><br /> **5** = по крайней мере одно задание производит попытку запуска после предыдущего сбоя<br /><br /> **6** = по крайней мере одно задание завершилось неуспешно|  
|**subscriber_type**|**int**|Тип подписчика.|  
|**subscription_type**|**int**|Тип подписки:<br /><br /> **0** = Принудительная<br /><br /> **1** = по запросу<br /><br /> **2** = both|  
|**priority**|**float(8)**|Число, показывающее приоритет подписки.|  
|**sync_type**|**tinyint**|Тип синхронизации подписки.|  
|**description**|**nvarchar(255)**|Короткое описание данной подписки слиянием.|  
|**merge_jobid**|**binary(16)**|Идентификатор задания агента слияния.|  
|**full_publication**|**tinyint**|Подписка к полной или фильтрованной публикации.|  
|**offload_enabled**|**bit**|Указывает, установлено ли на запуск выполнение разгрузки агента репликации на подписчике. Если равно NULL, выполняется на издателе.|  
|**offload_server**|**sysname**|Имя сервера, на который запущен агент.|  
|**use_interactive_resolver**|**int**|Возвращает сведения о том, был ли использован интерактивный сопоставитель во время взаимодействия. Если **0**, интерактивный Сопоставитель не используется.|  
|**Имя узла**|**sysname**|Значение задается, если подписка фильтруется по значению [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) функции.|  
|**subscriber_security_mode**|**smallint**|Режим безопасности на подписчике, где **1** означает проверку подлинности Windows, и **0** означает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности.|  
|**subscriber_login**|**sysname**|Имя входа на подписчике.|  
|**subscriber_password**|**sysname**|Фактический пароль подписчика никогда не возвращается. Результат скрывается " **\*\*\*\*\*\*** " строка.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpmergesubscription** используется в репликации слиянием для возвращения сведений о подписке, хранящиеся на издателе или переиздающем подписчике.  
  
 Для анонимных подписок *subscription_type*значение всегда равно **1** (по запросу). Тем не менее, необходимо выполнить [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md) на подписчике сведения об анонимных подписках.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных или списке доступа к публикации для публикации, к которой принадлежит подписки могут выполнять процедуру **sp_ helpmergesubscription**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
