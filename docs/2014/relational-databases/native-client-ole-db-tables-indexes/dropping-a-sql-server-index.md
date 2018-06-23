---
title: Удаление индекса SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 38e103cd19950846dd9c88d0b4bdc0d5d385ba1f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097953"
---
# <a name="dropping-a-sql-server-index"></a>Удаление индекса SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **IIndexDefinition::DropIndex** функции. Это позволяет пользователю удаления индекса из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет некоторые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ограничения PRIMARY KEY и UNIQUE, что индексы. Владелец таблицы, владелец базы данных и члены некоторых административных ролей можно изменить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы, удаление ограничения. По умолчанию только владелец таблицы может удалять существующие индексы. Таким образом **DropIndex** об успешном или неуспешном зависит не только от прав доступа пользователя приложения но и от типа индекса.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в *pwszName* членом *uName* объединения в *pTableID* параметра. *EKind* членом *pTableID* должен быть равен DBKIND_NAME.  
  
 Пользователь задает имя индекса в виде символьной строки в Юникоде в *pwszName* членом *uName* объединения в *pIndexID* параметра. *EKind* членом *pIndexID* должен быть равен DBKIND_NAME. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента не поддерживает функцию OLE DB удаления всех индексов в таблице при *pIndexID* имеет значение null. Если *pIndexID* имеет значение null, возвращается E_INVALIDARG.  
  
## <a name="see-also"></a>См. также  
 [Таблицы и индексы](tables-and-indexes.md)   
 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)   
 [DROP INDEX (Transact-SQL)](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
