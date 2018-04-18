---
title: sp_link_publication (Transact-SQL) | Документы Microsoft
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
applies_to:
- SQL Server
f1_keywords:
- sp_link_publication_TSQL
- sp_link_publication
helpviewer_keywords:
- sp_link_publication
ms.assetid: 1945ed24-f9f1-4af6-94ca-16d8e864706e
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d80016d32818b0435903b71e6b2f1444fc1ae28d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="splinkpublication-transact-sql"></a>sp_link_publication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Задает сведения о конфигурации и безопасности, применяемые триггерами синхронизации немедленно обновляемых подписок при подключении к издателю. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре СУБД (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
> [!IMPORTANT]  
>  При определенных условиях данная хранимая процедура могут отклоняться на подписчике [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] пакет обновления 1 или более поздней версии, а издатель работает более ранней версии. Если в этом случае хранимая процедура завершается ошибкой, обновите издатель до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 1 (SP1) или более поздней версии.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_link_publication [ @publisher = ] 'publisher'   
        , [ @publisher_db = ] 'publisher_db'   
        , [ @publication = ] 'publication'   
        , [ @security_mode = ] security_mode  
    [ , [ @login = ] 'login' ]  
    [ , [ @password = ]'password' ]  
    [ , [ @distributor = ] 'distributor' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publisher**=] **"***издатель***"**  
 Имя издателя для связи. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@publisher_db**=] **"***publisher_db***"**  
 Имя базы данных издателя для связи. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@publication**=] **"***публикации***"**  
 Имя публикации для связи. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@security_mode**=] *security_mode*  
 Режим безопасности, который подписчик использует для подключения к удаленному издателю для немедленного обновления. *security_mode* — **int**, и может принимать одно из следующих значений. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Использует [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности с именем входа, указанное в этой хранимой процедуре как *входа* и *пароль*.<br /><br /> Примечание: В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], этот параметр используется для указания динамического удаленного вызова процедур (RPC).|  
|**1**|Использует контекст безопасности (проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или Windows) пользователя, редактирующего подписчика.<br /><br /> Примечание: Эта учетная запись должна существовать на издателе с достаточными правами. В случае использования проверки подлинности Windows должно поддерживаться делегирование учетной записи безопасности.|  
|**2**|Использует существующее, определенное пользователем имя входа связанного сервера создан с помощью **sp_link_publication**.|  
  
 [ **@login**=] **"***входа***"**  
 Имя входа. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. Этот параметр должен быть указан при *security_mode* — **0**.  
  
 [ **@password**=] **"***пароль***"**  
 Пароль. *пароль* — **sysname**, значение по умолчанию NULL. Этот параметр должен быть указан при *security_mode* — **0**.  
  
 [  **@distributor=** ] **"***распространителя***"**  
 Имя распространителя. *распространитель* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_link_publication** используется для немедленного обновления подписок при репликации транзакций.  
  
 **sp_link_publication** может использоваться для подписок, push и pull. Ее можно вызывать как до, так и после создания подписки. Запись вставляется или обновляется в [MSsubscription_properties &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) системной таблицы.  
  
 Для принудительных подписок запись можно очистить с помощью [sp_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md). Для подписок по запросу запись можно очистить с помощью [sp_droppullsubscription &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md) или [sp_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md). Можно также вызвать **sp_link_publication** с пустым паролем для очистки записи в [MSsubscription_properties &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) системной таблицы, для обеспечения безопасности.  
  
 Режим по умолчанию, применяемый для немедленного обновления подписчика при соединении с издателем, не позволяет устанавливать соединение с проверкой подлинности Windows. Для подключения в режиме с проверкой подлинности Windows на издателе должен быть настроен связанный сервер, и это соединение должно применяться для немедленного обновления подписчика. Для этого необходимо **sp_link_publication** должны выполняться с *security_mode* = **2**. В случае использования проверки подлинности Windows должно поддерживаться делегирование учетной записи безопасности.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent_failover](../../relational-databases/replication/codesnippet/tsql/sp-link-publication-tran_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_link_publication**.  
  
## <a name="see-also"></a>См. также  
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [sp_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
