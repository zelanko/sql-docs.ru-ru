---
title: CDC.lsn_time_mapping (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- cdc.lsn_time_mapping
- cdc.lsn_time_mapping_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.lsn_time_mapping
ms.assetid: 1cb7aedc-48a4-486e-9b91-d30c4bd4084e
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 402443b42a44131e023923267d34b322e3c0c670
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102632"
---
# <a name="cdclsntimemapping-transact-sql"></a>cdc.lsn_time_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждой транзакции, имеющей строки в таблице изменений. Эта таблица используется, чтобы сопоставить значения номера LSN фиксации и время фиксации транзакции. Записи также могут регистрироваться. Для этого нет необходимости создавать таблицы изменений. Это позволяет фиксировать завершение процесса обработки номеров LSN в периоды низкой или неизменяющейся нагрузки.  
  
 Не рекомендуется непосредственно запрашивать системные таблицы. Вместо этого выполните [sys.fn_cdc_map_lsn_to_time &#40;Transact-SQL&#41; ](../../relational-databases/system-functions/sys-fn-cdc-map-lsn-to-time-transact-sql.md) и [sys.fn_cdc_map_time_to_lsn &#40;Transact-SQL&#41; ](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md) системные функции.  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**start_lsn**|**binary(10)**|Номер LSN проводимой транзакции в журнале.|  
|**tran_begin_time**|**datetime**|Время начала транзакции с заданным номером LSN.|  
|**tran_end_time**|**datetime**|Время завершения транзакции.|  
|**tran_id**|**varbinary(10)**|Идентификатор транзакции.|  
  
## <a name="see-also"></a>См. также  
 [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [CDC. &#60;capture_instance&#62;_CT &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
  
  
