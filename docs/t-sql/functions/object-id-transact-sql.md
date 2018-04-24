---
title: OBJECT_ID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- OBJECT_ID
- OBJECT_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], IDs
- identification numbers [SQL Server], database objects
- checking object exists
- IDs [SQL Server], database objects
- OBJECT_ID function
- database objects [SQL Server], IDs
- displaying object IDs
- viewing object IDs
- verifying object exists
ms.assetid: f89286db-440f-4218-a828-30881ce3077a
caps.latest.revision: 63
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5394da834fd6ec3b329b913663a7f5bfe7b862b8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="objectid-transact-sql"></a>OBJECT_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает идентификационный номер объекта базы данных для объекта области схемы.  
  
> [!IMPORTANT]  
>  Запросы на объекты, не относящиеся к области схемы, например триггеры DDL, не могут выполняться с использованием OBJECT_ID. Для объектов, не найденных в представлении каталога [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md), идентификационный номер проставляется с помощью запроса к соответствующему представлению каталога. Например, чтобы получить идентификационный номер триггера DDL, используйте инструкцию `SELECT OBJECT_ID FROM sys.triggers WHERE name = 'DatabaseTriggerLog``'`.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
OBJECT_ID ( '[ database_name . [ schema_name ] . | schema_name . ]   
  object_name' [ ,'object_type' ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 **'** *object_name* **'**  
 Объект, который должен использоваться. Аргумент *object_name* имеет тип **varchar** или **nvarchar**. Если значение *object_name* имеет тип **varchar**, оно неявно преобразовывается в тип **nvarchar**. Не обязательно указывать имена базы данных и схемы.  
  
 **'** *object_type* **'**  
 Объект области схемы. Аргумент *object_type* имеет тип **varchar** или **nvarchar**. Если значение *object_type* имеет тип **varchar**, оно неявно преобразовывается в тип **nvarchar**. Список типов объектов см. в столбце **type** представления [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
## <a name="exceptions"></a>Исключения  
 Для пространственного индекса функция OBJECT_ID возвращает значение NULL.  
  
 В случае ошибки возвращает значение NULL.  
  
 Пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые пользователю были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как OBJECT_ID, могут вернуть значение NULL в случае, если пользователь не имеет разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Remarks  
 Если параметр системной функции является необязательным, то предполагаются текущие база данных, главный компьютер, пользователь сервера или пользователь базы данных. За встроенными функциями всегда должны следовать круглые скобки.  
  
 Если указано имя временной таблицы, то имя базы данных должно стоять перед именем временной таблицы, если только текущей не является база данных **tempdb**. Например, `SELECT OBJECT_ID('tempdb..#mytemptable')`.  
  
 Системные функции можно использовать в списке выбора, в предложении WHERE и в любом месте, где разрешается использование выражений. Дополнительные сведения см. в статьях [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md) и [WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-object-id-for-a-specified-object"></a>A. Получение идентификатора указанного объекта  
 Следующий пример возвращает идентификатор объекта для таблицы `Production.WorkOrder` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE master;  
GO  
SELECT OBJECT_ID(N'AdventureWorks2012.Production.WorkOrder') AS 'Object ID';  
GO  
```  
  
### <a name="b-verifying-that-an-object-exists"></a>Б. Проверка существования объекта  
 Следующий пример проверяет существование указанной таблицы, проверяя наличие у таблицы идентификатора объекта. Если таблица существует, то она удаляется. Если таблица не существует, то инструкция `DROP TABLE` не выполняется.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'dbo.AWBuildVersion', N'U') IS NOT NULL  
DROP TABLE dbo.AWBuildVersion;  
GO  
```  
  
### <a name="c-using-objectid-to-specify-the-value-of-a-system-function-parameter"></a>В. Использование функции OBJECT_ID для указания параметра системной функции  
 В приведенном ниже примере возвращаются сведения для всех индексов и секций таблицы `Person.Address` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] с помощью функции [sys.dm_db_index_operational_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md).  
  
> [!IMPORTANT]  
>  При использовании для возврата значений параметров функций DB_ID и OBJECT_ID языка [!INCLUDE[tsql](../../includes/tsql-md.md)] необходимо убедиться в допустимости возвращаемого идентификатора. Если имя базы данных или объекта не может быть найдено, например если база данных или объект не существуют или неправильно записаны, то обе функции возвратят значение NULL. Функция **sys.dm_db_index_operational_stats** интерпретирует значение NULL как значение шаблона, соответствующее всем базам данных или все объектам. Так как эта операция может быть непреднамеренной, примеры в этом разделе демонстрируют безопасный способ определения идентификаторов базы данных и объекта.  
  
```  
DECLARE @db_id int;  
DECLARE @object_id int;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
IF @db_id IS NULL   
  BEGIN;  
    PRINT N'Invalid database';  
  END;  
ELSE IF @object_id IS NULL  
  BEGIN;  
    PRINT N'Invalid object';  
  END;  
ELSE  
  BEGIN;  
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);  
  END;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-returning-the-object-id-for-a-specified-object"></a>Г. Получение идентификатора указанного объекта  
 Следующий пример возвращает идентификатор объекта для таблицы `FactFinance` в базе данных [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].  
  
```  
SELECT OBJECT_ID('AdventureWorksPDW2012.dbo.FactFinance') AS 'Object ID';  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.dm_db_index_operational_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [OBJECT_DEFINITION (Transact-SQL)](../../t-sql/functions/object-definition-transact-sql.md)   
 [OBJECT_NAME (Transact-SQL)](../../t-sql/functions/object-name-transact-sql.md)  
  
  

