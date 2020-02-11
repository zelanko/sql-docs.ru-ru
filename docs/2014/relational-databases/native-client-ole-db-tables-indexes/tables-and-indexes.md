---
title: Таблицы и индексы | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4f0b3fcf58f3f2767fbdc653327bec334545bdd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63213527"
---
# <a name="tables-and-indexes"></a>Таблицы и индексы
  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента предоставляет интерфейсы **IIndexDefinition** и **ITableDefinition** , позволяя потребителям создавать, изменять и удалять [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы и индексы. Допустимые определения таблиц и индексов зависят от версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Возможность создавать и удалять таблицы и индексы зависит от прав доступа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователя клиентского приложения. Удаление таблицы может быть еще более ограничено присутствием декларативного ограничения ссылочной целостности или другими факторами.  
  
 Большинство приложений нацелены [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на использование SQL-DMO вместо этих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерфейсов поставщика собственного клиента OLE DB. SQL-DMO — коллекция объектов OLE-автоматизации, которые поддерживают все административные функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Приложения, ориентированные на несколько поставщиков OLE DB, используют стандартные интерфейсы OLE DB, поддерживаемые различными поставщиками OLE DB.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет следующее свойство в специфическом для поставщика наборе свойств DBPROPSET_SQLSERVERCOLUMN.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|Тип: VT_BSTR<br /><br /> Чтение и запись.<br /><br /> По умолчанию: NULL<br /><br /> Описание: это свойство используется только в интерфейсе **ITableDefinition**. Строка, указанная в этом свойстве, используется при создании инструкции [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql).<br /><br /> .|  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание таблиц SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [Добавление столбца к таблице SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [Удаление столбца из таблицы SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [Удаление таблицы SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [Создание индексов SQL Server](../../relational-databases/indexes/indexes.md)  
  
-   [Удаление индекса SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [DROP TABLE &#40;&#41;Transact-SQL](/sql/t-sql/statements/drop-table-transact-sql)   
 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)   
 [DROP INDEX (Transact-SQL)](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
