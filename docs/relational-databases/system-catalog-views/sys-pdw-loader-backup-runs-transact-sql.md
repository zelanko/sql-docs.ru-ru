---
title: sys.pdw_loader_backup_runs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2b72034c-6a11-46b9-a76c-7a88b2bea360
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8da926d5e3e12619a249fe593fac4b1be5df2bf6
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36875012"
---
# <a name="syspdwloaderbackupruns-transact-sql"></a>sys.pdw_loader_backup_runs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о текущих и выполненных операциях backup и restore в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], а также о текущих и выполненных резервного копирования, восстановления и операций загрузки в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Эта информация сохраняется и после перезапуска системы.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Уникальный идентификатор для определенной резервной копии, восстановления или запуска нагрузочного теста.<br /><br /> Ключ для этого представления.||  
|name|**nvarchar(255)**|Значение NULL для загрузки. Необязательное имя резервного копирования или восстановления.||  
|submit_time|**datetime**|Время, когда был отправлен запрос.||  
|start_time|**datetime**|Время запуска операции.||  
|end_time|**datetime**|Время операции завершения, ошибкой или был отменен.||  
|total_elapsed_time|**int**|Общее время, прошедшее между start_time и текущее время, или между start_time и end_time для завершения, отмены или неудачных запусков.|Если total_elapsed_time превышает максимальное значение для целого числа (24,8 дня в миллисекундах), он вызывает ошибку материализации из-за переполнения.<br /><br /> Максимальное значение в миллисекундах соответствует 24,8 дня.|  
|operation_type|**nvarchar(16) в формате**|Тип загрузки.|«РЕЗЕРВНОЕ КОПИРОВАНИЕ», «ЗАГРУЗИТЬ», «ВОССТАНОВЛЕНИЕ»|  
|mode|**nvarchar(16) в формате**|Режим выполнения типа.|Operation_type = **резервного КОПИРОВАНИЯ**<br />**РАЗНОСТНАЯ РЕЗЕРВНАЯ КОПИЯ**<br />**ПОЛНОЕ**<br /><br /> Operation_type = **НАГРУЗКИ**<br />**ДОБАВИТЬ**<br />**ПЕРЕЗАГРУЗИТЬ**<br />**UPSERT**<br /><br /> Operation_type = **восстановления**<br />**DATABASE**<br />**HEADER_ONLY**|  
|database_name|**nvarchar(255)**|Имя базы данных, который является контекстом этой операции||  
|имя_таблицы|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|Principal_id|**int**|Идентификатор пользователя, запросившего операцию.||  
|session_id|**nvarchar(32)**|Идентификатор сеанса, выполняющего операцию.|См. в разделе session_id в [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|request_id|**nvarchar(32)**|Идентификатор запроса, выполняющего операцию. Для загрузки это текущего или последнего запроса, связанный с этой нагрузки...|См. в разделе request_id в [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|status|**nvarchar(16) в формате**|Состояние выполнения.|«ОТМЕНЕНО», «ЗАВЕРШЕНО», «СБОЙ», «QUEUED», «РАБОТАЕТ»|  
|Ход выполнения|**int**|Процент завершения.|0 до 100|  
|command|**nvarchar(4000)**|Полный текст команды, отправленные пользователем.|Будет усечено, если длиной более 4000 символов (считая пробелы).|  
|rows_processed|**bigint**|Количество строк, обработанных в ходе этой операции.||  
|rows_rejected|**bigint**|Количество строк, отклоненных в рамках этой операции.||  
|rows_inserted|**bigint**|Количество строк, вставляемых в таблицу базы данных как часть этой операции.||  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
