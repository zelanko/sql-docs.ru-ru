---
title: sys.dm_cdc_log_scan_sessions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cdc_log_scan_sessions
- dm_cdc_log_scan_sessions_TSQL
- sys.dm_cdc_log_scan_sessions_TSQL
- sys.dm_cdc_log_scan_sessions
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], log scan reporting
- sys.dm_cdc_log_scan_sessions dynamic management view
ms.assetid: d337e9d0-78b1-4a07-8820-2027d0b9f87c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d789ec1dd936b7eb40ecae56226a5879754a2260
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47698592"
---
# <a name="change-data-capture---sysdmcdclogscansessions"></a>Change Data Capture - sys.dm_cdc_log_scan_sessions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого сеанса просмотра журнала в текущей базе данных. Последняя строка соответствует текущему сеансу. Данное представление можно использовать, чтобы получить сведения о состоянии текущего сеанса просмотра журнала либо статистические сведения обо всех сеансах с момента последнего запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификатор сеанса.<br /><br /> Значение 0 в данной строке означает, что возвращаемые данные представляют собой статистику всех сеансов с момента последнего запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**start_time**|**datetime**|Время начала сеанса.<br /><br /> Когда **session_id** = 0, время начала сбора статистики.|  
|**end_time**|**datetime**|Время окончания сеанса.<br /><br /> NULL = сеанс активен.<br /><br /> Когда **session_id** = 0, время окончания последнего сеанса.|  
|**duration**|**bigint**|Продолжительность сеанса в секундах.<br /><br /> Значение 0 означает, что сеанс не содержит транзакций системы отслеживания измененных данных.<br /><br /> Когда **session_id** = 0, суммарную длительность (в секундах) всех сеансов с помощью транзакций системы отслеживания измененных данных.|  
|**scan_phase**|**Nvarchar(200)**|Текущая стадия сеанса. Ниже приведены возможные значения и их описания.<br /><br /> 1: чтение конфигурации<br />2: первая проверка, построение хэш-таблицы<br />3: во-вторых сканирования<br />4: во-вторых сканирования<br />5: во-вторых сканирования<br />6: управление версиями схемы<br />7: последнего сканирования<br />8: Готово<br /><br /> Когда **session_id** = 0, это значение всегда равно «Aggregate».|  
|**error_count**|**int**|Количество обнаруженных ошибок.<br /><br /> Когда **session_id** = 0, общее число ошибок во всех сеансах.|  
|**start_lsn**|**nvarchar(23)**|Начальный номер LSN для сеанса.<br /><br /> Когда **session_id** = 0, первый номер LSN последнего сеанса.|  
|**current_lsn**|**nvarchar(23)**|Текущий номер LSN, который был просмотрен.<br /><br /> Когда **session_id** = 0, текущий номер LSN равен 0.|  
|**end_lsn**|**nvarchar(23)**|Конечный номер LSN сеанса.<br /><br /> NULL = сеанс активен.<br /><br /> Когда **session_id** = 0, конечный номер LSN последнего сеанса.|  
|**tran_count**|**bigint**|Количество проведенных транзакций системы отслеживания измененных данных. Этот счетчик заполняется на второй стадии.<br /><br /> Когда **session_id** = 0, то число обработанных транзакций во всех сеансах.|  
|**last_commit_lsn**|**nvarchar(23)**|Номер LSN последней обработанной записи в журнале фиксирования.<br /><br /> Когда **session_id** = 0, последняя запись журнала фиксации LSN для любого сеанса.|  
|**last_commit_time**|**datetime**|Время последней обработки записи в журнале фиксирования.<br /><br /> Когда **session_id** = 0, время последней фиксации запись журнала для любого сеанса.|  
|**log_record_count**|**bigint**|Количество просмотренных записей журнала.<br /><br /> Когда **session_id** = 0, количество записей, проверенных для всех сеансов.|  
|**schema_change_count**|**int**|Количество обнаруженных операций языка DDL. Значение данного счетчика заполняется на шестой стадии.<br /><br /> Когда **session_id** = 0, то число операций DDL, обработанных во всех сеансах.|  
|**command_count**|**bigint**|Количество выполненных команд.<br /><br /> Когда **session_id** = 0, то число команд, обработанных во всех сеансах.|  
|**first_begin_cdc_lsn**|**nvarchar(23)**|Первый номер LSN, содержащий транзакции системы отслеживания измененных данных.<br /><br /> Когда **session_id** = 0, первый номер LSN, содержащий транзакции системы отслеживания измененных данных.|  
|**last_commit_cdc_lsn**|**nvarchar(23)**|Номер LSN последней записи в журнале фиксирования, содержащей транзакции системы отслеживания измененных данных.<br /><br /> Когда **session_id** = 0, последняя запись журнала фиксации LSN для любого сеанса, содержащий транзакции системы отслеживания измененных данных|  
|**last_commit_cdc_time**|**datetime**|Время обработки последней записи в журнале фиксирования, содержащей транзакции системы отслеживания измененных данных.<br /><br /> Когда **session_id** = 0, время последнего журнала фиксации записи для любого сеанса, содержащий транзакции системы отслеживания измененных данных.|  
|**Задержка**|**int**|Разница в секундах между **end_time** и **last_commit_cdc_time** в сеансе. Этот счетчик заполняется в конце седьмой стадии.<br /><br /> Когда **session_id** = 0, последнее значение ненулевое значение задержки, записанное сеансом.|  
|**empty_scan_count**|**int**|Количество последовательных сеансов, не содержащих транзакций системы отслеживания измененных данных.|  
|**failed_sessions_count**|**int**|Число сеансов, завершившихся неудачно.|  
  
## <a name="remarks"></a>Примечания  
 Значения в этом динамическом административном представлении сбрасываются при каждом запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW DATABASE STATE **sys.dm_cdc_log_scan_sessions** динамическое административное представление. Дополнительные сведения о разрешениях на динамические административные представления, см. в разделе [динамические административные представления и функции &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается информация о самом последнем сеансе.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT session_id, start_time, end_time, duration, scan_phase  
    error_count, start_lsn, current_lsn, end_lsn, tran_count  
    last_commit_lsn, last_commit_time, log_record_count, schema_change_count  
    command_count, first_begin_cdc_lsn, last_commit_cdc_lsn,   
    last_commit_cdc_time, latency, empty_scan_count, failed_sessions_count  
FROM sys.dm_cdc_log_scan_sessions  
WHERE session_id = (SELECT MAX(b.session_id) FROM sys.dm_cdc_log_scan_sessions AS b);  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sys.dm_cdc_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-errors.md)  
  
  

