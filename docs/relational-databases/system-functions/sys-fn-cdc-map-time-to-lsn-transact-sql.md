---
title: sys.fn_cdc_map_time_to_lsn (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_map_time_to_lsn
- fn_cdc_map_time_to_lsn_TSQL
- sys.fn_cdc_map_time_to_lsn_TSQL
- fn_cdc_map_time_to_lsn
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_map_time_to_lsn
- sys.fn_cdc_map_time_to_lsn
ms.assetid: 6feb051d-77ae-4c93-818a-849fe518d1d4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: aa27ea82c70cd1ffa65ce2b1d04376257abd8964
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47715998"
---
# <a name="sysfncdcmaptimetolsn-transact-sql"></a>sys.fn_cdc_map_time_to_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение регистрационный номер последовательности журнала из **start_lsn** столбца в [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) системная таблица в течение определенного времени. Эту функцию можно использовать для систематического сопоставления диапазона типа данных datetime в диапазон на основе номера LSN, необходимые для функций перечисления системы отслеживания измененных данных [cdc.fn_cdc_get_all_changes_ < экземпляр_отслеживания >](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md) и [cdc.fn _cdc_get_net_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md) для возврата данных изменений в пределах диапазона.  
  
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
 **"**< оператор_отношения >**"** {наибольшее меньше, чем | наибольшее меньше чем или равно | наименьший больше, чем | наименьший больше или равно}  
 Используется для идентификации уникального номера LSN в в **cdc.lsn_time_mapping** таблицы со связанным **tran_end_time** которое удовлетворяет связи по сравнению с *tracking_time*  значение.  
  
 *оператор_отношения* — **nvarchar(30)**.  
  
 *tracking_time*  
 Значение типа datetime для сопоставления. *tracking_time* — **datetime**.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **binary(10)**  
  
## <a name="remarks"></a>Примечания  
 Чтобы понять, каким образом **sys.fn_cdc_map_time_lsn** может использоваться для сопоставления диапазона типа данных datetime номер LSN, рассмотрим следующий сценарий. Предположим, что потребителю нужно получать изменения данных ежедневно. То есть потребителю нужны изменения только за определенные сутки. Нижней границей диапазона будет полночь предыдущего дня, не входя в диапазон. Верхней границей будет полночь заданного дня. В следующем примере показан как функция **sys.fn_cdc_map_time_to_lsn** можно использовать для систематического сопоставления этого диапазона на основе времени в диапазон на основе номера LSN, необходимые функции перечисления системы отслеживания измененных данных для возврата всех изменения в пределах диапазона.  
  
 `DECLARE @begin_time datetime, @end_time datetime, @begin_lsn binary(10), @end_lsn binary(10);`  
  
 `SET @begin_time = '2007-01-01 12:00:00.000';`  
  
 `SET @end_time = '2007-01-02 12:00:00.000';`  
  
 `SELECT @begin_lsn = sys.fn_cdc_map_time_to_lsn('smallest greater than', @begin_time);`  
  
 `SELECT @end_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal', @end_time);`  
  
 `SELECT * FROM cdc.fn_cdc_get_net_changes_HR_Department(@begin_lsn, @end_lsn, 'all` `');`  
  
 Оператор отношения '`smallest greater than`' используется для ограничения изменений теми, которые произошли после полуночи предыдущего дня. Если несколько записей с другой номер LSN значениями имеют **tran_end_time** значение, указанное в качестве нижней границы в [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) таблицы, то функция возвращает наименьший номер LSN, обеспечивая включаются все записи. Для верхней границы, оператор отношения "`largest less than or equal to`" позволяют гарантировать, что этот диапазон входят все записи за день, в том числе не иметь полуночи как их **tran_end_time** значение. Если несколько записей с другой номер LSN значениями имеют **tran_end_time** значение, указанное в качестве верхней границы, функция возвратит наибольший номер LSN, обеспечивая все записи.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется `sys.fn_cdc_map_time_lsn` функцию, чтобы определить, существуют ли все строки в [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) таблицы с **tran_end_time** значение, которое больше или равным полуночи. Запрос может применяться, например, для определения того, обработал ли процесс отслеживания изменения, зафиксированные до полуночи предыдущего дня, чтобы продолжить извлечение данных изменений для этого дня.  
  
```  
DECLARE @extraction_time datetime, @lsn binary(10);  
SET @extraction_time = '2007-01-01 12:00:00.000';  
SELECT @lsn = sys.fn_cdc_map_time_to_lsn ('smallest greater than or equal', @extraction_time);  
IF @lsn IS NOT NULL  
BEGIN  
<some action>  
END  
```  
  
## <a name="see-also"></a>См. также  
 [CDC.lsn_time_mapping &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)   
 [sys.fn_cdc_map_lsn_to_time &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-lsn-to-time-transact-sql.md)   
 [CDC.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [CDC.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
