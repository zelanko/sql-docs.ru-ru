---
title: Создание хранимых процедур, скомпилированных в собственном коде | Документация Майкрософт
description: Сведения о функциях Transact-SQL, поддерживаемых только для хранимых процедур, скомпилированных в собственном коде. Сведения о создании скомпилированных в собственном коде хранимых процедур в SQL Server.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e6b34010-cf62-4f65-bbdf-117f291cde7b
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fd6c808ecc53838feb9466283c83919231ce67ad
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537595"
---
# <a name="creating-natively-compiled-stored-procedures"></a>Создание хранимых процедур, скомпилированных в собственном коде
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Скомпилированные в собственном коде хранимые процедуры не реализуют полные возможности программирования [!INCLUDE[tsql](../../includes/tsql-md.md)] и контактную зону запросов. Некоторые конструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] не могут быть использованы внутри хранимых процедур, скомпилированных в собственном коде. Дополнительные сведения см. в разделе [Поддерживаемые функции для модулей, скомпилированных в собственном коде T-SQL](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
Следующие функции [!INCLUDE[tsql](../../includes/tsql-md.md)] поддерживаются только для хранимых процедур, скомпилированных в собственном коде.  
  
-   Блоки ATOMIC. Дополнительные сведения см. в статье [Atomic Blocks](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md).  
  
-   Ограничения `NOT NULL` для параметров и переменных. Нельзя присвоить значения **NULL** параметрам или переменным, объявленным как **NOT NULL**. Дополнительные сведения см. в статье [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md).  
  
    -   `CREATE PROCEDURE dbo.myproc (@myVarchar VARCHAR(32) NOT NULL) AS (...)`  
  
    -   `DECLARE @myVarchar VARCHAR(32) NOT NULL = "Hello"; -- Must initialize to a value.`  
  
    -   `SET @myVarchar = NULL; -- Compiles, but fails during run time.`  
  
-   Привязка к схеме хранимых процедур, скомпилированных в собственном коде.  
  
Скомпилированные в собственном коде хранимые процедуры создаются с помощью [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md). В следующем примере показаны оптимизированная для памяти таблица и скомпилированная в собственном коде хранимая процедура, используемая для вставки строк в таблицу.  
  
```sql  
CREATE TABLE [dbo].[T2] (  
  [c1] [int] NOT NULL, 
  [c2] [datetime] NOT NULL,
  [c3] nvarchar(5) NOT NULL, 
  CONSTRAINT [PK_T1] PRIMARY KEY NONCLUSTERED ([c1])  
  ) WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
CREATE PROCEDURE [dbo].[usp_2] (@c1 int, @c3 nvarchar(5)) 
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
)  
  DECLARE @c2 datetime = GETDATE();  
  INSERT INTO [dbo].[T2] (c1, c2, c3) values (@c1, @c2, @c3);  
END  
GO  
```  
 
В образце кода **NATIVE_COMPILATION** указывает, что данная хранимая процедура [!INCLUDE[tsql](../../includes/tsql-md.md)] представляет собой хранимую процедуру, скомпилированную в собственном коде. Требуются следующие параметры.  
  
|Параметр|Описание|  
|------------|-----------------|  
|**SCHEMABINDING**|Скомпилированная в собственном коде хранимая процедура должна быть привязана к схеме объектов, на которые она ссылается. Это означает, что таблицы, на которые ссылается процедура, не могут быть удалены. Таблицы, на которые имеются ссылки в процедуре, должны содержать имя схемы, а подстановочные знаки (\*) в запросах недопустимы (то есть не нужно использовать выражения наподобие `SELECT * from...`). Параметр**SCHEMABINDING** поддерживается только для хранимых процедур, скомпилированных в собственном коде, в этой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**BEGIN ATOMIC**|Тело хранимой процедуры, скомпилированной в собственном коде, должно представлять собой только один блок ATOMIC. Блоки ATOMIC гарантируют атомарное выполнение хранимой процедуры. Если процедура вызывается вне контекста активной транзакции, то запускает новую транзакцию, которая фиксируется после блока ATOMIC. Блоки ATOMIC в хранимых процедурах, скомпилированных в собственном коде, имеют два обязательных параметра:<br /><br /> **TRANSACTION ISOLATION LEVEL**. См. раздел [Уровни изоляции транзакций у оптимизированных для памяти таблиц](https://msdn.microsoft.com/library/8a6a82bf-273c-40ab-a101-46bd3615db8a) , содержащий описание поддерживаемых уровней изоляции.<br /><br /> **LANGUAGE**. Для хранимой процедуры необходимо назначить один из доступных языков или псевдонимов языка.|  
  
## <a name="see-also"></a>См. также:  
 [Скомпилированные в собственном коде хранимые процедуры](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
