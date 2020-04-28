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
ms.openlocfilehash: bf7712ceb55fc368d493be9999cd0b8d4d9f474c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771573"
---
# <a name="sp_helpsubscription-transact-sql"></a>sp_helpsubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
`[ @publication = ] 'publication'`Имя связанной публикации. Аргумент *publication* имеет тип **sysname**и значение по **%** умолчанию, которое возвращает все сведения о подписке для этого сервера.  
  
`[ @article = ] 'article'`Имя статьи. Аргумент *article* имеет тип **sysname**и значение по **%** умолчанию, которое возвращает все сведения о подписке для выбранных публикаций и подписчиков. В **этом случае для**полной подписки на публикацию возвращается только одна запись.  
  
`[ @subscriber = ] 'subscriber'`Имя подписчика, для которого необходимо получить сведения о подписке. Аргумент *Subscriber* имеет тип **sysname**и значение по **%** умолчанию, которое возвращает все сведения о подписке для выбранных публикаций и статей.  
  
`[ @destination_db = ] 'destination_db'`Имя целевой базы данных. Аргумент *destination_db* имеет тип **sysname**и значение по **%** умолчанию.  
  
`[ @found = ] 'found'OUTPUT`Флаг, указывающий возвращаемые строки. Аргумент *Found*имеет **тип int** и выходной параметр и значение по умолчанию 23456.  
  
 **1** указывает, что публикация найдена.  
  
 значение **0** указывает, что публикация не найдена.  
  
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**, а значение по умолчанию — имя текущего сервера.  
  
> [!NOTE]  
>  нельзя указывать *Издатель* , кроме случая, когда он является издателем Oracle.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**абонент**|**sysname**|Имя подписчика.|  
|**публикации**|**sysname**|Имя публикации.|  
|**рассмотрен**|**sysname**|Имя статьи.|  
|**Целевая база данных**|**sysname**|Имя целевой базы данных, в которую помещаются реплицируемые данные.|  
|**состояние подписки**|**tinyint**|Состояние подписки:<br /><br /> **0** = неактивно<br /><br /> **1** = подписано<br /><br /> **2** = активно|  
|**synchronization type**|**tinyint**|Тип синхронизации подписки:<br /><br /> **1** = автоматический<br /><br /> **2** = нет|  
|**Тип подписки**|**int**|Тип подписки:<br /><br /> **0** = принудительная отправка<br /><br /> **1** = по запросу<br /><br /> **2** = анонимный|  
|**full subscription**|**bit**|На все ли статьи публикации подписана данная подписка:<br /><br /> **0** = нет<br /><br /> **1** = да|  
|**имя подписки**|**nvarchar(255)**|Имя подписки.|  
|**update mode**|**int**|**0** = только для чтения<br /><br /> **1** = немедленно обновляемая подписка|  
|**distribution job id**|**двоичный (16)**|Идентификатор задания агента распространителя.|  
|**loopback_detection**|**bit**|Механизм распознавания обратной связи определяет, отправляет ли агент распространителя транзакции, созданные в подписчике, обратно подписчику:<br /><br /> **0** = отправляет обратно.<br /><br /> **1** = не отправляет обратно.<br /><br /> Используется с двунаправленной репликацией транзакций. Дополнительные сведения см. в разделе [Двунаправленная репликация транзакций](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md).|  
|**offload_enabled**|**bit**|Указывает, было ли установлено разгрузочное выполнение агента репликации для запуска на подписчике.<br /><br /> Если значение **равно 0**, агент выполняется на издателе.<br /><br /> Если значение равно **1**, агент выполняется на подписчике.|  
|**offload_server**|**sysname**|Имя сервера, используемого для удаленной активации агента. Если значение равно NULL, то используется текущая offload_server, указанная в [MSdistribution_agents](../../relational-databases/system-tables/msdistribution-agents-transact-sql.md) таблице.|  
|**dts_package_name**|**sysname**|Указывает имя пакета служб DTS.|  
|**dts_package_location**|**int**|Расположение пакета служб DTS, если он назначен для подписки. Если пакет существует, значение **0** указывает расположение пакета на **распространителе**. Значение **1** указывает **подписчика**.|  
|**subscriber_security_mode**|**smallint**|Режим безопасности на подписчике, где **1** означает проверку подлинности Windows, **0** а 0 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — проверку подлинности.|  
|**subscriber_login**|**sysname**|Имя входа на подписчике.|  
|**subscriber_password**||Фактический пароль подписчика никогда не возвращается. Результат скрывается строкой "**&#42;&#42;&#42;&#42;&#42;&#42;**".|  
|**job_login**|**sysname**|Имя учетной записи Windows, под которой работает агент распространителя.|  
|**job_password**||Фактический пароль задания никогда не возвращается. Результат скрывается строкой "**&#42;&#42;&#42;&#42;&#42;&#42;**".|  
|**distrib_agent_name**|**nvarchar (100)**|Имя задания агента, которое синхронизирует подписку.|  
|**subscriber_type**|**tinyint**|Тип подписчика. Может быть одним из следующих.<br /><br /> **0** = SQL Server подписчика<br /><br /> **1** = сервер источника данных ODBC<br /><br /> **2** = база данных Microsoft Jet (не рекомендуется)<br /><br /> **3** = поставщик OLE DB|  
|**subscriber_provider**|**sysname**|Уникальный программный идентификатор (PROGID), с которым регистрируется поставщик OLE DB для источника данных, отличного от SQL Server.|  
|**subscriber_datasource**|**nvarchar(4000)**|Имя источника данных, понятное поставщику OLE DB.|  
|**subscriber_providerstring**|**nvarchar(4000)**|Идентифицирующая источник данных строка соединения, зависящая от поставщика OLE DB.|  
|**subscriber_location**|**nvarchar(4000)**|Расположение базы данных, подразумевается поставщик OLE DB.|  
|**subscriber_catalog**|**sysname**|Каталог, используемый при соединении с поставщиком OLE DB.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpsubscription** используется в моментальных снимках и репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение по умолчанию имеют роль **Public** . Пользователям всего лишь возвращаются сведения о подписках, которые они создали. Сведения обо всех подписках возвращаются членам предопределенной роли сервера **sysadmin** на издателе или членам предопределенной роли базы данных **db_owner** в базе данных публикации.  
  
## <a name="see-also"></a>См. также:  
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
