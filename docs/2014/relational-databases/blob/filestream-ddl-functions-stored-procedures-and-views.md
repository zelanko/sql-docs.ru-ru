---
title: Инструкции DDL, функции, хранимые процедуры и представления для FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
ms.assetid: 9ecb49ee-f64e-4d30-a803-e4064a21950a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5fdcf6fbc7a7c9eb325d87a5eec838a5854664c9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66010129"
---
# <a name="filestream-ddl-functions-stored-procedures-and-views"></a>FILESTREAM DDL, функции, хранимые процедуры и представления
  Содержит список инструкций Transact-SQL и объектов базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поддерживающих FILESTREAM.  
  
 Список объектов базы данных, которые поддерживают функцию FileTable, см. в разделе [FileTable DDL, Functions, Stored Procedures, and Views](../views/views.md).  
  
##  <a name="ddl"></a> Инструкции языка описания данных (DDL) Transact-SQL  
  
-   [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql)  
  
-   [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)  
  
-   [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [DROP INDEX (Transact-SQL)](/sql/t-sql/statements/drop-index-transact-sql)DROP INDEX  
  
##  <a name="func"></a> Системные функции  
  
-   [GET_FILESTREAM_TRANSACTION_CONTEXT (Transact-SQL)](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql)  
  
-   [PathName (Transact-SQL)](/sql/relational-databases/system-functions/pathname-transact-sql)  
  
##  <a name="proc"></a> Системные хранимые процедуры  
  
-   [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [sp_filestream_force_garbage_collection (Transact-SQL)](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection)  
  
##  <a name="cat"></a> Системные представления — представления каталога  
  
-   [sys.database_filestream_options (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)  
  
##  <a name="dmv"></a> Системные представления — динамические административные представления  
  
-   [sys.dm_filestream_file_io_handles (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql)  
  
-   [sys.dm_filestream_file_io_requests (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql)  
  
##  <a name="api"></a> Программные API  
  
-   [Доступ к данным FILESTREAM с OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md)  
  
-   [Управляемый API — класс SqlFileStream](https://go.microsoft.com/fwlink/?LinkId=220875)  
  
  
