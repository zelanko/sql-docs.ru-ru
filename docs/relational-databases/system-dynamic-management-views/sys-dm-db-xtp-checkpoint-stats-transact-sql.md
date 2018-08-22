---
title: sys.dm_db_xtp_checkpoint_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_checkpoint_stats
- dm_db_xtp_checkpoint_stats_TSQL
- sys.dm_db_xtp_checkpoint_stats
- sys.dm_db_xtp_checkpoint_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_checkpoint_stats dynamic management view
ms.assetid: 8d0b18ca-db4d-4376-9905-3e4457727c46
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 00a859096b0a816b24f858529365dd2d7568b2ee
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395999"
---
# <a name="sysdmdbxtpcheckpointstats-transact-sql"></a>sys.dm_db_xtp_checkpoint_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Возвращает статистику об операциях контрольной точки OLTP в памяти в текущей базе данных. Если база данных не имеет объектов OLTP в памяти, возвращается пустой результирующий набор.  
  
 Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
```  
SELECT * FROM db.sys.dm_db_xtp_checkpoint_stats;  
```  
  
**[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] существенно отличается от более поздние версии и обсуждается ниже в разделе в [SQL Server 2014](#bkmk_2014).**
  
## <a name="includesssql15includessssql15-mdmd-and-later"></a>[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и более поздние версии  
 В следующей таблице описаны столбцы в `sys.dm_db_xtp_checkpoint_stats`, начиная с версии **[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]**.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|last_lsn_processed|**bigint**|Последний номер LSN, увиденное контроллера.|  
|end_of_log_lsn|**numeric(38)**|Номер LSN конца журнала.|  
|bytes_to_end_of_log|**bigint**|Необработанные контроллером, соответствующих байтам между байтов журнала `last_lsn_processed` и `end_of_log_lsn`.|  
|log_consumption_rate|**bigint**|Интенсивность использования журнала транзакций контроллером (в КБ/с).|  
|active_scan_time_in_ms|**bigint**|Время, проведенное контроллер в активно просматривать журнал транзакций.|  
|total_wait_time_in_ms|**bigint**|Совокупное время ожидания для контроллера при Просмотр в журнал не.|  
|waits_for_io|**bigint**|Число ожиданий журналов ввода-ВЫВОДА, возникшие в потоке контроллера.|  
|io_wait_time_in_ms|**bigint**|Совокупное время, потраченное на ожидание на ввод-ВЫВОД журнала потоком контроллера.|  
|waits_for_new_log_count|**bigint**|Число ожиданий, вызванной поток контроллер будет создан новый журнал.|  
|new_log_wait_time_in_ms|**bigint**|Совокупное время, потраченное на ожидание на новый журнал потоком контроллера.|  
|idle_attempts_count|**bigint**|Количество раз, контроллер перешел в состояние простоя.|  
|tx_segments_dispatched|**bigint**|Количество сегментов, увиденное контроллера и распределения их по сериализаторов. Сегмент — непрерывная часть журнала, который представляет модуль сериализации. В настоящее время имеет размер в 1 МБ, но можно изменить в будущем.|  
|segment_bytes_dispatched|**bigint**|Общее число байтов, подготовленных к отправке посредством контроллера для сериализаторов, с момента перезапуска базы данных.|  
|bytes_serialized|**bigint**|Общее число байт сериализации с момента перезапуска базы данных.|  
|serializer_user_time_in_ms|**bigint**|Время, проведенное сериализаторы в пользовательском режиме.|  
|serializer_kernel_time_in_ms|**bigint**|Время, проведенное сериализаторы в режиме ядра.|  
|xtp_log_bytes_consumed|**bigint**|Общее число байтов журнала, с момента перезапуска базы данных.|  
|checkpoints_closed|**bigint**|Количество закрытых контрольных точек с момента перезапуска базы данных.|  
|last_closed_checkpoint_ts|**bigint**|Отметка времени последней контрольной точки, закрыт.|  
|hardened_recovery_lsn|**numeric(38)**|Номер LSN начнется восстановление.|  
|hardened_root_file_guid|**uniqueidentifier**|Идентификатор GUID корневым файлом, записаны на диск в результате последней завершенной контрольной точки.|  
|hardened_root_file_watermark|**bigint**|**Внутренняя только**. Насколько он допустим для чтения до корневого файла (это только — внутри соответствующего типа вызывается BSN).|  
|hardened_truncation_lsn|**numeric(38)**|Номер LSN точки усечения.|  
|log_bytes_since_last_close|**bigint**|Байт с последнего Закройте текущий конец журнала.|  
|time_since_last_close_in_ms|**bigint**|Время с момента последнего закрытия контрольной точки.|  
|current_checkpoint_id|**bigint**|В настоящее время новые сегменты назначаются до этой контрольной точки. В системе контрольной точки представляют собой конвейер. Текущая контрольная точка является то, что сегменты из журнала назначены. После достижения ограничения контрольной точки выпускается контроллер и новый создан как текущую.|  
|current_checkpoint_segment_count|**bigint**|Количество сегментов в текущей контрольной точки.|  
|recovery_lsn_candidate|**bigint**|**Внутренне только**. Кандидат для выбора как recoverylsn при закрытии current_checkpoint_id.|  
|outstanding_checkpoint_count|**bigint**|Число контрольных точек в конвейере, ожидающих будет закрыта.|  
|closing_checkpoint_id|**bigint**|Идентификатор закрывающей контрольной точки.<br /><br /> Сериализаторы работают параллельно, поэтому когда они завершили контрольной точки является кандидатом закрыть поток будет закрыт. Закрыть поток можно только закрыть по одному, но он должен быть в порядке, поэтому контрольной точки закрытия является тот, который занимается закрыть поток.|  
|recovery_checkpoint_id|**bigint**|Идентификатор контрольной точки для использования в процессе восстановления.|  
|recovery_checkpoint_ts|**bigint**|Отметка времени контрольной точки восстановления.|  
|bootstrap_recovery_lsn|**numeric(38)**|Номер LSN восстановления для начальной загрузки.|  
|bootstrap_root_file_guid|**uniqueidentifier**|Идентификатор GUID корневого файла для начальной загрузки.|  
|internal_error_code|**bigint**|Ошибка, отображается каким-либо контроллер, сериализатор, close и слияния потоков.|
|bytes_of_large_data_serialized|**bigint**|Объем данных, который был сериализован. |  
  
##  <a name="bkmk_2014"></a> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 В следующей таблице описаны столбцы в `sys.dm_db_xtp_checkpoint_stats`, для **[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]**.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|log_to_process_in_bytes|**bigint**|Число байтов журнала до регистрационного номера транзакции в журнале и в конце текущего потока транзакций.|  
|total_log_blocks_processed|**bigint**|Общее количество блоков журнала, обработанных с момента запуска сервера.|  
|total_log_records_processed|**bigint**|Общее количество записей журнала, обработанных с момента запуска сервера.|  
|xtp_log_records_processed|**bigint**|Общее количество записей журнала In-Memory OLTP, обработанных с момента запуска сервера.|  
|total_wait_time_in_ms|**bigint**|Совокупное время ожидания в миллисекундах.|  
|waits_for_io|**bigint**|Число ожиданий ввода-вывода для журнала.|  
|io_wait_time_in_ms|**bigint**|Совокупное время, потраченное на ожидание ввода-вывода для журнала.|  
|waits_for_new_log|**bigint**|Число ожиданий для нового журнала.|  
|new_log_wait_time_in_ms|**bigint**|Совокупное время, затраченное на новый журнал.|  
|log_generated_since_last_checkpoint_in_bytes|**bigint**|Размер журнала, созданного с момента создания последней контрольной точки In-Memory OLTP.|  
|ms_since_last_checkpoint|**bigint**|Время в миллисекундах с момента создания последней контрольной точки In-Memory OLTP.|  
|checkpoint_lsn|**Числовой (38)**|Регистрационный номер транзакции в журнале восстановления (LSN), связанный с последней завершенной контрольной точкой In-Memory OLTP.|  
|current_lsn|**Числовой (38)**|Регистрационный номер транзакции в журнале, который обрабатывается в данный момент.|  
|end_of_log_lsn|**Числовой (38)**|Число номеров LSN в конце журнала.|  
|task_address|**varbinary(8)**|Адрес задачи SOS_Task. Соединение с sys.dm_os_tasks для поиска дополнительных сведений.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW DATABASE STATE` на сервере.  
  
## <a name="see-also"></a>См. также  
 [Оптимизированные для памяти динамические административные представления таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
