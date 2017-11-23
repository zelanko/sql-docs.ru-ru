---
title: "sys.fn_cdc_get_min_lsn (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server (starting with 2008)
f1_keywords:
- sys.fn_cdc_get_min_lsn
- fn_cdc_get_min_lsn
- fn_cdc_get_min_lsn_TSQL
- sys.fn_cdc_get_min_lsn_TSQL
dev_langs: TSQL
helpviewer_keywords:
- fn_cdc_get_min_lsn
- sys.fn_cdc_get_min_lsn
ms.assetid: bd49e28a-128b-4f6b-8545-6a2ec3f4afb3
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a9b301a82d09fa5bb26184ef6de3342b34070ac4
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysfncdcgetminlsn-transact-sql"></a>sys.fn_cdc_get_min_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение столбца start_lsn для указанного экземпляра отслеживания из [cdc.change_tables](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md) системной таблицы. Это значение представляет нижнюю конечную точку интервала допустимости для экземпляра отслеживания.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_cdc_get_min_lsn ( 'capture_instance_name' )  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *capture_instance_name* **"**  
 Имя экземпляра отслеживания. *capture_instance_name* — **sysname**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **binary(10)**  
  
## <a name="remarks"></a>Замечания  
 Возвращает значение 0x00000000000000000000, если экземпляр отслеживания не существует или если участник не авторизован для доступа к данным изменений, связанным с этим экземпляром отслеживания.  
  
 Эта функция обычно используется, чтобы вернуть нижнюю конечную точку временной шкалы системы отслеживания измененных данных для экземпляра отслеживания. Эту функцию можно также использовать для проверки того, входят ли конечные точки диапазона запроса во временную шкалу экземпляра отслеживания, перед запросом данных изменений. Важно выполнять такие проверки, поскольку нижняя конечная точка экземпляра отслеживания изменяется во время очистки таблиц изменений. Если между запросами информации об изменениях прошло достаточно много времени, даже нижняя конечная точка, установленная на верхнюю конечную точку предыдущего запроса информации об изменениях, может лежать вне текущей временной шкалы.  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner. Всем остальным пользователям необходимо разрешение SELECT для всех отслеживаемых столбцов в исходной таблице. Кроме того, если для экземпляра отслеживания была определена шлюзовая роль, требуется членство в этой роли базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-minimum-lsn-value-for-a-specified-capture-instance"></a>A. Возврат минимального значения номера LSN для заданного экземпляра отслеживания  
 Следующий пример возвращает минимальное значение номера LSN для экземпляра отслеживания `HumanResources_Employee` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE AdventureWorks2-12;  
GO  
SELECT sys.fn_cdc_get_min_lsn ('HumanResources_Employee')AS min_lsn;  
  
```  
  
### <a name="b-verifying-the-low-endpoint-of-a-query-range"></a>Б. Проверка нижней конечной точки диапазона запроса  
 Следующий пример использует минимальное значение номера LSN, возвращенное функцией `sys.fn_cdc_get_min_lsn` для проверки того, является ли предложенная нижняя конечная точка запроса данных изменений действительной для текущей временной шкалы экземпляра отслеживания `HumanResources_Employee`. В примере предполагается, что предыдущая верхняя точка номера LSN для экземпляра отслеживания была сохранена и является доступной для установки переменной `@save_to_lsn`. Для этого примера переменной `@save_to_lsn` присвоено значение 0x000000000000000000, чтобы принудительно запустить раздел обработки ошибок.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @min_lsn binary(10), @from_lsn binary(10),@save_to_lsn binary(10), @to_lsn binary(10);  
-- Sets @save_to_lsn to the previous high endpoint saved from the last change data request.  
SET @save_to_lsn = 0x000000000000000000;  
-- Sets the upper endpoint for the query range to the current maximum LSN.  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
-- Sets the @min_lsn parameter to the current minimum LSN for the capture instance.  
SET @min_lsn = sys.fn_cdc_get_min_lsn ('HumanResources_Employee');  
-- Sets the low endpoint for the query range to the LSN that follows the previous high endpoint.  
SET @from_lsn = sys.fn_cdc_increment_lsn(@save_to_lsn);  
-- Tests to verify the low endpoint is valid for the current capture instance.  
IF (@from_lsn < @min_lsn)  
    BEGIN  
        RAISERROR('Low endpoint of the request interval is invalid.', 16, -1);  
    END  
ELSE  
-- Return the changes occurring within the query range.  
    SELECT * FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee(@from_lsn, @to_lsn, 'all');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.fn_cdc_get_max_lsn &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-cdc-get-max-lsn-transact-sql.md)   
 [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)  
  
  
