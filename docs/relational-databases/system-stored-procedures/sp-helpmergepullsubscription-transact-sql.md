---
title: sp_helpmergepullsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergepullsubscription
- sp_helpmergepullsubscription_TSQL
helpviewer_keywords:
- sp_helpmergepullsubscription
ms.assetid: 6f3125f3-0dfa-40bd-b725-8aa1591234f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: adbb39c32f09898e6d521b0ecff3c06c1a6494f2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47639982"
---
# <a name="sphelpmergepullsubscription-transact-sql"></a>sp_helpmergepullsubscription (Transact-SQL)
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
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию **%**. Если *публикации* — **%**, возвращаются сведения обо всех публикациях слиянием и подписках текущей базы данных.  
  
 [  **@publisher=**] **"***издателя***"**  
 Имя издателя. *издатель*— **sysname**, значение по умолчанию **%**.  
  
 [  **@publisher_db=**] **"***publisher_db***"**  
 Имя базы данных издателя. *publisher_db*— **sysname**, значение по умолчанию **%**.  
  
 [  **@subscription_type=**] **"***subscription_type***"**  
 Указывает, следует ли показывать подписки по запросу. *subscription_type*— **nvarchar(10)**, значение по умолчанию **'pull'**. Допустимые значения: **«push»**, **'pull'**, или **«both»**.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**nvarchar(1000)**|Имя подписки.|  
|**публикации**|**sysname**|Имя публикации.|  
|**издатель**|**sysname**|Имя издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**подписчик**|**sysname**|Имя подписчика.|  
|**subscription_db**|**sysname**|Имя базы данных подписки.|  
|**status**|**int**|Состояние подписки:<br /><br /> **0** — неактивная подписка<br /><br /> **1** = Активная подписка<br /><br /> **2** — удаленная подписка<br /><br /> **3** — Отключенная подписка<br /><br /> **4** — подключенная подписка<br /><br /> **5** = подписка была помечена для повторной инициализации с передачей<br /><br /> **6** = сбой подключения подписки<br /><br /> **7** — подписка, восстановленная из резервной копии|  
|**subscriber_type**|**int**|Тип подписчика:<br /><br /> **1** = глобальный<br /><br /> **2** = local<br /><br /> **3** = анонимная|  
|**subscription_type**|**int**|Тип подписки:<br /><br /> **0** = Принудительная<br /><br /> **1** = по запросу<br /><br /> **2** = анонимная|  
|**priority**|**float(8)**|Приоритет подписки. Значение должно быть меньше, чем **100,00**.|  
|**sync_type**|**tinyint**|Тип синхронизации подписки:<br /><br /> **1** = automatic<br /><br /> **2** = моментальный снимок не используется.|  
|**Описание**|**nvarchar(255)**|Краткое описание подписки по запросу.|  
|**merge_jobid**|**binary(16)**|Идентификатор задания агента слияния.|  
|**enabled_for_syncmgr**|**int**|Может ли подписка быть синхронизирована через [!INCLUDE[msCoName](../../includes/msconame-md.md)] диспетчер синхронизации.|  
|**last_updated**|**nvarchar(26)**|Время последней успешной синхронизации подписки агентом слияния.|  
|**publisher_login**|**sysname**|Имя входа издателя.|  
|**publisher_password**|**sysname**|Пароль издателя.|  
|**publisher_security_mode**|**int**|Указывает режим безопасности издателя:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1** = проверка подлинности Windows|  
|**распространитель**|**sysname**|Имя распространителя.|  
|**distributor_login**|**sysname**|Имя входа распространителя.|  
|**distributor_password**|**sysname**|Пароль распространителя.|  
|**distributor_security_mode**|**int**|Указывает режим безопасности распространителя:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1** = проверка подлинности Windows|  
|**ftp_address**|**sysname**|Приводится только для обратной совместимости. Сетевой адрес службы протокола передачи файлов FTP распространителя.|  
|**ftp_port**|**int**|Приводится только для обратной совместимости. Номер порта службы FTP распространителя.|  
|**ftp_login**|**sysname**|Приводится только для обратной совместимости. Имя пользователя, используемое для подключения к службе FTP.|  
|**ftp_password**|**sysname**|Приводится только для обратной совместимости. Пароль пользователя, используемый для подключения к службе FTP.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Место, где размещается папка моментального снимка, если размещение отличается от размещения по умолчанию или задано дополнительно.|  
|**working_directory**|**nvarchar(255)**|Полный путь к каталогу, куда передаются файлы моментальных снимков по протоколу FTP, если указан соответствующий параметр.|  
|**use_ftp**|**bit**|Подписка на публикацию осуществляется через Интернет, также настраиваются свойства адреса FTP. Если **0**, подписка не использует протокол FTP. Если **1**, подписка использует протокол FTP.|  
|**offload_agent**|**bit**|Указывает, может ли агент быть активирован и запущен удаленно. Если **0**, агент не может быть активирован удаленно.|  
|**offload_server**|**sysname**|Имя сервера, используемого для удаленной активации.|  
|**use_interactive_resolver**|**int**|Возвращает сведения о том, был ли использован интерактивный сопоставитель во время взаимодействия. Если **0**, интерактивный Сопоставитель не используется.|  
|**subid**|**uniqueidentifier**|Идентификатор подписчика.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Путь к папке, в которой сохраняются файлы моментальных снимков.|  
|**last_sync_status**|**int**|Состояние синхронизации:<br /><br /> **1** — запуск<br /><br /> **2** = выполнено успешно<br /><br /> **3** = выполняется<br /><br /> **4** = бездействует<br /><br /> **5** — повтор после сбоя<br /><br /> **6** = ошибка<br /><br /> **7** — сбой проверки<br /><br /> **8** — проверка пройдена<br /><br /> **9** — Запрошено завершение работы|  
|**last_sync_summary**|**sysname**|Описание последних результатов синхронизации.|  
|**use_web_sync**|**bit**|Указывает, может ли подписка быть синхронизирована по протоколу HTTPS, где значение **1** означает, что эта функция включена.|  
|**internet_url**|**nvarchar(260)**|UR-адрес, который представляет собой адрес средства прослушивания репликации для веб-синхронизации.|  
|**internet_login**|**nvarchar(128)**|Имя входа, используемое агентом слияния для подключения к веб-серверу, на котором доступна веб-синхронизация с обычной проверкой подлинности.|  
|**internet_password**|**nvarchar(524)**|Пароль для имени входа, используемого агентом слияния при подключении к веб-серверу, на котором доступна веб-синхронизация с использованием обычной проверки подлинности.|  
|**internet_security_mode**|**int**|Режим проверки подлинности, используемый при подключении к серверу веб-синхронизации. Значение **1** означает проверку подлинности Windows, а значение **0** означает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности.|  
|**internet_timeout**|**int**|Время (в секундах) перед отменой запроса на веб-синхронизацию.|  
|**Имя узла**|**nvarchar(128)**|Указывает переопределяемое значение [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) когда эта функция используется в предложении WHERE параметризованного фильтра строк.|  
|**job_login**|**nvarchar(512)**|Учетная запись Windows, под которой запускается агент слияния, который возвращается в формате *домена*\\*username*.|  
|**job_password**|**sysname**|По соображениям безопасности значение "**\*\*\*\*\*\*\*\*\*\***" — всегда возвращается.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpmergepullsubscription** используется в репликации слиянием. В результирующем наборе, даты, возвращенной в **last_updated** форматируется как *ггггммдд чч:мм:сс.мс*.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера и **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_helpmergepullsubscription**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
