---
title: FILESTREAM, функции, хранимые процедуры и представления | Документация Майкрософт
description: FILESTREAM работает с конкретными инструкциями Transact-SQL, API, функциями, хранимыми процедурами и представлениями. Узнайте, какие инструкции и объекты поддерживают FILESTREAM.
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
ms.assetid: 9ecb49ee-f64e-4d30-a803-e4064a21950a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fe2ed55cd68ee6852ab071a7ff8ca428150737d9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85642691"
---
# <a name="filestream-functions-stored-procedures-and-views"></a>FILESTREAM, функции, хранимые процедуры и представления
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Содержит список инструкций Transact-SQL и объектов базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поддерживающих FILESTREAM.  
  
 Список объектов базы данных, которые поддерживают функцию FileTable, см. в разделе [FileTable DDL, Functions, Stored Procedures, and Views](../../relational-databases/blob/filetable-ddl-functions-stored-procedures-and-views.md).  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> Инструкции языка описания данных (DDL) Transact-SQL  
  
-   [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
-   [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)  
  
-   [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
  
-   [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  
-   [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
  
-   [DROP INDEX (Transact-SQL)](../../t-sql/statements/drop-index-transact-sql.md)
  
##  <a name="system-functions"></a><a name="func"></a> Системные функции  
  
-   [GET_FILESTREAM_TRANSACTION_CONTEXT (Transact-SQL)](../../t-sql/functions/get-filestream-transaction-context-transact-sql.md)  
  
-   [PathName (Transact-SQL)](../../relational-databases/system-functions/pathname-transact-sql.md)  
  
##  <a name="system-stored-procedures"></a><a name="proc"></a> Системные хранимые процедуры  
  
-   [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
-   [sp_filestream_force_garbage_collection (Transact-SQL)](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)  
  
##  <a name="system-views---catalog-views"></a><a name="cat"></a> Системные представления — представления каталога  
  
-   [sys.database_filestream_options (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md)  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> Системные представления — динамические административные представления  
  
-   [sys.dm_filestream_file_io_handles (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql.md)  
  
-   [sys.dm_filestream_file_io_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql.md)  
  
##  <a name="programming-apis"></a><a name="api"></a> Программные API  
  
-   [Доступ к данным FILESTREAM с OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
-   [Управляемый API — класс SqlFileStream](https://go.microsoft.com/fwlink/?LinkId=220875)  
  
  
