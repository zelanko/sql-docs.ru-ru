---
title: sys.dm_exec_describe_first_result_set (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_describe_first_result_set
- sys.dm_exec_describe_first_result_set_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_describe_first_result_set catalog view
ms.assetid: 6ea88346-0bdb-4f0e-9f1f-4d85e3487d23
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7c57e90b9a7fbe4846698f04e3cde808eed64985
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624742"
---
# <a name="sysdmexecdescribefirstresultset-transact-sql"></a>sys.dm_exec_describe_first_result_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Данная функция динамического управления принимает [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции в качестве параметра и описывает метаданные первого результирующего набора для инструкции.  
  
 **sys.dm_exec_describe_first_result_set** имеет тот же результат определение набора, что [sys.dm_exec_describe_first_result_set_for_object &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md) и аналогичен [sp_ describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md).  
  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_exec_describe_first_result_set(@tsql, @params, @include_browse_information)  
```  
  
## <a name="arguments"></a>Аргументы  
 *\@tsql*  
 Одна или несколько инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. *Transact SQL_batch* может быть **nvarchar (***n***)** или **nvarchar(max)**.  
  
 *\@params*  
 \@params обеспечивает строку объявления параметров для [!INCLUDE[tsql](../../includes/tsql-md.md)] пакетной службы, схожего с sp_executesql. Параметры могут быть **nvarchar(n)** или **nvarchar(max)**.  
  
 Строка, содержащая определения всех параметров, внедренных в [!INCLUDE[tsql](../../includes/tsql-md.md)] *_batch*. Строка должна представлять собой константу в Юникоде либо переменную в этом же формате. Определение каждого параметра состоит из имени параметра и типа данных. *n* — заполнитель, указывающий Дополнительные определения параметра. Каждый параметр, указанный в инструкции языка должен быть определен в \@params. Если [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция или пакет в инструкции не содержит параметров, \@params не является обязательным. Значением по умолчанию для этого аргумента является NULL.  
  
 *\@include_browse_information*  
 Если имеет значение 1, то каждый запрос анализируется так, как будто он имеет параметр FOR BROWSE для запроса. Возвращаются дополнительные ключевые столбцы и сведения об исходной таблице.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
 Общие метаданные возвращаются в результирующем наборе. Одна строка для каждого из столбцов в метаданных результатов описывает тип и допустимость значения NULL для столбца в формате, показанном в следующей таблице. Если первая инструкция не существует для каждого пути управления, возвращается результирующий набор с нулем строк.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**is_hidden**|**bit**|Указывает, что столбец является дополнительным, добавленным в информационных целях и для просмотра сведений и фактически не присутствует в результирующем наборе.|  
|**column_ordinal**|**int**|Содержит порядковый номер столбца в результирующем наборе. Позиция первого столбца будет указана как 1.|  
|**name**|**sysname**|Содержит имя столбца, если его можно определить. В противном случае содержит NULL.|  
|**is_nullable**|**bit**|Содержит следующие значения.<br /><br /> Значение 1, если в столбце допускаются значения NULL.<br /><br /> Значение 0, если в столбце не допускаются значения NULL.<br /><br /> Значение 1, если невозможно определить, допускаются ли в столбце значения NULL.|  
|**system_type_id**|**int**|Содержит system_type_id для типа данных столбца, как указано в sys.types. Для типов CLR, даже если system_type_name возвращает NULL, этот столбец вернет значение 240.|  
|**system_type_name**|**nvarchar(256)**|Содержит имя и аргументы (длина, точность, масштаб и т. д.), указанные для типа данных столбца.<br /><br /> Если тип данных является пользовательским псевдонимом, то здесь указывается базовый системный тип данных.<br /><br /> Если тип данных является определенным пользователем типом CLR, то в этом столбце возвращается NULL.|  
|**max_length**|**smallint**|Максимальная длина столбца (в байтах).<br /><br /> -1 = тип данных столбца — **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, или **xml**.<br /><br /> Для **текст** столбцы, **max_length** значение будет равно 16 или значение, заданное параметром **sp_tableoption «text in row»**.|  
|**Точность**|**tinyint**|Точность столбца, если он является числовым. В противном случае возвращается 0.|  
|**Масштаб**|**tinyint**|Масштаб значений столбца в случае числового выражения. В противном случае возвращается 0.|  
|**collation_name**|**sysname**|Имя параметров сортировки столбца, если он символьный. В противном случае возвращается NULL.|  
|**user_type_id**|**int**|Для типов CLR и псевдонимов содержит user_type_id для типа данных столбца, как указано в sys.types. В противном случае значение равно NULL.|  
|**user_type_database**|**sysname**|Для типов CLR и псевдонимов содержит имя базы данных, в которой этот тип определен. В противном случае значение равно NULL.|  
|**user_type_schema**|**sysname**|Для типов CLR и псевдонимов содержит имя схемы, в которой этот тип определен. В противном случае значение равно NULL.|  
|**user_type_name**|**sysname**|Для типов CLR и псевдонимов содержит имя типа. В противном случае значение равно NULL.|  
|**assembly_qualified_type_name**|**nvarchar(4000)**|Для типов CLR возвращает имя сборки и класса, определяющего тип. В противном случае значение равно NULL.|  
|**xml_collection_id**|**int**|Содержит xml_collection_id для типа данных столбца, как указано в sys.columns. Этот столбец возвращает значение NULL, если возвращаемый тип не связан с коллекцией схем XML.|  
|**xml_collection_database**|**sysname**|Содержит базу данных, в которой определена коллекция схем XML, связанная с этим типом. Этот столбец возвращает значение NULL, если возвращаемый тип не связан с коллекцией схем XML.|  
|**xml_collection_schema**|**sysname**|Содержит схему, в которой определена коллекция схем XML, связанная с этим типом. Этот столбец возвращает значение NULL, если возвращаемый тип не связан с коллекцией схем XML.|  
|**xml_collection_name**|**sysname**|Содержит имя коллекции схем XML, связанной с этим типом. Этот столбец возвращает значение NULL, если возвращаемый тип не связан с коллекцией схем XML.|  
|**is_xml_document**|**bit**|Возвращает значение 1, если возвращается тип данных XML, который гарантированно будет полным XML-документом (включая корневой узел), а не фрагментом XML. В противном случае возвращается 0.|  
|**is_case_sensitive**|**bit**|Возвращает значение 1, если столбец относится к строковому типу с учетом регистра. В противном случае возвращается значение 0.|  
|**is_fixed_length_clr_type**|**bit**|Возвращает значение 1, если столбец относится к типу CLR с фиксированной длиной. В противном случае возвращается значение 0.|  
|**source_server**|**sysname**|Имя сервера происхождения (в случае происхождения от удаленного сервера). Имя дается так, как оно отображается в представлении каталога sys.servers. Возвращает NULL, если столбец поступает с локального сервера или если невозможно определить, с какого сервера он поступил. Заполняется только при запросе просмотра информации.|  
|**source_database**|**sysname**|Имя исходной базы данных, возвращаемое столбцом этого результата. Возвращает NULL, если не удалось определить базу данных. Заполняется только при запросе просмотра информации.|  
|**source_schema**|**sysname**|Имя исходной схемы, возвращаемое столбцом в этом результате. Возвращает NULL, если не удалось определить схему. Заполняется только при запросе просмотра информации.|  
|**source_table**|**sysname**|Имя исходной таблицы, возвращаемое столбцом в этом результате. Возвращает NULL, если не удалось определить таблицу. Заполняется только при запросе просмотра информации.|  
|**source_column**|**sysname**|Имя исходного столбца, возвращаемое результирующим столбцом. Возвращает NULL, если не удалось определить столбец. Заполняется только при запросе просмотра информации.|  
|**is_identity_column**|**bit**|Возвращает значение 1, если столбец является столбцом идентификаторов, либо значение 0 в противном случае. Возвращает NULL, если не удалось определить, является ли столбец столбцом идентификаторов.|  
|**is_part_of_unique_key**|**bit**|Возвращает значение 1, если столбец является частью уникального индекса (включая ограничения уникальности и первичности), либо значение 0 в противном случае. Возвращает NULL, если не удалось определить, является ли столбец частью уникального индекса. Заполняется только при запросе просмотра информации.|  
|**is_updateable**|**bit**|Возвращает значение 1, если столбец можно обновлять, либо значение 0 в противном случае. Возвращает NULL, если не удалось определить, можно ли обновлять столбец.|  
|**is_computed_column**|**bit**|Возвращает значение 1, если столбец является вычисляемым столбцом, либо значение 0 в противном случае. Возвращает NULL, если не удается определить, является ли столбец вычисляемым столбцом.|  
|**is_sparse_column_set**|**bit**|Возвращает значение 1, если столбец является разреженным, и значение 0 в противном случае. Возвращает NULL, если не удалось определить, является ли столбец частью набора разреженных столбцов.|  
|**ordinal_in_order_by_list**|**smallint**|положение этого столбца в списке ORDER BY. Возвращает NULL, если столбец отсутствует в списке ORDER BY или если список ORDER BY нельзя определить однозначно.|  
|**order_by_list_length**|**smallint**|Длина списка ORDER BY. Возвращает NULL, если список ORDER BY отсутствует или если список ORDER BY нельзя однозначно определить. Обратите внимание на то, что это значение будет одним и тем же для всех строк, возвращаемых процедурой sp_describe_first_result_set.|  
|**order_by_is_descending**|**smallint NULL**|Если значение ordinal_in_order_by_list не равно NULL, **order_by_is_descending** столбец сообщает направление в предложении ORDER BY для этого столбца. В противном случае возвращается значение NULL.|  
|**error_number**|**int**|Содержит номер ошибки, возвращаемый этой функцией. Столбец будет содержать NULL, если не возникло ошибок.|  
|**error_severity**|**int**|Содержит серьезность ошибки, возвращаемую этой функцией. Столбец будет содержать NULL, если не возникло ошибок.|  
|**error_state**|**int**|Содержит сообщение о состоянии. возвращенное функцией. Столбец будет содержать NULL, если не возникло ошибок.|  
|**error_message**|**nvarchar(4096)**|Содержит сообщение, возвращаемое этой функцией. Столбец будет содержать NULL, если не возникло ошибок.|  
|**error_type**|**int**|Содержит целое число, представляющее возвращаемую ошибку. Соответствует error_type_desc. См. список под замечаниями.|  
|**error_type_desc**|**nvarchar(60)**|Содержит короткую строку в верхнем регистре, представляющую возвращаемую ошибку. Сопоставляется с error_type. См. список под замечаниями.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция использует тот же алгоритм, **sp_describe_first_result_set**. Дополнительные сведения см. в разделе [sp_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md).  
  
 В следующей таблице содержится список типов ошибок и их описания  
  
|error_type|error_type|Описание|  
|-----------------|-----------------|-----------------|  
|1|MISC|Все ошибки, которые не описаны иным образом.|  
|2|SYNTAX|В пакете возникла синтаксическая ошибка.|  
|3|CONFLICTING_RESULTS|Результат удалось определить из-за конфликта между двумя возможными первыми инструкциями.|  
|4|DYNAMIC_SQL|Результат не удалось определить из-за динамического SQL, который потенциально мог вернуть первый результат.|  
|5|CLR_PROCEDURE|Результат не удалось определить из-за того, что хранимая процедура CLR потенциально могла вернуть первый результат.|  
|6|CLR_TRIGGER|Результат не удалось определить из-за того, что триггер CLR потенциально мог вернуть первый результат.|  
|7|EXTENDED_PROCEDURE|Результат не удалось определить из-за того, что расширенная хранимая процедура потенциально могла вернуть первый результат.|  
|8|UNDECLARED_PARAMETER|Результат не удалось определить из-за того, что тип данных одного или более столбцов результирующего набора потенциально зависит от необъявленного параметра.|  
|9|RECURSION|Не удается определить результат, так как в пакете содержится рекурсивная инструкция.|  
|10|TEMPORARY_TABLE|Не удалось определить результат, так как пакет содержит временную таблицу и не поддерживается **sp_describe_first_result_set** .|  
|11|UNSUPPORTED_STATEMENT|Не удалось определить результат, так как пакет содержит инструкцию, которая не поддерживается **sp_describe_first_result_set** (FETCH, REVERT и т.д.).|  
|12|OBJECT_TYPE_NOT_SUPPORTED|\@Object_id, передаваемые функции не поддерживается (т. е. не является хранимой процедурой)|  
|13|OBJECT_DOES_NOT_EXIST|\@, Передаваемое функции object_id не найден в системном каталоге.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение на выполнение \@аргумент tsql.  
  
## <a name="examples"></a>Примеры  
 Дополнительные примеры из раздела [sp_describe_first_result_set &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) могут быть адаптированы к использованию **sys.dm_exec_describe_first_result_set**.  
  
### <a name="a-returning-information-about-a-single-transact-sql-statement"></a>A. Возврат сведений об отдельной инструкции Transact-SQL  
 Следующий код возвращает сведения о результатах инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_exec_describe_first_result_set  
(N'SELECT object_id, name, type_desc FROM sys.indexes', null, 0) ;  
```  
  
### <a name="b-returning-information-about-a-procedure"></a>Б. Возврат сведений о процедуре  
 В следующем примере создается хранимая процедура с именем pr_TestProc, которая возвращает два результирующих набора. Затем пример показывает, что **sys.dm_exec_describe_first_result_set** возвращает сведения о первом результирующем наборе в процедуре.  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE PROC Production.TestProc  
AS  
SELECT Name, ProductID, Color FROM Production.Product ;  
SELECT Name, SafetyStockLevel, SellStartDate FROM Production.Product ;  
GO  
  
SELECT * FROM sys.dm_exec_describe_first_result_set  
('Production.TestProc', NULL, 0) ;  
```  
  
### <a name="c-returning-metadata-from-a-batch-that-contains-multiple-statements"></a>В. Возврат метаданных из пакета, содержащего несколько инструкций  
 В следующем примере выполняется оценка пакета, содержащего две инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Результирующий набор описывает первый возвращенный результирующий набор.  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT * FROM sys.dm_exec_describe_first_result_set(  
N'SELECT CustomerID, TerritoryID, AccountNumber FROM Sales.Customer WHERE CustomerID = @CustomerID;  
SELECT * FROM Sales.SalesOrderHeader;',  
N'@CustomerID int', 0) AS a;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)   
 [sp_describe_undeclared_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)   
 [sys.dm_exec_describe_first_result_set_for_object &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md)  
  
  
