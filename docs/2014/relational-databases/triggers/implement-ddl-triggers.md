---
title: Реализация триггеров DDL | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL triggers, implementing
ms.assetid: f44e5340-1d18-40e9-828e-0ffcca091ae3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8f62e0fe8bc1e0f2ed7fbb4cd48c6725cfb098d9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086534"
---
# <a name="implement-ddl-triggers"></a>Реализация триггеров DDL
  В этом разделе приведены сведения, необходимые для создания, изменения, выключения и удаления триггеров DDL.  
  
## <a name="creating-ddl-triggers"></a>Создание триггеров DDL  
 Триггеры DDL создаются при помощи инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER для триггеров DDL.  
  
 **Создание триггера DDL**  
  
-   [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql)  
  
> [!IMPORTANT]  
>  Возможность возвращать результирующие наборы из триггеров будет удалена в следующей версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Триггеры, возвращающие результирующие наборы, могут привести к непредвиденному поведению приложений, не предназначенных для работы с ними. Не используйте в разрабатываемых приложениях триггеры, возвращающие результирующие наборы, и запланируйте изменение приложений, которые используют их в настоящее время. Чтобы триггеры не возвращали результирующие наборы в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], задайте значение параметра [disallow results from triggers](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md) , равное 1. В будущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]для этого параметра по умолчанию будет задаваться значение 1.  
  
## <a name="modifying-ddl-triggers"></a>Изменение триггеров DDL  
 Если необходимо изменить определение триггера DDL, можно удалить и вновь создать триггер или переопределить существующий триггер одной инструкцией.  
  
 Если изменилось имя объекта, на который ссылается триггер DDL, текст триггера необходимо соответствующим образом изменить. Поэтому перед переименованием объекта вначале выведите зависимости объекта, чтобы определить, не повлияет ли предлагаемое изменение на работу каких-либо триггеров.  
  
 Может быть также зашифровано определение триггера.  
  
 **Изменение триггера**  
  
-   [ALTER TRIGGER (Transact-SQL)](/sql/t-sql/statements/alter-trigger-transact-sql)  
  
 **Просмотр зависимостей триггера**  
  
-   [Представление каталога sys.sql_expression_dependencies (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [Функция динамического управления sys.dm_sql_referenced_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [sys.dm_sql_referencing_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="disabling-and-dropping-ddl-triggers"></a>Отключение и удаление триггеров DDL  
 Если триггер DDL больше не нужен, он может быть отключен или удален.  
  
 Отключение триггера DDL не приводит к его удалению, Триггер все еще существует как объект в текущей базе данных. Однако этот триггер не будет срабатывать при выполнении инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , на которые он был запрограммирован. Отключенные триггеры DDL можно повторно включать. После включения триггер DDL вновь начинает срабатывать так, как это было указано при его создании. При создании триггеров DDL они включаются по умолчанию.  
  
 При удалении триггера DDL он удаляется из текущей базы данных. Удаление триггера DDL никоим образом не влияет на объекты или данные, на которые распространялась область действия триггера.  
  
 **Отключение триггера DDL**  
  
-   [DISABLE TRIGGER (Transact-SQL)](/sql/t-sql/statements/disable-trigger-transact-sql)  
  
-   [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)  
  
 **Включение триггера DDL**  
  
-   [ENABLE TRIGGER (Transact-SQL)](/sql/t-sql/statements/enable-trigger-transact-sql)  
  
-   [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)  
  
 **Удаление триггера DDL**  
  
-   [DROP TRIGGER (Transact-SQL)](/sql/t-sql/statements/drop-trigger-transact-sql)  
  
  
