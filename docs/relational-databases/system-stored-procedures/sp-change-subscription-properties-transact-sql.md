---
title: sp_change_subscription_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_change_subscription_properties_TSQL
- sp_change_subscription_properties
helpviewer_keywords:
- sp_change_subscription_properties
ms.assetid: cf8137f9-f346-4aa1-ae35-91a2d3c16f17
author: stevestein
ms.author: sstein
ms.openlocfilehash: cfc42dbf08b6718e72970a703f56fb0bfff850f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771410"
---
# <a name="sp_change_subscription_properties-transact-sql"></a>sp_change_subscription_properties (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Обновляет данные для подписок по запросу. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_change_subscription_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @property = ] 'property'  
        , [ @value = ] 'value'  
    [ , [ @publication_type = ] publication_type ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных издателя. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @property = ] 'property'`Изменяемое свойство. *свойство* имеет тип **sysname**.  
  
`[ @value = ] 'value'`Новое значение свойства. *value* имеет тип **nvarchar (1000)** и не имеет значения по умолчанию.  
  
`[ @publication_type = ] publication_type`Указывает тип репликации публикации. *publication_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Тип публикации|  
|-----------|----------------------|  
|**0**|Транзакционную|  
|**1**|Моментальный снимок|  
|**2**|Объединить|  
|NULL (по умолчанию)|Репликация определяет тип публикации. Так как хранимая процедура должна выполнять просмотр в нескольких таблицах, работа при указании этого значения производится медленнее, чем в случае, когда предоставлен точный тип публикации.|  
  
 Эта таблица описывает свойства статей и значения этих свойств.  
  
|Свойство|Значение|Description|  
|--------------|-----------|-----------------|  
|**alt_snapshot_folder**||Указывает местоположение альтернативной папки для моментального снимка. Если это свойство имеет значение NULL, файлы моментальных снимков выбираются из места по умолчанию, задаваемого издателем.|  
|**distrib_job_login**||Имя входа учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой выполняется агент.|  
|**distrib_job_password**||Пароль учетной записи Windows, от имени которой выполняется агент.|  
|**distributor_login**||Имя входа распространителя.|  
|**distributor_password**||Пароль распространителя.|  
|**distributor_security_mode**|**1**|При подключении к подписчику используется проверка подлинности Windows.|  
||**0**|При подключении к подписчику используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**dts_package_name**||Указывает имя пакета служб SQL Server 2000 Data Transformation Services (DTS). Это значение может задаваться, если только публикация является транзакционной или публикацией моментальных снимков.|  
|**dts_package_password**||Указывает пароль на пакет. Аргумент *dts_package_password* имеет тип **sysname** и значение по умолчанию NULL, которое указывает, что свойство Password должно остаться без изменений.<br /><br /> Примечание. пакет служб DTS должен иметь пароль.<br /><br /> Это значение может задаваться, если только публикация является транзакционной или публикацией моментальных снимков.|  
|**dts_package_location**||Местоположение, где хранится пакет служб DTS. Это значение может задаваться, если только публикация является транзакционной или публикацией моментальных снимков.|  
|**dynamic_snapshot_location**||Указывает путь к папке, в которой сохраняются файлы моментальных снимков. Это значение может задаваться, если только публикация является публикацией слиянием.|  
|**ftp_address**||Только для обратной совместимости.|  
|**ftp_login**||Только для обратной совместимости.|  
|**ftp_password**||Только для обратной совместимости.|  
|**ftp_port**||Только для обратной совместимости.|  
|**имя узла**||Имя узла, используемое при соединении с издателем.|  
|**internet_login**||Имя входа, используемое агентом слияния для подключения к веб-серверу, на котором доступна веб-синхронизация с обычной проверкой подлинности.|  
|**internet_password**||Пароль, используемый агентом слияния для подключения к веб-серверу, на котором доступна веб-синхронизация с обычной проверкой подлинности.|  
|**internet_security_mode**|**1**|Для веб-синхронизации используется встроенная проверка подлинности Windows. При веб-синхронизации рекомендуется использовать обычную проверку подлинности. Дополнительные сведения см. в разделе [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).|  
||**0**|Для веб-синхронизации используется обычная проверка подлинности.<br /><br /> Примечание. для веб-синхронизации требуется подключение SSL к веб-серверу.|  
|**internet_timeout**||Время (в секундах) перед отменой запроса на веб-синхронизацию.|  
|**internet_url**||UR-адрес, который представляет собой адрес средства прослушивания репликации для веб-синхронизации.|  
|**merge_job_login**||Имя входа учетной записи Windows, от имени которой выполняется агент.|  
|**merge_job_password**||Пароль учетной записи Windows, от имени которой выполняется агент.|  
|**publisher_login**||Имя входа издателя. Изменение *publisher_login* поддерживается только для подписок на публикации слиянием.|  
|**publisher_password**||Пароль издателя. Изменение *publisher_password* поддерживается только для подписок на публикации слиянием.|  
|**publisher_security_mode**|**1**|При подключении к подписчику используется проверка подлинности Windows. Изменение *publisher_security_mode* поддерживается только для подписок на публикации слиянием.|  
||**0**|При подключении к издателю используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**use_ftp**|**условия**|Использование FTP вместо обычного протокола для получения моментальных снимков.|  
||**IsFalse**|Использование обычного протокола для получения моментальных снимков.|  
|**use_web_sync**|**условия**|Включение веб-синхронизации.|  
||**IsFalse**|Отключение веб-синхронизации.|  
|**working_directory**||Имя рабочего каталога, используемого для временного хранения файлов данных и схем для публикации, если для передачи файлов моментальных снимков используется протокол передачи файлов (FTP).|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_change_subscription_properties** используется во всех типах репликации.  
  
 **sp_change_subscription_properties** используется для подписок по запросу.  
  
 Для издателей Oracle значение *publisher_db* игнорируется, так как Oracle допускает только одну базу данных на экземпляр сервера.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_change_subscription_properties**.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств подписки по запросу](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
