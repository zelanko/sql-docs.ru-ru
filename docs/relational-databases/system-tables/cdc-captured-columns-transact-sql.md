---
title: CDC.captured_columns (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- cdc.captured_columns
- cdc.captured_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.captured_columns
ms.assetid: 7bb4d408-d764-4ef6-802c-f271c8d39c2a
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1f5089e21ea96c5e145dc3a62540436044a52150
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="cdccapturedcolumns-transact-sql"></a>cdc.captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого столбца, отслеживаемого в экземпляре отслеживания. По умолчанию отслеживаются все столбцы в исходной таблице. Однако столбцы могут включаться или исключаться из процесса отслеживания, если исходная таблица включается для системы отслеживания измененных данных путем указания списка столбцов. Дополнительные сведения см. в разделе [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
 Мы рекомендуем вам **не запрашивать системные таблицы непосредственно**. Вместо этого выполните [sys.sp_cdc_get_source_columns](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md) хранимой процедуры.  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор исходной таблицы, которой принадлежит отслеживаемый столбец.|  
|**column_name**|**sysname**|Имя отслеживаемого столбца.|  
|**column_id**|**int**|Идентификатор отслеживаемого столбца в исходной таблице.|  
|**column_type**|**sysname**|Тип отслеживаемого столбца.|  
|**column_ordinal**|**int**|Порядковый номер столбца (начиная с 1) в исходной таблице. Метаданные столбца в исходной таблице исключаются. Порядковый номер 1 присваивается первому отслеживаемому столбцу.|  
|**is_computed**|**бит**|Указывает, что отслеживаемый столбец является вычисляемым столбцом в исходной таблице.|  
  
## <a name="see-also"></a>См. также  
 [CDC.change_tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
  
  
