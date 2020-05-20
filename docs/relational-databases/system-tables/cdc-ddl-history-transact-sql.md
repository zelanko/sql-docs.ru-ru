---
title: CDC. ddl_history (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.ddl_history_TSQL
- cdc.ddl_history
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.ddl_history
ms.assetid: cb97ea71-da2f-441a-bbd2-db1f5f48ab49
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7cff85a61d7483be34852a79dfb8f3590eff0d4a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832428"
---
# <a name="cdcddl_history-transact-sql"></a>cdc.ddl_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого изменения языка DDL, внесенного в таблицы, поддерживающие систему отслеживания измененных данных. Данную таблицу можно использовать, чтобы определить время изменений DDL в исходной таблице и какие именно изменения были сделаны. Исходные таблицы, не имеющие изменений языка DDL, не имеют в этой таблице соответствующей записи.  
  
 Не рекомендуется непосредственно запрашивать системные таблицы. Вместо этого выполните хранимую процедуру [sys. sp_cdc_get_ddl_history](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md) .  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**source_object_id**|**int**|Идентификатор исходной таблицы, в которой произошло изменение языка DDL.|  
|**object_id**|**int**|Идентификатор таблицы изменений, связанной с экземпляром отслеживания исходной таблицы.|  
|**required_column_update**|**bit**|Указывает на изменение типа данных в отслеживаемом столбце исходной таблицы. Данное изменение изменило столбец таблицы изменений.|  
|**ddl_command**|**nvarchar(max)**|Инструкция языка DDL, примененная к исходной таблице.|  
|**ddl_lsn**|**binary(10)**|Номер LSN, связанный с фиксацией изменения языка DDL.|  
|**ddl_time**|**datetime**|Дата и время выполнения изменения языка DDL в исходной таблице.|  
  
## <a name="see-also"></a>См. также  
 [sys. sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [CDC. fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
