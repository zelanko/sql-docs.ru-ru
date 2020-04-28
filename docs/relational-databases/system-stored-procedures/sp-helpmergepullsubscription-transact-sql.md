---
title: sp_helpmergepullsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergepullsubscription
- sp_helpmergepullsubscription_TSQL
helpviewer_keywords:
- sp_helpmergepullsubscription
ms.assetid: 6f3125f3-0dfa-40bd-b725-8aa1591234f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: c92ea8e2f172d9cb5b40559c2a7b77a60153065b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68137711"
---
# <a name="sp_helpmergepullsubscription-transact-sql"></a>sp_helpmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о подписках по запросу, существующих на стороне подписчика. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergepullsubscription [ [ @publication=] 'publication']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
```  
  
## <a name="argument"></a>Аргумент  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и значение по **%** умолчанию. Если *publication* параметр publication **%** имеет значение, то возвращаются сведения обо всех публикациях слиянием и подписках в текущей базе данных.  
  
`[ @publisher = ] 'publisher'`Имя издателя. Аргумент *Publisher*имеет тип **sysname**и значение по **%** умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных издателя. Аргумент *publisher_db*имеет тип **sysname**и значение по **%** умолчанию.  
  
`[ @subscription_type = ] 'subscription_type'`Указывает, следует ли отображать подписки по запросу. *subscription_type*имеет тип **nvarchar (10)** и значение по умолчанию **"Pull"**. Допустимые значения: **"Push"**, **"Pull**" или **"both"**.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**nvarchar (1000)**|Имя подписки.|  
|**публикации**|**sysname**|Имя публикации.|  
|**издателя**|**sysname**|Имя издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**абонент**|**sysname**|Имя подписчика.|  
|**subscription_db**|**sysname**|Имя базы данных подписки.|  
|**status**|**int**|Состояние подписки:<br /><br /> **0** = неактивная подписка<br /><br /> **1** = активная подписка<br /><br /> **2** = удаленная подписка<br /><br /> **3** = отсоединенная подписка<br /><br /> **4** = подключенная подписка<br /><br /> **5** = подписка помечена для повторной инициализации с передачей<br /><br /> **6** = не удалось присоединить подписку.<br /><br /> **7** = подписка восстановлена из резервной копии|  
|**subscriber_type**|**int**|Тип подписчика:<br /><br /> **1** = глобальный<br /><br /> **2** = локальный<br /><br /> **3** = анонимный|  
|**subscription_type**|**int**|Тип подписки:<br /><br /> **0** = принудительная отправка<br /><br /> **1** = по запросу<br /><br /> **2** = анонимный|  
|**приоритеты**|**float (8)**|Приоритет подписки. Значение должно быть меньше **100,00**.|  
|**sync_type**|**tinyint**|Тип синхронизации подписки:<br /><br /> **1** = автоматический<br /><br /> **2** = моментальный снимок не используется.|  
|**nописание**|**nvarchar(255)**|Краткое описание подписки по запросу.|  
|**merge_jobid**|**двоичный (16)**|Идентификатор задания агента слияния.|  
|**enabled_for_syncmgr**|**int**|Можно ли синхронизировать подписку с помощью диспетчера [!INCLUDE[msCoName](../../includes/msconame-md.md)] синхронизации.|  
|**last_updated**|**nvarchar (26)**|Время последней успешной синхронизации подписки агентом слияния.|  
|**publisher_login**|**sysname**|Имя входа издателя.|  
|**publisher_password**|**sysname**|Пароль издателя.|  
|**publisher_security_mode**|**int**|Указывает режим безопасности издателя:<br /><br /> **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности<br /><br /> **1** = проверка подлинности Windows|  
|**распространение**|**sysname**|Имя распространителя.|  
|**distributor_login**|**sysname**|Имя входа распространителя.|  
|**distributor_password**|**sysname**|Пароль распространителя.|  
|**distributor_security_mode**|**int**|Указывает режим безопасности распространителя:<br /><br /> **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности<br /><br /> **1** = проверка подлинности Windows|  
|**ftp_address**|**sysname**|Приводится только для обратной совместимости. Сетевой адрес службы протокола передачи файлов FTP распространителя.|  
|**ftp_port**|**int**|Приводится только для обратной совместимости. Номер порта службы FTP распространителя.|  
|**ftp_login**|**sysname**|Приводится только для обратной совместимости. Имя пользователя, используемое для подключения к службе FTP.|  
|**ftp_password**|**sysname**|Приводится только для обратной совместимости. Пароль пользователя, используемый для подключения к службе FTP.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Место, где размещается папка моментального снимка, если размещение отличается от размещения по умолчанию или задано дополнительно.|  
|**working_directory**|**nvarchar(255)**|Полный путь к каталогу, куда передаются файлы моментальных снимков по протоколу FTP, если указан соответствующий параметр.|  
|**use_ftp**|**bit**|Подписка на публикацию осуществляется через Интернет, также настраиваются свойства адреса FTP. Если значение **равно 0**, то подписка не использует протокол FTP. Если значение равно **1**, то подписка использует протокол FTP.|  
|**offload_agent**|**bit**|Указывает, может ли агент быть активирован и запущен удаленно. Если значение **равно 0**, агент не может быть активирован удаленно.|  
|**offload_server**|**sysname**|Имя сервера, используемого для удаленной активации.|  
|**use_interactive_resolver**|**int**|Возвращает сведения о том, был ли использован интерактивный сопоставитель во время взаимодействия. Если значение **равно 0**, интерактивный сопоставитель не используется.|  
|**subid**|**uniqueidentifier**|Идентификатор подписчика.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Путь к папке, в которой сохраняются файлы моментальных снимков.|  
|**last_sync_status**|**int**|Состояние синхронизации:<br /><br /> **1** = запуск<br /><br /> **2** = успех<br /><br /> **3** = выполняется<br /><br /> **4** = бездействие<br /><br /> **5** = повторная попытка после предыдущего сбоя<br /><br /> **6** = сбой<br /><br /> **7** = неудачная проверка<br /><br /> **8** = проверка пройдена<br /><br /> **9** = запрошено завершение работы|  
|**last_sync_summary**|**sysname**|Описание последних результатов синхронизации.|  
|**use_web_sync**|**bit**|Указывает, может ли подписка быть синхронизирована по протоколу HTTPS, где значение **1** означает, что эта функция включена.|  
|**internet_url**|**nvarchar(260)**|UR-адрес, который представляет собой адрес средства прослушивания репликации для веб-синхронизации.|  
|**internet_login**|**nvarchar(128)**|Имя входа, используемое агентом слияния для подключения к веб-серверу, на котором доступна веб-синхронизация с обычной проверкой подлинности.|  
|**internet_password**|**nvarchar (524)**|Пароль для имени входа, используемого агентом слияния при подключении к веб-серверу, на котором доступна веб-синхронизация с использованием обычной проверки подлинности.|  
|**internet_security_mode**|**int**|Режим проверки подлинности, используемый при подключении к серверу веб-синхронизации. Значение **1** означает проверку подлинности Windows, а значение **0** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверку подлинности.|  
|**internet_timeout**|**int**|Время (в секундах) перед отменой запроса на веб-синхронизацию.|  
|**hostname**|**nvarchar(128)**|Задает перегруженное значение для [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) , когда эта функция используется в предложении WHERE параметризованного фильтра строк.|  
|**job_login**|**nvarchar(512)**|Учетная запись Windows, под которой выполняется агент слияния, который возвращается в формате *домен*\\*имя_пользователя*.|  
|**job_password**|**sysname**|По соображениям безопасности всегда возвращается значение**\*\*\*\*\*\*\*\*"\***".|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpmergepullsubscription** используется в репликации слиянием. В результирующем наборе дата, возвращаемая в **last_updated** , форматируется как *ГГГГММДД чч: мм: СС. FFF*.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** и **db_owner** предопределенной роли базы данных могут выполнять **sp_helpmergepullsubscription**.  
  
## <a name="see-also"></a>См. также:  
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
