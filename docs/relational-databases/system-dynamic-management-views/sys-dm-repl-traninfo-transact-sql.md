---
title: sys.dm_repl_traninfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_traninfo
- dm_repl_traninfo
- sys.dm_repl_traninfo_TSQL
- dm_repl_traninfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_traninfo dynamic management view
ms.assetid: 5abe2605-0506-46ec-82b5-6ec08428ba13
author: stevestein
ms.author: sstein
ms.openlocfilehash: fc4f107ef1c26aa51f3f1d58f910be9721f2a51a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067835"
---
# <a name="sysdmrepltraninfo-transact-sql"></a>sys.dm_repl_traninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о каждой транзакции репликации или системы отслеживания измененных данных.  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**fp2p_pub_exists**|**tinyint**|Если транзакция публикуется в базе данных при помощи одноранговой репликации транзакции. Если да, это значение равно 1, иначе — 0.|  
|**db_ver**|**int**|Версия базы данных.|  
|**comp_range_address**|**varbinary(8)**|Определяет диапазон частичного отката, который должен быть пропущен.|  
|**textinfo_address**|**varbinary(8)**|Адрес в памяти структуры кэшированных текстовых данных.|  
|**fsinfo_address**|**varbinary(8)**|Адрес в памяти структуры кэшированных данных о файловых потоках.|  
|**begin_lsn**|**Nvarchar(64)**|Регистрационный номер (LSN) начальной записи транзакции в журнале.|  
|**commit_lsn**|**Nvarchar(64)**|Номер LSN записи в журнале фиксирования транзакции.|  
|**dbid**|**smallint**|Идентификатор базы данных.|  
|**rows**|**int**|Идентификатор реплицированной команды в транзакции.|  
|**xdesid**|**Nvarchar(64)**|Идентификатор транзакции.|  
|**artcache_table_address**|**varbinary(8)**|Адрес в памяти структуры кэшированной таблицы статьи, использованной в последний раз для данной транзакции.|  
|**server**|**nvarchar(514)**|Имя сервера.|  
|**server_len_in_bytes**|**smallint**|Длина символьной строки имени сервера, в байтах.|  
|**базой данных**|**nvarchar(514)**|Имя базы данных.|  
|**db_len_in_bytes**|**smallint**|Длина символьной строки имени базы данных, в байтах.|  
|**Инициатор**|**nvarchar(514)**|Имя сервера, где была создана транзакция.|  
|**originator_len_in_bytes**|**smallint**|Длина символьной строки, в байтах, имени сервера, где была создана транзакция.|  
|**orig_db**|**nvarchar(514)**|Имя базы данных, в которой была создана транзакция.|  
|**orig_db_len_in_bytes**|**smallint**|Длина символьной строки, в байтах, имени базы данных, в которой была создана транзакция.|  
|**cmds_in_tran**|**int**|Количество реплицированных команд в текущей транзакции, используемое для определения того, когда должна быть зафиксирована логическая транзакция.|  
|**is_boundedupdate_singleton**|**tinyint**|Указывается, влияет ли обновление уникального столбца только на одну строку.|  
|**begin_update_lsn**|**Nvarchar(64)**|Номер LSN, используемый при обновлении уникального столбца.|  
|**delete_lsn**|**Nvarchar(64)**|Номер LSN, удаляемый как часть обновления.|  
|**last_end_lsn**|**Nvarchar(64)**|Последний номер LSN в логической транзакции.|  
|**fcomplete**|**tinyint**|Указывает, является ли команда командой частичного обновления.|  
|**fcompensated**|**tinyint**|Указывает, участвует ли транзакция в частичном откате.|  
|**fprocessingtext**|**tinyint**|Указывает, содержит ли транзакция столбец типа данных binary large.|  
|**max_cmds_in_tran**|**int**|Максимальное число команд в логической транзакции, указываемое агентом чтения журнала.|  
|**begin_time**|**datetime**|Время начала транзакции.|  
|**commit_time**|**datetime**|Время фиксации транзакции.|  
|**session_id**|**int**|Идентификатор сеанса просмотра журнала системы отслеживания измененных данных. Этот столбец сопоставлен со **session_id** столбца в [sys.dm_cdc_logscan_sessions](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md).|  
|**session_phase**|**int**|Номер, указывающий этап, на котором находился сеанс во время возникновения ошибки. Этот столбец сопоставлен со **phase_number** столбца в [sys.dm_cdc_errors](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-errors.md).|  
|**is_known_cdc_tran**|**bit**|Показывает, какая транзакция отслеживается системой отслеживания измененных данных.<br /><br /> 0 = транзакция репликации транзакций.<br /><br /> 1 = транзакция системы отслеживания измененных данных.|  
|**error_count**|**int**|Количество обнаруженных ошибок.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE на базу данных публикации или базу данных, для которой включена система отслеживания измененных данных.  
  
## <a name="remarks"></a>Примечания  
 Сведения возвращаются только для объектов или таблиц реплицированной базы данных, для которых включена система отслеживания измененных данных и которые загружены в данный момент времени в кэш статьи.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с репликацией &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)   
 [Динамические административные представления, связанные с системой отслеживания измененных данных (Transact-SQL)](https://msdn.microsoft.com/library/2a771d7d-693a-4f56-9227-02cd00e0e200)  
  
  

