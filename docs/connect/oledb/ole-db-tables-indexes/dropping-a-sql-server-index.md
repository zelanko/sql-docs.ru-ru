---
title: Удаление индекса SQL Server | Документация Майкрософт
description: Удаление индекса sql server с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 990318037a3f1b35e311a983859507a364c52127
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47669172"
---
# <a name="dropping-a-sql-server-index"></a>Удаление индекса SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server предоставляет **IIndexDefinition::DropIndex** функции. Это позволяет потребителям удалять индексы из таблицы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Драйвер OLE DB для SQL Server предоставляет некоторые [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ограничения PRIMARY KEY и UNIQUE, что индексы. Владелец таблицы, владелец базы данных и члены некоторых административных ролей могут изменять таблицу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], удаляя ограничения. По умолчанию только владелец таблицы может удалять существующие индексы. Таким образом, будет ли функция **DropIndex** выполнена успешно или с ошибкой, зависит не только от прав доступа пользователя приложения, но также и от указанного типа индекса.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
 Потребитель задает имя индекса в виде строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pIndexID*. Элемент *eKind* параметра *pIndexID* должен быть равен DBKIND_NAME. Драйвер OLE DB для SQL Server не поддерживает функцию OLE DB удаления всех индексов таблицы, если значение параметра *pIndexID* равно NULL. Если значение параметра *pIndexID* равно NULL, то возвращается E_INVALIDARG.  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и индексы](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX (Transact-SQL)](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
