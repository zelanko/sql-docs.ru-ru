---
title: Удаление столбца из таблицы SQL Server | Документация Майкрософт
description: Удаление столбца из таблицы SQL Server с помощью OLE DB Driver for SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- OLE DB Driver for SQL Server, columns
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 7e367c1b0664b0b43007db3a465dcbec0ffa90d9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993987"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Удаление столбца из таблицы SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server предоставляет функцию **ITableDefinition::DropColumn**. Она позволяет пользователю удалить столбец из таблицы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
 Пользователь задает имя столбца в элементе *pwszName* объединения *uName*, передаваемого в параметре *pColumnID*. Имя столбца задается в виде символьной строки в Юникоде. Элемент *eKind* параметра *pColumnID* должен быть равен DBKIND_NAME.  
  
## <a name="example"></a>Пример  
  
### <a name="code"></a>Код  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и индексы](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
