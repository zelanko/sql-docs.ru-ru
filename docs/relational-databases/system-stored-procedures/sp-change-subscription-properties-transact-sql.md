---
title: sp_change_subscription_properties (Трансакт-СЗЛ) Документы Майкрософт
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
ms.openlocfilehash: e033e446fc771ad87542474edb1e90caf08faebd
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528792"
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
`[ @publisher = ] 'publisher'`Это имя издателя. *издатель* **sysname**, без по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Это название базы данных Издателя. *publisher_db* **sysname,** без по умолчанию.  
  
`[ @publication = ] 'publication'`Это название публикации. *публикация* **sysname,** без по умолчанию.  
  
`[ @property = ] 'property'`Является ли свойство, необходимо изменить. *свойство* **sysname**.  
  
`[ @value = ] 'value'`Это новая стоимость имущества. *значение* **nvarchar (1000)**, без по умолчанию.  
  
`[ @publication_type = ] publication_type`Определяет тип репликации публикации. *publication_type* является **int,** и может быть одним из этих значений.  
  
|Значение|Тип публикации|  
|-----------|----------------------|  
|**0**|Транзакционную|  
|**1**|Моментальный снимок|  
|**2**|Объединить|  
|NULL (по умолчанию)|Репликация определяет тип публикации. Так как хранимая процедура должна выполнять просмотр в нескольких таблицах, работа при указании этого значения производится медленнее, чем в случае, когда предоставлен точный тип публикации.|  
  
 Эта таблица описывает свойства статей и значения этих свойств.  
  
|Свойство|Значение|Описание|  
|--------------|-----------|-----------------|  
|**alt_snapshot_folder**||Указывает местоположение альтернативной папки для моментального снимка. Если это свойство имеет значение NULL, файлы моментальных снимков выбираются из места по умолчанию, задаваемого издателем.|  
|**distrib_job_login**||Имя входа учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой выполняется агент.|  
|**distrib_job_password**||Пароль учетной записи Windows, от имени которой выполняется агент.|  
|**distributor_login**||Имя входа распространителя.|  
|**distributor_password**||Пароль распространителя.|  
|**distributor_security_mode**|**1**|При подключении к подписчику используется проверка подлинности Windows.|  
||**0**|При подключении к подписчику используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**dts_package_name**||Указывает имя пакета служб SQL Server 2000 Data Transformation Services (DTS). Это значение может задаваться, если только публикация является транзакционной или публикацией моментальных снимков.|  
|**dts_package_password**||Указывает пароль на пакет. *dts_package_password* **sysname** с невыполнением null, который указывает, что свойство пароля должно быть оставлено без изменений.<br /><br /> Примечание: Пакет DTS должен иметь пароль.<br /><br /> Это значение может задаваться, если только публикация является транзакционной или публикацией моментальных снимков.|  
|**dts_package_location**||Местоположение, где хранится пакет служб DTS. Это значение может задаваться, если только публикация является транзакционной или публикацией моментальных снимков.|  
|**dynamic_snapshot_location**||Указывает путь к папке, в которой сохраняются файлы моментальных снимков. Это значение может задаваться, если только публикация является публикацией слиянием.|  
|**ftp_address**||Только для обратной совместимости.|  
|**ftp_login**||Только для обратной совместимости.|  
|**ftp_password**||Только для обратной совместимости.|  
|**ftp_port**||Только для обратной совместимости.|  
|**Узла**||Имя узла, используемое при соединении с издателем.|  
|**internet_login**||Имя входа, используемое агентом слияния для подключения к веб-серверу, на котором доступна веб-синхронизация с обычной проверкой подлинности.|  
|**internet_password**||Пароль, используемый агентом слияния для подключения к веб-серверу, на котором доступна веб-синхронизация с обычной проверкой подлинности.|  
|**internet_security_mode**|**1**|Для веб-синхронизации используется встроенная проверка подлинности Windows. При веб-синхронизации рекомендуется использовать обычную проверку подлинности. Дополнительные сведения см. в разделе [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).|  
||**0**|Для веб-синхронизации используется обычная проверка подлинности.<br /><br /> Примечание: Синхронизация веб-страниц требует подключения TLS к веб-серверу.|  
|**internet_timeout**||Время (в секундах) перед отменой запроса на веб-синхронизацию.|  
|**internet_url**||UR-адрес, который представляет собой адрес средства прослушивания репликации для веб-синхронизации.|  
|**merge_job_login**||Имя входа учетной записи Windows, от имени которой выполняется агент.|  
|**merge_job_password**||Пароль учетной записи Windows, от имени которой выполняется агент.|  
|**publisher_login**||Имя входа издателя. Изменение *publisher_login* поддерживается только для подписки для объединения публикаций.|  
|**publisher_password**||Пароль издателя. Изменение *publisher_password* поддерживается только для подписки для объединения публикаций.|  
|**publisher_security_mode**|**1**|При подключении к подписчику используется проверка подлинности Windows. Изменение *publisher_security_mode* поддерживается только для подписки для объединения публикаций.|  
||**0**|При подключении к издателю используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**use_ftp**|**true**|Использование FTP вместо обычного протокола для получения моментальных снимков.|  
||**false**|Использование обычного протокола для получения моментальных снимков.|  
|**use_web_sync**|**true**|Включение веб-синхронизации.|  
||**false**|Отключение веб-синхронизации.|  
|**working_directory**||Имя рабочего каталога, используемого для временного хранения файлов данных и схем для публикации, если для передачи файлов моментальных снимков используется протокол передачи файлов (FTP).|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успех) или **1** (неудача)  
  
## <a name="remarks"></a>Примечания  
 **sp_change_subscription_properties** используется во всех типах репликации.  
  
 **sp_change_subscription_properties** используется для вытягивания подписок.  
  
 Для Oracle Publishers значение *publisher_db* игнорируется, так как Oracle разрешает только одну базу данных на экземпляр сервера.  
  
## <a name="permissions"></a>Разрешения  
 Выполнять **sp_change_subscription_properties**могут только члены **сисадмина** фиксированной роли сервера или **db_owner** фиксированной роли базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств подписки Pull](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [sp_addmergepullsubscription &#40;&#41;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_addmergepullsubscription_agent &#40;&#41;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [sp_addpullsubscription&#41;&#40;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_addpullsubscription_agent &#40;&#40;&#41;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
