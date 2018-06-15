---
title: Таблицы и индексы | Документы Microsoft
description: Создание, изменение и droping таблиц и индексов, с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- OLE DB Driver for SQL Server, tables
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 5f6b4f1bde4b123ba2a8a807a5bd91abe12cdad2
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307723"
---
# <a name="tables-and-indexes"></a>Таблицы и индексы
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server предоставляет **IIndexDefinition** и **ITableDefinition** интерфейсов, что позволяет пользователям создавать, изменять и удалять [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблиц и индексов. Допустимые определения таблиц и индексов зависят от версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Возможность создавать и удалять таблицы и индексы зависит от прав доступа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] пользователя клиентского приложения. Удаление таблицы может быть еще более ограничено присутствием декларативного ограничения ссылочной целостности или другими факторами.  
  
 Большинство приложений, предназначенных для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать SQL-DMO вместо этих драйвер OLE DB для SQL Server интерфейсы. SQL-DMO — коллекция объектов OLE-автоматизации, которые поддерживают все административные функции [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Приложения, ориентированные на несколько поставщиков OLE DB, используют стандартные интерфейсы OLE DB, поддерживаемые различными поставщиками OLE DB.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] определяет следующее свойство в специфическом для поставщика наборе свойств DBPROPSET_SQLSERVERCOLUMN.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|Тип: VT_BSTR<br /><br /> Записи R Чтение и запись:<br /><br /> По умолчанию: значение Null<br /><br /> Описание: Это свойство используется только в **ITableDefinition**. Строка, указанная в это свойство используется при создании [CREATE TABLE](../../../t-sql/statements/create-table-transact-sql.md)<br /><br /> .|  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание таблиц SQL Server](../../oledb/ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [Добавление столбца в таблицу SQL Server](../../oledb/ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [Удаление столбца из таблицы SQL Server](../../oledb/ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [Удаление таблицы SQL Server](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [Создание индексов SQL Server](../../oledb/ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [Удаление индекса SQL Server](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для SQL Server программирования](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [DROP TABLE (Transact-SQL)](../../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX (Transact-SQL)](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
