---
title: Получение сведений о триггерах DDL | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: triggers
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-ddl
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata [SQL Server], triggers
- status information [SQL Server], DDL triggers
- DDL triggers, metadata
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
caps.latest.revision: 31
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: cdd7d700e4e95a057f86e5c37ee3c730c17feb9e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="get-information-about-ddl-triggers"></a>Получение сведений о триггерах DDL
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
  Представления каталога, приведенные в этом разделе, можно использовать для получения сведений о триггерах DDL.  
  
 **Получение сведений о событиях или группах событий, при возникновении которых может сработать триггер DDL.**  
  
-   [sys.trigger_event_types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql.md)  
  
 **Просмотр зависимостей триггера**  
  
-   [Представление каталога sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
-   [Функция динамического управления sys.dm_sql_referenced_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)  
  
-   [sys.dm_sql_referencing_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)  
  
## <a name="database-scoped-ddl-triggers"></a>Триггеры DDL уровня базы данных  
 **Сведения о триггерах с областью действия на уровне базы данных**  
  
-   [sys.triggers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)  
  
 **Сведения о событиях базы данных, вызывающих срабатывание триггеров**  
  
-   [sys.trigger_events (Transact-SQL)](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)  
  
 **Определения триггеров уровня базы данных**  
  
-   [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)  
  
 **Сведения о триггерах среды CLR уровня базы данных**  
  
-   [sys.assembly_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)  
  
## <a name="server-scoped-ddl-triggers"></a>Триггеры DDL уровня сервера  
 **Сведения о триггерах с областью действия на уровне сервера**  
  
-   [sys.server_triggers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)  
  
 **Сведения о событиях сервера, вызывающих срабатывание триггеров**  
  
-   [sys.server_trigger_events (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)  
  
 **Определения триггеров с областью действия на уровне сервера**  
  
-   [sys.server_sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)  
  
 **Сведения о триггерах CLR с областью действия на уровне сервера**  
  
-   [sys.server_assembly_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Триггеры DDL](../../relational-databases/triggers/ddl-triggers.md)  
  
  
