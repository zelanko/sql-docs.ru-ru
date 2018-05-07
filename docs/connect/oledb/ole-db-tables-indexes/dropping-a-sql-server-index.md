---
title: Удаление индекса SQL Server | Документы Microsoft
description: Удаление индекса sql server с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 6c1ce25341ac4d5f092e61f2d8f23d1ea0baaade
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="dropping-a-sql-server-index"></a>Удаление индекса SQL Server

  Драйвер OLE DB для SQL Server предоставляет **IIndexDefinition::DropIndex** функции. Это позволяет пользователю удаления индекса из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы.  
  
 Драйвер OLE DB для SQL Server предоставляет некоторые [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ограничения PRIMARY KEY и UNIQUE, что индексы. Владелец таблицы, владелец базы данных и члены некоторых административных ролей можно изменить [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы, удаление ограничения. По умолчанию только владелец таблицы может удалять существующие индексы. Таким образом **DropIndex** об успешном или неуспешном зависит не только от прав доступа пользователя приложения но и от типа индекса.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в *pwszName* членом *uName* объединения в *pTableID* параметра. *EKind* членом *pTableID* должен быть равен DBKIND_NAME.  
  
 Пользователь задает имя индекса в виде символьной строки в Юникоде в *pwszName* членом *uName* объединения в *pIndexID* параметра. *EKind* членом *pIndexID* должен быть равен DBKIND_NAME. Драйвер OLE DB для SQL Server не поддерживает функцию OLE DB удаления всех индексов в таблице при *pIndexID* имеет значение null. Если *pIndexID* имеет значение null, возвращается E_INVALIDARG.  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и индексы](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX (Transact-SQL)](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
