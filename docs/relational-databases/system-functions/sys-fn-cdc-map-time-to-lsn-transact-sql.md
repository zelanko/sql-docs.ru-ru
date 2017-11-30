---
title: "sys.fn_cdc_map_time_to_lsn (Transact-SQL) | Документы Microsoft"
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
- sys.fn_cdc_map_time_to_lsn
- fn_cdc_map_time_to_lsn_TSQL
- sys.fn_cdc_map_time_to_lsn_TSQL
- fn_cdc_map_time_to_lsn
dev_langs: TSQL
helpviewer_keywords:
- fn_cdc_map_time_to_lsn
- sys.fn_cdc_map_time_to_lsn
ms.assetid: 6feb051d-77ae-4c93-818a-849fe518d1d4
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 17fa114ada92487d2629dc58f02f80ff91d55e35
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sysfncdcmaptimetolsn-transact-sql"></a>sys.fn_cdc_map_time_to_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение регистрационный номер последовательности журналов из **start_lsn** столбца в [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) системная таблица в течение определенного времени. Эту функцию можно использовать для систематического сопоставления диапазонов datetime в диапазон номеров LSN, необходимые для функций перечисления системы отслеживания измененных данных [cdc.fn_cdc_get_all_changes_ < экземпляр_отслеживания >](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md) и [cdc.fn _cdc_get_net_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md) для возврата изменений данных в пределах диапазона.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_cdc_map_time_to_lsn ( '<relational_operator>', tracking_time )  
  
<relational_operator> ::=  
{  largest less than  
 | largest less than or equal  
 | smallest greater than  
 | smallest greater than or equal  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 **"**< оператор_отношения >**"** {наибольшее меньше, чем | самое большое меньше чем или равно | наименьший больше, чем | наименьший больше или равно}  
 Используется для идентификации уникального номера LSN в в **cdc.lsn_time_mapping** со связанным **tran_end_time** которое удовлетворяет связи по сравнению с *tracking_time*  значение.  
  
 *оператор_отношения* — **nvarchar(30)**.  
  
 *tracking_time*  
 Значение типа datetime для сопоставления. *tracking_time* — **datetime**.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **binary(10)**  
  
## <a name="remarks"></a>Замечания  
 Чтобы понять, как **sys.fn_cdc_map_time_lsn** можно использовать для сопоставления datetime диапазоны номеров LSN, рассмотрим следующий сценарий. Предположим, что потребителю нужно получать изменения данных ежедневно. То есть потребителю нужны изменения только за определенные сутки. Нижней границей диапазона будет полночь предыдущего дня, не входя в диапазон. Верхней границей будет полночь заданного дня. В следующем примере показан способ функция **sys.fn_cdc_map_time_to_lsn** можно использовать для систематического сопоставления этого диапазона времени в диапазон номеров LSN, необходимые для функций перечисления системы отслеживания измененных данных для возврата всех изменения в пределах диапазона.  
  
 `DECLARE @begin_time datetime, @end_time datetime, @begin_lsn binary(10), @end_lsn binary(10);`  
  
 `SET @begin_time = '2007-01-01 12:00:00.000';`  
  
 `SET @end_time = '2007-01-02 12:00:00.000';`  
  
 `SELECT @begin_lsn = sys.fn_cdc_map_time_to_lsn('smallest greater than', @begin_time);`  
  
 `SELECT @end_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal', @end_time);`  
  
 `SELECT * FROM cdc.fn_cdc_get_net_changes_HR_Department(@begin_lsn, @end_lsn, 'all` `');`  
  
 Оператор отношения '`smallest greater than`' используется для ограничения изменений теми, которые произошли после полуночи предыдущего дня. Если несколько записей с другой номер LSN значениями имеют **tran_end_time** значение, определенное в качестве нижней границы в [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) таблицы, функция возвратит наименьший номер LSN, что позволит все операции включаются. Для верхней границы, оператор отношения '`largest less than or equal to`"позволяет убедиться, что диапазон включает все записи за день, включая те, в которых равны полуночи как их **tran_end_time** значение. Если несколько записей с другой номер LSN значениями имеют **tran_end_time** значение, указанной в качестве верхней границы, функция возвратит наибольший номер LSN, обеспечивая включение всех записей.  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется `sys.fn_cdc_map_time_lsn` функцию, чтобы определить, существуют ли все строки в [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) в таблице **tran_end_time** значение, которое больше или равным полуночи. Запрос может применяться, например, для определения того, обработал ли процесс отслеживания изменения, зафиксированные до полуночи предыдущего дня, чтобы продолжить извлечение данных изменений для этого дня.  
  
```  
DECLARE @extraction_time datetime, @lsn binary(10);  
SET @extraction_time = '2007-01-01 12:00:00.000';  
SELECT @lsn = sys.fn_cdc_map_time_to_lsn ('smallest greater than or equal', @extraction_time);  
IF @lsn IS NOT NULL  
BEGIN  
<some action>  
END  
```  
  
## <a name="see-also"></a>См. также:  
 [CDC.lsn_time_mapping &#40; Transact-SQL &#41;](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)   
 [sys.fn_cdc_map_lsn_to_time &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-cdc-map-lsn-to-time-transact-sql.md)   
 [CDC.fn_cdc_get_net_changes_ &#60; capture_instance &#62; &#40; Transact-SQL &#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [CDC.fn_cdc_get_all_changes_ &#60; capture_instance &#62;  &#40; Transact-SQL &#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
