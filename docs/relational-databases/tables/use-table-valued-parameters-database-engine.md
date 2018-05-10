---
title: Использование параметров, возвращающих табличные значения (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- table-valued parameters
- table-valued parameters, about table-valued parameters
- parameters [SQL Server], table-valued
- TVP See table-valued parameters
ms.assetid: 5e95a382-1e01-4c74-81f5-055612c2ad99
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ff370e7b4814397b067fd82c566fe809bc27e18a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="use-table-valued-parameters-database-engine"></a>Использование параметров, возвращающих табличные значения (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращающие табличные значения параметры объявляются с помощью определяемых пользователем табличных типов. Возвращающие табличные значения параметры можно использовать, чтобы отправить несколько строк данных в инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] или в процедуру, например хранимую процедуру или функцию, не создавая при этом временной таблицы или большого количества параметров.  
  
 Возвращающие табличные значения параметры похожи на массивы параметров в OLE DB и ODBC, но они обеспечивают большую гибкость и больше интегрированы с [!INCLUDE[tsql](../../includes/tsql-md.md)]. Преимуществом возвращающих табличные значения параметров также является возможность участия в операциях, основанных на наборах.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] передает возвращающие табличные значения параметры подпрограммам по ссылке, чтобы избежать создания копий входных данных. Можно создавать и выполнять процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] с возвращающими табличные значения параметрами и вызывать их из кода [!INCLUDE[tsql](../../includes/tsql-md.md)] , управляемых и собственных клиентов на любом управляемом языке.  
  
 **В этом разделе:**  
  
 [Преимущества](#Benefits)  
  
 [Ограничения](#Restrictions)  
  
 [Возвращающие табличные значения параметры и операции BULK INSERT](#BulkInsert)  
  
 [Пример](#Example)  
  
##  <a name="Benefits"></a> Преимущества  
 Область действия возвращающего табличное значение параметра такая же, как и у других параметров, — хранимая процедура, функция или динамический текст [!INCLUDE[tsql](../../includes/tsql-md.md)] . Аналогично область действия у переменной типа table точно такая же, как и у любой другой переменной, созданной с помощью инструкции DECLARE. Возвращающие табличные значения переменные можно объявлять в динамических инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] , а затем передавать эти переменные как возвращающие табличные значения параметры хранимым процедурам и функциям.  
  
 Возвращающие табличные значения параметры обеспечивают большую гибкость и в некоторых случаях более высокую производительность, чем временные таблицы или другие методы передачи списка параметров. Возвращающие табличные значения параметры имеют следующие преимущества.  
  
-   Не запрашивают блокировки для первичного заполнения данными от клиента.  
  
-   Предоставляют простую модель программирования.  
  
-   Позволяют включать в одиночную процедуру сложную бизнес-логику.  
  
-   Сокращают количество циклов приема-передачи с сервером.  
  
-   Могут иметь структуру таблицы с другим количеством элементов.  
  
-   Строго типизированы.  
  
-   Позволяют клиенту указать порядок сортировки и уникальные ключи.  
  
-   Кэшируются как временная таблица при использовании в хранимой процедуре. Начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], возвращающие табличное значение параметры также кэшируется для параметризированных запросов.  
  
##  <a name="Restrictions"></a> Ограничения  
 Возвращающие табличные значения параметры имеют следующие ограничения.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не ведет статистику столбцов возвращающих табличные значения параметров.  
  
-   Возвращающие табличные значения параметры должны передаваться процедурам [!INCLUDE[tsql](../../includes/tsql-md.md)] как входные параметры типа READONLY. Над возвращающими табличные значения параметрами, находящимися в теле процедуры, нельзя выполнять операции DML, такие как UPDATE, DELETE или INSERT.  
  
-   Возвращающий табличное значение параметр не может быть использован в качестве цели для инструкции SELECT INTO или INSERT EXEC. Возвращающий табличное значение параметр может присутствовать в предложении FROM инструкции SELECT INTO, в строке или хранимой процедуре INSERT EXEC.  
  
##  <a name="BulkInsert"></a> Возвращающие табличные значения параметры и Операции BULK INSERT  
 Использование возвращающих табличные значения параметров похоже на другие способы использования переменных, основанных на наборах. Однако применение возвращающих табличные значения параметров при работе с большими наборами данных часто позволяет добиться увеличения производительности. По сравнению с массовыми операциями, имеющими большие начальные затраты, возвращающие табличные значения параметры показывают хорошую производительность при вставке менее 1000 строк.  
  
 Возвращающие табличные значения параметры, используемые повторно, могут использовать кэширование временных таблиц. Это кэширование таблиц позволяет обеспечить лучшую масштабируемость, чем в эквивалентных операциях BULK INSERT. С помощью маленьких операций вставки строк можно добиться небольшого увеличения производительности, применяя списки параметров или пакетные инструкции вместо операций BULK INSERT или возвращающих табличные значения параметров. Однако эти методы сложнее программировать, а производительность быстро падает при увеличении количества строк.  
  
 Возвращающие табличные значения параметры работают также хорошо или даже лучше, чем эквивалентная реализация массива параметров.  
  
##  <a name="Example"></a> Пример  
 В следующем примере используется язык [!INCLUDE[tsql](../../includes/tsql-md.md)] и показывается, как создать тип возвращающего табличное значение параметра, объявить ссылающуюся на него переменную, заполнить список параметров, а затем передать значения хранимой процедуре.  
  
```  
USE AdventureWorks2012;  
GO  
  
/* Create a table type. */  
CREATE TYPE LocationTableType AS TABLE   
( LocationName VARCHAR(50)  
, CostRate INT );  
GO  
  
/* Create a procedure to receive data for the table-valued parameter. */  
CREATE PROCEDURE dbo. usp_InsertProductionLocation  
    @TVP LocationTableType READONLY  
    AS   
    SET NOCOUNT ON  
    INSERT INTO AdventureWorks2012.Production.Location  
           (Name  
           ,CostRate  
           ,Availability  
           ,ModifiedDate)  
        SELECT *, 0, GETDATE()  
        FROM  @TVP;  
        GO  
  
/* Declare a variable that references the type. */  
DECLARE @LocationTVP AS LocationTableType;  
  
/* Add data to the table variable. */  
INSERT INTO @LocationTVP (LocationName, CostRate)  
    SELECT Name, 0.00  
    FROM AdventureWorks2012.Person.StateProvince;  
  
/* Pass the table variable data to a stored procedure. */  
EXEC usp_InsertProductionLocation @LocationTVP;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)   
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [sys.types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)   
 [sys.parameters (Transact-SQL)](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)   
 [sys.parameter_type_usages (Transact-SQL)](../../relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql.md)   
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md)  
  
  
