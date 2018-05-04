---
title: sys.fn_cdc_get_max_lsn (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- sys.fn_cdc_get_max_lsn
- fn_cdc_get_max_lsn
- fn_cdc_get_max_lsn_TSQL
- sys.fn_cdc_get_max_lsn_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_max_lsn
- sys.fn_cdc_get_max_lsn
ms.assetid: 93f3a4c8-b91f-4ebb-8e96-9397bb3a1c43
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6ef2aa09f9d91f88fdd3122d2def327e503ca0da
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysfncdcgetmaxlsn-transact-sql"></a>sys.fn_cdc_get_max_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает максимальный регистрационный номер (LSN) из столбца start_lsn в [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) системной таблицы. Эту функцию можно использовать для возврата верхней конечной точки временной шкалы системы отслеживания измененных данных для любого экземпляра отслеживания.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_cdc_get_max_lsn ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **binary(10)**  
  
## <a name="remarks"></a>Замечания  
 Эта функция возвращает максимальный номер LSN в столбце start_lsn [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) таблицы. Этот последний номер LSN, обрабатываемый процессом отслеживания, когда изменения передаются в таблицы изменений базы данных. Он служит в качестве верхней конечной точки для любой временной шкалы, связанной с экземплярами отслеживания, определенными для базы данных.  
  
 Эта функция обычно используется, чтобы получить подходящую верхнюю конечную точку для интервала запроса.  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в роли базы данных public.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-maximum-lsn-value"></a>A. Возвращение максимального значения номера LSN  
 В следующем примере возвращается максимальное значение номера LSN для всех экземпляров отслеживания в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
SELECT sys.fn_cdc_get_max_lsn()AS max_lsn;  
```  
  
### <a name="b-setting-the-high-endpoint-of-a-query-range"></a>Б. Установка верхней конечной точки запроса по диапазону  
 В следующем примере номер LSN, возвращенный функцией `sys.fn_cdc_get_max_lsn`, используется для установки верхней конечной точки запроса по диапазону для экземпляра отслеживания `HumanResources_Employee`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10);  
SET @from_lsn = sys.fn_cdc_get_min_lsn(N'HumanResources_Employee');  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SELECT * FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee(@from_lsn, @to_lsn, 'all');  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sys.fn_cdc_get_min_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)  
  
  
