---
title: sys. fn_cdc_map_lsn_to_time (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_map_lsn_to_time_TSQL
- sys.fn_cdc_map_lsn_to_time
- fn_cdc_map_lsn_to_time_TSQL
- fn_cdc_map_lsn_to_time
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_cdc_map_lsn_to_time
- fn_cdc_map_lsn_to_time
ms.assetid: 405aa29c-8bd8-42d3-9f39-7494b643fc6f
author: rothja
ms.author: jroth
ms.openlocfilehash: c3573b876a10b4400969bf63200682e91bfc45fb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68046345"
---
# <a name="sysfn_cdc_map_lsn_to_time-transact-sql"></a>sys.fn_cdc_map_lsn_to_time (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение даты и времени из столбца **tran_end_time** в системной таблице [CDC. lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) для указанного регистрационного номера транзакции в журнале (LSN). Эту функцию можно использовать для систематического сопоставления диапазонов LSN с диапазонами дат в таблице изменений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_cdc_map_lsn_to_time ( lsn_value )  
```  
  
## <a name="arguments"></a>Аргументы  
 *lsn_value*  
 Значение LSN для сопоставления. *lsn_value* является **двоичным (10)**.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **datetime**  
  
## <a name="remarks"></a>Remarks  
 Эта функция может использоваться для определения времени фиксации изменения на основе значения **__ $ start_lsn** , возвращенного в строке данных об изменениях.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере функция `sys.fn_cdc_map_lsn_to_time` используется для определения времени фиксации, связанного с последним изменением, которое было обработано в заданном интервале LSN для экземпляра отслеживания `HumanResources_Employee`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @max_lsn binary(10);  
SELECT @max_lsn = MAX(__$start_lsn)  
FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee(@from_lsn, @to_lsn, 'all');  
SELECT sys.fn_cdc_map_lsn_to_time(@max_lsn);  
GO   
```  
  
## <a name="see-also"></a>См. также  
 [CDC. lsn_time_mapping &#40;&#41;Transact-SQL](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)   
 [sys. fn_cdc_map_time_to_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)   
 [CDC. fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [CDC. fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
