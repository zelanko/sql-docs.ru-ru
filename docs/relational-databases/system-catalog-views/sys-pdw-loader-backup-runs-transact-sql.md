---
title: "sys.pdw_loader_backup_runs (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 2b72034c-6a11-46b9-a76c-7a88b2bea360
caps.latest.revision: "10"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5ebdadbeeba70444eda300f44480e49fa9992d29
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwloaderbackupruns-transact-sql"></a>sys.pdw_loader_backup_runs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о выполняющихся и завершенных операциях backup и restore в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], а также о выполняющихся и завершенных резервного копирования, восстановления и операций загрузки в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Сведения, сохраняются после перезагрузки системы.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Уникальный идентификатор для конкретного резервного копирования, восстановления или запуска нагрузочного теста.<br /><br /> Ключ для этого представления.||  
|имя|**nvarchar(255)**|Значение NULL для загрузки. Необязательное имя для резервного копирования или восстановления.||  
|submit_time|**datetime**|Время, когда был отправлен запрос.||  
|start_time|**datetime**|Время запуска операции.||  
|end_time|**datetime**|Время операции завершения, ошибкой или был отменен.||  
|total_elapsed_time|**int**|Общее время, прошедшее между start_time и текущее время или между start_time и end_time для завершения, отмены или сбоя запусков.|Если total_elapsed_time превышает максимальное значение для целого числа (24.8 дней в миллисекундах), это приведет к переполнению материализации сбой из-за.<br /><br /> Максимальное значение в миллисекундах соответствует 24.8 дней.|  
|operation_type|**nvarchar(16) в формате**|Тип нагрузки.|«РЕЗЕРВНОЕ КОПИРОВАНИЕ», «ЗАГРУЗИТЬ», «ВОССТАНОВЛЕНИЕ»|  
|mode|**nvarchar(16) в формате**|Режим выполнения типа.|Operation_type = **резервной копии**<br />**РАЗНОСТНАЯ РЕЗЕРВНАЯ КОПИЯ**<br />**ПОЛНОЕ**<br /><br /> Operation_type = **НАГРУЗКИ**<br />**ДОБАВЛЕНИЕ**<br />**ПЕРЕЗАГРУЗИТЬ**<br />**UPSERT**<br /><br /> Operation_type = **восстановления**<br />**DATABASE**<br />**HEADER_ONLY**|  
|database_name|**nvarchar(255)**|Имя базы данных, представляющего собой контекст этой операции||  
|имя_таблицы|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|Principal_id|**int**|Идентификатор пользователя, запросившего операцию.||  
|session_id|**nvarchar(32)**|Идентификатор сеанса, выполняющего операцию.|В разделе session_id в [sys.dm_pdw_exec_sessions &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|request_id|**nvarchar(32)**|Идентификатор запроса, выполняющего операцию. Для загрузки это текущего или последнего запроса, связанного с этой нагрузки...|В разделе request_id в [sys.dm_pdw_exec_requests &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|status|**nvarchar(16) в формате**|Состояние выполнения.|«ОТМЕНЕН», «ЗАВЕРШЕНО», «ОШИБКА», «QUEUED», «РАБОТАЕТ»|  
|Ход выполнения|**int**|Процент завершения.|от 0 до 100|  
|command|**nvarchar(4000)**|Полный текст команды, отправленные пользователю.|Если более 4000 символов (считая пробелы) будет усечено.|  
|rows_processed|**bigint**|Количество строк, обработанных в ходе этой операции.||  
|rows_rejected|**bigint**|Число строк, отклоненных в рамках этой операции.||  
|rows_inserted|**bigint**|Количество строк, вставляемых в таблицу базы данных в рамках этой операции.||  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
