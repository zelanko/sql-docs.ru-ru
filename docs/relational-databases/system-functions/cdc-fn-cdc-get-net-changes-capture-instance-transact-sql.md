---
title: "CDC.fn_cdc_get_net_changes_&lt;capture_instance&gt; (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_net_changes_<capture_instance>
- change data capture [SQL Server], querying metadata
- cdc.fn_cdc_get_net_changes_<capture_instance>
ms.assetid: 43ab0d1b-ead4-471c-85f3-f6c4b9372aab
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 853392a1a2db64c832c93d633def5dff30acceb6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="cdcfncdcgetnetchangesltcaptureinstancegt-transact-sql"></a>cdc.fn_cdc_get_net_changes_&lt;capture_instance&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку сетевого изменения для каждой исходной строки, измененных в течение указанного диапазона чисел последовательности журнале (LSN).  
  
 **Подождите, какова номера LSN?** Каждая запись в [журнала транзакций SQL Server](../logs/the-transaction-log-sql-server.md) однозначно идентифицируется порядковый номер транзакции в журнале (LSN). Номера LSN упорядочены таким образом, что если помеченное номером LSN2 больше LSN1, изменение, записи журнала, на который ссылается помеченное номером LSN2, произошло **после** изменение, номер LSN записи в журнале.  
  
 Номер LSN записи журнала, в которой произошло важное событие может быть полезен при формировании правильных последовательностей восстановления. Поскольку номера LSN упорядочены, их можно сравнить на равенство и неравенство (то есть \<, >, =, \<=, > =). Такие сравнения полезны при построении последовательностей восстановления.  
  
 Если в исходной строке имеется несколько изменений во время диапазон номеров LSN, одну строку, с окончательным содержимым строки возвращается функцией перечисления, описанных ниже. Например, если транзакция вставляет строку в исходной таблице и последующая транзакция в диапазон номеров LSN обновляет один или несколько столбцов в этой строке, функция возвращает только **один** строку, включающую значения обновленных столбцов.  
  
 Эта функция перечисления создается, когда в исходной таблице включается система отслеживания измененных данных с указанием сетевого отслеживания. Чтобы включить сетевое отслеживание, исходная таблица должна иметь первичный ключ или уникальный индекс. Имя функции является производным и в формате CDC.fn_cdc_get_net_changes_*capture_instance*, где *capture_instance* является значение, заданное для экземпляра отслеживания, когда исходная таблица была включить для отслеживания измененных данных. Дополнительные сведения см. в разделе [sys.sp_cdc_enable_table &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
cdc.fn_cdc_get_net_changes_capture_instance ( from_lsn , to_lsn , '<row_filter_option>' )  
  
<row_filter_option> ::=  
{ all  
 | all with mask  
 | all with merge  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *from_lsn*  
 Номер LSN, представляющий нижнюю конечную точку диапазона LSN, включаемую в результирующий набор. *from_lsn* — **binary(10)**.  
  
 Только строки в [cdc. &#91; capture_instance &#93; _CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) изменить таблицу со значением __ $start_lsn, больше или равно *from_lsn* включаются в результирующий набор.  
  
 *to_lsn*  
 Номер LSN, представляющий верхнюю конечную точку диапазона LSN, включаемую в результирующий набор. *to_lsn* — **binary(10)**.  
  
 Только строки в [cdc. &#91; capture_instance &#93; _CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) изменить таблицу со значением __ $start_lsn, меньшим или равным *from_lsn* или равно *to_lsn* , включены в результирующий набор.  
  
 *< row_filter_option >* :: = {все | все с маской | все со слиянием}  
 Параметр, управляющий содержимым столбцов метаданных, а также строк, возвращаемых в результирующем наборе. Может быть одним из следующих:  
  
 all  
 Возвращает номер LSN окончательного изменения строки и операцию, необходимую для применения строки в столбцах метаданных __ $start_lsn и \_ \_$operation. Столбец \_ \_$update_mask всегда имеет значение NULL.  
  
 all with mask  
 Возвращает номер LSN окончательного изменения строки и операцию, необходимую для применения строки в столбцах метаданных __ $start_lsn и \_ \_$operation. Кроме того, если операция обновления возвращает (\_\_$operation = 4) измененные при обновлении отслеживаемые столбцы помечаются в значении, возвращаемом в \_ \_$update_mask.  
  
 all with merge  
 Возвращает номер LSN окончательного изменения строки в столбцах метаданных __$start_lsn. Столбец \_ \_$operation будет иметь одно из двух значений: 1 для удаления и 5, чтобы указать, что операцию, необходимую для применения изменений, вставки или обновления. Столбец \_ \_$update_mask всегда имеет значение NULL.  
  
 Поскольку логика определения точной операции для конкретного изменения дополнительно усложняет запрос, эта операция предназначена для увеличения производительности запроса, когда достаточно указать, что операция изменения является вставкой или обновлением, но не требуется явно выбирать тип операции. Этот параметр особенно полезен в целевых средах, в которых операция слияния доступна непосредственно, например в среде [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|__$start_lsn|**binary(10)**|Номер LSN, связанный с фиксацией транзакции изменения.<br /><br /> Все изменения, зафиксированные в одной транзакции, имеют общий номер LSN фиксации. Например если операция обновления в исходной таблице изменяет два столбца в двух строках, таблица изменений будет содержать четыре строки с же start_lsnvalue$ __.|  
|__$operation|**int**|Определяет операцию языка обработки данных (DML), необходимую для применения строки информации об изменениях к целевому источнику данных.<br /><br /> Если параметр row_filter_option имеет значение all или all with mask, то значение в этом столбце может быть одним из следующих:<br /><br /> 1 = удаление<br /><br /> 2 = вставка<br /><br /> 4 = обновление<br /><br /> Если параметр row_filter_option имеет значение all with merge, то значение в этом столбце может быть одним из следующих:<br /><br /> 1 = удаление|  
|__$update_mask|**varbinary(128)**|Битовая маска, в которой каждому отслеживаемому столбцу, определенному для экземпляра отслеживания, соответствует один бит. В этом значении все определенные биты установлены в значение 1, если__$operation = 1 или 2. Когда \_ \_$operation = 3 или 4, значение 1 устанавливаются только биты, соответствующие столбцам, которые изменены.|  
|*\<отслеживаемые столбцы исходной таблицы>*|непостоянно|Остальные столбцы, возвращенные функцией, — это столбцы из исходной таблицы, определенные как отслеживаемые при создании экземпляра отслеживания. Если в списке отслеживаемых столбцов не указано ни одного столбца, возвращаются все столбцы в исходной таблице.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner. Всем остальным пользователям необходимо разрешение SELECT для всех отслеживаемых столбцов в исходной таблице. Кроме того, если для экземпляра отслеживания была определена шлюзовая роль, требуется членство в этой роли базы данных. Если вызывающий объект не располагает разрешением на просмотр исходных данных, функция возвращает ошибку 208 (недопустимое имя объекта).  
  
## <a name="remarks"></a>Remarks  
 Если указанный диапазон номеров LSN выходит за пределы временной шкалы для отслеживания изменений в экземпляре отслеживания, функция возвращает ошибку 208 (недопустимое имя объекта).  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется функция `cdc.fn_cdc_get_net_changes_HR_Department` сообщить о сетевых изменениях в исходной таблице `HumanResources.Department` во время в заданном интервале времени.  
  
 Вначале используется функция `GETDATE`, чтобы отметить начало интервала времени. После того как к исходной таблице применяются несколько инструкций DML, функция `GETDATE` вызывается вновь, чтобы отметить конец интервала времени. Функция [sys.fn_cdc_map_time_to_lsn](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md) затем используется для сопоставления интервал времени, ограниченный значениями номеров LSN диапазона запроса системы отслеживания изменений данных. Наконец, к функции `cdc.fn_cdc_get_net_changes_HR_Department` выполняется запрос, чтобы получить сетевые изменения в исходной таблице за этот интервал времени. Обратите внимание, что вставленная, а затем удаленная строка не появляется в результирующем наборе функции. Это происходит потому, что вставленная, а затем удаленная строка в окне запроса не выполняет сетевых изменений в исходной таблице за этот период времени. Прежде чем запустить этот пример, необходимо выполнить пример Б в [sys.sp_cdc_enable_table &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @begin_time datetime, @end_time datetime, @from_lsn binary(10), @to_lsn binary(10);  
-- Obtain the beginning of the time interval.  
SET @begin_time = GETDATE() -1;  
-- DML statements to produce changes in the HumanResources.Department table.  
INSERT INTO HumanResources.Department (Name, GroupName)  
VALUES (N'MyDept', N'MyNewGroup');  
  
UPDATE HumanResources.Department  
SET GroupName = N'Resource Control'  
WHERE GroupName = N'Inventory Management';  
  
DELETE FROM HumanResources.Department  
WHERE Name = N'MyDept';  
  
-- Obtain the end of the time interval.  
SET @end_time = GETDATE();  
-- Map the time interval to a change data capture query range.  
SET @from_lsn = sys.fn_cdc_map_time_to_lsn('smallest greater than or equal', @begin_time);  
SET @to_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal', @end_time);  
  
-- Return the net changes occurring within the query window.  
SELECT * FROM cdc.fn_cdc_get_net_changes_HR_Department(@from_lsn, @to_lsn, 'all');  
```  
  
## <a name="see-also"></a>См. также  
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [sys.fn_cdc_map_time_to_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)   
 [sys.sp_cdc_enable_table &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_help_change_data_capture &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [Об отслеживании измененных данных (SQL Server)](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
