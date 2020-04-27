---
title: Поддержка Transact-SQL для выполняющейся в памяти OLTP | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1db4c6895fb499458c198008319302a25b8cd34b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63156226"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a>Поддержка Transact-SQL для In-Memory OLTP
  Доступ к оптимизированным для памяти таблицам можно получить с помощью любого запроса Transact-SQL или операции DML (SELECT, INSERT, UPDATE или DELETE), нерегламентированных пакетов и модулей SQL, таких как хранимые процедуры, функции, возвращающие табличное значение, триггеры и представления. Дополнительные сведения см. в разделе [доступ к оптимизированным для памяти таблицам с использованием интерпретированного языка Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).  
  
 Хранимые процедуры, которые ссылаются только на оптимизированные для памяти таблицы, могут быть скомпилированы в собственном коде и обычно предоставляют значительное повышение производительности по сравнению с интерпретируемыми хранимыми процедурами (на базе диска). Для оптимизации доступа к таблицам, оптимизированным для памяти, используйте хранимые процедуры, скомпилированные в собственном коде. Дополнительные сведения см. в статье [Хранимые процедуры, скомпилированные в собственном коде](natively-compiled-stored-procedures.md).  
  
 При создании и изменении объектов базы данных (инструкций DDL) были изменены следующие инструкции.  
  
-   [Параметры Alter Database File и Filegroup &#40;&#41;Transact-SQL](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (см `MEMORY_OPTIMIZED_DATA`.)  
  
-   [Создание &#40;базы данных SQL Server&#41;Transact-SQL](/sql/t-sql/statements/create-database-sql-server-transact-sql) ( `MEMORY_OPTIMIZED_DATA`см.)  
  
-   [CREATE PROCEDURE &#40;&#41;Transact-SQL](/sql/t-sql/statements/create-procedure-transact-sql) (см `NATIVE_COMPILATION`. `SCHEMABINDING`, `EXECUTE AS`, и `BEGIN ATOMIC`).  
  
-   [CREATE TABLE &#40;&#41;Transact-SQL](/sql/t-sql/statements/create-table-transact-sql) (см `MEMORY_OPTIMIZED`. `DURABILITY`, `BUCKET_COUNT` `INDEX`,, и `HASH`).  
  
-   [CREATE TYPE &#40;&#41;Transact-SQL](/sql/t-sql/statements/create-type-transact-sql) (см `MEMORY_OPTIMIZED`. `BUCKET_COUNT`, `INDEX`, и `HASH`).  
  
-   [DECLARE @local_variable &#40;&#41;TRANSACT-SQL](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (см `NULL`  |  `NOT NULL`.)  
  
 Таблицы, оптимизированные для памяти, поддерживают ограничения `PRIMARY KEY` и `NOT NULL`. Дополнительные сведения о реализации неподдерживаемых ограничений см. в разделе [Миграция ограничений проверки и внешнего ключа](../../database-engine/migrating-check-and-foreign-key-constraints.md).  
  
 Дополнительные сведения о неподдерживаемых компонентах см. в разделе [Конструкции языка Transact-SQL, не поддерживаемые в In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Поддерживаемые типы данных](supported-data-types-for-in-memory-oltp.md)  
  
-   [Доступ к таблицам, оптимизированным для памяти, с помощью интерпретируемых инструкций Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)  
  
-   [Системные представления, хранимые процедуры, динамические административные представления и типы ожидания для выполняющейся в памяти OLTP](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)  
  
## <a name="see-also"></a>См. также  
 [Выполняющаяся в памяти OLTP &#40;оптимизации в памяти&#41;](in-memory-oltp-in-memory-optimization.md)   
 [Проблемы миграции для хранимых процедур, скомпилированных в собственном виде](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Поддерживаемые функции SQL Server](unsupported-sql-server-features-for-in-memory-oltp.md)   
 [скомпилированные в собственном коде хранимые процедуры](natively-compiled-stored-procedures.md)  
  
  
