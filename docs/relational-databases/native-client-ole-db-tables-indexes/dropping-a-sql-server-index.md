---
title: Удаление индекса SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: efb206bda68421a8de81e0f1b03b541d839ef3cc
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429513"
---
# <a name="dropping-a-sql-server-index"></a>Удаление индекса SQL Server
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **IIndexDefinition::DropIndex** функции. Это позволяет клиентам для удаления индекса из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет некоторые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ограничения PRIMARY KEY и UNIQUE, что индексы. Владелец таблицы, владелец базы данных и члены некоторых административных ролей можно изменить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы, удаление ограничения. По умолчанию только владелец таблицы может удалять существующие индексы. Таким образом **DropIndex** об успехе или неудаче зависит не только от прав доступа пользователя приложения, но также к от указанного типа индекса.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде *pwszName* членом *uName* объединения в *pTableID* параметра. *EKind* членом *pTableID* должен быть равен DBKIND_NAME.  
  
 Пользователь задает имя индекса в виде символьной строки в Юникоде *pwszName* членом *uName* объединения в *pIndexID* параметра. *EKind* членом *pIndexID* должен быть равен DBKIND_NAME. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента не поддерживает функцию OLE DB удаления всех индексов в таблице при *pIndexID* имеет значение null. Если *pIndexID* имеет значение null, возвращается E_INVALIDARG.  
  
## <a name="see-also"></a>См. также  
 [Таблицы и индексы](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX (Transact-SQL)](../../t-sql/statements/drop-index-transact-sql.md)  
  
  
