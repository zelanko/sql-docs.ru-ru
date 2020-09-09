---
description: sp_link_publication (Transact-SQL)
title: sp_link_publication (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_link_publication_TSQL
- sp_link_publication
helpviewer_keywords:
- sp_link_publication
ms.assetid: 1945ed24-f9f1-4af6-94ca-16d8e864706e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b80c28d86ae4d7022ad8784adfa7ab9023e3ebd0
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543244"
---
# <a name="sp_link_publication-transact-sql"></a>sp_link_publication (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Задает сведения о конфигурации и безопасности, применяемые триггерами синхронизации немедленно обновляемых подписок при подключении к издателю. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
> [!IMPORTANT]
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
> 
> [!IMPORTANT]
>  При определенных условиях эта хранимая процедура может завершиться ошибкой, если на подписчике установлен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] пакет обновления 1 (SP1) или более поздней версии, а на издателе запущена более ранняя версия. Если в этом случае хранимая процедура завершается ошибкой, обновите издатель до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 1 (SP1) или более поздней версии.  
  
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
`[ @publisher = ] 'publisher'` Имя издателя для связи. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` Имя базы данных издателя для связи. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'` Имя публикации, с которой необходимо создать ссылку. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @security_mode = ] security_mode` Режим безопасности, используемый подписчиком для подключения к удаленному издателю для немедленного обновления. *security_mode* имеет **тип int**и может принимать одно из следующих значений. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Использует [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверку подлинности с именем входа, указанным в этой хранимой процедуре, в качестве *имени входа* и *пароля*.<br /><br /> Примечание. в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот параметр использовался для указания динамического удаленного вызова процедур (RPC).|  
|**1**|Использует контекст безопасности (проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или Windows) пользователя, редактирующего подписчика.<br /><br /> Примечание. Эта учетная запись также должна существовать у издателя с достаточными привилегиями. В случае использования проверки подлинности Windows должно поддерживаться делегирование учетной записи безопасности.|  
|**2**|Использует существующее, определяемое пользователем имя входа для связанного сервера, созданное с помощью **sp_link_publication**.|  
  
`[ @login = ] 'login'` Имя входа. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. Этот параметр должен быть указан, если *security_mode* равен **0**.  
  
`[ @password = ] 'password'` Пароль. Аргумент *Password* имеет тип **sysname**и значение по умолчанию NULL. Этот параметр должен быть указан, если *security_mode* равен **0**.  
  
`[ @distributor = ] 'distributor'` Имя распространителя. Аргумент *распространитель* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_link_publication** используется немедленно обновляемыми подписками в репликации транзакций.  
  
 **sp_link_publication** можно использовать как для принудительной подписки, так и для подписок по запросу. Ее можно вызывать как до, так и после создания подписки. Запись вставляется или обновляется в MSsubscription_properties &#40;в системной таблице [&#41;Transact-SQL ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) .  
  
 Для принудительных подписок запись может быть очищена с помощью [sp_subscription_cleanup &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md). Для подписок по запросу запись может быть очищена с помощью [sp_droppullsubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md) или [sp_subscription_cleanup &#40;transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md). Можно также вызвать **sp_link_publication** с ПАРОЛем null, чтобы очистить запись в [MSsubscription_properties &#40;системной таблице&#41;Transact-SQL ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) для обеспечения безопасности.  
  
 Режим по умолчанию, применяемый для немедленного обновления подписчика при соединении с издателем, не позволяет устанавливать соединение с проверкой подлинности Windows. Для подключения в режиме с проверкой подлинности Windows на издателе должен быть настроен связанный сервер, и это соединение должно применяться для немедленного обновления подписчика. Для этого необходимо, чтобы **sp_link_publication** был запущен с *security_mode*  =  **2**. В случае использования проверки подлинности Windows должно поддерживаться делегирование учетной записи безопасности.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent_failover](../../relational-databases/replication/codesnippet/tsql/sp-link-publication-tran_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_link_publication**.  
  
## <a name="see-also"></a>См. также:  
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [sp_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
