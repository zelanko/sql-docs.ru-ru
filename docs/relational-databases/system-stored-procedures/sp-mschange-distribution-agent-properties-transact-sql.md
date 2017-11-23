---
title: "sp_MSchange_distribution_agent_properties (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_MSchange_distribution_agent_properties
- sp_MSchange_distribution_agent_properties_TSQL
helpviewer_keywords: sp_MSchange_distribution_agent_properties
ms.assetid: 7dac5e68-bf84-433a-a531-66921f35126f
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a08ef7bb0fbbfcdfffd676c63bc2f1396fed4e5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spmschangedistributionagentproperties-transact-sql"></a>sp_MSchange_distribution_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства задания агента распространителя, выполняющегося на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии распространителя. Эта хранимая процедура используется для изменения свойств, если издатель запущен на экземпляре [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Эта хранимая процедура выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_MSchange_distribution_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @subscriber = ] 'subscriber'   
        , [ @subscriber_db = ] 'subscriber_db'   
        , [ @property = ] 'property'   
        , [ @value = ] 'value' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher**  =] **"***издатель***"**  
 Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher_db=** ] **"***publisher_db***"**  
 Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publication =** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@subscriber=** ] **"***подписчика***"**  
 Имя подписчика. *подписчик* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@subscriber_db=** ] **"***subscriber_db***"**  
 Имя базы данных подписки. *subscriber_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@property =** ] **"***свойство***"**  
 Изменяемое свойство публикации. *Свойство* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@value =** ] **"***значение***"**  
 Новое значение свойства. *значение* — **nvarchar(524)**, значение по умолчанию NULL.  
  
 В следующей таблице приводятся свойства задания агента распространителя, доступные для изменения, а также ограничения на значения этих свойств.  
  
|Свойство|Значение|Description|  
|--------------|-----------|-----------------|  
|**distrib_job_login**||Имя входа учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой выполняется агент.|  
|**distrib_job_password**||Пароль учетной записи Windows, под которой запускается задание агента.|  
|**subscriber_catalog**||Каталог, используемый при соединении с поставщиком OLE DB. *Данное свойство допустимо только для не -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *подписчиков.*|  
|**subscriber_datasource**||Имя источника данных, понятное поставщику OLE DB. *Данное свойство допустимо только для не -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *подписчиков.*|  
|**subscriber_location**||Местоположение базы данных, понятное поставщику OLE DB. *Данное свойство допустимо только для не -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *подписчиков.*|  
|**subscriber_login**||Имя входа, используемое при подключении к подписчику для синхронизации подписки.|  
|**subscriber_password**||Пароль подписчика.<br /><br /> [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]|  
|**subscriber_provider**||Уникальный программный идентификатор (PROGID), с которым зарегистрирован поставщик OLE DB для источника данных, не относящихся к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Данное свойство допустимо только для не -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *подписчиков.*|  
|**subscriber_providerstring**||Идентифицирующая источник данных строка соединения, зависящая от поставщика OLE DB. *Данное свойство допустимо только для подписчиков, отличных от подписчиков SQL Server.*|  
|**subscriber_security_mode**|**1**|Проверка подлинности Windows.<br /><br /> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]|  
||**0**|Проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**subscriber_type**|**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Подписчик|  
||**1**|Сервер источника данных ODBC|  
||**3**|Поставщик OLE DB|  
|**потоки подписки**||Обозначает количество соединений, разрешенных для агента распространителя с тем, чтобы он применял пакеты изменений параллельно с подписчиком. *Не поддерживается для не -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *подписчиков, издателей Oracle или для одноранговых подписок.*|  
  
> [!NOTE]  
>  После изменения имени входа и пароля агента необходимо остановить и повторно запустить агент, чтобы изменения вступили в силу.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_MSchange_distribution_agent_properties** используется в репликации моментальных снимков и репликации транзакций.  
  
 Если издатель запущен на экземпляре [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии, следует использовать [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md) для изменения свойств задания агента слияния, синхронизирующего принудительную подписку, выполняется на распространителе.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера на распространителе могут выполнять **sp_MSchange_distribution_agent_properties**.  
  
## <a name="see-also"></a>См. также:  
 [sp_addpushsubscription_agent &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)   
 [sp_addsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)  
  
  
