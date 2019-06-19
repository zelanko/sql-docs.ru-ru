---
title: Перенос вычисляемых столбцов | Документация Майкрософт
ms.custom: ''
ms.date: 12/17/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 64a9eade-22c3-4a9d-ab50-956219e08df1
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 07e50f290d7e1e0a9202c1aaeae02d1dce76dbfa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65104419"
---
# <a name="migrating-computed-columns"></a>Перенос вычисляемых столбцов

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Вычисляемые столбцы не поддерживаются в оптимизированных для памяти таблицах. Однако вычисляемый столбец можно смоделировать.

Начиная с версии [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] вычисляемые столбцы поддерживаются в оптимизированных для памяти таблицах и индексах.

Должна быть определена необходимость сохранять вычисляемые столбцы при переносе таблиц на диске в таблицы, оптимизированные для памяти. Различные характеристики производительности таблиц, оптимизированных для памяти, и скомпилированных в собственной коде хранимых процедур могут поставить под сомнение необходимость сохранения.  
  
## <a name="non-persisted-computed-columns"></a>Несохраняемые вычисляемые столбцы  
 Для моделирования эффектов несохраняемого вычисляемого столбца можно создать представление на таблице, оптимизированной для памяти. В инструкции SELECT, определяющей представление, добавьте определение вычисляемого столбца в представление. За исключением скомпилированных в собственном коде хранимых процедур, запросы, в которых используются значения из вычисляемого столбца, должны читать данные из представления. Внутри скомпилированных в собственном коде хранимых процедур необходимо обновить все инструкции выборки, обновления и удаления в соответствии с определением вычисляемого столбца.  
  
```sql  
-- Schema for the table dbo.OrderDetails:  
-- OrderId int not null primary key,  
-- ProductId int not null,  
-- SalePrice money not null,  
-- Quantity int not null,  
-- Total money not null  
--  
-- Total is computed as SalePrice * Quantity and is not persisted.  
CREATE VIEW dbo.v_order_details AS  
   SELECT  
      OrderId,  
      ProductId,  
      SalePrice,  
      Quantity,  
      Quantity * SalePrice AS Total  
   FROM dbo.order_details  
```  
  
## <a name="persisted-computed-columns"></a>Материализованные вычисляемые столбцы  
 Для моделирования эффектов материализованного вычисляемого столбца создайте хранимую процедуру для вставки в таблицу и еще одну хранимую процедуру для обновления таблицы. При вставке или обновлении таблицы вызывайте для выполнения данных задач эти хранимые процедуры. Внутри хранимых процедур вычисляйте значения для вычисляемых полей в соответствии с входными данными аналогично определению вычисляемого столбца в исходной таблице на диске. Затем вставляйте данные или обновляйте таблицу по мере необходимости внутри хранимой процедуры.  
  
```sql  
-- Schema for the table dbo.OrderDetails:  
-- OrderId int not null primary key,  
-- ProductId int not null,  
-- SalePrice money not null,  
-- Quantity int not null,  
-- Total money not null  
--  
-- Total is computed as SalePrice * Quantity and is persisted.  
-- we need to create insert and update procedures to calculate Total.  

CREATE PROCEDURE sp_insert_order_details   
@OrderId int, @ProductId int, @SalePrice money, @Quantity int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (LANGUAGE = N'english', TRANSACTION ISOLATION LEVEL = SNAPSHOT)  

-- compute the value here.   
-- this stored procedure works with single rows only.  
-- for bulk inserts, accept a table-valued parameter into the stored procedure  
-- and use an INSERT INTO SELECT statement.  

DECLARE @total money = @SalePrice * @Quantity  
INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)  
VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
@OrderId int, @ProductId int, @SalePrice money, @Quantity int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (LANGUAGE = N'english', TRANSACTION ISOLATION LEVEL = SNAPSHOT)  

-- compute the value here.   
-- this stored procedure works with single rows only.  

DECLARE @total money = @SalePrice * @Quantity  
UPDATE dbo.OrderDetails   
SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
WHERE OrderId = @OrderId  
END  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Миграция в In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
