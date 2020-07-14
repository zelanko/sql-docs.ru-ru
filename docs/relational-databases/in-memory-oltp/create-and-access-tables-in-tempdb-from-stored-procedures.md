---
title: Создание таблиц в TempDB и доступ к ним из хранимых процедур
description: TempDB не поддерживает создание таблиц и обращение к ним из скомпилированных в собственном коде хранимых процедур. Используйте оптимизированные для памяти таблицы, либо табличные типы и табличные переменные.
ms.custom: seo-dt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 12be8011-b76c-45c1-8f55-7f46e0e374e9
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 60be5a470cffa69ab58251b57c1668ab5213a212
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723347"
---
# <a name="create-and-access-tables-in-tempdb-from-stored-procedures"></a>Создание таблиц в TempDB и доступ к ним из хранимых процедур
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Создание и обращение к таблицам в базе данных TempDB из скомпилированных в собственном коде хранимых процедур не поддерживается. Вместо этого используйте оптимизированные для памяти таблицы с параметром DURABILITY=SCHEMA_ONLY или табличные типы и переменные. 

Дополнительные сведения об оптимизации временных таблиц для памяти и табличных переменных см. в разделе: [Улучшение производительности временной таблицы и табличной переменной с помощью оптимизации памяти](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md).
  
  В следующем примере показано, как временную таблицу с тремя столбцами (id, ProductID, Quantity) можно заменить табличной переменной **\@OrderQuantityByProduct** типа **dbo.OrderQuantityByProduct**:  
  
```sql  
CREATE TYPE dbo.OrderQuantityByProduct   
  AS TABLE   
   (id INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=100000),   
    ProductID INT NOT NULL,   
    Quantity INT NOT NULL) WITH (MEMORY_OPTIMIZED=ON)  
GO  
CREATE PROCEDURE dbo.usp_OrderQuantityByProduct   
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = N'ENGLISH'  
)  
  -- declare table variables for the list of orders   
  DECLARE @OrderQuantityByProduct dbo.OrderQuantityByProduct  
  
  -- populate input  
  INSERT @OrderQuantityByProduct SELECT ProductID, Quantity FROM dbo.[Order Details]  
  end  
```  
  
## <a name="see-also"></a>См. также:  
 [Проблемы миграции, связанные с хранимыми процедурами, скомпилированными в собственном коде](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Конструкции языка Transact-SQL, не поддерживаемые в выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
