---
title: sp_helpsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpsubscription_TSQL
- sp_helpsubscription
helpviewer_keywords:
- sp_helpsubscription
ms.assetid: ff96bcbf-e2b9-4da8-8515-d80d4ce86c16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 07259854acfcad39a583b117a51bcda9de809486
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527886"
---
# <a name="sphelpsubscription-transact-sql"></a>sp_helpsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет сведения о подписке, связанные с определенной публикацией, статьей, подписчиком или набором подписок. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpsubscription [ [ @publication = ] 'publication' ]   
    [ , [ @article = ] 'article' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @destination_db = ] 'destination_db' ]   
    [ , [ @found=] found OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя связанной публикации. *Публикация* — **sysname**, значение по умолчанию **%**, который возвращает сведения обо всех подписках для этого сервера.  
  
`[ @article = ] 'article'` — Имя статьи. *статья* — **sysname**, значение по умолчанию **%**, который возвращает сведения обо всех подписках для выбранных публикаций и подписчиков. Если **все**, возвращаются только одна запись для полной подписки на публикацию.  
  
`[ @subscriber = ] 'subscriber'` Это имя подписчика, для которого возвращаются сведения о подписке. *подписчик* — **sysname**, значение по умолчанию **%**, который возвращает сведения обо всех подписках для выбранных публикаций и статей.  
  
`[ @destination_db = ] 'destination_db'` — Имя целевой базы данных. *destination_db* — **sysname**, значение по умолчанию **%**.  
  
`[ @found = ] 'found'OUTPUT` — Это флаг для указания возвращаемых строк. *найти*— **int** и ВЫХОДНОЙ параметр, значение по умолчанию 23456.  
  
 **1** указывает, что публикация найдена.  
  
 **0** указывает, что публикация не найдена.  
  
`[ @publisher = ] 'publisher'` — Имя издателя. *издатель* — **sysname**и значение по умолчанию — имя текущего сервера.  
  
> [!NOTE]  
>  *издатель* указывать не нужно, если он не является издателем Oracle.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**подписчик**|**sysname**|Имя подписчика.|  
|**публикации**|**sysname**|Имя публикации.|  
|**Статья**|**sysname**|Имя статьи.|  
|**Целевая база данных**|**sysname**|Имя целевой базы данных, в которую помещаются реплицируемые данные.|  
|**Состояние подписки**|**tinyint**|Состояние подписки:<br /><br /> **0** = неактивно<br /><br /> **1** = подписка<br /><br /> **2** = активно|  
|**Тип синхронизации**|**tinyint**|Тип синхронизации подписки:<br /><br /> **1** = automatic<br /><br /> **2** = нет|  
|**Тип подписки**|**int**|Тип подписки:<br /><br /> **0** = Принудительная<br /><br /> **1** = по запросу<br /><br /> **2** = анонимная|  
|**Полная подписка**|**bit**|На все ли статьи публикации подписана данная подписка:<br /><br /> **0** = Нет<br /><br /> **1** = Да|  
|**имя подписки**|**nvarchar(255)**|Имя подписки.|  
|**режим обновления**|**int**|**0** = только для чтения<br /><br /> **1** = немедленно обновляемая подписка|  
|**Идентификатор задания распространения**|**binary(16)**|Идентификатор задания агента распространителя.|  
|**loopback_detection**|**bit**|Механизм распознавания обратной связи определяет, отправляет ли агент распространителя транзакции, созданные в подписчике, обратно подписчику:<br /><br /> **0** = отправляет обратно.<br /><br /> **1** = не отправляет обратно.<br /><br /> Используется с двунаправленной репликацией транзакций. Дополнительные сведения см. в статье [Bidirectional Transactional Replication](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md).|  
|**offload_enabled**|**bit**|Указывает, было ли установлено разгрузочное выполнение агента репликации для запуска на подписчике.<br /><br /> Если **0**, агент выполняется на издателе.<br /><br /> Если **1**, агент выполняется на подписчике.|  
|**offload_server**|**sysname**|Имя сервера, используемого для удаленной активации агента. Если значение равно NULL, затем текущего столбца offload_server из [MSdistribution_agents](../../relational-databases/system-tables/msdistribution-agents-transact-sql.md) таблица используется.|  
|**dts_package_name**|**sysname**|Указывает имя пакета служб DTS.|  
|**dts_package_location**|**int**|Расположение пакета служб DTS, если он назначен для подписки. Если имеется пакет значение **0** указывает, что пакет находится на **распространителя**. Значение **1** указывает **подписчика**.|  
|**subscriber_security_mode**|**smallint**|Режим безопасности на подписчике, где **1** означает проверку подлинности Windows, и **0** означает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности.|  
|**subscriber_login**|**sysname**|Имя входа на подписчике.|  
|**subscriber_password**||Фактический пароль подписчика никогда не возвращается. Результат скрывается "**&#42;&#42;&#42;&#42;&#42;&#42;**" строка.|  
|**job_login**|**sysname**|Имя учетной записи Windows, под которой работает агент распространителя.|  
|**job_password**||Фактический пароль задания никогда не возвращается. Результат скрывается "**&#42;&#42;&#42;&#42;&#42;&#42;**" строка.|  
|**distrib_agent_name**|**nvarchar(100)**|Имя задания агента, которое синхронизирует подписку.|  
|**subscriber_type**|**tinyint**|Тип подписчика. Может быть одним из следующих.<br /><br /> **0** = подписчик SQL Server<br /><br /> **1** = сервер источника данных ODBC<br /><br /> **2** = база данных Microsoft JET (устаревший)<br /><br /> **3** = поставщик OLE DB|  
|**subscriber_provider**|**sysname**|Уникальный программный идентификатор (PROGID), с которым регистрируется поставщик OLE DB для источника данных, отличного от SQL Server.|  
|**subscriber_datasource**|**nvarchar(4000)**|Имя источника данных, понятное поставщику OLE DB.|  
|**subscriber_providerstring**|**nvarchar(4000)**|Идентифицирующая источник данных строка соединения, зависящая от поставщика OLE DB.|  
|**subscriber_location**|**nvarchar(4000)**|Расположение базы данных, подразумевается поставщик OLE DB.|  
|**subscriber_catalog**|**sysname**|Каталог, используемый при соединении с поставщиком OLE DB.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpsubscription** используется в репликации моментальных снимков и репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение по умолчанию принадлежат роли **public** . Пользователям всего лишь возвращаются сведения о подписках, которые они создали. Сведения по всем подпискам возвращаются членам **sysadmin** предопределенной роли сервера на издателе или члены **db_owner** предопределенной роли базы данных в базе данных публикации.  
  
## <a name="see-also"></a>См. также  
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
