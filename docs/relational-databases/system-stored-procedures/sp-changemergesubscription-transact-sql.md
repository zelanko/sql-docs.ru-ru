---
title: sp_changemergesubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergesubscription_TSQL
- sp_changemergesubscription
helpviewer_keywords:
- sp_changemergesubscription
ms.assetid: fd820f35-c189-4e2d-884d-b60c1c469f58
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3b37e09147652e856ac0c4c8160c1d7d3caf6f6d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993130"
---
# <a name="spchangemergesubscription-transact-sql"></a>sp_changemergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет выбранные свойства принудительной подписки слиянием. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changemergesubscription [ [ @publication= ] 'publication' ]  
    [ , [ @subscriber= ] 'subscriber'  
    [ , [ @subscriber_db= ] 'subscriber_db' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации, который требуется изменить. *Публикация* — **sysname**, значение по умолчанию NULL. Публикация уже должна существовать и соответствовать правилам для идентификаторов.  
  
`[ @subscriber = ] 'subscriber'` — Имя подписчика. *подписчик* — **sysname**, значение по умолчанию NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'` — Имя базы данных подписки. *subscriber_db*— **sysname**, значение по умолчанию NULL.  
  
`[ @property = ] 'property'` — Это свойство, изменяемое для данной публикации. *Свойство* — **sysname**, и может принимать одно из значений в таблице.  
  
`[ @value = ] 'value'` Новое значение для указанного *свойство*. *значение* — **nvarchar(255)**, и может принимать одно из значений в таблице.  
  
|Свойство|Значение|Описание|  
|--------------|-----------|-----------------|  
|**Описание**||Описание этой подписки слиянием.|  
|**priority**||Приоритет подписки. При обнаружении конфликтов применяемый по умолчанию сопоставитель выбирает победителя исходя из приоритетов.|  
|**merge_job_login**||Имя входа учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой выполняется агент.|  
|**merge_job_password**||Пароль учетной записи Windows, от имени которой выполняется агент.|  
|**publisher_security_mode**|**1**|При подключении к подписчику используется проверка подлинности Windows.|  
||**0**|При подключении к издателю используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**publisher_login**||Имя входа на издатель.|  
|**publisher_password**||Надежный пароль для указанного имени входа на издатель.|  
|**subscriber_security_mode**|**1**|При подключении к подписчику используется проверка подлинности Windows.|  
||**0**|При подключении к подписчику используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**subscriber_login**||Имя входа на подписчик.|  
|**subscriber_password**||Надежный пароль для указанного имени входа на подписчик.|  
|**sync_type**|**Автоматически**|Схема и начальные данные для опубликованных таблиц вначале передаются подписчику.|  
||**Нет**|Подписчик уже имеет схему и начальные данные для опубликованных таблиц; системные таблицы и данные передаются всегда.|  
|**use_interactive_resolver**|**true**|Возможно разрешение конфликтов в интерактивном режиме для всех статей, которые позволяют разрешение конфликтов в интерактивном режиме.|  
||**false**|Конфликты разрешаются в автоматическом режиме с помощью применяемого по умолчанию или пользовательского сопоставителя.|  
|NULL (по умолчанию)|NULL (по умолчанию)||  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_changemergesubscription** используется в репликации слиянием.  
  
 После изменения имени входа и пароля агента необходимо остановить и повторно запустить агент, чтобы изменения вступили в силу.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_changemergesubscription**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
