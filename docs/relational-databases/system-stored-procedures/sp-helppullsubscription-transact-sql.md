---
title: sp_helppullsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppullsubscription_TSQL
- sp_helppullsubscription
helpviewer_keywords:
- sp_helppullsubscription
ms.assetid: a0d9c3f1-1fe9-497c-8e2f-5b74f47a7346
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1ab2afba10ff754b5bd99d36df02d642cc5c6bb0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771438"
---
# <a name="sp_helppullsubscription-transact-sql"></a>sp_helppullsubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Отображает сведения об одной или более подписках на подписчике. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helppullsubscription [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @show_push = ] 'show_push' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя удаленного сервера. Аргумент *Publisher* имеет тип **sysname**и значение по **%** умолчанию, которое возвращает сведения для всех издателей.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных издателя. Аргумент *publisher_db* имеет тип **sysname**и значение по **%** умолчанию, которое возвращает все базы данных издателя.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и значение по **%** умолчанию, которое возвращает все публикации. Если этот параметр равен ALL, возвращаются только подписки по запросу с independent_agent = **0** .  
  
`[ @show_push = ] 'show_push'`Указывает, должны ли возвращаться все принудительные подписки. *show_push*имеет тип **nvarchar (5)** и значение по умолчанию false, которое не возвращает принудительные подписки.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**издателя**|**sysname**|Имя издателя.|  
|**база данных издателя**|**sysname**|Имя базы данных издателя.|  
|**публикации**|**sysname**|Имя публикации.|  
|**independent_agent**|**bit**|Указывает, имеется ли для данной публикации изолированный агент распространителя.|  
|**Тип подписки**|**int**|Тип подписки для публикации.|  
|**агент распространителя**|**nvarchar (100)**|Агент распространителя, управляющий подпиской.|  
|**publication description**|**nvarchar(255)**|Описание публикации.|  
|**last updating time**|**date**|Время последнего обновления сведений о подписке. Строка в формате Юникод с датой ISO (114) + время ODBC (121). Формат «ггггммдд чч:мн:ссс.ммм», где «гггг» — год, «мм» — месяц, «дд» — день, «чч» — час, «мн» — минуты, «ссс» — секунды и «ммм» — миллисекунды.|  
|**имя подписки**|**varchar (386)**|Имя подписки.|  
|**Метка времени последней транзакции**|**varbinary (16)**|Отметка времени последней реплицированной транзакции.|  
|**update mode**|**tinyint**|Тип допустимых обновлений.|  
|**distribution agent job_id**|**int**|Идентификатор задания агента распространителя.|  
|**enabled_for_synmgr**|**int**|Можно ли синхронизировать подписку с помощью диспетчера [!INCLUDE[msCoName](../../includes/msconame-md.md)] синхронизации.|  
|**subscription guid**|**двоичный (16)**|Глобальный идентификатор версии подписки в публикации.|  
|**subid**|**двоичный (16)**|Глобальный идентификатор для анонимной подписки.|  
|**immediate_sync**|**bit**|Указывает, выполняется ли создание (повторное создание) файлов синхронизации при каждом запуске агента моментальных снимков.|  
|**имя для входа издателя**|**sysname**|Идентификатор входа, используемый на издателе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Пароль издателя**|**nvarchar (524)**|Пароль (шифрованный), используемый на издателе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**publisher security_mode**|**int**|Режим безопасности, реализованный на издателе:<br /><br /> **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности<br /><br /> **1** = проверка подлинности Windows<br /><br /> **2** = триггеры синхронизации используют статическую запись **sysservers** для удаленного вызова процедур (RPC), а *Издатель* должен быть определен в таблице **sysservers** как удаленный сервер или связанный сервер.|  
|**распространение**|**sysname**|Имя распространителя.|  
|**distributor_login**|**sysname**|Идентификатор входа, используемый на распространителе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**distributor_password**|**nvarchar (524)**|Пароль (шифрованный), используемый на распространителе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**distributor_security_mode**|**int**|Режим безопасности, реализованный на распространителе:<br /><br /> **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности<br /><br /> **1** = проверка подлинности Windows|  
|**ftp_address**|**sysname**|Только для обратной совместимости.|  
|**ftp_port**|**int**|Только для обратной совместимости.|  
|**ftp_login**|**sysname**|Только для обратной совместимости.|  
|**ftp_password**|**nvarchar (524)**|Только для обратной совместимости.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Место, где размещается папка моментального снимка, если размещение отличается от размещения по умолчанию или задано дополнительно.|  
|**working_directory**|**nvarchar(255)**|Абсолютный путь к каталогу, куда были переданы файлы моментального снимка с использованием FTP, если эта установка включена.|  
|**use_ftp**|**bit**|Подписка на публикацию осуществляется через Интернет. При этом настроены параметры адресации через FTP. Если значение **равно 0**, то подписка не использует протокол FTP. Если значение равно **1**, то подписка использует протокол FTP.|  
|**publication_type**|**int**|Задает тип репликации для публикации:<br /><br /> **0** = репликация транзакций<br /><br /> **1** = репликация моментальных снимков<br /><br /> **2** = репликация слиянием|  
|**dts_package_name**|**sysname**|Указывает имя пакета служб DTS.|  
|**dts_package_location**|**int**|Местоположение, где хранится пакет служб DTS:<br /><br /> **0** = распространитель<br /><br /> **1** = подписчик|  
|**offload_agent**|**bit**|Указывает, может ли агент быть активирован удаленно. Если значение **равно 0**, агент не может быть активирован удаленно.|  
|**offload_server**|**sysname**|Указывает сетевое имя сервера, используемого для удаленной активации.|  
|**last_sync_status**|**int**|Состояние подписки:<br /><br /> **0** = все задания ожидают запуска<br /><br /> **1** = одно или несколько заданий запускаются<br /><br /> **2** = все задания выполнены успешно<br /><br /> **3** = по крайней мере одно задание исполняется<br /><br /> **4** = все задания запланированы и бездействуют<br /><br /> **5** = по крайней мере одно задание пытается выполнить после предыдущего сбоя<br /><br /> **6** = не удалось успешно выполнить по крайней мере одно задание|  
|**last_sync_summary**|**sysname**|Описание последних результатов синхронизации.|  
|**last_sync_time**|**datetime**|Время последнего обновления сведений о подписке. Строка в формате Юникод с датой ISO (114) + время ODBC (121). Формат «ггггммдд чч:мн:ссс.ммм», где «гггг» — год, «мм» — месяц, «дд» — день, «чч» — час, «мн» — минуты, «ссс» — секунды и «ммм» — миллисекунды.|  
|**job_login**|**nvarchar(512)**|Учетная запись Windows, с которой запускается агент распространителя, которая возвращается в формате *домен*\\*имя_пользователя*.|  
|**job_password**|**sysname**|По соображениям безопасности всегда возвращается значение**\*\*\*\*\*\*\*\*"\***".|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helppullsubscription** используется в моментальных снимках и репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_helppullsubscription** .  
  
## <a name="see-also"></a>См. также:  
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
