---
title: sp_changesubscription (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 10/28/2015
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
- changesubscription
- sp_changesubscription
- changesubscription_TSQL
- sp_changesubscription_TSQL
helpviewer_keywords:
- sp_changesubscription
ms.assetid: f9d91fe3-47cf-4915-b6bf-14c9c3d8a029
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5deb6f968da296368f7c3a2d3afdd1d0c301a152
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spchangesubscription-transact-sql"></a>sp_changesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства моментального снимка или транзакционной принудительной подписки или подписки по запросу, участвующей в репликации транзакций, обновляемой посредством очередей. Для изменения свойств всех других типов подписок по запросу, используйте [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md). **sp_changesubscription** выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре СУБД (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changesubscription [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
        , [ @property = ] 'property'  
        , [ @value = ] 'value'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publication**=] **"***публикации***"**  
 Имя публикации, которую нужно изменить. *Публикация*— **sysname**, не имеет значения по умолчанию  
  
 [ **@article** =] **"***статьи***"**  
 Имя изменяемой статьи. *статья* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@subscriber** =] **"***подписчика***"**  
 Имя подписчика. *подписчик* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@destination_db** =] **"***destination_db***"**  
 Имя базы данных подписки. *destination_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@property=**] **"***свойство***"**  
 Свойство, изменяемое для данной подписки. *Свойство* — **nvarchar(30)**, и может принимать одно из значений в таблице.  
  
 [  **@value=**] **"***значение***"**  
 Новое значение для указанного *свойства*. *значение* — **nvarchar(4000)**, и может принимать одно из значений в таблице.  
  
|property|Значение|Описание|  
|--------------|-----------|-----------------|  
|**distrib_job_login**||Имя входа учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой выполняется агент.|  
|**distrib_job_password**||Пароль учетной записи Windows, от имени которой выполняется агент.|  
|**subscriber_catalog**||Каталог, используемый при соединении с поставщиком OLE DB. Данное свойство допустимо только для не -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.|  
|**subscriber_datasource**||Имя источника данных, понятное поставщику OLE DB. *Данное свойство допустимо только для не -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *подписчиков.*|  
|**subscriber_location**||Местоположение базы данных, понятное поставщику OLE DB. *Данное свойство допустимо только для не -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *подписчиков.*|  
|**subscriber_login**||Имя входа на подписчик.|  
|**subscriber_password**||Надежный пароль для указанного имени входа.|  
|**subscriber_security_mode**|**1**|При подключении к подписчику используется проверка подлинности Windows.|  
||**0**|При подключении к подписчику используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**subscriber_provider**||Уникальный программный идентификатор (PROGID), с которым зарегистрирован поставщик OLE DB для источника данных, не относящихся к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Данное свойство допустимо только для не -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *подписчиков.*|  
|**subscriber_providerstring**||Идентифицирующая источник данных строка соединения, зависящая от поставщика OLE DB. *Данное свойство допустимо только для не -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *подписчиков.*|  
|**потоки подписки**||Количество дозволенных соединений на каждого агента распространителя при применении пакета изменения параллельно с подписчиком. Диапазон значений от **1** для **64** поддерживается для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей. Это свойство должно быть **0** для отличного[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков, издателей Oracle или одноранговых для подписки.|  
|**subscriber_type**|**1**|Сервер источника данных ODBC|  
||**3**|Поставщик OLE DB|  
|**оптимизированные для памяти**|**бит**|Указывает, что подписка поддерживает оптимизированные для памяти таблицы. *memory_optimized* — **бит**, где 1 равен true (подписка поддерживает оптимизированные для памяти таблицы).|  
  
 [  **@publisher =** ] **"***издатель***"**  
 Задает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует указывать для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_changesubscription** используется в моментальных снимков и репликации транзакций.  
  
 **sp_changesubscription** может использоваться только для изменения свойств принудительных подписок или подписки по запросу участвующих в репликации транзакций обновление посредством очередей. Для изменения свойств всех других типов подписок по запросу, используйте [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md).  
  
 После изменения имени входа и пароля агента необходимо остановить и повторно запустить агент, чтобы изменения вступили в силу.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_changesubscription**.  
  
## <a name="see-also"></a>См. также  
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
