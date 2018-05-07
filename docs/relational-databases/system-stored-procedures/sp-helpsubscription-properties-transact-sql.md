---
title: sp_helpsubscription_properties (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_helpsubscription_properties
- sp_helpsubscription_properties_TSQL
helpviewer_keywords:
- sp_helpsubscription_properties
ms.assetid: 7a76a645-97eb-47ac-b3ea-e2d75012cbed
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 83f6699993f9ee4d0d3df4662bb75e4e07edb942
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpsubscriptionproperties-transact-sql"></a>sp_helpsubscription_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Получает сведения о безопасности из [MSsubscription_properties](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) таблицы. Эта хранимая процедура выполняется на подписчике.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpsubscription_properties [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db =] 'publisher_db' ]   
    [ , [ @publication =] 'publication' ]  
    [ , [ @publication_type = ] publication_type ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=**] **"***издатель***"**  
 Имя издателя. *издатель* — **sysname**, значение по умолчанию **%**, котором возвращаются сведения обо всех издателях.  
  
 [  **@publisher_db=**] **"***publisher_db***"**  
 Имя базы данных издателя. *publisher_db* — **sysname**, значение по умолчанию **%**, который возвращает сведения обо всех базах данных издателя.  
  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *публикации* — **sysname**, значение по умолчанию **%**, который возвращает сведения обо всех публикациях.  
  
 [  **@publication_type=**] *publication_type*  
 — Тип публикации. *publication_type* — **int**, значение по умолчанию NULL. Если указано, *publication_type* должен быть одним из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Публикация транзакций|  
|**1**|Публикация моментальных снимков|  
|**2**|Публикация слиянием|  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**издатель**|**sysname**|Имя издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**Публикации**|**sysname**|Имя публикации.|  
|**publication_type**|**int**|Тип публикации:<br /><br /> **0** = публикация транзакций<br /><br /> **1** = моментальный снимок<br /><br /> **2** = публикация слиянием|  
|**publisher_login**|**sysname**|Идентификатор входа, используемый на издателе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**publisher_password**|**nvarchar(524)**|Пароль (шифрованный), используемый на издателе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**publisher_security_mode**|**int**|Режим безопасности, реализованный на издателе:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1** = проверка подлинности Windows|  
|**Распространитель**|**sysname**|Имя распространителя.|  
|**имя_входа_распространителя**|**sysname**|Имя входа распространителя.|  
|**distributor_password**|**nvarchar(524)**|Пароль распространителя (шифрованный).|  
|**distributor_security_mode**|**int**|Режим безопасности, используемый на распространителе:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1** = проверка подлинности Windows|  
|**ftp_address**|**sysname**|Только для обратной совместимости. Сетевой адрес службы протокола FTP для распространителя.|  
|**ftp_port**|**int**|Только для обратной совместимости. Номер порта службы FTP для распространителя.|  
|**ftp_login**|**sysname**|Только для обратной совместимости. Имя пользователя, используемое для подключения к службе FTP.|  
|**ftp_password**|**nvarchar(524)**|Только для обратной совместимости. Пароль пользователя, используемый для подключения к службе FTP.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Указывает местоположение альтернативной папки для моментального снимка.|  
|**working_directory**|**nvarchar(255)**|Имя рабочего каталога, используемого для хранения файлов данных и схемы.|  
|**use_ftp**|**бит**|Указывает использование протокола FTP вместо обычного протокола для получения моментальных снимков. Если **1**, используется протокол FTP.|  
|**dts_package_name**|**sysame**|Указывает имя пакета служб DTS.|  
|**dts_package_password**|**nvarchar(524)**|Задает пароль для пакета, если он имеется.|  
|**dts_package_location**|**int**|Местоположение, где хранится пакет служб DTS.<br /><br /> **0** = пакет размещен на распространителе.<br /><br /> **1** = пакет размещен на подписчике.|  
|**offload_agent**|**бит**|Указывает, может ли агент быть активирован удаленно. Если **0**, агент не может быть активирован удаленно.|  
|**offload_server**|**sysname**|Указывает сетевое имя сервера, используемого для удаленной активации.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Указывает путь к папке, в которой сохраняются файлы моментальных снимков.|  
|**use_web_sync**|**бит**|Указывает, если подписку можно синхронизировать через HTTPS, где значение **1** означает, что эта функция включена.|  
|**internet_url**|**nvarchar(260)**|UR-адрес, который представляет собой адрес средства прослушивания репликации для веб-синхронизации.|  
|**internet_login**|**nvarchar(128)**|Имя входа, используемое агентом слияния для подключения к веб-серверу, на котором доступна веб-синхронизация с обычной проверкой подлинности.|  
|**internet_password**|**nvarchar(524)**|Пароль для имени входа, используемого агентом слияния при подключении к веб-серверу, на котором доступна веб-синхронизация с использованием обычной проверки подлинности.|  
|**internet_security_mode**|**int**|Режим проверки подлинности, используемый при соединении с веб-сервером, на котором размещается веб-синхронизация, где значение **1** означает проверку подлинности Windows, а значение **0** — обычную проверку подлинности.|  
|**internet_timeout**|**int**|Время (в секундах) перед отменой запроса на веб-синхронизацию.|  
|**Имя узла**|**nvarchar(128)**|Задает значение для функции HOST_NAME(), если эта функция используется в предложении WHERE параметризованного фильтра строк.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helpsubscription_properties** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_helpsubscription_properties**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
