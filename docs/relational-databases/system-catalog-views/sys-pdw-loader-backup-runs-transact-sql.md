---
title: sys. pdw_loader_backup_runs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2b72034c-6a11-46b9-a76c-7a88b2bea360
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6ca5fc44e34153411e32a890b509d86caacbd9db
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86196984"
---
# <a name="syspdw_loader_backup_runs-transact-sql"></a>sys. pdw_loader_backup_runs (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит сведения о текущих и завершенных операциях резервного копирования и восстановления в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] , а о текущих и завершенных операциях резервного копирования, восстановления и загрузки в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] . Эта информация сохраняется и после перезапуска системы.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Уникальный идентификатор для конкретного выполнения операции резервного копирования, восстановления или загрузки.<br /><br /> Ключ для этого представления.||  
|name|**nvarchar(255)**|Значение NULL для Load. Необязательное имя для резервного копирования или восстановления.||  
|submit_time|**datetime**|Время отправки запроса.||  
|start_time|**datetime**|Время начала операции.||  
|end_time|**datetime**|Время завершения, сбоя или отмены операции.||  
|total_elapsed_time|**int**|Общее время, прошедшее между start_time и текущим временем, а также между start_time и end_time для завершенных, отмененных или неудачных запусков.|Если total_elapsed_time превышает максимальное значение для целого числа (24,8 дней в миллисекундах), это приведет к сбою материализации из-за переполнения.<br /><br /> Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
|operation_type|**nvarchar (16)**|Тип нагрузки.|"BACKUP", "LOAD", "RESTORE"|  
|mode|**nvarchar (16)**|Режим в пределах типа запуска.|Для operation_type = **BACKUP**<br />**DIFFERENTIAL (разностная)**<br />**ПОЛНОЕ**<br /><br /> Для operation_type = **Load**<br />**Добавление**<br />**ПЕРЕЗАГРУЗИТЬ**<br />**UPSERT**<br /><br /> Для operation_type = **RESTORE**<br />**СУБД**<br />**HEADER_ONLY**|  
|database_name|**nvarchar(255)**|Имя базы данных, которая является контекстом этой операции||  
|имя_таблицы|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|Principal_id|**int**|Идентификатор пользователя, запросившего операцию.||  
|session_id|**nvarchar(32)**|Идентификатор сеанса, выполняющего операцию.|См. раздел session_id в [sys. dm_pdw_exec_sessions &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|request_id|**nvarchar(32)**|Идентификатор запроса, выполняющего операцию. Для загрузки это текущий или последний запрос, связанный с этой нагрузкой.|См. раздел request_id в [sys. dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|status|**nvarchar (16)**|Состояние запуска.|"ОТМЕНЕНО", "ЗАВЕРШЕНО", "СБОЙ", "В ОЧЕРЕДИ", "ВЫПОЛНЯЕТСЯ"|  
|progress|**int**|Процент выполнения.|0–100|  
|.|**nvarchar(4000)**|Полный текст команды, отправленной пользователем.|Будет обрезано, если длиннее 4000 символов (пробелов).|  
|rows_processed|**bigint**|Количество строк, обработанных как часть этой операции.||  
|rows_rejected|**bigint**|Количество строк, отклоненных в рамках этой операции.||  
|rows_inserted|**bigint**|Число строк, вставленных в таблицы базы данных в рамках этой операции.||  
  
## <a name="see-also"></a>См. также  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md) (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
  
  
