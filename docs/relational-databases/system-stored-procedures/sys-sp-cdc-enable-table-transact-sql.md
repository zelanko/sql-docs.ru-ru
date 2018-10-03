---
title: sys.sp_cdc_enable_table (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_enable_table_TSQL
- sp_cdc_enable_table_TSQL
- sys.sp_cdc_enable_table
- sp_cdc_enable_table
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], enabling tables
- sys.sp_cdc_enable_table
- sp_cdc_enable_table
ms.assetid: 26150c09-2dca-46ad-bb01-3cb3165bcc5d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e8dafc5dce762810b2348d41e84fd71fcdb2e436
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832531"
---
# <a name="sysspcdcenabletable-transact-sql"></a>sys.sp_cdc_enable_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Активирует систему отслеживания измененных данных в указанной исходной таблице текущей базы данных. Когда таблица доступна для системы отслеживания измененных данных, запись каждой операции языка обработки данных DML, применяемая к каждой из таблиц, записывается в журнал транзакций. Процесс системы отслеживания измененных данных получает эти сведения из журнала и записывает их в таблицу изменений, к которой осуществляется доступ с помощью набора функций.  
  
 Система отслеживания измененных данных доступна не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_enable_table   
  [ @source_schema = ] 'source_schema',   
  [ @source_name = ] 'source_name' ,  [,[ @capture_instance = ] 'capture_instance' ]  
  [,[ @supports_net_changes = ] supports_net_changes ]  
  , [ @role_name = ] 'role_name'  
  [,[ @index_name = ] 'index_name' ]  
  [,[ @captured_column_list = ] 'captured_column_list' ]  
  [,[ @filegroup_name = ] 'filegroup_name' ]  
  [,[ @allow_partition_switch = ] 'allow_partition_switch' ]  
  [;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@source_schema =** ] **"***source_schema***"**  
 Имя схемы, к которой относится исходная таблица. *source_schema* — **sysname**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
 [  **@source_name =** ] **"***source_name***"**  
 Имя исходной таблицы, из которой требуется включить систему отслеживания измененных данных. *source_name* — **sysname**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
 *source_name* должен существовать в текущей базе данных. В таблицах **cdc** схемы нельзя включить для отслеживания измененных данных.  
  
 [  **@role_name =** ] **"***имя_роли***"**  
 Имя роли базы данных, которая использовалась для доступа к данным изменений. *имя_роли* — **sysname** и должен быть указан. Если явно задано значение NULL, то шлюзовая роль не используется для ограничения доступа к информации об изменениях.  
  
 Если роль с указанным именем уже существует, то будет использована она. Если роль с указанным именем не существует, то система пытается ее создать. При создании роли базы данных из ее имени удаляются конечные строковые пробелы справа. Если участник не обладает разрешением на создание роли внутри базы данных, выполнение хранимой процедуры оканчивается ошибкой.  
  
 [  **@capture_instance =** ] **"***capture_instance***"**  
 Имя экземпляра системы отслеживания, используемого для внутреннего именования объектов системы отслеживания измененных данных. *capture_instance* — **sysname** и не может иметь значение NULL.  
  
 Если не указан, имя является производным от имен исходных схемы и имени исходной таблицы в формате *schemaname_sourcename*. *capture_instance* не может превышать 100 символов и должно быть уникальным в базе данных. Указанный или производным, *capture_instance* усекается из любой пробел справа от строки.  
  
 Исходная таблица не может иметь более двух экземпляров системы отслеживания. Дополнительные сведения см. [sys.sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md).  
  
 [  **@supports_net_changes =** ] *supports_net_changes*  
 Показывает, должна ли быть включена поддержка запросов сетевых изменений для данного экземпляра системы отслеживания. *supports_net_changes* — **бит** значение по умолчанию 1, если таблица имеет первичный ключ или таблица имеет уникальный индекс, который был определен с помощью @index_name параметра. В противном случае данный параметр по умолчанию принимает значение 0.  
  
 Если значение равно 0, то формируются только функции, запрашивающие все изменения.  
  
 Если значение равно 1, то создаются функции для запроса суммарных изменений.  
  
 Если *supports_net_changes* имеет значение 1, *index_name* должен быть указан, или исходная таблица должна иметь определен первичный ключ.  
  
 [  **@index_name =** ] **"*** index_name*"  
 Имя уникального индекса, используемого для уникальной идентификации строк в исходной таблице. *index_name* — **sysname** и может иметь значение NULL. Если указано, *index_name* должно быть допустимым уникальным индексом в исходной таблице. Если *index_name* указан, то указанные столбцы индекса имеет приоритет над любой первичными ключевыми столбцами в качестве уникального идентификатора строки для таблицы.  
  
 [  **@captured_column_list =** ] **"***captured_column_list***"**  
 Указывает столбцы исходной таблицы, которые необходимо включить в таблицу изменений. *captured_column_list* — **nvarchar(max)** и может иметь значение NULL. Если аргумент имеет значение NULL, то в таблицу изменений включаются все столбцы.  
  
 Имена столбцов должны ссылаться на допустимые столбцы исходной таблицы. Столбцы, определенные в индекс первичного ключа или столбцы, определенные в индексе, который ссылается *index_name* должен быть включен.  
  
 *captured_column_list* — это разделенный запятыми список имен столбцов. Отдельные имена столбцов могут быть заключены в двойные кавычки ("") или квадратные скобки ([]). Если имя столбца содержит внедренную запятую, то его необходимо заключать в кавычки.  
  
 *captured_column_list* не может содержать следующих зарезервированных имен столбцов: **__ $start_lsn**, **__ $end_lsn**, **__ $seqval**, **__ $ Операция**, и **__ $update_mask**.  
  
 [  **@filegroup_name =** ] **"***filegroup_name***"**  
 Файловая группа, используемая для хранения таблицы изменений, созданной для экземпляра системы отслеживания. *filegroup_name* — **sysname** и может иметь значение NULL. Если указано, *filegroup_name* должен быть определен в текущей базе данных. Если значение равно NULL, то используется файловая группа, заданная по умолчанию.  
  
 Для хранения системы отслеживания информации об изменениях рекомендуется создать отдельную файловую группу.  
  
 [  **@allow_partition_switch=** ] **"***allow_partition_switch***"**  
 Указывает, возможно ли выполнение команды SWITCH PARTITION инструкции ALTER TABLE для таблицы, в которой включена система отслеживания измененных данных. *allow_partition_switch* — **бит**, значение по умолчанию 1.  
  
 Для несекционированных таблиц параметр переключателя всегда равен 1, а указанный параметр не учитывается. Если переключателю явно присваивается значение 0 для несекционированной таблицы, то выдается предупреждение 22857, показывающее, что параметр переключателя пропущен. Если переключателю явно присваивается значение 0 для секционированной таблицы, то выдается предупреждение 22356, показывающее, что операции переключения секций исходной таблицы будут запрещены. Помимо этого, если параметру переключателя явно или по умолчанию присвоено значение 1 и активизированная таблица секционирована, то выдается предупреждение 22855, показывающее, что переключатели секций не будут заблокированы. При любом переключении секций система отслеживания информации об изменениях не будет отслеживать изменения, являющиеся результатом переключения. При обработке изменений это приведет к несогласованности информации об изменениях.  
  
> [!IMPORTANT]  
>  Команда SWITCH PARTITION — это операция метаданных, однако ее выполнение влечет изменение данных. Изменения данных, связанные с этой операцией, не отслеживаются в таблицах изменений системы отслеживания информации об изменениях. Предположим, существует таблица, состоящая из трех секций, и в эту таблицу внесены изменения. Процесс отслеживания отследит операции вставки, обновления и удаления, которые пользователь выполнил в таблице. Однако, если секция переключается в другую таблицу (например, чтобы выполнить массовое удаление), строки, перемещенные в рамках этой операции, не отслеживаются как удаленные строки в таблице изменений. Аналогично, если новая секция с предварительно заполненными строками добавляется в таблицу, эти строки не отражаются в таблице изменений. Это может привести к несогласованности данных, когда изменения передаются приложению и применяются к целевому объекту.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Прежде чем включить для таблицы системы отслеживания измененных данных, необходимо активизировать саму таблицу. Чтобы определить, включена ли для сбора данных изменений базы данных, запросите **is_cdc_enabled** столбца в [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога. Чтобы включить базу данных, используйте [sys.sp_cdc_enable_db](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md) хранимой процедуры.  
  
 Когда система отслеживания информации об изменениях включена для таблицы, создается таблица изменений и одна или две функции запроса. Таблица изменений выступает в качестве репозитория для изменений исходной таблицы, извлеченных из журнала транзакций процессом отслеживания. Функции запроса используются для извлечения данных из таблицы изменений. Имена этих функций являются производными от *capture_instance* параметр одним из следующих способов:  
  
-   Все функции изменения: **cdc.fn_cdc_get_all_changes_ < экземпляр_отслеживания >**  
  
-   Функции суммарных изменений: **cdc.fn_cdc_get_net_changes_ < экземпляр_отслеживания >**  
  
 **sys.sp_cdc_enable_table** также создает задания отслеживания и очистки для базы данных, если исходная таблица является первой таблицы в базе данных для включения отслеживания измененных данных и не существует публикаций транзакций для базы данных. Он задает **is_tracked_by_cdc** столбца в [sys.tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) представление 1 каталога.  
  
> [!NOTE]  
>  При включении системы отслеживания информации об изменениях для таблицы агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не должен быть запущен. Однако процесс отслеживания не является процессом журнала транзакций и сохраняет записи в таблицу изменений, если агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не запущен.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **db_owner** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-enabling-change-data-capture-by-specifying-only-required-parameters"></a>A. Включение системы отслеживания измененных данных путем задания только требуемых параметров  
 В следующем примере включается система отслеживания измененных данных для таблицы `HumanResources.Employee`. Необходимо задавать только значения требуемых параметров.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_enable_table  
    @source_schema = N'HumanResources'  
  , @source_name = N'Employee'  
  , @role_name = N'cdc_Admin';  
GO  
```  
  
### <a name="b-enabling-change-data-capture-by-specifying-additional-optional-parameters"></a>Б. Включение системы отслеживания измененных данных путем задания дополнительных необязательных параметров  
 В следующем примере включается система отслеживания измененных данных для таблицы `HumanResources.Department`. Должны быть указаны все параметры, кроме `@allow_partition_switch`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_enable_table  
    @source_schema = N'HumanResources'  
  , @source_name = N'Department'  
  , @role_name = N'cdc_admin'  
  , @capture_instance = N'HR_Department'   
  , @supports_net_changes = 1  
  , @index_name = N'AK_Department_Name'   
  , @captured_column_list = N'DepartmentID, Name, GroupName'   
  , @filegroup_name = N'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sys.sp_cdc_disable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-table-transact-sql.md)   
 [sys.sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [CDC.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [CDC.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [sys.sp_cdc_help_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)  
  
  
