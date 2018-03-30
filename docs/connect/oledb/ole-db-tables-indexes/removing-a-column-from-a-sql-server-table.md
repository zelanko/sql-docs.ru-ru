---
title: Удаление столбца из таблицы SQL Server | Документы Microsoft
description: Удаление столбца из таблицы SQL Server с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- OLE DB Driver for SQL Server, columns
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4047c464ac1f2a27222f8d15160cbeaf75ba37c6
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Удаление столбца из таблицы SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server предоставляет **ITableDefinition::DropColumn** функции. Это позволяет пользователю удалить столбец из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в *pwszName*членом *uName* объединения в *pTableID* параметра. *EKind*членом *pTableID* должен быть равен DBKIND_NAME.  
  
 Пользователь задает имя столбца в *pwszName*членом *uName* объединения в *pColumnID* параметра. Имя столбца задается в виде символьной строки в Юникоде. *EKind* членом *pColumnID* должен быть равен DBKIND_NAME.  
  
## <a name="example"></a>Пример  
  
### <a name="code"></a>код  
  
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
  
## <a name="see-also"></a>См. также  
 [Таблицы и индексы](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
