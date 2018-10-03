---
title: Добавление столбца в таблицу SQL Server | Документация Майкрософт
description: Добавление столбца в таблицу SQL Server, с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- OLE DB Driver for SQL Server, columns
- adding columns
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 43e279a80bdddd8b34e570116dace51aac60c9ee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684722"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Добавление столбца к таблице SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server предоставляет **ITableDefinition::AddColumn** функции. Это позволяет пользователю добавить столбец в таблицу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 При добавлении столбца к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицу, драйвер OLE DB для SQL Server потребителя ограничен следующим образом:  
  
-   Если значение DBPROP_COL_AUTOINCREMENT равно VARIANT_TRUE, то значение DBPROP_COL_NULLABLE должно быть равно VARIANT_FALSE.  
  
-   Если столбец принадлежит к типу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **timestamp**, значение DBPROP_COL_NULLABLE должно быть равно VARIANT_FALSE.  
  
-   Для столбца любого другого типа DBPROP_COL_NULLABLE должно быть равно VARIANT_TRUE.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
 Имя столбца задается в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в элементе *dbcid* параметра *pColumnDesc* типа DBCOLUMNDESC. Элемент *eKind* должен быть равен DBKIND_NAME.  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и индексы](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md)  
  
  
