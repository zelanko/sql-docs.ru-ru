---
title: "Поддержка Transact-SQL для выполняющейся в памяти OLTP | Документация Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
caps.latest.revision: 52
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cc975fbbdb4118158e4beacef63f45a63c479d38
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="transact-sql-support-for-in-memory-oltp"></a>Поддержка Transact-SQL для In-Memory OLTP
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] содержат параметры синтаксиса для поддержки выполняющейся в памяти OLTP:  
  
-   [Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md) (добавлен **MEMORY_OPTIMIZED_DATA**)  
  
-   [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)  
  
-   [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md) (добавлен **MEMORY_OPTIMIZED_DATA**)  
  
-   [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)  
  
-   [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
  
-   [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)  
  
-   [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)  
  
-   [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
    В скомпилированной в собственном коде хранимой процедуре можно объявить такую переменную, как **NOT NULL**. Это невозможно сделать в обычной хранимой процедуре.  
  
 **AUTO_UPDATE_STATISTICS** может иметь значение **ON** для таблиц, оптимизированных для памяти, начиная с SQL Server 2016. Дополнительные сведения см. в разделе [sp_autostats (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md).  
  
 [SET STATISTICS XML (Transact-SQL)](../../t-sql/statements/set-statistics-xml-transact-sql.md) ON не поддерживается для скомпилированных в собственном коде хранимых процедур.  
  
 Дополнительные сведения о неподдерживаемых компонентах см. в разделе [Конструкции языка Transact-SQL, не поддерживаемые в In-Memory OLTP](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
 Сведения о поддерживаемых конструкциях в скомпилированных в собственном коде хранимых процедурах см. в разделах [Поддерживаемые функции для модулей, скомпилированных в собственном коде T-SQL](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md) и [Поддерживаемые конструкции DDL для модулей, скомпилированных в собственном коде T-SQL](../../relational-databases/in-memory-oltp/supported-ddl-for-natively-compiled-t-sql-modules.md).  
  
## <a name="see-also"></a>См. также:  
 [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)   
 [Проблемы миграции, связанные с хранимыми процедурами, скомпилированными в собственном коде](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Неподдерживаемые функции SQL Server для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md)   
 [Скомпилированные в собственном коде хранимые процедуры](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
