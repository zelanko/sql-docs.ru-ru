---
title: "CDC.fn_cdc_get_all_changes_&lt;capture_instance&gt; (Transact-SQL) | Документы Microsoft"
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
dev_langs: TSQL
helpviewer_keywords:
- fn_cdc_get_all_changes_<capture_instance>
- change data capture [SQL Server], querying metadata
- cdc.fn_cdc_get_all_changes_<capture_instance>
ms.assetid: c6bad147-1449-4e20-a42e-b51aed76963c
caps.latest.revision: "31"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 111fab345e7679745e72ebe874dabcca3bed62fb
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="cdcfncdcgetallchangesltcaptureinstancegt--transact-sql"></a>CDC.fn_cdc_get_all_changes_&lt;capture_instance&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого изменения в исходной таблице в заданном диапазоне номеров LSN. Если за истекший период исходная строка претерпевала несколько изменений, в результирующем наборе отображается каждое из них. Помимо данных об изменениях, результирующий набор содержит четыре столбца метаданных, предоставляющих информацию, необходимую для применения изменений к другим источникам данных. Параметры фильтрации строк управляют как содержимым столбцов метаданных, так и строк, возвращаемых в результирующем наборе. Если параметру фильтрации строк присвоено значение «all», то каждое изменение фиксируется в виде отдельной строки. Если указан параметр «all update old», операции обновления представлены в виде двух строк: одна содержит значения отслеживаемых столбцов до обновления, другая содержит значения отслеживаемых столбцов после обновления.  
  
 Данная функция перечисления создается, если для исходной таблицы включена система отслеживания измененных данных. Имя функции является производным и использует формат **cdc.fn_cdc_get_all_changes_***capture_instance* где *capture_instance* представляет значение, заданное для сбора данных экземпляр при включении исходной таблицы для отслеживания измененных данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
cdc.fn_cdc_get_all_changes_capture_instance ( from_lsn , to_lsn , '<row_filter_option>' )  
  
<row_filter_option> ::=  
{ all  
 | all update old  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *from_lsn*  
 Значение нижней границы диапазона номеров LSN, включенных в результирующий набор. *from_lsn* — **binary(10)**.  
  
 Только строки в [cdc. &#91; capture_instance &#93; _CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) изменить таблицу со значением в **__ $start_lsn** больше или равно *from_lsn* включаются в результирующий набор.  
  
 *to_lsn*  
 Значение верхней границы диапазона номеров LSN, включенных в результирующий набор. *to_lsn* — **binary(10)**.  
  
 Только строки в [cdc. &#91; capture_instance &#93; _CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) изменить таблицу со значением в **__ $start_lsn** меньше или равно *from_lsn* или равно *to_lsn* включаются в результирующий набор.  
  
 <row_filter_option> ::= { all | all update old }  
 Параметр, управляющий содержимым столбцов метаданных, а также строк, возвращаемых в результирующем наборе.  
  
 Может быть одним из следующих:  
  
 all  
 Возвращает все изменения в пределах указанного диапазона номеров LSN. При использовании этого параметра для изменений, произошедших в результате операции обновления, возвращаются строки, содержащие только новые значения, записанные после обновления.  
  
 all update old  
 Возвращает все изменения в пределах указанного диапазона номеров LSN. Если указан этот параметр, то для изменений, произошедших в результате операции обновления, возвращаются строки, содержащие как старые значения столбцов, так и новые значения, записанные после обновления.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**__$start_lsn**|**binary(10)**|Номер LSN фиксации, связанный с изменением, хранящим последовательность фиксации данного изменения. Все изменения, зафиксированные в одной транзакции, имеют общий номер LSN фиксации.|  
|**__$seqval**|**binary(10)**|Последовательное значение, используемое для упорядочивания изменений строк в пределах транзакции.|  
|**__$operation**|**int**|Определяет операцию языка обработки данных (DML), необходимую для применения строки информации об изменениях к целевому источнику данных. Возможен один из следующих вариантов.<br /><br /> 1 = удаление<br /><br /> 2 = вставка<br /><br /> 3 = обновление (значения отслеживаемого столбца перед операцией обновления). Данное значение используется, только если параметр фильтрации строк равен «all update old».<br /><br /> 4 = обновление (значения отслеживаемого столбца после операции обновления).|  
|**__$update_mask**|**varbinary(128)**|Битовая маска, в которой каждому отслеживаемому столбцу, определенному для экземпляра отслеживания, соответствует один бит. Это значение все определенные биты установлены в значение 1, если **__ $operation** = 1 или 2. Когда **__ $operation** = 3 или 4, значение 1 устанавливаются только биты, соответствующие столбцам, которые изменены.|  
|**\<отслеживаемых столбцов исходной таблицы >**|непостоянно|Оставшиеся столбцы, возвращенные функцией, представляют собой отслеживаемые столбцы, определенные в момент создания экземпляра отслеживания. Если в списке отслеживаемых столбцов не указано ни одного столбца, возвращаются все столбцы в исходной таблице.|  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных. Всем остальным пользователям необходимо разрешение SELECT для всех отслеживаемых столбцов в исходной таблице. Кроме того, если для экземпляра отслеживания была определена шлюзовая роль, требуется членство в этой роли базы данных. Если вызывающий объект не имеет разрешения на просмотр исходных данных, то функция возвращает ошибку 229 («SELECT отказано в разрешении на объект «fn_cdc_get_all_changes_...», база данных "\<DatabaseName >", схеме «cdc».»).  
  
## <a name="remarks"></a>Замечания  
 Если указанный диапазон номеров LSN выходит за пределы временной шкалы отслеживания изменений в экземпляре системы отслеживания, то функция возвращает ошибку 208 (Для процедуры или функции cdc.fn_cdc_get_all_changes указано недостаточное количество аргументов).  
  
 Столбцы типа данных **изображения**, **текст**, и **ntext** всегда назначается значение NULL значения при **__ $operation** = 1 или **__ $ Операция** = 3. Столбцы типа данных **varbinary(max)**, **varchar(max)**, или **nvarchar(max)** назначаются НУЛЕВОЕ значение, если **__ $operation** = 3 Если столбец не изменен во время обновления. Когда **__ $operation** = 1, этим столбцам присваиваются их значения во время удаления. Вычисляемые столбцы, которые включены в экземпляр системы отслеживания, всегда имеют значение NULL.  
  
## <a name="examples"></a>Примеры  
 Несколько [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] шаблоны доступны, показывающие, как использовать функции запроса системы отслеживания измененных данных. Эти шаблоны доступны на **представление** в меню [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Дополнительные сведения см. в разделе [обозреватель шаблонов](http://msdn.microsoft.com/library/b9ee55c5-bb44-4f76-90ac-792d8d83b4c8).  
  
 Этот пример иллюстрирует шаблон `Enumerate All Changes for Valid Range Template`. В нем функция `cdc.fn_cdc_get_all_changes_HR_Department` сообщает обо всех текущих доступных изменениях для экземпляра системы отслеживания `HR_Department`, который определен для исходной таблицы HumanResources.Department в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
-- ========  
-- Enumerate All Changes for Valid Range Template  
-- ========  
USE AdventureWorks2012;  
GO  
  
DECLARE @from_lsn binary(10), @to_lsn binary(10);  
SET @from_lsn = sys.fn_cdc_get_min_lsn('HR_Department');  
SET @to_lsn   = sys.fn_cdc_get_max_lsn();  
SELECT * FROM cdc.fn_cdc_get_all_changes_HR_Department  
  (@from_lsn, @to_lsn, N'all');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CDC.fn_cdc_get_net_changes_ &#60; capture_instance &#62; &#40; Transact-SQL &#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [sys.fn_cdc_map_time_to_lsn &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)   
 [sys.sp_cdc_get_ddl_history &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md)   
 [процедуру sys.sp_cdc_get_captured_columns &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md)   
 [sys.sp_cdc_help_change_data_capture &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [Об отслеживании измененных данных (SQL Server)](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
