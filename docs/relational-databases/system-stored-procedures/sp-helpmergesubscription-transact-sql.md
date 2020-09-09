---
description: sp_helpmergesubscription (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 48d40b3209311968443a6c6d2b713b4aa1e3d43a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535203"
---
# <a name="sp_helpmergesubscription-transact-sql"></a>sp_helpmergesubscription (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и значение по умолчанию **%** . Публикация уже должна существовать и соответствовать правилам идентификаторов. Если значение равно NULL или **%** , возвращаются сведения обо всех публикациях слиянием и подписках в текущей базе данных.  
  
`[ @subscriber = ] 'subscriber'` Имя подписчика. Аргумент *Subscriber* имеет тип **sysname**и значение по умолчанию **%** . Если этот аргумент равен NULL или %, возвращаются сведения обо всех подписках данной публикации.  
  
`[ @subscriber_db = ] 'subscriber_db'` Имя базы данных подписки. Аргумент *subscriber_db*имеет тип **sysname**и значение по умолчанию **%** , которое возвращает сведения обо всех базах данных подписки.  
  
`[ @publisher = ] 'publisher'` Имя издателя. Издатель должен быть действительным сервером. Аргумент *Publisher*имеет тип **sysname**и значение по умолчанию **%** , которое возвращает сведения обо всех издателях.  
  
`[ @publisher_db = ] 'publisher_db'` Имя базы данных издателя. Аргумент *publisher_db*имеет тип **sysname**и значение по умолчанию **%** , которое возвращает сведения обо всех базах данных издателя.  
  
`[ @subscription_type = ] 'subscription_type'` Тип подписки. *subscription_type*имеет тип **nvarchar (15)** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Push** (по умолчанию)|Принудительная подписка|  
|**собирает**|Подписка по запросу|  
|**как**|Обе подписки: по запросу и принудительная подписка|  
  
`[ @found = ] 'found'OUTPUT` Флаг, указывающий возвращаемые строки. Аргумент *Found*имеет **тип int** и параметр OUTPUT и значение по умолчанию NULL. **1** указывает, что публикация найдена. значение **0** указывает, что публикация не найдена.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**sysname**|Имя подписки.|  
|**публикации**|**sysname**|Имя публикации.|  
|**publisher**|**sysname**|Имя издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**абонент**|**sysname**|Имя подписчика.|  
|**subscriber_db**|**sysname**|Имя базы данных подписки.|  
|**status**|**int**|Состояние подписки.<br /><br /> **0** = все задания ожидают запуска<br /><br /> **1** = одно или несколько заданий запускаются<br /><br /> **2** = все задания выполнены успешно<br /><br /> **3** = по крайней мере одно задание исполняется<br /><br /> **4** = все задания запланированы и бездействуют<br /><br /> **5** = по крайней мере одно задание пытается выполнить после предыдущего сбоя<br /><br /> **6** = не удалось успешно выполнить по крайней мере одно задание|  
|**subscriber_type**|**int**|Тип подписчика.|  
|**subscription_type**|**int**|Тип подписки:<br /><br /> **0** = принудительная отправка<br /><br /> **1** = по запросу<br /><br /> **2** = оба|  
|**priority**|**float (8)**|Число, показывающее приоритет подписки.|  
|**sync_type**|**tinyint**|Тип синхронизации подписки.|  
|**description**|**nvarchar(255)**|Короткое описание данной подписки слиянием.|  
|**merge_jobid**|**двоичный (16)**|Идентификатор задания агента слияния.|  
|**full_publication**|**tinyint**|Подписка к полной или фильтрованной публикации.|  
|**offload_enabled**|**bit**|Указывает, установлено ли на запуск выполнение разгрузки агента репликации на подписчике. Если равно NULL, выполняется на издателе.|  
|**offload_server**|**sysname**|Имя сервера, на который запущен агент.|  
|**use_interactive_resolver**|**int**|Возвращает сведения о том, был ли использован интерактивный сопоставитель во время взаимодействия. Если значение **равно 0**, то интерактивный сопоставитель не используется.|  
|**hostname**|**sysname**|Значение, предоставляемое, если подписка фильтруется по значению функции [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) .|  
|**subscriber_security_mode**|**smallint**|Режим безопасности на подписчике, где **1** означает проверку подлинности Windows, а **0** — [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверку подлинности.|  
|**subscriber_login**|**sysname**|Имя входа на подписчике.|  
|**subscriber_password**|**sysname**|Фактический пароль подписчика никогда не возвращается. Результат скрывается **\*\*\*\*\*\*** строкой "".|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpmergesubscription** используется в репликации слиянием для возврата сведений о подписке, хранящихся на издателе, или при повторной публикации подписчика.  
  
 Для анонимных подписок значение *subscription_type*всегда равно **1** (Pull). Однако для получения сведений о анонимных подписках необходимо выполнить [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md) на подписчике.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , **db_owner** предопределенной роли базы данных или списка доступа к публикации для публикации, которой принадлежит подписка, могут выполнять **sp_helpmergesubscription**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
