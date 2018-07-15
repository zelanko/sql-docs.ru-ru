---
title: Инструкции DDL, функции, хранимые процедуры и представления для FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: filestream
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9ecb49ee-f64e-4d30-a803-e4064a21950a
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a99b40c77183e3c403409d47c211b7733e3235ae
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320424"
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
  
##  <a name="dmv"></a> Системные представления — динамические административные представления  
  
-   [sys.dm_filestream_file_io_handles (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql)  
  
-   [sys.dm_filestream_file_io_requests (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql)  
  
##  <a name="api"></a> Программные API  
  
-   [Доступ к данным FILESTREAM с OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md)  
  
-   [Управляемый API — класс SqlFileStream](http://go.microsoft.com/fwlink/?LinkId=220875)  
  
  
