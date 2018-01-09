---
title: "Удаление столбца из таблицы SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-tables-indexes
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- SQL Server Native Client OLE DB provider, columns
ms.assetid: 210811b7-cbd6-421e-bc6e-df9482236768
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b51237868e7431efcfe7e11031f6862f917022e4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Удаление столбца из таблицы SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **ITableDefinition::DropColumn** функции. Это позволяет пользователю удалить столбец из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в *pwszName*членом *uName* объединения в *pTableID* параметра. *EKind*членом *pTableID* должен быть равен DBKIND_NAME.  
  
 Пользователь задает имя столбца в *pwszName*членом *uName* объединения в *pColumnID* параметра. Имя столбца задается в виде символьной строки в Юникоде. *EKind* членом *pColumnID* должен быть равен DBKIND_NAME.  
  
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
 [Таблицы и индексы](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
