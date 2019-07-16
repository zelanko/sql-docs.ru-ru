---
title: CDC.fn_cdc_get_all_changes_&lt;capture_instance&gt; (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_all_changes_<capture_instance>
- change data capture [SQL Server], querying metadata
- cdc.fn_cdc_get_all_changes_<capture_instance>
ms.assetid: c6bad147-1449-4e20-a42e-b51aed76963c
author: rothja
ms.author: jroth
ms.openlocfilehash: 0a4e0e62121d289f9eb897c79abb2991a57890a4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68043049"
---
# <a name="cdcfncdcgetallchangesltcaptureinstancegt--transact-sql"></a>CDC.fn_cdc_get_all_changes_&lt;capture_instance&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого изменения в исходной таблице в заданном диапазоне номеров LSN. Если за истекший период исходная строка претерпевала несколько изменений, в результирующем наборе отображается каждое из них. Помимо данных об изменениях, результирующий набор содержит четыре столбца метаданных, предоставляющих информацию, необходимую для применения изменений к другим источникам данных. Параметры фильтрации строк управляют как содержимым столбцов метаданных, так и строк, возвращаемых в результирующем наборе. Если параметру фильтрации строк присвоено значение «all», то каждое изменение фиксируется в виде отдельной строки. Если указан параметр «all update old», операции обновления представлены в виде двух строк: одна содержит значения отслеживаемых столбцов до обновления, другая содержит значения отслеживаемых столбцов после обновления.  
  
 Данная функция перечисления создается, если для исходной таблицы включена система отслеживания измененных данных. Имя функции является производным и использует формат **cdc.fn_cdc_get_all_changes_** _capture_instance_ где *capture_instance* является значение, указанное для сбора данных экземпляр, при включении исходной таблицы для отслеживания измененных данных.  
  
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
 Значение нижней границы диапазона номеров LSN, включенных в результирующий набор. *from_lsn* — **binary(10)** .  
  
 Только строки в [cdc.&#91; capture_instance&#93;_CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) изменить таблицу со значением в **__ $start_lsn** больше или равно *from_lsn* включаются в результирующий набор.  
  
 *to_lsn*  
 Значение верхней границы диапазона номеров LSN, включенных в результирующий набор. *to_lsn* — **binary(10)** .  
  
 Только строки в [cdc.&#91; capture_instance&#93;_CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) изменить таблицу со значением в **__ $start_lsn** меньше или равно *from_lsn* или равным *to_lsn* включены в результирующем наборе.  
  
 <row_filter_option> ::= { all | all update old }  
 Параметр, управляющий содержимым столбцов метаданных, а также строк, возвращаемых в результирующем наборе.  
  
 Может быть одним из следующих:  
  
 all  
 Возвращает все изменения в пределах указанного диапазона номеров LSN. При использовании этого параметра для изменений, произошедших в результате операции обновления, возвращаются строки, содержащие только новые значения, записанные после обновления.  
  
 all update old  
 Возвращает все изменения в пределах указанного диапазона номеров LSN. Если указан этот параметр, то для изменений, произошедших в результате операции обновления, возвращаются строки, содержащие как старые значения столбцов, так и новые значения, записанные после обновления.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**__$start_lsn**|**binary(10)**|Номер LSN фиксации, связанный с изменением, хранящим последовательность фиксации данного изменения. Все изменения, зафиксированные в одной транзакции, имеют общий номер LSN фиксации.|  
|**__$seqval**|**binary(10)**|Последовательное значение, используемое для упорядочивания изменений строк в пределах транзакции.|  
|**__$operation**|**int**|Определяет операцию языка обработки данных (DML), необходимую для применения строки информации об изменениях к целевому источнику данных. Возможен один из следующих вариантов.<br /><br /> 1 = удаление<br /><br /> 2 = вставка<br /><br /> 3 = обновление (значения отслеживаемого столбца перед операцией обновления). Данное значение используется, только если параметр фильтрации строк равен «all update old».<br /><br /> 4 = обновление (значения отслеживаемого столбца после операции обновления).|  
|**__$update_mask**|**varbinary(128)**|Битовая маска, в которой каждому отслеживаемому столбцу, определенному для экземпляра отслеживания, соответствует один бит. Это значение все определенные биты установлены в значение 1, если **__ $operation** = 1 или 2. Когда **__ $operation** = 3 или 4, значение 1 устанавливаются только биты, соответствующие измененным столбцам.|  
|**\<отслеживаемые столбцы исходной таблицы>**|непостоянно|Оставшиеся столбцы, возвращенные функцией, представляют собой отслеживаемые столбцы, определенные в момент создания экземпляра отслеживания. Если в списке отслеживаемых столбцов не указано ни одного столбца, возвращаются все столбцы в исходной таблице.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных. Всем остальным пользователям необходимо разрешение SELECT для всех отслеживаемых столбцов в исходной таблице. Кроме того, если для экземпляра отслеживания была определена шлюзовая роль, требуется членство в этой роли базы данных. Если вызывающий объект не имеет разрешения на просмотр исходных данных, то функция возвращает ошибку 229 ("объект «fn_cdc_get_all_changes_...», запрещено разрешение SELECT, базы данных"\<DatabaseName > ", схемы «cdc».»).  
  
## <a name="remarks"></a>Примечания  
 Если указанный диапазон номеров LSN выходит за пределы временной шкалы отслеживания изменений в экземпляре системы отслеживания, то функция возвращает ошибку 208 (Для процедуры или функции cdc.fn_cdc_get_all_changes указано недостаточное количество аргументов).  
  
 Столбцы типа данных **изображение**, **текст**, и **ntext** всегда назначаются значения NULL значение, если **__ $operation** = 1 или **__ $ Операция** = 3. Столбцы типа данных **varbinary(max)** , **varchar(max)** , или **nvarchar(max)** назначаются НУЛЕВОЕ значение, если **__ $operation** = 3 Если столбец изменен во время обновления. Когда **__ $operation** = 1, этим столбцам присваиваются их значения во время удаления. Вычисляемые столбцы, которые включены в экземпляр системы отслеживания, всегда имеют значение NULL.  
  
## <a name="examples"></a>Примеры  
 Несколько [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] доступны шаблоны, показывающие, как использовать функции запроса системы отслеживания измененных данных. Эти шаблоны доступны на **представление** меню в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Дополнительные сведения см. в разделе [обозреватель шаблонов](../../ssms/template/template-explorer.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [CDC.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [sys.fn_cdc_map_time_to_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)   
 [sys.sp_cdc_get_ddl_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md)   
 [процедуру sys.sp_cdc_get_captured_columns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md)   
 [sys.sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [Об отслеживании измененных данных (SQL Server)](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
