---
title: CDC. captured_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.captured_columns
- cdc.captured_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.captured_columns
ms.assetid: 7bb4d408-d764-4ef6-802c-f271c8d39c2a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b4bfba2f8a8512926a42c12236e5baf0d07ceda9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758724"
---
# <a name="cdccaptured_columns-transact-sql"></a>cdc.captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает по одной строке для каждого столбца, отслеживаемого в экземпляре отслеживания. По умолчанию отслеживаются все столбцы в исходной таблице. Однако столбцы могут включаться или исключаться из процесса отслеживания, если исходная таблица включается для системы отслеживания измененных данных путем указания списка столбцов. Дополнительные сведения см. в разделе [sys. sp_cdc_enable_table &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
 Рекомендуется **не выполнять запросы к системным таблицам напрямую**. Вместо этого выполните хранимую процедуру [sys. sp_cdc_get_source_columns](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md) .  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор исходной таблицы, которой принадлежит отслеживаемый столбец.|  
|**column_name**|**sysname**|Имя отслеживаемого столбца.|  
|**column_id**|**int**|Идентификатор отслеживаемого столбца в исходной таблице.|  
|**column_type**|**sysname**|Тип отслеживаемого столбца.|  
|**column_ordinal**|**int**|Порядковый номер столбца (начиная с 1) в исходной таблице. Метаданные столбца в исходной таблице исключаются. Порядковый номер 1 присваивается первому отслеживаемому столбцу.|  
|**is_computed**|**bit**|Указывает, что отслеживаемый столбец является вычисляемым столбцом в исходной таблице.|  
  
## <a name="see-also"></a>См. также  
 [CDC. change_tables &#40;&#41;Transact-SQL](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
  
  
