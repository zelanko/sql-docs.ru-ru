---
title: Добавление столбца к таблице SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f6d5654db4b86995dcc38833afb514e707969f8d
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012960"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Добавление столбца к таблице SQL Server
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB Native Client предоставляет функцию **ITableDefinition:: addColumn** . Это позволяет пользователю добавить столбец в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При добавлении столбца в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребитель поставщика OLE DB собственного клиента ограничивается следующим образом:  
  
-   Если значение DBPROP_COL_AUTOINCREMENT равно VARIANT_TRUE, то значение DBPROP_COL_NULLABLE должно быть равно VARIANT_FALSE.  
  
-   Если столбец принадлежит к типу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp**, значение DBPROP_COL_NULLABLE должно быть равно VARIANT_FALSE.  
  
-   Для столбца любого другого типа DBPROP_COL_NULLABLE должно быть равно VARIANT_TRUE.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
 Имя столбца задается в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в элементе *dbcid* параметра *pColumnDesc* типа DBCOLUMNDESC. Элемент *eKind* должен быть равен DBKIND_NAME.  
  
## <a name="see-also"></a>См. также  
 [Таблицы и индексы](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
