---
title: CDC. lsn_time_mapping (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.lsn_time_mapping
- cdc.lsn_time_mapping_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.lsn_time_mapping
ms.assetid: 1cb7aedc-48a4-486e-9b91-d30c4bd4084e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 417e57b6872ca5b54f7acefb28f65b2652f41da7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758691"
---
# <a name="cdclsn_time_mapping-transact-sql"></a>cdc.lsn_time_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает по одной строке для каждой транзакции, имеющей строки в таблице изменений. Эта таблица используется, чтобы сопоставить значения номера LSN фиксации и время фиксации транзакции. Записи также могут регистрироваться. Для этого нет необходимости создавать таблицы изменений. Это позволяет фиксировать завершение процесса обработки номеров LSN в периоды низкой или неизменяющейся нагрузки.  
  
 Не рекомендуется непосредственно запрашивать системные таблицы. Вместо этого выполните функции [sys. fn_cdc_map_lsn_to_time &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-lsn-to-time-transact-sql.md) и [sys. fn_cdc_map_time_to_lsn &#40;transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md) .  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**start_lsn**|**binary(10)**|Номер LSN проводимой транзакции в журнале.|  
|**tran_begin_time**|**datetime**|Время начала транзакции с заданным номером LSN.|  
|**tran_end_time**|**datetime**|Время завершения транзакции.|  
|**tran_id**|**varbinary (10)**|Идентификатор транзакции.|  
  
## <a name="see-also"></a>См. также:  
 [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [CDC. &#60;capture_instance&#62;_CT &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
  
  
