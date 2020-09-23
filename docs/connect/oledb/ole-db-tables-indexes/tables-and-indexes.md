---
title: Таблицы и индексы (драйвер OLE DB)
description: Сведения об интерфейсах IIndexDefinition и ITableDefinition драйвера OLE DB, позволяющих объектам-получателям создавать, изменять и удалять таблицы и индексы SQL Server.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af39d73d6e542702f5798e07de78fb69fcfd0fda
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861863"
---
# <a name="tables-and-indexes"></a>Таблицы и индексы
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server предоставляет интерфейсы **IIndexDefinition** и **ITableDefinition**, позволяя потребителям создавать, изменять и удалять таблицы и индексы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Допустимые определения таблиц и индексов зависят от версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Возможность создавать и удалять таблицы и индексы зависит от прав доступа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] пользователя клиентского приложения. Удаление таблицы может быть еще более ограничено присутствием декларативного ограничения ссылочной целостности или другими факторами.  
  
 Большинство приложений, нацеленных на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], используют объекты SQL-DMO вместо этих интерфейсов OLE DB Driver for SQL Server. SQL-DMO — коллекция объектов OLE-автоматизации, которые поддерживают все административные функции [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Приложения, ориентированные на несколько поставщиков OLE DB, используют стандартные интерфейсы OLE DB, поддерживаемые различными поставщиками OLE DB.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] определяет следующее свойство в специфическом для поставщика наборе свойств DBPROPSET_SQLSERVERCOLUMN.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|Тип: VT_BSTR<br /><br /> Ч/З запись<br /><br /> Значение по умолчанию: NULL<br /><br /> Описание. Это свойство используется только в интерфейсе **ITableDefinition**. Строка, указанная в этом свойстве, используется при создании инструкции [CREATE TABLE](../../../t-sql/statements/create-table-transact-sql.md).<br /><br /> .|  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание таблиц SQL Server](../../oledb/ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [Добавление столбца в таблицу SQL Server](../../oledb/ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [Удаление столбца из таблицы SQL Server](../../oledb/ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [Удаление таблицы SQL Server](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [Создание индексов SQL Server](../../oledb/ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [Удаление индекса SQL Server](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>См. также:  
 [Программирование драйвера OLE DB для SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [DROP TABLE (Transact-SQL)](../../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX (Transact-SQL)](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
