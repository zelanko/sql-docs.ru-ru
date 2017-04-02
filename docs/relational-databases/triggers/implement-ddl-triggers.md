---
title: "Реализация триггеров DDL | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-ddl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Триггеры DDL, реализация"
ms.assetid: f44e5340-1d18-40e9-828e-0ffcca091ae3
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Реализация триггеров DDL
  В этом разделе приведены сведения, необходимые для создания, изменения, выключения и удаления триггеров DDL.  
  
## Создание триггеров DDL  
 Триггеры DDL создаются при помощи инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER для триггеров DDL.  
  
 **Создание триггера DDL**  
  
-   [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)  
  
> [!IMPORTANT]  
>  Возможность возвращать результирующие наборы из триггеров будет удалена в следующей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Триггеры, возвращающие результирующие наборы, могут привести к непредвиденному поведению приложений, не предназначенных для работы с ними. Не используйте в разрабатываемых приложениях триггеры, возвращающие результирующие наборы, и запланируйте изменение приложений, которые используют их в настоящее время. Чтобы триггеры не возвращали результирующие наборы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], задайте значение параметра [disallow results from triggers](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md) , равное 1. В будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]для этого параметра по умолчанию будет задаваться значение 1.  
  
## Изменение триггеров DDL  
 Если необходимо изменить определение триггера DDL, можно удалить и вновь создать триггер или переопределить существующий триггер одной инструкцией.  
  
 Если изменилось имя объекта, на который ссылается триггер DDL, текст триггера необходимо соответствующим образом изменить. Поэтому перед переименованием объекта вначале выведите зависимости объекта, чтобы определить, не повлияет ли предлагаемое изменение на работу каких-либо триггеров.  
  
 Может быть также зашифровано определение триггера.  
  
 **Изменение триггера**  
  
-   [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)  
  
 **Просмотр зависимостей триггера**  
  
-   [Представление каталога sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
-   [Функция динамического управления sys.dm_sql_referenced_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)  
  
-   [sys.dm_sql_referencing_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)  
  
## Отключение и удаление триггеров DDL  
 Если триггер DDL больше не нужен, он может быть отключен или удален.  
  
 Отключение триггера DDL не приводит к его удалению, Триггер все еще существует как объект в текущей базе данных. Однако этот триггер не будет срабатывать при выполнении инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , на которые он был запрограммирован. Отключенные триггеры DDL можно повторно включать. После включения триггер DDL вновь начинает срабатывать так, как это было указано при его создании. При создании триггеров DDL они включаются по умолчанию.  
  
 При удалении триггера DDL он удаляется из текущей базы данных. Удаление триггера DDL никоим образом не влияет на объекты или данные, на которые распространялась область действия триггера.  
  
 **Отключение триггера DDL**  
  
-   [DISABLE TRIGGER (Transact-SQL)](../../t-sql/statements/disable-trigger-transact-sql.md)  
  
-   [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  
 **Включение триггера DDL**  
  
-   [ENABLE TRIGGER (Transact-SQL)](../../t-sql/statements/enable-trigger-transact-sql.md)  
  
-   [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  
 **Удаление триггера DDL**  
  
-   [DROP TRIGGER (Transact-SQL)](../../t-sql/statements/drop-trigger-transact-sql.md)  
  
  