---
title: sys.dm_cdc_errors (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cdc_errors_TSQL
- dm_cdc_errors
- sys.dm_cdc_errors
- sys.dm_cdc_errors_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cdc_errors dynamic management view
- change data capture [SQL Server], error reporting
ms.assetid: 898f2d76-9e63-45ef-94da-8034e86004ab
author: stevestein
ms.author: sstein
ms.openlocfilehash: 506dae205356504c76d47ffe324b82f9f34665f5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68018002"
---
# <a name="change-data-capture---sysdmcdcerrors"></a>Change Data Capture - sys.dm_cdc_errors
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку для каждой ошибки, встреченной во время сеанса просмотра журнала системы отслеживания измененных данных.  
 
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификатор сеанса.<br /><br /> 0 = ошибка не происходила в течение сеанса просмотра журнала.|  
|**phase_number**|**int**|Номер, указывающий этап, в котором находился сеанс во время возникновения ошибки. Описание каждого этапа, см. в разделе [sys.dm_cdc_log_scan_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md).|  
|**entry_time**|**datetime**|Дата и время регистрации ошибки. Это значение соответствует отметке времени в журнале ошибок SQL.|  
|**error_number**|**int**|Идентификатор сообщения об ошибке.|  
|**error_severity**|**int**|Степень серьезности сообщения, от 1 до 25.|  
|**error_state**|**int**|Номер состояния ошибки.|  
|**error_message**|**nvarchar(1024)**|Текст сообщения ошибки.|  
|**start_lsn**|**nvarchar(23)**|Начальное значение номера LSN для строк, которые обрабатывались во время возникновения ошибки.<br /><br /> 0 = ошибка не происходила в течение сеанса просмотра журнала.|  
|**begin_lsn**|**nvarchar(23)**|Начальное значение номера LSN для транзакции, которая обрабатывалась во время возникновения ошибки.<br /><br /> 0 = ошибка не происходила в течение сеанса просмотра журнала.|  
|**sequence_value**|**nvarchar(23)**|Номер LSN для строк, которые обрабатывались во время возникновения ошибки.<br /><br /> 0 = ошибка не происходила в течение сеанса просмотра журнала.|  
  
## <a name="remarks"></a>Примечания  
 **sys.dm_cdc_errors** содержит сведения об ошибках для 32 предыдущих сеансов.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW DATABASE STATE **sys.dm_cdc_errors** динамическое административное представление. Дополнительные сведения о разрешениях на динамические административные представления, см. в разделе [динамические административные представления и функции &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="see-also"></a>См. также  
 [sys.dm_cdc_log_scan_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md)   
 [sys.dm_repl_traninfo &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-repl-traninfo-transact-sql.md)  
  
  

