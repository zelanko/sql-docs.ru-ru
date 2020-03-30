---
title: Пример настройки массового копирования
description: Описание таблиц, используемых в примерах с массовым копированием, и примеры скриптов SQL для создания таблиц в базе данных AdventureWorks.
ms.date: 09/30/2019
dev_langs:
- sql
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 4b156f3f9deeb6f74393631555c0fc8ad0e9acf2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "78897039"
---
# <a name="bulk-copy-example-setup"></a>Пример настройки массового копирования

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Класс <xref:Microsoft.Data.SqlClient.SqlBulkCopy> можно использовать для записи данных только в таблицы SQL Server. В примерах кода в этом разделе используется образец базы данных SQL Server **AdventureWorks**. Чтобы не допустить изменения существующих таблиц, примеры кода записывают данные в таблицы, которые сначала необходимо создать.  
  
Таблицы **BulkCopyDemoMatchingColumns** и **BulkCopyDemoDifferentColumns** основаны на таблице **AdventureWorks** **Production.Products**. В примерах кода, использующих эти таблицы, данные из таблицы **Production.Products** добавляются к одной из этих таблиц-образцов. Таблица **BulkCopyDemoDifferentColumns** используется для демонстрации сопоставления столбцов из источника данных с целевой таблицей. Таблица **BulkCopyDemoMatchingColumns** используется в большинстве других примеров.  
  
Некоторые примеры кода демонстрируют использование одного класса <xref:Microsoft.Data.SqlClient.SqlBulkCopy> для записи в несколько таблиц. В этих примерах в качестве целевых таблиц применяются **BulkCopyDemoOrderHeader** и **BulkCopyDemoOrderDetail**. Эти таблицы основаны на таблицах **Sales.SalesOrderHeader** и **Sales.SalesOrderDetail** из базы данных **AdventureWorks**.  
  
> [!NOTE]
>  Образцы кода **SqlBulkCopy** предоставляются только для демонстрации синтаксиса применения **SqlBulkCopy**. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL `INSERT … SELECT` для копирования данных.  
  
## <a name="table-setup"></a>Настройка таблицы  
Чтобы создать таблицы, необходимые для правильной работы примеров кода, выполните следующие инструкции Transact-SQL в базе данных SQL Server.  
  
```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Операции массового копирования в SQL Server](bulk-copy-operations-sql-server.md)
